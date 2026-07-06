# DollarTracker Stable v3

Local-only mobile ledger app.

## Important fixes

- Balance loads from storage immediately on first open.
- USD/KHR choice stays saved after refresh/app close.
- Copy button has 3 layers:
  1. Clipboard API
  2. iOS textarea fallback
  3. Manual prompt fallback
- Clear All Records uses a tap-twice system, not browser confirm.
- Records migrate from older Wifey Money/DollarTracker storage keys.
- Service worker now uses network-first for app files to reduce stale cache bugs.
- Flag paths are PNG:
  - `flag-en.png`
  - `flag-kh.png`

## Upload these files

- index.html
- styles.css
- app.js
- manifest.webmanifest
- service-worker.js
- icon.svg
- flag-en.png
- flag-kh.png
- README.md

## If iPhone still shows old behavior

It means iOS is still running old cached JavaScript. Delete the Home Screen app and clear the website data for the GitHub Pages domain, then open and add it again.


## v3.0.1 Text field fix

- Disabled autocomplete/autocorrect/spellcheck on the transaction form.
- Draft description now saves on input, change, and blur.
- This reduces iPhone/PWA cases where a previous description like AC comes back after typing AC.


## v3.1 Simple PIN + Editable History

Simple stable additions only:
- Added simple PIN protection for edit, delete, and clear records.
- Skipped Face ID/passkey for now to avoid browser/PWA complexity.
- Added editable history records.
- History record amounts now display their original recorded amount/currency.
- Added `exchangeRateAtEntry` so changing current exchange rate does not rewrite history amounts.


## v3.2 Simple Features

Added low-risk practical features:
- Categories for records.
- Monthly Summary card.
- Quick Description chips.
- Edit History Log for changed records.
- PIN section now hides the PIN input after PIN is set.
- History money-in amounts no longer show `+`.
- Money-in history amount is green.
- History amounts remain locked to the original recorded amount/currency.


## v3.3 Bank PIN + Calculator

Careful larger update:
- Flag images moved to root folder: `flag-en.png`, `flag-kh.png`.
- No `assets/` folder is required anymore.
- Removed the old bank wording everywhere; quick descriptions use AC/ACLEDA only.
- Added bank-style custom PIN setup with 4 PIN or 6 PIN choice.
- PIN entry uses an in-app number pad, not the phone letter keyboard.
- Protected unlock session lasts 5 minutes while the app is open.
- Unlock resets when the app is closed/backgrounded/reopened.
- Added Lock Now button.
- Added calculator inside the Add page, not the navbar.
- Calculator supports USD/KHR and fills the amount field.
- KHR uses whole Riel only, no decimals.
- Navbar active state now slides like a smooth dragging pill.


## v3.3.1 Rechecked Patch

- Fixed KHR backup/import edge case:
  if a record has `exchangeRateAtEntry` but no `amountUSD`, migration now uses the entry rate, not the current settings rate.
- Bumped app version and service worker cache again.
- Re-ran static and logic checks before delivery.


## 3.4.0-phase1-deepfix-final

Final Phase 1 deepfix:
- Rebuilt from stable v3.3.1.
- Replaced the entire old v3.3 PIN/calculator CSS block.
- Removed PIN/security UI and logic.
- Kept calculator, but made the open button SVG icon-only.
- Used the approved chrome dollar PNG icon for app icons.
- Used user-provided root language flags.


## 3.4.0-phase2-history-filter

Phase 2: Cleaner History page
- Search stays visible on History.
- All/In/Out chips stay visible.
- From date, To date, Sort, Clear Filters moved into a bottom sheet.
- Added Filter button with active state when advanced filters are applied.
- Confirmed no old PIN/security logic was present before building.


## 3.4.0-phase3-performance

Phase 3: Performance cleanup
- Debounced History search rendering only.
- Amount, date, sort, transaction, and settings inputs still update immediately.
- `translateUI()` no longer runs inside every normal render.
- Translations still run on boot, page change, and language change.
- Built from the clean Phase 2 History Filter version after checking no PIN/security leftovers.


## 3.4.0-phase4-backup-calc-polish

Phase 4: Backup reminder + calculator polish
- Adds a non-blocking backup reminder banner on Home.
- Reminder appears when records exist and no backup exists, or last backup is 7+ days old.
- Dismiss hides the reminder for the day.
- Export Backup from the banner updates the backup date and hides the reminder.
- Calculator backspace key now uses an iOS-style delete/backspace SVG icon in the requested slot.
- Built from Phase 3 after checking no PIN/security leftovers.


## 3.4.0-phase5-budget-caps

Phase 5: Category budget caps
- Adds monthly budget caps for Food, Transfer, Shopping, Transport, Savings, and Other.
- Budgets are stored internally in USD in `settings.categoryBudgets`.
- Budget inputs display in the current USD/KHR mode.
- KHR budget inputs use whole Riel display.
- Home shows monthly budget progress using this month's Out records.
- Built from Phase 4 after checking no PIN/security leftovers.


## 3.4.0-phase6-categories-chart

Phase 6: Manageable categories + monthly category breakdown
- Categories can be added, renamed, removed, and reset to defaults.
- Other is protected and cannot be removed.
- Removing a category moves existing records in that category to Other.
- Resetting categories restores default categories and moves custom-category records to Other.
- Budgets follow the current category list.
- Added This Month category breakdown bar chart.
- Built from Phase 5 after checking no PIN/security leftovers.
