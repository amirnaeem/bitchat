# Running Apps on iPhone 14 Pro: Quick Setup Guide

## Option 1: Direct Device Testing (Free)

### Requirements
- **Mac computer** (macOS Monterey 12.0+)
- **Xcode** (latest version from Mac App Store)
- **iPhone 14 Pro** with USB-C to Lightning cable
- **Apple ID** (free)

### Step-by-Step Setup

#### 1. Install Xcode
```bash
# Download from Mac App Store (free)
# Or install command line tools
xcode-select --install
```

#### 2. Enable Developer Mode on iPhone 14 Pro
1. Go to **Settings > Privacy & Security**
2. Scroll down to **Developer Mode**
3. Toggle it **ON**
4. Restart your iPhone when prompted
5. Confirm activation after restart

#### 3. Create a Simple App Project
1. Open Xcode
2. **File > New > Project**
3. Choose **iOS > App**
4. Fill in details:
   - Product Name: `MyTestApp`
   - Interface: `SwiftUI`
   - Language: `Swift`
   - Bundle Identifier: `com.yourname.mytestapp`

#### 4. Set Up Your Apple ID in Xcode
1. **Xcode > Settings > Accounts**
2. Click **+** and sign in with your Apple ID
3. Select your Apple ID and click **Manage Certificates**
4. Click **+** and choose **iOS Development**

#### 5. Configure Project for Your Device
1. Select your project in Xcode navigator
2. Under **Signing & Capabilities**:
   - **Team**: Select your Apple ID
   - **Bundle Identifier**: Make it unique (e.g., `com.yourname.mytestapp`)
   - Check **Automatically manage signing**

#### 6. Connect and Trust Your iPhone 14 Pro
1. Connect iPhone to Mac with cable
2. **Trust this computer** on iPhone
3. Enter iPhone passcode
4. In Xcode, select your iPhone from device menu (top toolbar)

#### 7. Run Your App
1. Click the **Play button** (▶️) in Xcode
2. App will build and install on your iPhone 14 Pro
3. **First time**: Go to **Settings > General > VPN & Device Management**
4. Trust your developer certificate

### Simple Test App Code
```swift
import SwiftUI

@main
struct MyTestApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}

struct ContentView: View {
    @State private var counter = 0
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Hello iPhone 14 Pro!")
                .font(.largeTitle)
                .padding()
            
            Text("Count: \(counter)")
                .font(.title)
            
            Button("Tap Me!") {
                counter += 1
            }
            .buttonStyle(.borderedProminent)
            .controlSize(.large)
        }
        .padding()
    }
}
```

---

## Option 2: TestFlight Distribution

### When to Use TestFlight
- Share app with multiple testers (up to 10,000)
- Test on devices you don't own
- Get feedback before App Store release
- Test in-app purchases

### Requirements
- **Apple Developer Account** ($99/year)
- **Completed app** ready for testing
- **App Store Connect** access

### TestFlight Setup Process

#### 1. Join Apple Developer Program
1. Go to [developer.apple.com](https://developer.apple.com)
2. **Account > Enroll**
3. Pay $99 annual fee
4. Wait for approval (1-2 days)

#### 2. Create App in App Store Connect
1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. **My Apps > + > New App**
3. Fill in app information:
   - **Name**: Your app name
   - **Bundle ID**: Must match Xcode project
   - **SKU**: Unique identifier
   - **Primary Language**: Choose language

#### 3. Configure Xcode for Distribution
```swift
// In your project settings:
// Signing & Capabilities tab
// - Team: Select your paid developer account
// - Bundle Identifier: Match App Store Connect
// - Signing Certificate: iOS Distribution
```

#### 4. Archive and Upload
1. In Xcode: **Product > Archive**
2. **Window > Organizer** opens
3. Select your archive
4. Click **Distribute App**
5. Choose **App Store Connect**
6. Follow upload process

#### 5. Set Up TestFlight Testing
1. In App Store Connect, go to your app
2. **TestFlight tab**
3. **Internal Testing** (up to 100 users):
   - Add team members by email
   - They get automatic access
4. **External Testing** (up to 10,000 users):
   - Create test groups
   - Add external testers by email
   - Requires Apple review (24-48 hours)

#### 6. Invite Testers
```
Testers receive email with TestFlight invitation
They download TestFlight app from App Store
Install and test your app
Provide feedback through TestFlight
```

---

## Quick Device Testing Checklist

### Before You Start
- [ ] Mac with Xcode installed
- [ ] iPhone 14 Pro with Developer Mode enabled
- [ ] USB-C to Lightning cable
- [ ] Apple ID signed into Xcode

### For Direct Testing (Free)
- [ ] Create new Xcode project
- [ ] Set unique Bundle Identifier
- [ ] Enable automatic code signing
- [ ] Connect iPhone and trust computer
- [ ] Run app from Xcode

### For TestFlight (Paid)
- [ ] Apple Developer account ($99/year)
- [ ] App created in App Store Connect
- [ ] Archive and upload build
- [ ] Add testers to TestFlight
- [ ] Send invitations

---

## Troubleshooting Common Issues

### "Unable to install app"
1. Check Bundle Identifier is unique
2. Trust developer certificate on iPhone
3. Ensure Developer Mode is enabled

### "No code signing identities found"
1. Sign into Apple ID in Xcode
2. Generate iOS Development certificate
3. Restart Xcode

### "This app cannot be installed because its integrity could not be verified"
1. Go to **Settings > General > VPN & Device Management**
2. Trust your developer profile
3. Try installing again

### iPhone not appearing in Xcode
1. Unlock iPhone and trust computer
2. Check cable connection
3. Restart both devices
4. Update Xcode if needed

---

## iPhone 14 Pro Specific Considerations

### Dynamic Island Testing
```swift
// Test Dynamic Island with Live Activities
import ActivityKit

// Your app can display content in Dynamic Island
// Perfect for testing on iPhone 14 Pro
```

### ProMotion Display (120Hz)
```swift
// Test smooth animations on 120Hz display
struct TestAnimation: View {
    @State private var rotation: Double = 0
    
    var body: some View {
        Rectangle()
            .frame(width: 100, height: 100)
            .rotationEffect(.degrees(rotation))
            .onAppear {
                withAnimation(.linear(duration: 2).repeatForever(autoreverses: false)) {
                    rotation = 360
                }
            }
    }
}
```

### Camera System Testing
```swift
// Test 48MP camera capabilities
import AVFoundation

// Request camera permission
// Test different camera modes (Wide, Ultra Wide, Telephoto)
// Test 4K video recording
```

---

## Next Steps

1. **Start Simple**: Create basic app and run on device
2. **Test Features**: Experiment with iPhone 14 Pro capabilities
3. **Add Testers**: Use TestFlight for broader testing
4. **Iterate**: Improve based on feedback
5. **Publish**: Submit to App Store when ready

The key is to start simple - just getting an app running on your iPhone 14 Pro is the first important milestone!