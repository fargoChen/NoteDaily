# NoteDaily

第版本android手机发现如下问题
Logs:

java.lang.VerifyError: com/test/android/MainActivity
	at java.lang.Class.newInstanceImpl(Native Method)
	at java.lang.Class.newInstance(Class.java:1130)
	at android.app.Instrumentation.newActivity(Instrumentation.java:1061)
	at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2141)
	at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2279)
	at android.app.ActivityThread.access$600(ActivityThread.java:144)
	at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1269)
	at android.os.Handler.dispatchMessage(Handler.java:99)
	at android.os.Looper.loop(Looper.java:137)
	at android.app.ActivityThread.main(ActivityThread.java:5215)
	at java.lang.reflect.Method.invokeNative(Native Method)
	at java.lang.reflect.Method.invoke(Method.java:525)
	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:760)
	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:576)
	at dalvik.system.NativeStart.main(Native Method)
	
	推测原因:
	MainActivity 中声明的类型，低版本手机未找到对应API，加载不成功。
