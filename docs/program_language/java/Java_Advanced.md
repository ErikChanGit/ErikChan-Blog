# Java 高级用法

## CallBack

- 定义一个接口作为 callback

```JavaScript
public interface CallbackWash {
  void wash();
}
```

- 实现 callback

```JavaScript
// 实现再煮完之后要洗碗
static void cooking(String food, CallbackWash callback) {
  try {
      System.out.println("Cooking "+food);
      Boolean result = future.get();
      System.out.println("result "+result);
      callback.wash();
    } catch (Exception e) {
      e.printStackTrace();
    }
}
```

- 调用 callback

```JavaScript
// 具体实现再调用的时候决定， 实现之前可以获取之前的结果作为参数
cooking("egg", new CallbackWash() {
      @Override
      public void wash() {
        System.out.println("Wash bowl...");
      }
});
```

## Try-with-resource

try-catch-finally 需要自己关闭资源，当打开了大量资源时，将会导致需要一个个关闭，使得代码量庞大。

try-with-resource 可以自动关闭打开的资源。

**用法：**

```JavaScript
try(
  InputStream fis = new FileInputStream(sourceFile);
            BufferedInputStream bis = new BufferedInputStream(fis, bufferSize);
            ) {
            int len = bis.available();
            b = new byte[len];
            bis.read(b, 0, len);
)
```