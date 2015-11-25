+++
title = "Android C2DM client 예제"
date = 2011-12-09T04:56:00Z
updated = 2015-11-20T10:25:55Z
categories = ["C2DM", "Push", "Android"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++
[파이썬으로 c2dm서버 만들기]:(/blog/2011/12/09/python으로-c2dm-server-만들기)
준비물 : c2dm account([파이썬으로 c2dm서버 만들기] 포스팅 참조)

만들 예제의 패키지 구조.  
![](http://4.bp.blogspot.com/-f9hw88JM4MU/TuHeizYCzYI/AAAAAAAADnE/_8JG2D4Tc50/s320/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA+2011-12-09+%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE+7.10.00.png)

우선 Manifest file의 Code.  
```
<manifest android:versioncode="1" android:versionname="1.0" package="com.leehack.c2dmtest" xmlns:android="http://schemas.android.com/apk/res/android">
    <uses-sdk android:minsdkversion="14">
        <application android:icon="@drawable/ic_launcher" android:label="@string/app_name">
            <activity android:label="@string/app_name" android:name=".C2DM_TESTActivity">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN">
                        <category android:name="android.intent.category.LAUNCHER"></category>
                    </action>
                </intent-filter>
            </activity>
            
            <!-- Only C2DM servers can send messages for the app. If permission is not set - any other app can generate it -->
            <receiver android:name=".push.C2DMReceiver" android:permission="com.google.android.c2dm.permission.SEND">
                <!-- Receive the actual message -->
                <intent-filter>
                    <action android:name="com.google.android.c2dm.intent.RECEIVE">
                        <category android:name="com.leehack.c2dmtest"></category>
                    </action>
                </intent-filter>
                <!-- Receive the registration id -->
                <intent-filter>
                    <action android:name="com.google.android.c2dm.intent.REGISTRATION">
                        <category android:name="com.leehack.c2dmtest">
                        </category>
                    </action>
                </intent-filter>
            </receiver>
        </application>
        <!-- Only this application can receive the messages and registration result -->
        <permission android:name="com.leehack.c2dmtest.permission.C2D_MESSAGE" android:protectionlevel="signature">
            <uses-permission android:name="com.leehack.c2dmtest.permission.C2D_MESSAGE"></uses-permission>
            <!-- This app has permission to register and receive message -->
            <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE"></uses-permission>
        </permission>
    </uses-sdk>
</manifest>
```

C2DMReceiver.java: 리시버 작성.  
```
package com.leehack.c2dmtest.push;
import android.app.Activity;
import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.content.SharedPreferences;
import android.util.Log;
import android.view.Gravity;
import android.widget.Toast;
public class C2DMReceiver extends BroadcastReceiver
{
    static String registration_id = null;
    private Context mContext;
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent.getAction().equals("com.google.android.c2dm.intent.REGISTRATION")) {
            handleRegistration(context, intent);
        } else if (intent.getAction().equals("com.google.android.c2dm.intent.RECEIVE")) {
        	//서버에 등록이 되면 Registration_id를 C2DM서버에서 보내준다. 받은 이 ID를 별도로 구성한 서버에 보내야 한다.
            handleMessage(context, intent);
        }
    }
    private void handleRegistration(Context context, Intent intent) {
        String registration = intent.getStringExtra("registration_id");
        if (intent.getStringExtra("error") != null) {
        	// Registration failed, should try again later.
        } else if (intent.getStringExtra("unregistered") != null) {
            registration = null;
        } else if (registration != null) {
            registration_id = registration;
            mContext = context;
            SharedPreferences sp  = mContext.getSharedPreferences("com.leehack.c2dmtest", Activity.MODE_PRIVATE);
            SharedPreferences.Editor ed = sp.edit();
            ed.putString("registration_id", registration_id);
            ed.commit();
            Toast toast = Toast.makeText(context, "Registration Id\n" + registration_id, Toast.LENGTH_LONG);
            toast.setGravity(Gravity.TOP | Gravity.CENTER, 0, 150);
            toast.show();
            Log.d("C2DMReceiver", "c2dm registered");
        }
    }
    //메세지가 도착하면 토스트로 도착한 메세지를 보여줌
    private void handleMessage(Context context, Intent intent) {
        String c2dm_msg = intent.getExtras().getString("msg");
        System.out.println("c2dm_msg======>" + c2dm_msg);
        Toast toast = Toast.makeText(context, "c2dmMessage\n" + c2dm_msg, Toast.LENGTH_LONG);
        toast.setGravity(Gravity.TOP | Gravity.CENTER, 0, 150);
        toast.show();
    }
}
```

PushHelper.java: c2dm 서버에 Register/Unregister 메소드 작성.  
```
package com.leehack.c2dmtest.push;
import android.app.Activity;
import android.app.PendingIntent;
import android.content.Context;
import android.content.Intent;
import android.content.SharedPreferences;
public class PushHelper {
	final static String c2dmDevId = "c2dm에 등록한 account";
	public static void c2dmRegister(Context context){
		SharedPreferences sp  = context.getSharedPreferences("com.leehack.c2dmtest", Activity.MODE_PRIVATE);
		if(sp.getString("registration_id", null) != null)
			return;
		Intent registrationIntent = new Intent(
			"com.google.android.c2dm.intent.REGISTER");
		registrationIntent.putExtra("app",
			PendingIntent.getBroadcast(context, 0, new Intent(), 0));
		registrationIntent.putExtra("sender", c2dmDevId);
		context.startService(registrationIntent);
	}
	public static void c2dmUnregister(Context context){
		Intent unregIntent = new Intent("com.google.android.c2dm.intent.UNREGISTER");
		unregIntent.putExtra("app", PendingIntent.getBroadcast(context, 0, new Intent(), 0));
		context.startService(unregIntent);
	}
}
```

C2DM_TESTActivity.java: Register와 Unregister버튼의 동작을 정의

```
package com.leehack.c2dmtest;
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import com.leehack.c2dmtest.push.PushHelper;

public class C2DM_TESTActivity extends Activity {
	/** Called when the activity is first created. */
	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.main);
		findViewById(R.id.button1).setOnClickListener(new OnClickListener() {
			@Override
			public void onClick(View v) {
			// TODO Auto-generated method stub
			PushHelper.c2dmRegister(C2DM_TESTActivity.this);
			}
		});
		findViewById(R.id.button2).setOnClickListener(new OnClickListener() {
			@Override
			public void onClick(View v) {
				// TODO Auto-generated method stub
				PushHelper.c2dmUnregister(C2DM_TESTActivity.this);
			}
		});
	}
}
```

앞으로 해야 할일!.  
1. 구글의 C2DM과 통신한 Push Server 구성.  
2. Register를 한 후 C2DMReceiver를 통해 C2DM 서버로 부터 전달받은 Registration_ID를 구성한 Push Server로 전달하는 로직 구성.  
    ([파이썬으로 c2dm서버 만들기] 포스팅을 참조하면 1번은 해결될 것이고 2번만 추가로 구성하면 된다)
