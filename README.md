# AMC - Android App Development, APK Build & Publishing Guide
# (AMC - એપ ડાઉનલોડ, APK બનાવવા અને પબ્લિશ કરવાની માર્ગદર્શિકા)

---

## 🇮🇳 ગુજરાતી માં માહિતી (Gujarati Guide)

### ૧. APK કેવી રીતે બનાવવી? (How to Make an APK?)
Android App (APK) બનાવવા માટે મુખ્યત્વે નીચેની રીતો વાપરી શકાય છે:

#### પદ્ધતિ ૧: Android Studio દ્વારા (તમામ કોડર માટે)
1. **Android Studio ડાઉનલોડ અને ઇન્સ્ટોલ કરો**: [Android Studio Official Website](https://developer.android.com/studio) પરથી ડાઉનલોડ કરો.
2. **પ્રોજેક્ટ ખોલો**: તમારો એન્ડ્રોઇડ પ્રોજેક્ટ કોડ (Java / Kotlin / React Native / Flutter) Android Studio માં Open કરો.
3. **APK બિલ્ડ કરો**:
   - Menu બારમાં **Build** પર ક્લિક કરો.
   - **Build Bundle(s) / APK(s)** વિકલ્પ પસંદ કરો.
   - **Build APK(s)** પર ક્લિક કરો.
4. **Build સફળ થાય એટલે**: નીચે જમણી બાજુ `locate` લિંક દેખાશે, તેના પર ક્લિક કરવાથી તૈયાર થયેલી `.apk` ફાઇલ મેળવી શકશો.

#### પદ્ધતિ ૨: Flutter અથવા React Native દ્વારા (CommandLine)
- **Flutter માટે**: `flutter build apk --release` Command ચલાવો. APK ફાઇલ `build/app/outputs/flutter-apk/app-release.apk` પાથ પર મળશે.
- **React Native માટે**: `cd android && ./gradlew assembleRelease` ચલાવો. APK ફાઇલ `android/app/build/outputs/apk/release/app-release.apk` પાથ પર મળશે.

---

### ૨. APK કેવી રીતે ડાઉનલોડ કરવી? (How to Download the APK?)
- **સ્થાનિક રીતે (Local PC માંથી)**: બિલ્ડ થયા પછી ઉપર બતાવ્યા મુજબ `build/outputs/apk/` ફોલ્ડર માંથી `.apk` ફાઇલ તમારા મોબાઇલમાં ટ્રાન્સફર (USB/Bluetooth/Drive દ્વારા) કરો.
- **GitHub Releases માંથી ડાઉનલોડ કરવા માટે**:
  1. GitHub રિપોઝિટરીમાં જઈને **Releases** વિભાગમાં જાઓ.
  2. ત્યાં મૂકેલી `.apk` લિંક પર ક્લિક કરીને ડાઉનલોડ કરો.
- **મોબાઇલમાં ઇન્સ્ટોલ કરો**: APK પર ક્લિક કરી **"Install from Unknown Sources"** પરમિશન Allow કરીને App ઇન્સ્ટોલ કરો.

---

### ૩. એપ ને Publish અને Use કેવી રીતે કરવી? (How to Publish & Use the App?)

#### Play Store પર Publish કરવા માટે:
1. **Google Play Console એકાઉન્ટ બનાવો**: [Google Play Console](https://play.google.com/console) પર એકાઉન્ટ રજીસ્ટર કરો ($25 વન-ટાઇમ ફી).
2. **Signed App Bundle (.aab) બનાવો**: Android Studio માં **Build > Generate Signed Bundle / APK** પસંદ કરી Signed Bundle ફાઇલ બનાવો.
3. **App Details ભરો**: App Name, Description, Screenshots, Privacy Policy ઉમેરો.
4. **App Review માં સબમિટ કરો**: Google દ્વારા રિવ્યુ થઈ ગયા પછી એપ Google Play Store પર લાઇવ થશે.

---

## 🇬🇧 English Guide

### 1. How to Create an APK?

#### Method 1: Using Android Studio
1. Install [Android Studio](https://developer.android.com/studio).
2. Open your project in Android Studio.
3. Go to top menu: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. Once completed, click **locate** to find your `.apk` file.

#### Method 2: Command Line (Flutter / React Native)
- **Flutter**: Run `flutter build apk --release`
- **React Native**: Run `cd android && ./gradlew assembleRelease`

---

### 2. How to Download & Install APK?
1. Locate the generated `.apk` file under `android/app/build/outputs/apk/release/` or `app/build/outputs/apk/debug/`.
2. Transfer the `.apk` file to your mobile phone.
3. Enable **"Install from Unknown Sources"** on your mobile device and tap the file to install.

---

### 3. How to Publish the App?
1. Create a Google Play Console developer account at [Google Play Console](https://play.google.com/console).
2. Generate a Signed App Bundle (`.aab`) in Android Studio via **Build > Generate Signed Bundle / APK**.
3. Upload the `.aab` file, complete store listing (graphics, description, privacy policy), and submit for review.
