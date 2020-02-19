FCAlertView
============

FCAlertView is a Flat Customizable AlertView, written in Swift

![CI Status](https://travis-ci.com/felarmir/FCAlertView.svg?branch=master)(https://travis-ci.com/felarmir/FCAlertView)

![Logo](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/RepoLogo2.png)

![BackgroundImage](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot.png)
![BackgroundImage](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot2.png)
![BackgroundImage](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot3.png)
![BackgroundImage](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot4.png)
![BackgroundImage](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot5.png)

#Objective C

For the Objective C version of FCAlertView, [click here](https://github.com/nimati/FCAlertView).

#Installation

### Using CocoaPods - Coming Soon

FCAlertView is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'FCAlertView'
```

### Manually

Clone or Download this Repo. Then simply drag the folder ```FCAlertView``` to your Xcode project. Please make sure to drag the whole folder, which includes assets needed for some alert types.

# Example

FCAlertView comes with an example app that you can use to try out all of the customizations below. It's recommended that you go through all of the docs before using the example app. To use the example app, clone or download FCAlertView, open and run ```Example/FCAlertView.xcworkspace```.

#Adding FCAlertView

Start by adding the following to your desired View Controller:

```Swift
import FCAlertView
```

### Presenting an FCAlertView

```Swift
let alert = FCAlertView()

alert.showAlert(inView: self,
				withTitle: "Alert Title",
				withSubtitle: "This is your alert's subtitle. Keep it short and concise. 😜👌",
				withCustomImage: nil,
				withDoneButtonTitle: nil,
				andButtons: nil)
```

## Base Customizations

- **Title (String?):** You can leave the Title as ```nil``` or Give it a ```String```.

- **Subtitle (String):** FCAlertView always requires a subtitle, even if you want just a few words, add it here instead of the title (then leave the title as nil). *Take a look at [Screenshot 2](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot2.png) for an example*.

-  **CustomImage (UIImage?):** You can leave this image as ```nil``` or Give it a ```UIImage``` which will show at the top of the alert. *Take a look at [Screenshot 4](https://github.com/nimati/FCAlertView/blob/master/Images/ScreenShots/ScreenShot4.png) for an example*.

- **DoneButtonTitle (String?):** You can leave this as ```nil``` to show "Ok" as the dismiss button for the AlertView, or Give it an ```String```.

- **Buttons ([String]?):** If you want to add buttons to your alert, simply add an array of 1 or 2 button titles as ```String``` here, anything more will be ignored as 2 is the max custom buttons you can add (aside from the done button). Read more about buttons and actions further down.

## Extra Customizations

This section includes all the tiny details that you can customize your alert with, which makes FCAlertView very customizable. Or leave it as is and enjoy the simplicity.

### Color Scheme

By default, FCAlertView doesn't include a color scheme, much like UIAlertView, but you can add one by adding this line:

```Swift

alert.colorScheme = UIColor(red: 150/255, green: 150/255, blue: 150/255, alpha: 1)
```

FCAlertView also comes with a set of pre-made colors that you can use:

![alt text](https://github.com/nimati/FCAlertView/blob/master/Images/FlatColors.png?raw=true "Flat Colors")

#####*Credit goes to [flatuicolors.com](http://flatuicolors.com) for the Beautiful Palette of Flat Colors*

Simply choose the color you'd like to use for your AlertView, and add:

```Swift
alert.colorScheme = UIColor.flatBlue // Replace "Blue" with your preferred color from the image above
alert.colorScheme = .flatBlue // Alternative
```

### Title and Subtitle Colors

#### Change Title Color by Adding one of:

```Swift
alert.titleColor = UIColor.flatPurple
alert.titleColor = .flatPurple
```

#### Change SubTitle Color by Adding one of

```Swift
alert.subTitleColor = UIColor.flatBlue
alert.subTitleColor = .flatBlue
```

### AlertView Rounded Corners

Change the Rounding of the FCAlertView's corners as desired using:

```Colors
alert.cornerRadius = 4 // Replace 4 with your desired corner radius amount (Set to 0.1 if you don't want rounding)
```

### Alert Types

FCAlertView comes with 3 pre-designed custom alert types. Success, Caution, or Warning, simply add the type while initializing the FCAlertView.

#### Success

```Swift
let alert = FCAlertView(type: .success)
```

#### Caution

```Swift
let alert = FCAlertView(type: .caution)
```

#### Warning

```Swift
let alert = FCAlertView(type: .warning)
```

### Dismissing FCAlertView

There are multiple ways you can dismiss an FCAlertView

#### Close on Outside Touch

When the user taps anywhere outside the alert, you can dismiss it by adding this line:

```Swift
alert.dismissOnOutsideTouch = true
```

#### Auto-Close the Alert

Dismiss the AlertView when a certain time has elapsed after the AlertView is presented, by adding this line:

```Swift
alert.autoHideSeconds = 5 // Replace 5 with the number of Seconds you'd like the view to appear for before dismissing itself
```

#### Done Button or Any Custom Buttons

All Buttons including the Done/Dismiss Button will make the FCAlertView dismiss.

#### Dismissing it yourself

If you'd like to dismiss the AlertView yourself, simply add the following line to where you need it:

```Swift
alert.dismissAlertView()
```

### Hiding Done/Dismiss Button

If you'd like to have no buttons on your AlertView (to simply display a notification or approval of something) or you want all your buttons to be a custom one which you've added yourself. Simply hide the Done buttons by adding this line:

```Swift
alert.hideDoneButton = true
```

### Hiding All Buttons

If you'd like to simply hide all buttons from your alert, you can do so by adding this line:

```Swift
alert.hideAllButtons = true
```

# Button Actions

To add actions to your buttons, you have to first delegate your FCAlertView with your view, and then add a helper method which will detect button touches. Here's how you can add an alert with buttons and perform actions:

First add the ```FCAlertViewDelegate``` protocol to your View Controller as such:

```Swift
import UIKit
import FCAlertView

class ViewController : FCAlertViewDelegate {...}

```

Now add your FCAlertView with Buttons where you need to present it:

```Swift
let alert = FCAlertView();

alert.delegate = self

alert.showAlert(inView: self,
             withTitle:"Alert Title",
          withSubtitle:"This is your alert's subtitle. Keep it short and concise. 😜👌",
       withCustomImage:nil,
   withDoneButtonTitle:nil,
            andButtons:["Button 1", "Button 2"]) // Set your button titles here

```

After adding your FCAlertView, you can detect button touches by adding this method to your class:

```Swift
func alertView(alertView: FCAlertView, clickedButtonIndex index: Int, buttonTitle title: String) {

	if title == "Button 1" {
		// Perform Action for Button 1
	}else if title == "Button 2"{
		// Perform Action for Button 2
	}
}
```

#### Done Button Method

If you'd also like to detect button touch for the Done/Dismiss button, simply add this method to your class:

```Swift
func FCAlertDoneButtonClicked(alertView: FCAlertView){
	// Done Button was Pressed, Perform the Action you'd like here.
}
```

# Other Helper Methods

Make sure to add the ```FCAlertViewDelegate``` protocol to your View Controller as such:

```Swift
import UIKit
import FCAlertView

class ViewController: FCAlertViewDelegate {...}

```

and setting the delegate of your FCAlertView, as such:

```Swift
let alert = FCAlertView()
alert.delegate = self
```

### Detect when FCAlertView has been dismissed

```Swift
func FCAlertViewDismissed(alertView: FCAlertView){
	// Your FCAlertView was Dismissed, Perform the Action you'd like here.
}
```

### Detect when FCAlertView is about to present

```Swift
func FCAlertViewWillAppear(alertView: FCAlertView){
	// Your FCAlertView will be Presented, Perform the Action you'd like here.
}
```

# More Customizations

FCAlertView is an ongoing project with the goal of becoming the most used custom AlertView for iOS. Improvements and changes are on the way, and here are some of the things that are coming soon with it:

- Swift Friendly
- Adding TextFields
- More Custom Animations
- Blur Background
- Alert Sounds
- Big and Beautiful Full Screen Alerts
- Landscape Orientation
- Frame Customizations
- More Types of Alerts (including Progress Types)
- iPad Friendly Alerts
- Improved Button Highlight and Customizations
- Something Missing? Email your suggestion [here](mailto:nima6tahami@gmail.com)

About FCAlertView
-----------------

FCAlertView is a fully customizable and beautifully designed AlertView. I designed FCAlertView beacuse I've always wanted to have access to change the different attributes of the default UIAlertView. Design wise, FCAlertView is similar looking to the default AlertView, however, as you start customizing it for your specific need, you realize it can do a lot more while looking flat and sharp.

FCAlertView lets you do things such as specify the number of buttons, the color scheme of the view, adding a small image to it, hide the view after a certain time, and more. A full description of how to customize FCAlertView to fit your alert can be found on http://github.com/nimati/FCAlertView.

The Vision for FC Libraries
---------------------------

My goal is to create a set of different libraries, each targetting a certain UI element of iOS, with the goal to improve the design and add more customizations. As such, FCAlertView is a more Flat/Customizable AlertView. With this mindset, I'd like to create more FC libraries, such as FCActionSheet, FCNotification (for quick, in app alerts), FCGuideView (for guiding your users around your app). If you also have a suggestion for an FC Library, please send it [here](mailto:nima6tahami@gmail.com).

> Ultimately, FC Libraries is here to improve the look and feel of your app for your end users. So all improvements and suggestions are welcome.

Cheers 🍻

### Author

Created and designed by [Nima Tahami](http://nimatahami.com).

Credits for the Beautiful Color Palette goes to [flatuicolors.com](http://flatuicolors.com).

Credit for the Beautiful Icons go to [ionicons.com](http://ionicons.com).

### License

FCAlertView is available under the MIT license. See the LICENSE file for more info.
