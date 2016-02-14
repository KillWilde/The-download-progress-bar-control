//
//  RoundProgressBar.h
//  Extension
//
//  Created by Megatron on 1/20/15.
//  Copyright (c) 2015 Megatron. All rights reserved.
//

#import <UIKit/UIKit.h>

@interface RoundProgressBar : UIView

@property (assign,nonatomic) float myRadius;             // 进度条的半径
@property (assign,nonatomic) BOOL showWord;              // default is YES
@property (assign,nonatomic) float circleWidth;          // 进度条宽度

-(void)changeStateWithPercentage:(float)num;             // 下载进度改变时调用，传入0-1之间的数
-(void)setNormalColorWithRGBValueR:(int)r11 G:(int)g11 B:(int)b11 andFinishedColorWithRGBValueR:(int)r22 G:(int)g22 B:(int)b22;    // 设置进度条正常颜色和完成颜色

@end
