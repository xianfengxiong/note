# AOP相关

### 1.Spring中对标记为@PostConstruct的方法进行AOP增强失败

2.Spring的AOP是通过代理实现，当其他IOC容器里的Bean注入该Bean时，实际上是注入的代理类，例如

`public class UserController {`

```java
// 这里的userService实际上是一个代理类，并不是原始的UserService
@Autowired
private UserService userService;
```

```
public void addUser(){
    userService.addUser();
}
```

`}`

