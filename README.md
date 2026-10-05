Saint-Clopedia
A warm, offline encyclopedia of Catholic saints for iPhone and iPad, in English and Spanish. Built with SwiftUI by Luminae Crown Studio LLC.

132 saints: apostles and early Church, martyrs, Doctors of the Church, mystics and religious, modern saints
Today tab: the saint of the day (or the feast being celebrated), plus upcoming feasts
Saints tab: alphabetical, grouped by category, searchable by name, patronage, or place (accent-insensitive)
Each saint: portrait, biography, feast day, years lived, birthplace, patronage, and a short prayer you can share
Favorites: saved on the device
EN | ES toggle at the top of each main screen; the choice is remembered, and Spanish is the default on Spanish-language devices
Design: parchment, burgundy, and gold with serif type; Dark Mode; Dynamic Type; animated splash screen
Private: no accounts, ads, analytics, or network access
Requirements
Xcode 26 or later (developed with Xcode 27)
iOS 17.0 or later
No third-party dependencies
Run it
Open SaintClopedia.xcodeproj in Xcode.
Choose an iPhone simulator and press Run. (Source folders are synced to the project, so new files are picked up automatically.)
To run on a device or archive for the App Store, select your team under Signing & Capabilities first.
Command-line build:

xcodebuild -project SaintClopedia.xcodeproj -scheme SaintClopedia \
  -destination 'platform=iOS Simulator,name=iPhone 17 Pro' CODE_SIGNING_ALLOWED=NO build
Project structure
Info.plist                      Launch screen (parchment + cross) and export-compliance key
SaintClopedia/
  SaintClopediaApp.swift        App entry, splash, midnight/foreground date refresh
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
Adding or editing a saint
Add an entry to saints.json. Required fields: id, name, title, category (apostle, doctor, martyr, mystic, or modern), feastMonth, feastDay, lifespan, origin, patronOf (may be empty), summary, biography. Optional: quote, prayer.
Add a matching entry to saints.es.json with the same id. Without one, that saint shows in English when Spanish is selected.
Optional portrait: add an image set named exactly like the id under Assets.xcassets/Saints/ and add its artist, license, and source to ImageCredits.json. Without one, the saint shows a category icon. Use only public-domain or properly licensed images.
Interface labels live in UIText in Models/AppLanguage.swift (English text is the key).
Content notes
Saint text, Spanish translations, and prayers were drafted with AI assistance and have not been reviewed by a theologian or a native Spanish speaker. Review them before release.
Prayers are original texts written for the app; they are not official liturgical prayers.
Feast days follow the General Roman Calendar; some countries and orders celebrate on other dates.
Portraits are public-domain or CC0 images from Wikimedia Commons.
Documents (docs/)
File	What it is
RELEASE_CHECKLIST.md	Pre-release review results and the remaining steps to submit
FACT_CHECK.md	Proofreading checklist for every saint (dates, patronage, claims)
AUTO_CHECK.md	Results of the automated cross-check against Wikidata/Wikipedia
APP_STORE.md	Draft App Store listing (English and Spanish), keywords, settings, screenshots
PRIVACY.md	Privacy policy draft (host it at a public URL for App Store Connect)
License and credits
App code and text © 2026 Luminae Crown Studio LLC (choose and add a license before publishing the source). Portrait credits are in Resources/ImageCredits.json and in the app (Saints tab → ⓘ).
