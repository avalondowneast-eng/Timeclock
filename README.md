# Time Clock

A simple time clock for your phone. Tap **Clock In** and **Clock Out**, and the app keeps a record of every shift and works out your pay, including overtime, weekend, holiday and night-shift pay.

It is a single web page (`index.html`). There is nothing to install from an app store, and there is no account or server. Your records stay on your own phone.

## Features

- Large green **Clock In** and red **Clock Out** buttons.
- A confirmation box before clocking in, clocking out, saving rates or deleting all records, to prevent accidental taps.
- A **pay rate** field and a **night shift differential** field on the main screen.
- A **View Records** screen with one row per shift and a totals row.
- **Edit**, **delete** and **add** shifts, to fix a forgotten clock-in or clock-out.
- **Export CSV** to copy or save your records into a spreadsheet.
- Works on iPhone (Safari) and Android (Chrome), and can be added to the home screen like an app.

## Records table columns

| Column | Meaning |
|---|---|
| Date Worked | The date the shift started |
| Day of Week | Mon, Tue, and so on |
| Time In / Time Out | Clock-in and clock-out times |
| Total Time Worked | Hours and minutes in the shift |
| Overtime (over 8 h/day) | Minutes worked after 8 hours in that calendar day |
| Weekend Time | Minutes worked on Saturday or Sunday (not holidays) |
| Holiday Time | Minutes worked on one of the 11 holidays below |
| Hourly Pay Rate | The base rate in effect for the shift (a range if the rate changed mid-shift) |
| Night Shift Differential ($/h) | Shown only if the shift includes hours between 6 pm and 6 am |
| Total Pay Earned | Pay for the shift, using all the rules below |

The Overtime, Weekend and Holiday columns can overlap, so they will not necessarily add up to the Total.

## Pay rules

Pay is calculated **minute by minute**, and each minute is classified separately.

**Pay rate**
- The rate in effect at each minute is used.
- When you save a new rate, it applies from that moment forward. Earlier time keeps the old rate.
- Time before the first saved rate uses the first rate.

**Overtime (by calendar day, midnight to midnight, across all shifts that day)**
- Hours 0 to 8: regular pay, 1 times the rate.
- Hours 8 to 10: **1.5 times** the rate (assumed overtime multiplier).
- Hours over 10: **2 times** the rate, or **1.5 times** in December.

**Weekends**
- Saturday and Sunday: **1.5 times** the rate.

**Holidays at 2.5 times the rate**
- New Year's Day (Jan 1)
- Memorial Day (last Monday in May)
- Independence Day (Jul 4)
- Labor Day (first Monday in September)
- Thanksgiving (fourth Thursday in November)
- Christmas Day (Dec 25)

**Holidays at 2 times the rate**
- Martin Luther King Jr. Day (third Monday in January)
- Presidents' Day (third Monday in February)
- Juneteenth (Jun 19)
- Columbus Day (second Monday in October)
- Veterans Day (Nov 11)

A holiday that falls on a weekend counts as a holiday. Holidays are matched to the calendar date only. A holiday your employer observes on a different day is not recognized.

**Overlapping rules**
- For each minute, the **highest** applicable multiplier is used. Multipliers do not stack.
- Example: overtime on a 2.5 times holiday pays 2.5 times.

**Night shift differential**
- Any minute between **6 pm and 6 am** earns the differential (default $1.30 per hour, editable).
- The differential is added **after** the multiplier and is not itself multiplied.
- Per-minute pay = (rate x multiplier + differential if night) / 60.
- The differential is one value. Changing it recalculates all records, including past ones.

**Worked example** (rate $20, differential $1.30): Tuesday 9 am to 8 pm is 11 hours.
- 9 am to 5 pm: 8 hours x $20 = $160
- 5 pm to 7 pm: 2 hours x $30 = $60
- 7 pm to 8 pm: 1 hour x $40 = $40
- Night differential, 6 pm to 8 pm: 2 x $1.30 = $2.60
- Total: **$262.60**

## How to use it

**First-time setup**
1. Type your hourly pay rate in the **Current pay rate** field.
2. Check the **Night shift differential** amount, and change it if needed.
3. Tap **Save rates**, then confirm.

**Every shift**
1. Tap **Clock In** and confirm when you start.
2. Tap **Clock Out** and confirm when you finish.

**View your records**
- Tap **View Records**. Swipe sideways to see all columns. The last row shows totals.

**Fix a mistake**
- **Edit a shift:** In View Records, tap **Edit** on its row, change the time in or out, and tap **Save changes**.
- **Delete a shift:** Open it with Edit, then tap **Delete this shift** and confirm.
- **Forgot to clock in:** Tap **Add missed shift** and enter both times.
- **Forgot to clock out:** While a shift is open, tap **Edit this open shift** and enter the time you left.
- The time out must be after the time in. Only one shift can be open at a time.

**Change your pay rate**
- Type the new rate, tap **Save rates**, and confirm. The new rate applies from that moment on.

**Export your data**
- In View Records, tap **Export CSV**. The app offers the file for saving or sharing. If that is not available, it copies the CSV so you can paste it into Notes, Mail or a spreadsheet.
- The export contains your shifts and pay. It does not contain your rate history, so keep a note of your rates.

## Install on your phone

**iPhone:** Open the web address in **Safari**, tap the **Share** icon, choose **Add to Home Screen**, then tap **Add**.

**Android:** Open the web address in **Chrome**, tap the **menu** (three dots), then choose **Add to Home screen** or **Install app**.

Always open the app from the same place. The home-screen icon and a browser tab can keep separate saved data.

## Publishing with GitHub Pages

1. Name the file `index.html` and upload it to a **public** GitHub repository.
2. In the repository, go to **Settings**, then **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
4. After a minute or two, your site is live at `https://YOURUSERNAME.github.io/REPOSITORY-NAME/`.
5. To update the app, upload a new `index.html` to the same repository.

## Data and privacy

- Records and rates are stored in the browser on the phone you use. They are not sent anywhere and cannot be seen from another device.
- Clearing browser data, deleting the home-screen icon, or tapping **Clear all records** deletes your records. Export to CSV regularly as a backup.
- Anyone who knows the web address can open the app, but they would see only their own empty data.

## Limitations

- Times use the phone's clock and time zone.
- Only completed shifts appear in the records table.
- Holidays use fixed calendar rules, with no observed-date adjustments.
- Export cannot run on a schedule, and records cannot be imported back from a CSV.
- This app is a personal record-keeping aid. Check its figures against your employer's payroll and written pay policies, and confirm the assumptions above, especially the 1.5 times overtime rate and the highest-multiplier-wins rule.
