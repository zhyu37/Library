=======
##SDWebImage 远程图片下载
>SDWebImage这个库提供来自web的远程图片的UIimageview的支持。
<p>提供的功能
<pre>
1. UIImageView类获取web图片并缓存到Cocoa Touch framework。
2. 异步图片下载。
3. 异步记忆和磁盘映像缓存自动缓存过期处理。
4. GIF图片支持。
5. web格式支持。
6. 背景图片压缩。
7. 确保相同URL不会被下载。
8. 确保错误的URL不会重复下载。
9. 确保主线程不会被堵塞。
10. 性能好。
11. 使用GCD和ARC。
12. 支持Arm64.
</pre>
<p>用法
<pre>
1. 远程图片下载+图片缓存
<code>
//头文件  #import <SDWebImage/UIImageView+WebCache.h>
//webImage+默认Image
[UIImageView sd_setImageWithURL:[NSURL URLWithString:@"http://www.domain.com/path/to/image.jpg"]
                      placeholderImage:[UIImage imageNamed:@"placeholder.png"]];
</code>
2. 通过Blocks,可以返回下载进度。
<code>
[cell.imageView sd_setImageWithURL:[NSURL URLWithString:@"http://www.domain.com/path/to/image.jpg"]
                      placeholderImage:[UIImage imageNamed:@"placeholder.png"]
                             completed:^(UIImage *image, NSError *error, SDImageCacheType cacheType, NSURL *imageURL) {
                                ... completion code here ...
                             }];
</code>
3. SDWebImageManager
//你能直接使用这个作用在别的UIView上面
<code>
SDWebImageManager *manager = [SDWebImageManager sharedManager];
[manager downloadImageWithURL:imageURL
                      options:0
                     progress:^(NSInteger receivedSize, NSInteger expectedSize) {
                         // progression tracking code
                     }
                     completed:^(UIImage *image, NSError *error, SDImageCacheType cacheType, BOOL finished, NSURL *imageURL) {
                         if (image) {
                             // do something with image
                         }
                     }];
</code>
</pre>
<p>https://github.com/rs/SDWebImage