# KrishiConnect — Farmer to Buyer Marketplace

KrishiConnect is a responsive **MERN Stack application** designed to connect Indian farmers directly with wholesale and institutional buyers. Farmers can list harvested crops, buyers can request test samples to inspect quality, farmers can accept or reject sample requests, and buyers can subsequently place direct purchase requests.

The application features full multilingual interface switching across **6 languages**:
- **English** (en)
- **Telugu / తెలుగు** (te)
- **Hindi / हिन्दी** (hi)
- **Tamil / தமிழ்** (ta)
- **Kannada / ಕನ್ನಡ** (kn)
- **Malayalam / മലയാളം** (ml)

---

## 🌾 Tech Stack

- **Frontend**: React.js (with Vite)
- **Styling**: Tailwind CSS (Dark green `#14532d` / `#166534`, Emerald `#16a34a`, soft amber accents, clean white cards)
- **Backend**: Node.js & Express.js
- **Database**: MongoDB with Mongoose (with built-in offline resilient memory-store fallback)
- **Authentication**: JWT & bcryptjs password hashing
- **API Client**: Axios with Bearer token & cookie authorization
- **Routing**: React Router DOM (v6)
- **Icons**: Lucide React
- **Image Uploads**: Multer (Local storage for development in `server/uploads/`)
- **Language Switching**: `i18next` & `react-i18next` with JSON locale files

---

## 📁 Project Structure

```text
krishiconnect/
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/
│   │   │   │   └── LanguageSelector.tsx
│   │   │   ├── crops/
│   │   │   │   ├── RequestSampleModal.tsx
│   │   │   │   └── PurchaseCropModal.tsx
│   │   │   ├── layout/
│   │   │   │   ├── Navbar.tsx
│   │   │   │   ├── Footer.tsx
│   │   │   │   └── MainLayout.tsx
│   │   │   └── marketplace/
│   │   │       └── CropCard.tsx
│   │   ├── context/
│   │   │   └── AuthContext.tsx
│   │   ├── i18n/
│   │   │   ├── index.ts
│   │   │   └── locales/
│   │   │       ├── en/translation.json
│   │   │       ├── te/translation.json
│   │   │       ├── hi/translation.json
│   │   │       ├── ta/translation.json
│   │   │       ├── kn/translation.json
│   │   │       └── ml/translation.json
│   │   ├── pages/
│   │   │   ├── public/
│   │   │   │   ├── LandingPage.tsx
│   │   │   │   ├── MarketplacePage.tsx
│   │   │   │   ├── CropDetailPage.tsx
│   │   │   │   ├── LoginPage.tsx
│   │   │   │   ├── RegisterPage.tsx
│   │   │   │   ├── FarmerLoginPage.tsx
│   │   │   │   ├── BuyerLoginPage.tsx
│   │   │   │   ├── FarmerRegisterPage.tsx
│   │   │   │   └── BuyerRegisterPage.tsx
│   │   │   ├── farmer/
│   │   │   │   ├── FarmerDashboardPage.tsx
│   │   │   │   ├── FarmerUploadCropPage.tsx
│   │   │   │   ├── FarmerMyCropsPage.tsx
│   │   │   │   ├── FarmerSampleRequestsPage.tsx
│   │   │   │   └── FarmerPurchasesPage.tsx
│   │   │   └── buyer/
│   │   │       ├── BuyerDashboardPage.tsx
│   │   │       ├── BuyerSampleRequestsPage.tsx
│   │   │       └── BuyerOrdersPage.tsx
│   │   ├── services/
│   │   │   └── api.ts
│   │   ├── types/
│   │   │   └── index.ts
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── index.css
│   └── package.json
├── server/
│   ├── src/
│   │   ├── config/
│   │   │   ├── db.js
│   │   │   └── index.js
│   │   ├── controllers/
│   │   │   ├── authController.js
│   │   │   ├── cropController.js
│   │   │   ├── sampleController.js
│   │   │   └── purchaseController.js
│   │   ├── middleware/
│   │   │   ├── auth.js
│   │   │   ├── upload.js
│   │   │   └── errorHandler.js
│   │   ├── models/
│   │   │   ├── User.js
│   │   │   ├── Crop.js
│   │   │   ├── SampleRequest.js
│   │   │   ├── PurchaseRequest.js
│   │   │   └── memStore.js
│   │   ├── routes/
│   │   │   ├── auth.js
│   │   │   ├── crops.js
│   │   │   ├── samples.js
│   │   │   └── purchases.js
│   │   ├── tests/
│   │   │   └── test_flow.js
│   │   ├── app.js
│   │   └── server.js
│   ├── uploads/
│   └── package.json
├── .env.example
├── package.json
└── README.md
```

---

## 🚀 Quick Start Guide (Visual Studio Code)

### Prerequisites
- Node.js (v18 or higher installed)
- (Optional) MongoDB local service or MongoDB Atlas cluster

### 1. Clone & Open in VS Code
Open the root `krishiconnect` folder in Visual Studio Code.

### 2. Environment Configuration
Create `server/.env`:
```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://127.0.0.1:27017/krishiconnect
JWT_SECRET=krishiconnect_secret_key_2026
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:5173
```
*(If using MongoDB Atlas, ensure your current IP address or `0.0.0.0/0` is added in Atlas Network Access. Even if Atlas is not reachable, KrishiConnect automatically falls back to an integrated memory-store with pre-seeded demo data.)*

### 3. Install Dependencies
Open a terminal in VS Code:
```powershell
# In root directory:
npm install

# In server directory:
cd server
npm install

# In client directory:
cd ../client
npm install
```

### 4. Running the Application
You can run both Frontend and Backend concurrently from the root directory:
```powershell
npm run dev
```

Alternatively, run in two separate VS Code terminal tabs:
**Terminal 1 (Backend Server):**
```powershell
cd server
npm run dev
```
*Server runs at `http://localhost:5000`*

**Terminal 2 (Frontend Client):**
```powershell
cd client
npm run dev
```
*Client runs at `http://localhost:5173`*

---

## 🔑 Pre-Seeded Demo Accounts

You can immediately sign in with one click or enter credentials:

| Role | Portal Link | Email | Password |
|---|---|---|---|
| **Farmer** | `/farmer/login` | `farmer@krishi.com` | `Farmer@123` |
| **Buyer** | `/buyer/login` | `buyer@krishi.com` | `Buyer@123` |

---

## 🧪 Automated End-to-End Verification Test

To verify all 13 core workflows programmatically:
```powershell
cd server
node tests/test_flow.js
```
Expected output:
```text
🌱 Starting KrishiConnect Integration Verification Test...
✅ Health check: ok KrishiConnect — Farmer to Buyer Marketplace
✅ Farmer Register [201]: Farmer account created successfully
✅ Buyer Register [201]: Buyer account created successfully
✅ Farmer Upload Crop [201]: Organic Sona Masoori Rice
✅ Browse Marketplace [200]: Found 1 matching crop(s)
✅ Buyer Request Sample [201]: PENDING
✅ Farmer Incoming Samples [200]: 1 request(s)
✅ Farmer Accept Sample [200]: Updated to ACCEPTED
✅ Buyer Sample Tracking [200]: Current status is "ACCEPTED"
✅ Buyer Purchase Request [201]: Quantity: 10, Total: ₹34000
✅ Farmer Incoming Purchases [200]: 1 order(s)
✅ Farmer Accept Purchase [200]: Status is now ACCEPTED, Remaining stock: 40
✅ Buyer Order History [200]: Latest order status is "ACCEPTED" with total ₹34000

🎉 ALL 13 TEST STEPS PASSED WITH 100% SUCCESS!
```

---

## 🌐 Language Switching

The language dropdown is situated in the top navigation bar. It dynamically translates navigation menus, forms, dashboard statistics, buttons, modals, and status badges without page reload:
- English
- Telugu (తెలుగు)
- Hindi (हिन्दी)
- Tamil (தமிழ்)
- Kannada (ಕನ್ನಡ)
- Malayalam (മലയാളം)

Language preferences are automatically persisted in `localStorage` and restored upon browser refresh.

---

## 📡 API Endpoints

### Authentication
- `POST /api/auth/register` - Register Farmer or Buyer
- `POST /api/auth/login` - Authenticate & generate JWT
- `GET /api/auth/me` - Get logged-in user profile

### Crops
- `POST /api/crops` - Upload crop listing (Farmer)
- `GET /api/crops` - Browse crops with search & location filter (Public)
- `GET /api/crops/:id` - Get single crop details
- `GET /api/crops/my-crops` - Get crops listed by current farmer
- `PUT /api/crops/:id` - Update price, quantity, and details
- `DELETE /api/crops/:id` - Remove crop listing

### Sample Requests
- `POST /api/samples` - Submit sample request (Buyer)
- `GET /api/samples/my-requests` - Track submitted sample requests (Buyer)
- `GET /api/samples/incoming` - View incoming sample requests (Farmer)
- `PATCH /api/samples/:id/status` - Accept or reject sample request (Farmer)

### Purchase Requests
- `POST /api/purchases` - Submit wholesale purchase (Buyer, validates available stock)
- `GET /api/purchases/my-requests` - View purchase history / orders (Buyer)
- `GET /api/purchases/incoming` - View incoming purchase requests (Farmer)
- `PATCH /api/purchases/:id/status` - Accept or reject purchase request (Farmer, decrements inventory)
