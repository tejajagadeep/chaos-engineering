# Purchase Tracker — Flutter App Development Conversation

## 1. Initial idea

The goal is to build an Android application for tracking purchases and expenses.

The app is called **Purchase Tracker**.

The main use case is buying touring accessories over time. Items can be added, edited, removed, purchased at different prices, and new items can be added whenever needed. The application should automatically recalculate totals whenever the list changes.

---

## 2. Example touring accessories

Initial list provided:

| Item | Price |
|---|---:|
| Riding jacket | ₹8,000 |
| Shoes ×2 | ₹10,000 |
| Knee protector ×2 | ₹6,000 |
| Gloves | ₹2,000 |
| Tent | ₹2,500 |
| Inflated Bed | ₹3,000 |
| Steel luggage | ₹23,000 |
| Other luggage bags | ₹30,000 |
| DJI camera | ₹58,000 |
| EJEAS V6Pro+ Intercom | ₹6,250 (₹6,000 + ₹250 fitting) |
| Fog lights | ₹20,000 |
| Tyre inflator | ₹3,000 |
| Bike repair kit | ₹5,000 |
| Helmet | ₹5,300 |
| Nylon 700x6x2 | ₹8,000 |

The originally stated grand total was **₹1,96,000**.

The application should calculate totals automatically rather than requiring manual recalculation.

---

## 3. App concept

The application should not be just a static calculator.

It should work as a dynamic purchase tracker:

- Add purchases
- Edit purchases
- Delete purchases
- Set quantity
- Set estimated/planned price
- Record actual purchase price
- Mark items as purchased or pending
- Automatically calculate totals
- Add new items at any time
- Store the data locally on the phone

---

## 4. Proposed Home Screen

Example:

```text
┌──────────────────────────────┐
│      Purchase Tracker        │
├──────────────────────────────┤
│                              │
│  Planned       Purchased     │
│  ₹1,96,000        ₹0         │
│                              │
│  Remaining                   │
│  ₹1,96,000                  │
│                              │
│  Your Purchases              │
│                              │
│  No purchases yet            │
│                              │
│                       [+]    │
└──────────────────────────────┘
```

A more complete version can show:

```text
PURCHASE TRACKER

Total Budget       ₹2,50,000
Amount Spent       ₹72,300
Remaining          ₹1,77,700

Items
────────────────────────
✓ Riding Jacket          ₹8,000
✓ Shoes ×2              ₹10,000
✓ Knee Protector ×2      ₹6,000
✓ Gloves                 ₹2,000
  Tent                   ₹2,500
  Inflated Bed           ₹3,000
  Steel Luggage         ₹23,000
  Other Luggage Bags    ₹30,000
  DJI Camera            ₹58,000
  EJEAS V6Pro+           ₹6,250
  Fog Lights            ₹20,000
  Tyre Inflator          ₹3,000
  Bike Repair Kit        ₹5,000
  Helmet                 ₹5,300
  Nylon 700x6x2          ₹8,000

────────────────────────
TOTAL                  ₹1,96,000
```

---

## 5. Add Purchase screen

When the user presses `+ Add Purchase`, the app can show:

```text
Add Purchase

Item Name
[ DJI Camera                  ]

Quantity
[ 1 ]

Price per item
[ ₹58,000                    ]

Category
[ Camera ▼ ]

Purchased?
[ ○ No   ● Yes ]

             [ SAVE ]
```

The app calculates:

```text
Quantity × Price per item = Item Total
```

Example:

```text
2 × ₹5,000 = ₹10,000
```

---

## 6. Editing a purchase

The user can tap an existing item and change its details.

Example:

```text
DJI Camera

Quantity
1

Price
₹52,000

Total
₹52,000

[ Save Changes ]
[ Delete Item ]
```

When the price changes from ₹58,000 to ₹52,000, the overall total automatically changes.

---

## 7. Planned price vs actual price

A useful feature is to maintain both planned and actual purchase prices.

Example:

| Item | Planned | Actual | Status |
|---|---:|---:|---|
| Riding Jacket | ₹8,000 | ₹7,500 | Purchased |
| Shoes ×2 | ₹10,000 | ₹9,200 | Purchased |
| Tent | ₹2,500 | — | Pending |
| DJI Camera | ₹58,000 | ₹54,999 | Purchased |

This allows the app to show:

```text
PLANNED TOTAL
₹1,96,000

ACTUAL SPENT
₹71,699

REMAINING PURCHASES
₹1,24,301
```

This is more useful than a simple expense calculator because it shows how much was actually spent compared with the original plan.

---

## 8. Purchase history

The app can maintain a history such as:

```text
28 Sep 2026
DJI Camera
₹54,999

25 Sep 2026
Riding Jacket
₹7,500

20 Sep 2026
Shoes ×2
₹9,200
```

This provides a record of where money was spent.

---

## 9. Categories

Possible categories for touring purchases:

- Riding Gear
- Camping
- Camera / Electronics
- Luggage
- Bike Tools
- Bike Accessories
- Safety
- Other

The app can later show category totals:

```text
CATEGORY SPENDING

Riding Gear       ₹30,700
Camping            ₹5,500
Electronics       ₹61,250
Luggage            ₹53,000
Bike Accessories  ₹23,000
Tools              ₹8,000
Safety             ₹5,300
────────────────────────
Total            ₹1,86,750
```

---

## 10. Possible future features

The application can be expanded later with:

### Budget

```text
Budget: ₹2,50,000
Spent:  ₹72,300
Left:   ₹1,77,700
```

### Search

Search for items such as:

```text
camera
helmet
luggage
```

### Sorting

Possible sorting options:

- Cheapest
- Most expensive
- Purchased
- Pending

### Notes

Example:

```text
Buy after October salary
```

### Payment methods

- Cash
- UPI
- Credit Card
- Debit Card

### Receipt/photo

Attach a photo of the purchase receipt.

### Export

Export purchase information to:

- Excel/CSV
- PDF

---

# Flutter Development

## 11. Technology choice

The selected technology is **Flutter**.

Flutter is free and open-source.

The application can be developed using:

- Flutter
- Dart
- Android Studio
- Android SDK
- Android Emulator or a physical Android phone

For the first version, local storage can be used so that the application works offline without requiring a server.

---

## 12. Basic project structure

The planned Flutter project can look like:

```text
purchase_tracker/
│
├── android/
├── ios/
├── lib/
│   └── main.dart
├── test/
├── web/
├── windows/
├── pubspec.yaml
└── README.md
```

The main application code will be inside the `lib` directory.

The initial entry point is:

```text
lib/main.dart
```

---

# Windows Development Setup

## 13. Development environment

The development computer is a **Windows PC**.

The recommended tools are:

- Flutter SDK
- Android Studio
- Android SDK
- Flutter plugin for Android Studio
- Dart plugin
- Android phone or Android Emulator

---

## 14. Flutter installation

Flutter can be downloaded from:

https://flutter.dev/

After installing Flutter, verify the installation from Command Prompt or Android Studio Terminal:

```bash
flutter doctor
```

Flutter Doctor checks the development environment.

A healthy setup will show entries similar to:

```text
[✓] Flutter
[✓] Android toolchain
[✓] Android Studio
[✓] Connected device
```

Some warnings may appear initially and can be fixed individually.

---

## 15. Android Studio

Android Studio can be downloaded from:

https://developer.android.com/studio

During setup, make sure the Android development components are installed.

After installing Android Studio, the Flutter plugin can be installed from:

```text
Android Studio
    ↓
Settings
    ↓
Plugins
    ↓
Marketplace
    ↓
Search: Flutter
```

The Dart plugin may also be requested.

---

# Running the App

## 16. Using an Android phone

For testing on a physical Android phone:

1. Enable Developer Options.
2. Enable USB debugging.
3. Connect the phone to the Windows PC.
4. Accept the USB debugging authorization prompt.

To check whether Flutter can see the phone:

```bash
flutter devices
```

Then run:

```bash
flutter run
```

Alternatively, select the phone from Android Studio's device selector and press the Run button.

---

## 17. Android Emulator

A physical phone is not required.

Android Studio can create an emulator through:

```text
Android Studio
    ↓
Device Manager
    ↓
Create Virtual Device
    ↓
Select a device
    ↓
Start
```

Then run:

```bash
flutter run
```

---

# Important Issue Encountered

## 18. Kotlin `.kt` files appeared

At one point the project showed Kotlin `.kt` files instead of Dart files.

`.kt` files are Kotlin files and are normal in the Android portion of a Flutter project, but the main Flutter application should contain Dart files.

A correct Flutter project should contain:

```text
lib/
    main.dart
```

If there is no `lib/main.dart`, it is likely that an Android/Kotlin project was created instead of a Flutter project.

---

## 19. Creating the correct Flutter project

In Android Studio:

```text
File
    ↓
New
    ↓
New Flutter Project
    ↓
Flutter
```

Set:

```text
Project name:
purchase_tracker

Application name:
Purchase Tracker
```

The Flutter SDK path must point to the installed Flutter SDK, for example:

```text
C:\srclutter
```

After creation, the project should contain:

```text
purchase_tracker/
│
├── android/
├── ios/
├── lib/
│   └── main.dart
├── test/
├── web/
├── windows/
├── pubspec.yaml
└── README.md
```

---

# Current Development Plan

The next development steps are:

## Step 1
Get the correct Flutter project running on Windows.

## Step 2
Replace the default Flutter counter application with the first Purchase Tracker screen.

## Step 3
Create the Purchase data model.

Example concept:

```text
Purchase
 ├── name
 ├── quantity
 ├── plannedPrice
 ├── actualPrice
 ├── category
 ├── purchased
 └── notes
```

## Step 4
Create the Add Purchase screen.

## Step 5
Implement automatic calculations.

For example:

```text
Item total = quantity × price
```

and:

```text
Planned total = sum of all planned item totals
```

```text
Actual spent = sum of purchased actual totals
```

```text
Remaining = Planned total - Actual spent
```

## Step 6
Add edit and delete functionality.

## Step 7
Add local database/storage.

## Step 8
Add categories, search, filtering, history and other features.

## Step 9
Improve the UI and user experience.

## Step 10
Build an Android APK/AAB and eventually publish the app if desired.

---

# Project Name

**Purchase Tracker**

The application is intended to be a practical personal purchase-management application, initially focused on touring accessories but designed so that it can later track any type of purchase.
