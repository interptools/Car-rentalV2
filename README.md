# Car Rental Fleet Management System (v4.0.0)

A static, multi-car rental system using HTML, Tailwind CSS, vanilla JavaScript, and Google Apps Script. This system handles customer bookings, vehicle availability calendars, email templates, and PDF agreement generation.

## System Architecture

- **`index.html`**: The public customer form. Includes a fleet dropdown, availability calendar, and the rental agreement.
- **`dashboard.html`**: The private owner dashboard. Includes a fleet filter, booking management, dynamic pricing, and PDF generation.
- **Google Apps Script**: The backend API that connects the frontend to Google Sheets.
- **Google Sheets**: The database storing all records.

*(Note: The JavaScript is written inline within the HTML files for easier management. There are no external .js files.)*

## Setup Instructions

### 1. Google Sheets & Apps Script
1. Create a new Google Sheet. Add a header column named exactly: **`Car ID`**
2. Go to **Extensions → Apps Script**.
3. Paste the backend code into `Code.gs`.
4. Go to **Project Settings → Script Properties** and add:
   - `SPREADSHEET_ID` (From your Google Sheet URL)
   - `ADMIN_KEY` (A secret password for your dashboard)
5. Click **Deploy → New deployment → Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Copy the `/exec` URL.

### 2. Frontend Configuration
Open both `index.html` and `dashboard.html` and find:
`const APPS_SCRIPT_URL = "..."`

Paste your new `/exec` URL inside the quotes.

### 3. Adding New Cars
To add a new car to the fleet:
1. Open `index.html`.
2. Scroll down to the `<script>` section and find the `CAR_CATALOG` object.
3. Duplicate the existing car block and update the details:
```javascript
"your_car_id": {
  id: "your_car_id",
  name: "Honda Civic 2024",
  plate: "XYZ 9876",
  color: "Red",
  image: "images/civic-red.jpg" 
}