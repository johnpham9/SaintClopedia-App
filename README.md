Saints Companion
A warm, offline encyclopedia of Catholic saints for iPhone and iPad, in English and Spanish. Built with SwiftUI by Luminae Crown Studio LLC.

App name	Saints Companion
Bundle ID	com.johnpham.saints-companion
Version	1.0 (build 1)
Platforms	iPhone and iPad, iOS 17.6 or later
App Store category	Reference
Languages	English, Spanish
Features
132 saints: apostles and the early Church, martyrs, Doctors of the Church, mystics and religious, and modern saints
Today tab: the saint of the day (or the feast being celebrated), plus the next upcoming feasts. It stays correct if the app is left open past midnight.
Saints tab: alphabetical, grouped by category, and searchable by name, title, patronage, or place (ignores case and accents, so "agustin" finds "Agustín")
Each saint: a portrait (114 of 132 have one), biography, feast day, years lived, birthplace, patronage, and a short prayer you can share
Favorites: saved on the device
EN | ES toggle at the top of each main screen. The choice is remembered, and Spanish is the default on devices set to Spanish. Saint text, prayers, labels, and dates all switch.
Design: parchment, burgundy, and gold with serif type; Dark Mode; Dynamic Type; animated splash screen
Private: no accounts, ads, analytics, or network access. See docs/PRIVACY.md.
Requirements
Xcode 26 or later (developed with Xcode 27)
iOS 17.6 or later
No third-party dependencies
Run it
Open SaintsCompanion.xcodeproj in Xcode.
Choose an iPhone or iPad simulator and press Run. (Source folders are synced to the project, so new files are picked up automatically.)
To run on a device or archive for the App Store, check your team under Signing & Capabilities (automatic signing is on).
Command-line build for the simulator:

xcodebuild -project SaintsCompanion.xcodeproj -scheme SaintsCompanion \
  -destination 'generic/platform=iOS Simulator' CODE_SIGNING_ALLOWED=NO build
Release to the App Store
In App Store Connect, create the app with bundle ID com.johnpham.saints-companion (it must match the project exactly and can't be changed later) and a SKU you haven't used.
In Xcode: Product → Archive, then Distribute App → App Store Connect.
Paste in the listing text from docs/APP_STORE.md, upload the screenshots from AppStore/Screenshots/, and host docs/PRIVACY.md at a public URL for the privacy policy field.
Work through docs/RELEASE_CHECKLIST.md. The saint text and Spanish still need a human proofread.
Bump CURRENT_PROJECT_VERSION (build) for every upload, and MARKETING_VERSION for every release.

Project structure
Saints-Companion/
  SaintsCompanion.xcodeproj
  Info.plist                      Launch screen (parchment + gold cross)
  SaintsCompanion/
    SaintsCompanionApp.swift      App entry, splash, midnight/foreground date refresh
    Models/
      Saint.swift                 Saint model, categories, feast-date and sort helpers
      SaintStore.swift            Loads data; language, favorites, search, feast days
      AppLanguage.swift           Language enum, Spanish model, interface strings (UIText)
    Views/
      RootView.swift              Tab bar
      SplashView.swift            Animated opening screen
      TodayView.swift             Today + Favorites screens
      SaintListView.swift         Saints list, rows, portrait circle
      SaintDetailView.swift       Saint page (portrait, biography, facts, patronage, prayer)
      CreditsView.swift           Image credits screen
      LanguageToggle.swift        EN | ES switch
    Theme/Theme.swift             Colors, serif type, shared styling
    Resources/
      saints.json                 All saint content (English)
      saints.es.json              Spanish text for every saint, keyed by saint id
      ImageCredits.json           Artist, license, and source for each portrait
    Assets.xcassets/
      AppIcon, LaunchCross        App icon and launch image
      Parchment, Card, AccentColor, Gold, GoldText, Ink   Color set (light and dark)
      Saints/<id>.imageset        One portrait per saint, named after the saint's id
  docs/                           Review and release documents (see below)
  AppStore/Screenshots/           App Store screenshots (iPhone 6.9", iPad 13")
Other Info.plist values (display name, category, orientations, export compliance) are set as build settings in the project, not in Info.plist.

Adding or editing a saint
Add an entry to saints.json. Required fields: id, name, title, category (apostle, doctor, martyr, mystic, or modern), feastMonth, feastDay, lifespan, origin, patronOf (may be empty), summary, biography. Optional: quote, prayer.
Add a matching entry to saints.es.json with the same id. Without one, that saint shows in English when Spanish is selected.
Optional portrait: add an image set named exactly like the id under Assets.xcassets/Saints/ and add its artist, license, and source to ImageCredits.json. Without one, the saint shows a category icon. Use only public-domain or properly licensed images.
Interface labels live in UIText in Models/AppLanguage.swift (English text is the key).
Saints are sorted alphabetically by name, ignoring "St."/"San"/"Santa", so entry order in the file doesn't matter.

Content notes
Saint text, Spanish translations, and prayers were drafted with AI assistance and have not been reviewed by a theologian or a native Spanish speaker. Review them before release.
Prayers are original texts written for the app; they are not official liturgical prayers.
Feast days follow the General Roman Calendar; some countries and orders celebrate on other dates.
Portraits are public-domain or CC0 images from Wikimedia Commons.
Documents
File	What it is
docs/RELEASE_CHECKLIST.md	Pre-release review results and the remaining steps to submit
docs/FACT_CHECK.md	Proofreading checklist for every saint (dates, patronage, claims)
docs/AUTO_CHECK.md	Results of the automated cross-check against Wikidata/Wikipedia
docs/APP_STORE.md	Draft App Store listing (English and Spanish), keywords, settings, screenshots
docs/PRIVACY.md	Privacy policy draft (host it at a public URL for App Store Connect)
AppStore/Screenshots/README.md	What each screenshot shows and where to upload it
License and credits
App code and text © 2026 Luminae Crown Studio LLC (choose and add a license before publishing the source). Portrait credits are in SaintsCompanion/Resources/ImageCredits.json and in the app (Saints tab → ⓘ).
