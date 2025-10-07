
- **Frontend (React):**
  - Displays dynamic form for inputs.
  - Shows instant results from API responses.
  - Provides Save / Load / Delete scenario options.
  - Gated report download after entering email.

- **Backend (FastAPI):**
  - REST API handles calculations and CRUD operations.
  - Applies backend constants for automation cost bias.
  - Validates inputs and manages data persistence in MongoDB.

- **Database (MongoDB):**
  - Stores saved scenarios and user leads (emails).
  - Collections:
    - `scenarios`: stores user inputs and computed results.
    - `leads`: stores emails collected during report generation.

---

##  Technologies & Frameworks

| Component | Technology | Purpose |
|------------|-------------|----------|
| **Runtime** | Node.js | Execute backend JavaScript |
| **Framework** | Express.js | REST API server |
| **Database** | MongoDB (Mongoose ODM) | Persist scenarios and email leads |
| **Validation** | Native JS validation  | Validate incoming data |
| **Environment** | dotenv | Manage environment variables |
| **CORS** | cors | Allow frontend-backend communication |
| **PDF (Optional)** | pdfkit / html-pdf | Generate downloadable reports |
---

##  Key Features & Functionality

### 1️ Quick Simulation
- Accepts invoice volume, staff size, wages, error rate, etc.
- Computes and displays:
  - Monthly savings
  - Payback period
  - ROI (%)
  - Cumulative and net savings

### 2️ Scenario Management
- Save simulations by name.
- Retrieve, update, and delete saved scenarios.

### 3️ Report Generation (Email-Gated)
- Requires email before download.
- Generates and serves HTML/PDF report.
- Email recorded in `leads` collection for analytics.

### 4️ Favorable ROI Logic
- Backend constants ensure automation **always shows positive ROI**.
- Bias factor `min_roi_boost_factor` amplifies savings slightly.


