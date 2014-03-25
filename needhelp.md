My end goal is to be able to show the next upcoming alarm in the badge for the clock app on my phone|ipad.

as a test (this is my first tweak) I have been attempting to just modify the badge of the clock app.

##imports##
    #import <Foundation/Foundation.h>
    #import <UIKit/UIKit.h>
    //#import "substrate.h"
    #import <SpringBoard/SBApplicationIcon.h>
    #import "SpringBoard.h"


##code attempts

    - (void)setBadgeForBundle:(NSString *)bundle toValue:(id)value
    {
        SBIcon *icon = (SBIcon *)[[[%c(SBIconViewMap) homescreenMap] iconModel] applicationIconForDisplayIdentifier:bundle];
        [icon setBadge:value];
        NSLog(@"CTZ-Badge info: %@", [icon displayName]);
    }
  
**call:**
```[self performSelector:@selector(setBadgeForBundle:toValue:) withObject:@"com.apple.mobiletimer" withObject:@"10"];```  

**output:**
```CTZ-Badge info: (null)```

--
    SBApplication *app = [[objc_getClass("SBApplicationController") sharedInstance] applicationWithDisplayIdentifier:@"com.apple.mobiletimer"];

    SBApplicationIcon *appIcon = [[objc_getClass("SBApplicationIcon") alloc] initWithApplication:app];
    [appIcon setBadge:@"999"];
    
**output:** ```nothing happens. there is an alert right afterwards. the alert fires but there is no change to the app badge.```

here is a copy of my current [tweak.xm](https://gist.github.com/Critter/df830981b989905b0a76)

anyone have any suggestions as to why this isn't working?
