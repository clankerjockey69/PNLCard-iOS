# PNL Card — iPhone app

This is a native SwiftUI + WKWebView wrapper for the **original uploaded PNL Card Generator.html**. The HTML is bundled locally and the app does not need a hosted website to open. Some original features (Google Fonts, video encoding, clipboard, photo sharing) may depend on internet connectivity or WebKit permissions and have **not been device-tested**.

## Build using GitHub Actions (no Mac needed)

1. Create a new GitHub repository (or use an existing empty one).
2. Upload **all files and folders** from this project, including the hidden `.github/workflows/build-ios.yml` file. GitHub's browser upload can accept files; preserve folder paths.
3. Commit to the `main` branch.
4. Open **Actions → Build iPhone IPA → Run workflow**. A push to `main` also starts the workflow.
5. When the run succeeds, open the run page, scroll to **Artifacts**, and download **PNLCard-unsigned-IPA**.
6. Unzip the downloaded GitHub artifact to obtain `PNLCard-unsigned.ipa`.

## Install on iPhone

**The GitHub artifact is unsigned and cannot be installed as-is.** Sign it with an authorized iOS signing method (such as a valid Apple developer certificate and provisioning profile, or a compatible personal sideloading/signing tool) before installing. Signing services and device provisioning requirements vary. Never share your Apple ID password or signing certificate private key with strangers.

If you have a paid Apple Developer account and valid distribution provisioning, you can add an authenticated signing/export step to the workflow; this sample deliberately does **not** request or store signing secrets.

## Customize

- Change the bundled UI in `PNLCard/Resources/index.html`.
- Change the bundle identifier in `project.yml` (`PRODUCT_BUNDLE_IDENTIFIER`) to one you control before signing.
- To build locally on a Mac: `brew install xcodegen`, `xcodegen generate`, then open `PNLCard.xcodeproj` in Xcode.

## Notes

- iOS 16 or newer.
- The original HTML is retained, including its attribution and external links.
- Video export, clipboard and image downloads may require additional WebKit-specific handling. The app has **not** been compiled or tested on an iPhone in this environment.
- A real native share-sheet bridge would be a future enhancement for more reliable exports.
