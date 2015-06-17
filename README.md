# FTMoreApps

[![CI Status](http://img.shields.io/travis/Felipe Tumonis/FTMoreApps.svg?style=flat)](https://travis-ci.org/Felipe Tumonis/FTMoreApps)
[![Version](https://img.shields.io/cocoapods/v/FTMoreApps.svg?style=flat)](http://cocoapods.org/pods/FTMoreApps)
[![License](https://img.shields.io/cocoapods/l/FTMoreApps.svg?style=flat)](http://cocoapods.org/pods/FTMoreApps)
[![Platform](https://img.shields.io/cocoapods/p/FTMoreApps.svg?style=flat)](http://cocoapods.org/pods/FTMoreApps)


## Description

FTMoreApps is an iOS library created to present a view controller inside your application to show your developer page of apps. It is very similar to the App Store visual.

## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

Just #import the FTMoreApps.h header, and call the one of the methods described below to present the view controller.

```objective-c
#import <FTMoreApps/FTMoreApps.h>

...

- (IBAction)buttonPressed:(id)sender {

    FTMoreApps *moreAppsManager = [FTMoreApps sharedManager];

    [moreAppsManager presentMoreAppsInViewController:self
                                         developerId:@"318226300" // You can find your developer id in your iTunes link of your apps: https://itunes.apple.com/us/artist/felipe-tumonis/id318226300?mt=8
                                     descriptionType:FTDescriptionTypeScreenshots
                                          completion:nil];

    /* 
    // OR
    [moreAppsManager presentMoreAppsInViewController:self
                                              appIds:@[@"app_id_1", @"app_id_2", ...] // The ids of the apps you want to show
                                     descriptionType:FTDescriptionTypeText
                                          completion:nil];
    */

    moreAppsManager.showActionButton = NO;
    moreAppsManager.showPrice = NO;
    moreAppsManager.title = NSLocalizedString(@"More apps", nil);

    moreAppsManager.willDismissBlock = ^{
        NSLog(@"will dismiss more apps view controller");
    };

    moreAppsManager.didDismissBlock = ^{
        NSLog(@"did dismiss more apps view controller");
    };

    moreAppsManager.didSelectAppBlock = ^(NSString *appId){
        NSLog(@"did select app id: %@", appId);
    };
}
```

## Requirements

This library requires iOS 8 and ARC.

## Installation

FTMoreApps is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "FTMoreApps"
```

Or, simply copy all the files into your project.

## Author

Felipe Tumonis, ftumonis@gmail.com

## License

FTMoreApps is available under the MIT license. See the LICENSE file for more info.
