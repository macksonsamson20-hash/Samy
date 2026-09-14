# Focus Tasks HTML to Android APK

This repository wraps the HTML app in an Android WebView and builds a debug APK using GitHub Actions.

## Files to know

- `app/src/main/assets/index.html` — replace this with your HTML frontend.
- `app/src/main/assets/` — put CSS, JavaScript, images, fonts, and other local assets here. Keep paths relative, for example `css/style.css`.
- `app/src/main/AndroidManifest.xml` — Android app permissions and app label.
- `.github/workflows/build-apk.yml` — GitHub Actions build workflow.

## Use it on GitHub

1. Create a new GitHub repository.
2. Upload all files in this project, preserving the `.github/workflows/build-apk.yml` path.
3. Commit and push to the `main` branch.
4. Open the repository's **Actions** tab.
5. Select **Build Android APK**, then click **Run workflow**.
6. When it finishes, open the workflow run and download the `focus-tasks-debug-apk` artifact.
7. Extract the artifact and install `app-debug.apk` on an Android device.

A push to `main` also starts a build automatically.

## Permissions

`INTERNET` is enabled by default. In `AndroidManifest.xml`, uncomment only the permissions the app actually needs. Dangerous permissions such as camera, location, microphone, notifications, and media access also require runtime permission prompts in the Android code; declaring them in the manifest alone does not grant access.

## Important limitations

The workflow creates a **debug APK** for testing. A public Play Store release needs a signed release build, a protected keystore, and GitHub Actions secrets. Never commit a keystore or access token to the repository.
