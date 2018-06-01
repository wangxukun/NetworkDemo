# NetworkDemo
Android实现网络下载
代码中的事件序列如下：
1. Activity启动一个NetworkFragment并传入一个指定的URL。
2. 当一个用户触发Activity的downloadData()方法，NetworkFragment执行DownloadTask。
3. AsyncTask上的onPreExecute()方法首先运行（在UI线程），并在设备未连接到网络时取消该任务。
4. 然后AsyncTask上的doInBackground()方法在后台线程上运行并调用downloadUrl()方法。
5. downloadUrl()方法将URL字符串作为参数，并使用HttpsURLConnection对象将Web内容作为InputStream获取。
6. InputStream传递给readStream()方法，该方法将流转换为字符串。
7. 最后，一旦后台工作完成，AsyncTask的onPostExecute()方法将在UI线程上运行，并使用DownloadCallback将结果作为字符串发送回UI。
