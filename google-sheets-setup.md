# Google Sheets RSVP Setup for Your Wedding Website

This file shows the exact steps to connect the website to a Google Sheet using Google Apps Script.

## 1. Create a new Google Sheet
- Open Google Sheets and create a new blank sheet.
- In row 1, add this header row across columns A–E:
  - `Full Name`
  - `Number of Guests`
  - `Attendance`
  - `Message`
  - `Submitted At`

## 2. Open Apps Script
- In the Google Sheet, go to `Extensions` > `Apps Script`.
- If there is existing code, replace it with the code below.

```javascript
function doPost(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    var data = JSON.parse(e.postData.contents || '{}');
    sheet.appendRow([
      data.fullName || '',
      data.guestCount || '',
      data.attendance || '',
      data.message || '',
      data.submittedAt || ''
    ]);
    return ContentService
      .createTextOutput(JSON.stringify({ status: 'success' }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    return ContentService
      .createTextOutput(JSON.stringify({ status: 'error', message: error.message }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

## 3. Deploy as Web App
- Click `Deploy` > `New deployment`.
- Select `Web app` as the deployment type.
- For `Execute as`, choose `Me`.
- For `Who has access`, choose `Anyone`.
- Click `Deploy` and copy the Web App URL.

> If you see the message “The Web App requires you to authorize access to your data,” this is normal.
> - Click `Continue`.
> - Choose your Google account.
> - Review the permissions and allow access.
> - If you see “This app isn't verified,” click `Advanced` and then `Go to project (unsafe)` because it's your own script.

## 4. Paste the Web App URL into the website
- Open `index.html`.
- Find the line near the top of the script:

```js
const GOOGLE_SHEETS_ENDPOINT = "PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

- Replace the placeholder value with your copied Web App URL.

## 5. Test the form
- Open the website in a browser.
- Fill out the RSVP form and submit.
- Verify the response appears as a new row in your Google Sheet.

---

> Note: I updated the website to use the neutral linen/khaki/camel/cocoa/espresso palette and improved the invitation-card animation.

If you want, I can also add a second form to store meal preferences or contact phone numbers.
