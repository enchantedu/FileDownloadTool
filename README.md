# FileDownloadTool
1.use NSURLSession to realize the download

2.can strat, suspend, restart the download

3.Use LPFileDownloadManager to manager your download


How to use？


1.Your model which saves the download file must confirm the Protocal:LPFileDownloadProtocal



2.Use LPFileDownloadManager to manager you download 



3.Realize LPFileDownloadManagerDelegate 

  //开始下载
- (void)fileDownloadManagerStartDownload:(LPFileDownloadOperation *)downloadOperation;

//下载过程，更新进度
- (void)fileDownloadManagerUpdateProgress:(LPFileDownloadOperation *)downloadOperation didReceiveData:(uint64_t)receiveLength progress:(NSString *)progress downloadSpeed:(NSString *)downloadSpeed;

//下载完成，包括成功和失败
- (void)fileDownloadManagerFinishDownload:(LPFileDownloadOperation *)downloadOperation onSuccess:(BOOL)downloadSucces error:(NSError *)error didFinishDownloadingToURL:(NSURL *)location;



4.add your model to the LPFileDownloadManagerstart to downloading a file

添加一个下载
    LPDownloadModel <LPFileDownloadProtocal>*downloadModel = [LPDownloadModel new];

[[LPFileDownloadManager sharedFileDownloadManager] addDownloadWithModel:downloadModel];

暂停下载

  [[LPFileDownloadManager sharedFileDownloadManager] suspendDownloadWithModel:downModel];

恢复下载

 [[LPFileDownloadManager sharedFileDownloadManager] recoverDownloadWithModel:downModel];
