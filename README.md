# Inconsistent Linking.getInitialURL() Result on Android in Expo

This repository demonstrates a bug in Expo's `Linking` API on Android where `getInitialURL()` sometimes returns `null` even after successfully opening a deep link.  The inconsistency makes reproducing the issue challenging.

## Bug Description
The app uses `Linking.getInitialURL()` to handle deep links. However, on Android, this method returns `null` intermittently despite a deep link successfully launching the app. This prevents the app from correctly processing the deep link and navigating to the appropriate screen.  The behavior is unpredictable; it might work correctly some times, and fail others.

## Steps to Reproduce
1. Clone this repository.
2. Run the app on an Android device or emulator.
3. Open a deep link that should trigger a route change within the app. 
4. Observe that sometimes `Linking.getInitialURL()` resolves with the correct URL, and other times it resolves to `null`, even if the app was opened with the same deep link.

## Solution
The provided solution uses a more robust method of handling initial URLs, leveraging the `Linking.addEventListener` to listen for incoming URLs and handling them accordingly, making it less reliant on the inconsistent behavior of `getInitialURL()`. 