##FFmpegTest
###利用 FFmpeg 做的一个视频播放的demo<br>
###支持各种视频格式播放（mp4/avi/rmvb/3gp/mov/flv/m3u8/rm）支持远程视频播放以及本地视频播放
- 图片展示<br>
![image](https://raw.githubusercontent.com/gaoyuhang/FFmpegTest/master/photo/1.png)
![image](https://raw.githubusercontent.com/gaoyuhang/FFmpegTest/master/photo/2.png)

##代码
```objc
   - (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath
{
    NSString *path;
    NSMutableDictionary *parameters = [NSMutableDictionary dictionary];
    
    if (indexPath.section == 0) {
        if (indexPath.row >= _remoteMovies.count) return;
        path = _remoteMovies[indexPath.row];
    } else {
        if (indexPath.row >= _localMovies.count) return;
        path = _localMovies[indexPath.row];
    }

    if ([path.pathExtension isEqualToString:@"wmv"])
        parameters[KxMovieParameterMinBufferedDuration] = @(5.0);

    if (UI_USER_INTERFACE_IDIOM() == UIUserInterfaceIdiomPhone)
        parameters[KxMovieParameterDisableDeinterlacing] = @(YES);

    KxMovieViewController *vc = [KxMovieViewController movieViewControllerWithContentPath:path
                                                                               parameters:parameters];
    [self presentViewController:vc animated:YES completion:nil];

}


