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

5. Appwrite Logic
- Sign up @ https://cloud.appwrite.io/
- Created project : JSM_react_native_crash_course
- Created lib folder -> appwrite.js to hold appwriteConfigs
- Created database 'aora' in appwrite dashboard and added Id to appwrite.js config file
- Created users and videos collection and added id to appwrite.js file
- Setup attributes under the users and videos collection
- Enabled 'Any' under permissions for user
- Setup a 'Many to One' relationship key called creator linking videos to the users collection
- Enabled 'All users' under permissions for videos
- Created a 'Storage' bucket called files and added id to appwrite.js
- Give users permissions and set file limit to 50MB
- Set Allowed file Extensions
- Implemented appwrite logic to get, and set users
- ```Bug``` User session needs to be cleared if you reload the app
- ```Bug``` attributes are case sensitive. Ref: https://appwrite.io/threads/1234271741652500642
- ```Bug``` account.CreateEmailSession is depreciated. User: account.createEmailPasswordSession(email, password)

5.1. Appwrite Logic Bug fix
- ```Bug``` User session needs to be cleared if you reload the app
- Extended the signIn function in appwrite.js to check if there is an existing session and return that session before attempting to sign a user in. Ref: https://appwrite.io/threads/1237659392124522546

6. Home Screen
- ```Lesson``` struglling to understand custom hooks with the use of useAppwrite.js to wrap appwrtie.js 
- Implemented the home screen content and layout
- Uploaded dummy videos to appwrite
- Fetched those videos and rendered them using custom components