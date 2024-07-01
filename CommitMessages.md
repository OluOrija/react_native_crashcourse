1. Initial commit
- Environment setup
    Expo Router Doc : https://docs.expo.dev/router/installation/
    Android Studio installation
    Android emulator setup
-   Basic react native app setup using
    run this command:
```bash
npx create-expo-app@latest ./ --template blank
```
- Understanding the relationship between index.jsx and _layout.jsx files

2. Files & Folder structure 
- understanding bracket folders
- square bracket folders
- Implemented the File and Folder Structure - which determines the navigation in the app
- Implemented the Bottom (Tabs) navigation menu
- Styled the bottom Nav menu using Tab screenOptions property

3. OnBoarding Screen Setup
- The index.jsx file under the app folder servers as the entry point for the app, so in effect the landing page, which had a call to action button to signup via email.
- Created the CustomButtom component using the TouchableOpacity object from react-native
- Manipulated the StatusBar 

4. Auth Screens
- Created a FormField component, a container to handle text input with logic to handle password field type
- Used Image, CustomButton, FormField components in a view->scrollView->safeAreaView to design the look and feel of the SignIn page, which was then copied and tweaked to design the SignUp page.
- No Logic yet but there is navigation between the entry point to the sign in and sign up pages and
