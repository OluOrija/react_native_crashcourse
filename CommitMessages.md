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

7. Trending videos section
- ```Bug``` The rendered videos are not playing : Possible bandwidth limit issue according to a comment on the tutorial video
- REF: 
@tuongnguyen590
1 month ago (edited)
If you get to the Home Page part (around 2:45:38) where the VideoCard component supposes to render thumbnail images but it doesn't. It's because the files the author provided had exceed the access bandwidth limit. You can upload your own videos and images to the same bucket created earlier in appwrite and update the video url as well as thumbnail url.
Update: Looks like Adrian and team had updated the thumbnails/videos link
- ```Tip``` Forgetting to reference the creator on a video will throw a null reference error
- Reworked the session management logic on SignIn

7.1 BUG
- Whilst trying to fix the session/context issue I got stuck with the error: appwrite error User (role: guests) missing scope (account)
- Commented out the GlobalProvider in app/_layout.jsx so we don't require a logged in user for now
- And in app/index.jsx I'm just returning (return <Redirect href="/home"/>) to force the app into the Home screen straight away.
- Living the BUG fix as a TODO: for now.

8. Search screen
- ```Fixed``` Error: AppwriteException: Searching by attribute "title" requires a fulltext index - Fix by creating a fulltext index on the videos collection

9. Profile screen
- Ongoing issues with user SignIn is affecting the functionality of the page.
- Deleting all users and fundling with creaEmailPasswordSession() method got me past the appwriterror. And reworking the method to check for the current session then deleting that session seems to be a more stable approach. Drawback is that it doesn't retain the session so all app refreshed require the user to login. TODO: investigate sesson manegement.

10. Create Screen
- Implemented the Create screen.
- Omn the front end we use a Video component imported from "expo-av" within a form, combined with the DocumentPicker.getDocumentAsync() function from DocumentPicker from "expo-document-picker".
- The flow goes: createFile on storage -> get file Preview from the asset uploaded to storage -> create a video post using the asset uploaded.
- Continued to rework the SignIn method to eliminate the AppwriteException: User(role:guests).... error

11. File Picker
- Swapped DocumentPicker with expo ImagePicker