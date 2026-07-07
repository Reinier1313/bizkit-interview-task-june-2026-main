# Technical Assessment Notes

### 1. Explanation of Fix (Task 2)
The original `rental_days` function calculated duration by subtracting dates directly (`to_date - from_date`), which evaluates to 0 days for same-day bookings and undercharges all accounts by one day. Because rentals are billed inclusively, I added `+ 1` to the timedelta day return statement in `app.py` to ensure accurate billing structures.

### 2. Double-Booking Failure Case
* **Existing Booking:** Canon DSLR Camera from 2026-01-10 to 2026-01-15
* **Example Wrongly Allowed:** 2026-01-09 to 2026-01-16 (An outer-bound wrap-around that bypassed the old conditional check entirely, but is now properly blocked).

### 3. AI Use Statement
I used Claude to double-check standard interval overlap logic statements and to audit all backend entry-points where the equipment maintenance rule needed to be applied. I verified the accuracy of the outputs manually by attempting conflicting test bookings on the frontend interface and reviewing the data saved to `bookings.json`.