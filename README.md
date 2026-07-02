# Web Meeting Booking Board

Browser-based booking board for post-exhibition web meetings.

## Overview

- Date range: July 1-31, 2026
- Weekdays are bookable
- Saturdays and Sundays are visible on the calendar but not selectable
- Daily slots: 10:00, 11:00, 13:00, 14:30, 16:00
- Staff: 島村, 小林, 高木, 見目, 藤之原, 奥田
- Storage: browser `localStorage`
- Saved fields: selected date/time, staff, and meeting memo only

## Notes

Reservation data stays in the browser used at the venue. It is not sent to
GitHub or any server. Personal information fields are intentionally not
collected on the public booking screen.
