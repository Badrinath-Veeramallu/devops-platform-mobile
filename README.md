# DevOps Learning Platform — Mobile App

Flutter application for the DevOps Learning Platform.

## Requirements

- Flutter SDK and Dart version compatible with `pubspec.yaml`
- Android Studio or a configured Android toolchain for Android builds
- Android emulator or physical Android device
- Xcode and command-line tools for iOS builds (iOS development requires macOS)
- A backend API reachable from the device

Check your setup:

```bash
flutter --version
flutter doctor
```

## Setup

Clone this repository, enter the directory, and fetch dependencies:

```bash
flutter pub get
```

The app supports an `API_URL` compile-time override using `--dart-define`.

## Run on Android

List available devices:

```bash
flutter devices
```

For the standard Android Studio emulator, use:

```bash
flutter run --dart-define=API_URL=http://10.0.2.2:5000/api
```

`10.0.2.2` is commonly the host computer address from the standard Android emulator. It is not generally correct for a physical phone.

For a physical phone on the same Wi-Fi, use your computer's LAN IP:

```bash
flutter run --dart-define=API_URL=http://YOUR_COMPUTER_LAN_IP:5000/api
```

Replace `YOUR_COMPUTER_LAN_IP` with the actual LAN IP. Ensure the backend is reachable from the device and the firewall/network allows the connection.

## Build Android APK

```bash
flutter build apk --dart-define=API_URL=http://YOUR_BACKEND_HOST:5000/api
```

For an APK intended for other users, use the deployed HTTPS backend URL rather than a development LAN address.

## Tests and analysis

```bash
flutter analyze
flutter test
```

## Platform notes

- The repository includes Android, iOS, macOS, Linux, Windows, and web folders. Successful dependency resolution does not guarantee every platform builds; each platform needs its own toolchain and configuration.
- Google sign-in and API calls may need additional platform-specific OAuth configuration.
- Flutter-generated files are recreated by Flutter tooling and are excluded where configured.

## Troubleshooting

- **App cannot reach the API:** check that the backend is running and `API_URL` is reachable from the emulator/device. `localhost` inside a phone/emulator refers to that device, not automatically to your computer.
- **No device listed:** start an emulator or connect/unlock a device; enable USB debugging if needed, then rerun `flutter devices`.
- **Build errors:** run `flutter doctor` and follow its guidance for the platform you're targeting.
