

## 定时任务

```java
// 周一到周五 整秒执行
@Scheduled(cron = "0 * * * * MON-FRI")

// 这些0,1,2,3,4,5秒执行
@Scheduled(cron = "0,1,2,3,4,5 * * * * MON-FRI")

// 这些30-40秒区间执行
@Scheduled(cron = "30-40 * * * * MON-FRI")

// 步长执行方式 每10秒执行一次
@Scheduled(cron = "*/50 * * * * MON-FRI")
public void process() {
  System.out.println("process....");
}
```

