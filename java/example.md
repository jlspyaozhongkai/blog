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
