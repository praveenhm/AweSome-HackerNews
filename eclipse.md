
# eclipse.ini

-startup
plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_1.0.200.v20090519
-product
com.springsource.sts.ide
--launcher.XXMaxPermSize
384M
-vm
C:/Dev-Praveen/Jdk_1.6.20/bin/javaw.exe
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms128m
-Xmx768m
-Xss4m
-XX:MaxPermSize=256m
-XX:MaxPermSize=384m
-XX:CompileThreshold=5
-XX:MaxGCPauseMillis=10
-XX:MaxHeapFreeRatio=70
-XX:+UseConcMarkSweepGC
-XX:+CMSIncrementalMode
-XX:+CMSIncrementalPacing
-Dcom.sun.management.jmxremote
