//
//  RoundProgressBar.m
//  Extension
//
//  Created by Megatron on 1/20/15.
//  Copyright (c) 2015 Megatron. All rights reserved.
//

#import "RoundProgressBar.h"

@interface RoundProgressBar ()
{
    CGPoint _myCenter;        // 圆圈中心
    CGPoint _lastPoint;       // 最后一次的绘制点
    float _currentState;      // 当前的进度
    UILabel *_lab;            // 当前进度
    int _r1;
    int _g1;
    int _b1;
    int _r2;
    int _g2;
    int _b2;
}
@end

@implementation RoundProgressBar

-(id)initWithFrame:(CGRect)frame
{
    self = [super initWithFrame:frame];
    if (self) {
        _myCenter = CGPointMake(frame.size.width * 0.5, frame.size.height * 0.5);
        _currentState = 0.0;
        self.showWord = YES;
    }
    return self;
}

-(void)drawRect:(CGRect)rect
{
    // 是否使用数字显示进度
    if (self.showWord == YES) {
        if (_lab == nil) {
            float w = sqrt(_myRadius * _myRadius * 2);
            _lab = [[UILabel alloc] initWithFrame:CGRectMake(0, 0, 2*w, w)];
            _lab.center = _myCenter;
            _lab.textAlignment = NSTextAlignmentCenter;
            _lab.backgroundColor = [UIColor clearColor];
            UIFont *font = [UIFont boldSystemFontOfSize:w / 2];
            _lab.font = font;
            [self addSubview:_lab];
        }
        NSString *str = [NSString stringWithFormat:@"%f",_currentState  * 100];
        if ((_currentState * 100) >= 10) {
            if (_currentState * 100 < 100) {
                str = [str substringWithRange:NSMakeRange(0, 2)];
            }
            else
            {
                str = @"100";
            }
        }
        else
        {
            str = [str substringWithRange:NSMakeRange(0, 1)];
        }
        str = [NSString stringWithFormat:@"%@%%",str];
        _lab.text = str;
    }
    
    CGPoint point1 = CGPointMake(_myCenter.x + sin(0) * _myRadius, _myCenter.y - cos(0) * _myRadius);
    if (_currentState == 0) {
        [self drawLineFromStartPoint:point1 andCenter:_myCenter andPercentage:1 andRGBColorR:_r1 G:_g1 B:_b1 andWidth:10 andRadius:_myRadius];
    }
    else
    {
        [self drawLineFromStartPoint:point1 andCenter:_myCenter andPercentage:1 andRGBColorR:_r1 G:_g1 B:_b1 andWidth:10 andRadius:_myRadius];
        // 准备完成的颜色
        [self drawLineFromStartPoint:point1 andCenter:_myCenter andPercentage:_currentState andRGBColorR:_r2 G:_g2 B:_b2 andWidth:10 andRadius:_myRadius];
    }
    
}

-(void)drawLineFromStartPoint:(CGPoint)point1 andCenter:(CGPoint)point2 andPercentage:(float)p andRGBColorR:(int)r G:(int)g B:(int)b andWidth:(float)width andRadius:(float)radius
{
    CGContextRef context = UIGraphicsGetCurrentContext();
    CGContextSetRGBStrokeColor(context, r/255.0, g/255.0, b/255.0, 1);
    CGContextSetLineWidth(context, self.circleWidth);
    CGContextMoveToPoint(context, point1.x, point1.y);     // 绘制起始点
    for (int i = 0; i <= (360 * p); i ++) {
        CGContextAddLineToPoint(context, point2.x + sin(i / 360.0 * 2 * M_PI) * radius, point2.y - cos(i / 360.0 * 2 * M_PI) * radius);
    }
    CGContextStrokePath(context);
}

// 刷新状态
-(void)changeStateWithPercentage:(float)num
{
    _currentState = num;
    if (num > 1.5) {
        return;
    }
    [self setNeedsDisplay];
}

-(void)setNormalColorWithRGBValueR:(int)r11 G:(int)g11 B:(int)b11 andFinishedColorWithRGBValueR:(int)r22 G:(int)g22 B:(int)b22
{
    _r1 = r11;
    _g1 = g11;
    _b1 = b11;
    _r2 = r22;
    _b2 = b22;
    _g2 = g22;
}

@end
