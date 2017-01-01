# AOP相关

### 1.Spring中对标记为@PostConstruct的方法进行AOP增强失败

2.Spring的AOP是通过代理实现，当其他IOC容器里的Bean注入该Bean时，实际上是注入的代理类，例如

```
public class UserContrller {
    // 这里的userService实际上是一个代理类，并不是原始的UserService
    @Autowired
    private UserService userService;
    public void addUser(){
        // 这里AOP会起作用，使用增强，因为userService是代理类
        userService.addUser();
    }
}
```



```
@Service
public class UserService {
    public void addUser(){
        // 这里并不会AOP增强，因为selectUser()就是this.selectUser()
        // this并不是代理类，所以方法内部自己调用并不会使用AOP增强
        selectUser();
        System.out.println("user service add user");
    }

    public void selectUser(){
        System.out.println("select user");
    }
}
```

```
@Aspect
public class UserAspect {
    @PointCut("* cn.wanru.user.service.*(..)")
    public void servicePointCut(){}
    @before("servicePointCut()")
    public void beforeAdvice(PointCut pointCut){
        System.out.println("before增强");
    }
}
```













