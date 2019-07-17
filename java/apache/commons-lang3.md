# commons-lang3

### Tag
```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
</dependency>
```

### Version - 3.8
##### Problem 1
Chinese parsing problem, Chinese returns unicode when I use the following method
```java
public static class TestJsonStyle{
    private String a;
    public void setA(String a){
        this.a = a;
    }
    @Override
    public String toString() {
        return ReflectionToStringBuilder.toString(this, ToStringStyle.JSON_STYLE);
    }
}

public static void main(String[] args) {
    TestJsonStyle jsonStyle = new TestJsonStyle();
    jsonStyle.setA("测试");
    System.out.println(jsonStyle.toString());
    //{"a":"\u6D4B\u8BD5"}
}
```
* Solving Methods
    * Solution 1
    ``` xml
    <!-- update commons-lang3 version to 3.7 -->
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
        <version>3.7</version>
    </dependency>
    ``` 
* GitHub Issues(If you have)
    * [test issues address](./commons-lang3.md)
