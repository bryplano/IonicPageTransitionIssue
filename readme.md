## Purpose

This application was built with the intent of reproducing an Ionic v4 page transition issue when using the `ion-input autofocus` property. See the [Ionic documentation](https://beta.ionicframework.com/docs/api/input/) for more about `ion-input`. 


## Reproducing the Issue

**These steps assume the following:**
- You have Xcode 9 or 10 installed
- You have an Apple Developer account installed & configured for running Ionic applications locally (note: you may need to change your provisioning profile / code signing in Xcode when running the app locally)
- You have the Ionic CLI & npm/NodeJS installed

1. Download this project as a ZIP export & unzip to a local directory
2. Open Terminal and navigate to the dir
3. Run `npm i`
4. Run `ionic cordova platform add ios`
5. The next step depends on the version of Xcode you're using.

5a. If Xcode 9 is installed, run:
```
ionic cordova run ios
```
5b. If Xcode 10 is installed, run: 
```
ionic cordova run ios -- --buildFlag="-UseModernBuildSystem=0"
``` 

6. When the simulator is running, tap on the **Go to detail** button
7. Notice the transition "stutters" when navigating between the pages
8. You can use a "swipe" gesture to go back to the first page by clicking-and-dragging from left-to-right on the left side of the simulator window


## Notes
- This issue is readily reproduceable *after* the first click of the button. It occurs occasionally on the first click
- This occurs on both devices and simulators (only tested on iOS 12+)
- If `autofocus` is set to `false` and the build is re-run, there is *no* stutter present during the transition