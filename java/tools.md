## Java 涉及的工具有如下
appletviewer	javac		jcmd		jjs		jstack		orbd		schemagen	wsimport
extcheck	javadoc		jconsole	jmap		jstat		pack200		serialver	xjc
idlj		javafxpackager	jdb		jmc		jstatd		policytool	servertool
jar		javah		jdeps		jps		jvisualvm	rmic		tnameserv
jarsigner	javap		jhat		jrunscript	keytool		rmid		unpack200
java		javapackager	jinfo		jsadebugd	native2ascii	rmiregistry	wsgen

## jps 查看java进程

查看 Hotspot虚拟 的java进程
```
jps
41552 RemoteMavenServer36
40741
41980 Launcher
41981 Demo
41998 Jps
```

## jstack 查看进程中线程调用栈

```
jstack 42140
2019-12-12 16:58:39
Full thread dump Java HotSpot(TM) 64-Bit Server VM (25.221-b11 mixed mode):

"Attach Listener" #12 daemon prio=9 os_prio=31 tid=0x00007fe7d2868800 nid=0x4e0b waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Service Thread" #11 daemon prio=9 os_prio=31 tid=0x00007fe7d301b000 nid=0x3c03 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C1 CompilerThread2" #10 daemon prio=9 os_prio=31 tid=0x00007fe7d4052000 nid=0x3b03 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C2 CompilerThread1" #9 daemon prio=9 os_prio=31 tid=0x00007fe7d4051800 nid=0x4503 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"C2 CompilerThread0" #8 daemon prio=9 os_prio=31 tid=0x00007fe7d3885000 nid=0x4603 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"JDWP Command Reader" #7 daemon prio=10 os_prio=31 tid=0x00007fe7d3018800 nid=0x4803 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"JDWP Event Helper Thread" #6 daemon prio=10 os_prio=31 tid=0x00007fe7d3833000 nid=0x3703 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"JDWP Transport Listener: dt_socket" #5 daemon prio=10 os_prio=31 tid=0x00007fe7d2832800 nid=0x4907 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Signal Dispatcher" #4 daemon prio=9 os_prio=31 tid=0x00007fe7d3002800 nid=0x3403 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

"Finalizer" #3 daemon prio=8 os_prio=31 tid=0x00007fe7d2820800 nid=0x3003 in Object.wait() [0x000070000a74e000]
   java.lang.Thread.State: WAITING (on object monitor)
        at java.lang.Object.wait(Native Method)
        - waiting on <0x00000007bf988ed8> (a java.lang.ref.ReferenceQueue$Lock)
        at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:144)
        - locked <0x00000007bf988ed8> (a java.lang.ref.ReferenceQueue$Lock)
        at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:165)
        at java.lang.ref.Finalizer$FinalizerThread.run(Finalizer.java:216)

"Reference Handler" #2 daemon prio=10 os_prio=31 tid=0x00007fe7d3009800 nid=0x5303 in Object.wait() [0x000070000a64b000]
   java.lang.Thread.State: WAITING (on object monitor)
        at java.lang.Object.wait(Native Method)
        - waiting on <0x00000007bf986c00> (a java.lang.ref.Reference$Lock)
        at java.lang.Object.wait(Object.java:502)
        at java.lang.ref.Reference.tryHandlePending(Reference.java:191)
        - locked <0x00000007bf986c00> (a java.lang.ref.Reference$Lock)
        at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:153)

"main" #1 prio=5 os_prio=31 tid=0x00007fe7d3003800 nid=0x2703 waiting on condition [0x000070000a039000]
   java.lang.Thread.State: TIMED_WAITING (sleeping)
        at java.lang.Thread.sleep(Native Method)
        at demo.Demo.main(Demo.java:15)

"VM Thread" os_prio=31 tid=0x00007fe7d382b800 nid=0x2f03 runnable

"GC task thread#0 (ParallelGC)" os_prio=31 tid=0x00007fe7d3006800 nid=0x1e07 runnable

"GC task thread#1 (ParallelGC)" os_prio=31 tid=0x00007fe7d3802800 nid=0x2003 runnable

"GC task thread#2 (ParallelGC)" os_prio=31 tid=0x00007fe7d3804000 nid=0x2b03 runnable

"GC task thread#3 (ParallelGC)" os_prio=31 tid=0x00007fe7d3804800 nid=0x2d03 runnable

"VM Periodic Task Thread" os_prio=31 tid=0x00007fe7d3023800 nid=0x3d03 waiting on condition

JNI global references: 1424

```

## jhat heap dump 分析工具

命令运行后开启http服务用于查看转储文件内容
```
jhat java_pid41707.hprof
Reading from java_pid41707.hprof...
Dump file created Thu Dec 12 16:22:22 CST 2019
Snapshot read, resolving...
Resolving 816081 objects...
Chasing references, expect 163 dots...................................................................................................................................................................
Eliminating duplicate references...................................................................................................................................................................
Snapshot resolved.
Started HTTP server on port 7000
Server is ready.
```

## jmap jvm内存转储 (jdk 11的jmap更不容易出问题)

```
jmap -dump:live,format=b,file=heap.bin 42602
Heap dump file created
```

(待补充)
