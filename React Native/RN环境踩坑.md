### 安装RN中遇到的深坑

#### 1. unable to load script from assets 'index.android bundle' 红萍报错
```text
<font color='red'>unable to load script from assets 'index.android bundle',
make sure your bundle is packaged correctly or youu're runing a packager server</font>
```
    第一步，先在工作目录创建：android/app/src/main 目录下创建一个  assets空文件夹
    第二步，运行命令 (ps:我也不知道这段是啥意思)
```text
react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/
```
    第三步，运行
```text
react-native run-android命令即可
```
