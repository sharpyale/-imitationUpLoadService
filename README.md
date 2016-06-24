# 测试项目,模拟后台压缩图片.压缩完毕后后整体提交数据

实现原理: <br>
1.提交数据时,将数据存放到任务表,并通知Service<br>
2.service 接收到数据后,创建任务,加入任务栈中,本事例中使用SingleThreadExecutor的特性,来作为顺序执行的任务栈,用于提交整体数据(压缩过的图片数据,和其他信息数据)<br>
3.使用FixedThreadPool管理压缩图片线程.<br>
4.使用CountDownLatch 控制压缩图片线程执行完毕后在整体提交数据,需要注意的是CountDown的size 一定要和图片的数量相等,否者会出现问题<br>
