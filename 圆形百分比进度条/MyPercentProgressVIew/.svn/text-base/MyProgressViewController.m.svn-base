//
//  MyProgressViewController.m
//  Extension
//
//  Created by Megatron on 1/20/15.
//  Copyright (c) 2015 Megatron. All rights reserved.
//

#import "MyProgressViewController.h"
#import "RoundProgressBar.h"

// 当前设备屏幕的宽高
#define SCREEN_HEIGHT [[UIScreen mainScreen] bounds].size.height
#define SCREEN_WIDTH [[UIScreen mainScreen] bounds].size.width

@interface MyProgressViewController ()
{
    RoundProgressBar *_myBar;
    RoundProgressBar *_myBarTwo;
    NSTimer *_myTimer;
    float _lastNum;
}
@end

@implementation MyProgressViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    _lastNum = 0;
    
    _myBar = [[RoundProgressBar alloc] initWithFrame:CGRectMake(0, 0, 150, 150)];
    _myBar.center = CGPointMake(SCREEN_WIDTH * 0.5, SCREEN_HEIGHT * 0.5);
    _myBar.myRadius = 50;
    _myBar.circleWidth = 10;
    _myBar.backgroundColor = [UIColor clearColor];
    [_myBar setNormalColorWithRGBValueR:181 G:181 B:181 andFinishedColorWithRGBValueR:41 G:194 B:248];
    [self.view addSubview:_myBar];
    self.view.backgroundColor = [UIColor whiteColor];
    
    _myBarTwo = [[RoundProgressBar alloc] initWithFrame:CGRectMake(0, 0, 50, 50)];
    _myBarTwo.center = CGPointMake(SCREEN_WIDTH * 0.5, SCREEN_HEIGHT * 0.5 + 150);
    _myBarTwo.myRadius = 20;
    _myBarTwo.circleWidth = 5;
    _myBarTwo.backgroundColor = [UIColor clearColor];
    [_myBarTwo setNormalColorWithRGBValueR:181 G:181 B:181 andFinishedColorWithRGBValueR:41 G:194 B:248];
    [self.view addSubview:_myBarTwo];
    self.view.backgroundColor = [UIColor whiteColor];
    
    _myTimer = [NSTimer scheduledTimerWithTimeInterval:0.2 target:self selector:@selector(changeState) userInfo:nil repeats:YES];
    
    UITapGestureRecognizer *tap = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(myTapAction:)];
    [self.view addGestureRecognizer:tap];
}

-(void)myTapAction:(UITapGestureRecognizer *)gesture
{
    _lastNum = 0;
}

- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

-(void)changeState
{
    _lastNum = _lastNum + 0.01;
    [_myBar changeStateWithPercentage:_lastNum];
    [_myBarTwo changeStateWithPercentage:_lastNum];
}

@end
