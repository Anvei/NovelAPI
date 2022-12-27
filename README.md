## NovelAPI
提供常见小说网站以及App的便捷API

#### API支持

1. SfacgAPI-APP（菠萝包轻小说）
2. HbookerAPI-APP（刺猬猫阅读）
3. BiqumuAPI-Website（http://www.biqumu.com/）
4. _143xsAPI-Website（https://www.147xs.org/）

#### 关于jar包

所有jar包在release文件夹下（打包的jar包内包含了gson、jsoup依赖）

#### 下载API的使用

- 获取一个DownloadTask实例

```java
DownloadTask downloadTask = DownloadTasks.getDownloadTask(NovelSource.Sfacg);
```

- 配置下载参数DownloadParams

```java
DownloadParams params = new DownloadParams();
// 文件将保存在该目录下
params.parent = new File("E:\\Text File\\Novel");
// 文件名
params.fileName = "咸鱼少女拒绝翻身.txt";
// sfacg小说ID
params.novelId = 233718;
// 多线程并行请求章节内容,开启后下载速度较快，但是对服务器造成的压力较大
params.multiThreadOn = true;									
```

- 下载小说

```java
downloadTask.startDownload(params);			// 开始下载
boolean res = downloadTask.waitFinished();	// 等待下载任务结束
System.out.println("Download success: " + res);
System.out.println("Status message: " + downloadTask.getStatusMsg());
```

#### SfacgAPI的使用

1. 模拟登录

```java
SfacgAPI api = new SfacgAPI("username", "password");
api.login();
```

2. 获取当前账号详细信息

```java
AccountJson info = api.getAccountJson();
```

3. 获取章节列表信息

```java
ChapListJson chapListJson = api.getChapListJson(591785);
```

4. 获取章节内容（支持vip章节：需要登录账号并且账号已经购买过vip章节）

```java
ChapContentJson chapContentJson = api.getChapContentJson(6742076);
```

5. 关键字搜索

```java
SearchResultJson searchResultJson = api.search("来自深渊");
```

#### 其他文档

其他文档在doc文件夹下

 
