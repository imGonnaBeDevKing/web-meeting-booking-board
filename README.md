# WEB会議予約

Browser-based booking board for post-exhibition web meetings.

## Overview

- Date range: July 1-31, 2026
- Weekdays are bookable, excluding holidays
- Saturdays, Sundays, and holidays are visible on the calendar but not selectable
- Closed holiday: July 20, 2026 (Marine Day / 海の日)
- Daily slots: 10:00, 11:00, 13:00, 14:30, 16:00
- Staff: 島村, 小林, 高木, 見目, 藤之原, 奥田
- Storage: Firebase Firestore, collection `reservations`
- Booked slots remain visible as unavailable and cannot be selected again
- Tap a booked slot to review the saved memo in read-only mode
- Desktop calendar cards show per-time availability chips for quick scanning
- Social preview image for Teams/LINE: `assets/og-image.jpg`
- Saved fields: selected booking date/time, staff, memo date/time, and meeting memo only

## Firebase / Firestore

- Hosting remains GitHub Pages. Firebase Hosting is not used.
- Firebase Project ID: `web-meeting-booking-board`
- Firestore database: `(default)`
- Firestore collection: `reservations`
- Document ID: `{staff}_{date}_{time}`, for example `島村_2026-07-03_10:00`
- The page uses `doc(db, "reservations", reservationId)` and `setDoc`; `addDoc` is not used.
- `onSnapshot` watches `reservations` so multiple devices update in real time.
- Firestore rules should allow read/create only and deny update/delete.
- Personal information fields are intentionally not collected or saved.

Saved fields are limited to:

- `staff`
- `date`
- `time`
- `datetimeLabel`
- `memoDate`
- `memoTime`
- `memoTimestampLabel`
- `memo`
- `createdAt`
- `updatedAt`

The client must not send these personal information keys:

- `company`
- `name`
- `email`
- `tel`
- `phone`
- `customerName`
- `contact`

## Verification

1. Open the GitHub Pages URL on two different devices or browser windows.
2. Select the same staff member on both devices.
3. On one device, choose an available weekday slot, enter memo date/time and the meeting memo, then confirm the booking.
4. Confirm that the same slot disappears from the other device without reloading.
5. In Firestore Console, confirm that a document was created in `reservations` with the fixed ID format `{staff}_{date}_{time}`.
6. Try the same staff/date/time again and confirm it cannot be booked twice.
