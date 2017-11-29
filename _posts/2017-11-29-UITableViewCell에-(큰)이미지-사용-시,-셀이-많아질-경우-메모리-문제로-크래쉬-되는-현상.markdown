---
layout: objc-swift
title: UITableViewCell 에 (큰)이미지 사용 시, 셀이 많아질 경우 메모리 문제로 크래쉬 되는 현상
date: 2017-11-29 15:50:37 +0900
categories: blog,jekyll,github
author: Maven Lim
---
# 문제점

UITableViewCell에 큰 이미지, 혹은 많은 이미지를 사용하는 경우 Cell 갯수가 많아질 때 메모리문제로 크래쉬가 일어난다.
단순히 UITableView의 Reuse가 메모리를 알아서 관리해줄 것으로 기대하고 있지만, UITableView Reuse의 역할은, 화면에 안보이는 셀을 화면에서 제거한 후, 이를 메모리에 보관했다가 해당 Row가 다시 보여질 때 빠르게 그리는 용도이다. 따라서, Cell에 붙은 이미지들 역시 모두 메모리상에 사라지지 않고 존재하고 있으므로, 많은 Row수, 또는 이미지 크기로 인해 사용된 메모리가 임계치를 초과하는 경우 앱이 크래쉬된다.

# 해결방법

UITableView에 다음과 같은 Delegate Method가 존재한다.

{% highlight objective-c %}
- (void)tableView:(UITableView *)tableView didEndDisplayingCell:(UITableViewCell *)cell forRowAtIndexPath:(NSIndexPath *)indexPath
{% endhighlight %}

Cell이 화면 밖으로 나갈 때 호출되며, 인자로 해당 Cell이 전달된다. 이 메소드가 호출될 때, 즉 Cell이 화면에 보이지 않을 때 이미지를 임시로 제거하여 가용메모리를 확보한다.



# 사용예시

## CustomTableCell.m
{% highlight objective-c %}
- (id)initWithStyle:(UITableViewCellStyle)style reuseIdentifier:(NSString *)reuseIdentifier imageURL:(NSString *)imageURL
{
     self = [super initWithStyle:style reuseIdentifier:reuseIdentifier];
     if (self) {
          // imageURL을 멤버변수에 보관
          _imageURLString = [[NSString alloc] initWithString:imageURL];

          // 이미지 뷰 역시 멤버변수로 갖는다.
          _thumbnailImageView = [[UIImageView alloc] initWithFrame:CGRectMake(10, 8, 88, 88)];
          [self addSubview:_thumbnailImageView];
     }
     return self;
}

- (void)attachImage
{
     [[SDWebImageManager sharedManager] downloadWithURL:[NSURL URLWithString:_imageURLString]
                                                options:0
                                               progress:nil
                                              completed:^(UIImage *image, NSError *error, SDImageCacheType cacheType, BOOL finished) {
                                                   if (!error) {
                                                        [_thumbnailImageView setImage:image];
                                                   } else {
                                                        NSLog(@"error: %@", error);
                                                   }
                                              }];
}

- (void)detachImage
{
     [_thumbnailImageView setImage:nil];
}
{% endhighlight %}

## ParentViewController.m
{% highlight objective-c %}
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
     NSString *cellId = [NSString stringWithFormat:@"Cell_%ld", indexPath.row];

     CustomTableCell *cell = [tableView dequeueReusableCellWithIdentifier:cellId];
     if (!cell) {
          cell = [[CustomTableCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:cellId imageURL:dataArray[indexPath.row]];
     }
     [cell attachImage];

     return cell;
}

- (void)tableView:(UITableView *)tableView didEndDisplayingCell:(UITableViewCell *)cell forRowAtIndexPath:(NSIndexPath *)indexPath
{
     if ([tableView.indexPathsForVisibleRows indexOfObject:indexPath] == NSNotFound) {
          if ([cell isKindOfClass:[CustomTableCell class]]) {
                CustomTableCell *tCell = (CustomTableCell *)cell;
                [tCell detachImage];
          }
 }
{% endhighlight %}

# 비고

이미지는 화면에 보일때마다 새로 그리는것이기 때문에, 해당 이미지가 로컬이 아닌 서버에 존재하는 경우 Cell이 새로 그려질때 마다 다운로드 딜레이가 생길 수 있다. 예시에서 사용한 SDWebImage 같은 라이브러리를 쓸 경우, 앱이 살아있는 동안 다운로드 받은 이미지가 기기에 캐쉬어있기 때문에 두번 째 요청부터는 로컬 이미지를 사용하여 다운로드에 발생되는 딜레이를 없앨 수 있다.

{% include short_profile_maven.html %}