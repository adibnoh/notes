# Init

## POD

[https://stackoverflow.com/questions/20755044/how-to-install-cocoapods](https://stackoverflow.com/questions/20755044/how-to-install-cocoapods)

1. sudo gem install cocoapods
2. cd <project_folder>
3. pod install

## Debugging

### Write console log

#### NSLog

`NSLog("Write anything here")` - Normal Log

`NSLog("Display string variable %@", message)` - Log with string variable

`NSLog("Display integer variable %d", number)` - Log with integer variable

`NSLog("Display signed integer variable %i", number)` - Log with signed integer variable

`NSLog("Display unsigned integer variable %u", number)` - Log with unsigned integer variable

`NSLog("Display float variable %f", number)` - Log with float variable

`NSLog("Display double variable %lf", number)` - Log with double variable

`NSLog("Multiple Variable: %d and %d",var1, var2)` - Log with multiple variable

## Firebase

Disable logging to console

![Screenshot](https://image.ibb.co/j2vZTp/Screenshot_2018_10_11_at_3_14_41_PM.png)

[How to disable Firebase/Core debug messages in iOS](https://stackoverflow.com/questions/40169286/how-to-disable-firebase-core-debug-messages-in-ios)

## Popup Alert

Add extension to UIViewController, this will allow us to call generic function to display popup alert from anywhere in our code

```swift

// add this function inside UIViewController extension class
extension UIViewController {
    func popupAlert(title: String?, message: String?, actionTitles:[String?], actions:[((UIAlertAction) -> Void)?]) {
        let alert = UIAlertController(title: title, message: message, preferredStyle: .alert)
        for (index, title) in actionTitles.enumerated() {
            let action = UIAlertAction(title: title, style: .default, handler: actions[index])
            alert.addAction(action)
        }
        self.present(alert, animated: true, completion: nil)
    }
}

// Call popupAlert
self.popupAlert(title: "Title", message: " Oops, xxxx ", actionTitles: ["Option1","Option2","Option3"], actions:[{action1 in

},{action2 in

}, nil])

```

[How to create uialertcontroller in global swift](https://stackoverflow.com/questions/38144019/how-to-create-uialertcontroller-in-global-swift)