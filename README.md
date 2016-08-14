# 一个简单的TableViewCell动画

##效果展示
![image](https://github.com/ySssssssss/-TableViewCell-/blob/master/cell.gif)

##核心代码
```objective-c
#pragma mark - 代理方法
- (void)tableView:(UITableView *)tableView willDisplayCell:(UITableViewCell *)cell forRowAtIndexPath:(NSIndexPath *)indexPath{
    
    //配置transform
    CATransform3D transform;
    transform = CATransform3DMakeRotation((90 * M_PI) / 180, 0.0, 0.7, 0.4);
    transform.m34 = 1.0 / -600;
    
    //定义cell的初始状态
    cell.layer.shadowColor = [UIColor blackColor].CGColor;
    cell.layer.shadowOffset = CGSizeMake(10, 10);
    cell.alpha = 0;
    
    cell.layer.transform = transform;
    cell.layer.anchorPoint = CGPointMake(0, 0.5);
    
    //定义cell的最后状态,并提交动画
    [UIView beginAnimations:@"transform" context:nil];
    [UIView setAnimationDuration:0.5];
    
    cell.layer.transform = CATransform3DIdentity;
    cell.alpha = 1;
    cell.layer.shadowOffset = CGSizeMake(0, 0);
    cell.frame = CGRectMake(0, cell.frame.origin.y, cell.frame.size.width, cell.frame.size.height);
    
    [UIView commitAnimations];
}
```
