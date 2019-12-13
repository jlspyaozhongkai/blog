### Java OOM 验证

```
* VM Args: -Xms20m -Xmx20m -XX:+HeapDumpOnOutOfMemoryError
* */
public class Demo {
   public static void main(String[] args) {
       List<DemoObject> list = new ArrayList<DemoObject>();

       while(true) {
           list.add(new DemoObject());
       }
   }
   static class DemoObject {

   }
}
```
运行得到dump文件 java_pid41707.hprof

```
file java_pid41707.hprof
java_pid41707.hprof: Java HPROF dump, created Thu Dec 12 08:22:22 2019
```

jhat可分析此文件，并且开了个http服务来查看具体
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
