
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

## ⚙️ Technologies & Frameworks

| Layer | Technology | Purpose |
|-------|-------------|----------|
| **Frontend** | React.js (Vite/CRA) | Build interactive UI |
| **Backend** | FastAPI (Python 3.10+) | Handle API logic and calculations |
| **Database** | MongoDB (Atlas or Local) | Persist scenarios and leads |
| **Styling** | CSS / Tailwind | Responsive and clean interface |
| **Deployment** | Render / Vercel | Hosting (optional) |

---

## 💡 Key Features & Functionality

### 1️⃣ Quick Simulation
- Accepts invoice volume, staff size, wages, error rate, etc.
- Computes and displays:
  - Monthly savings
  - Payback period
  - ROI (%)
  - Cumulative and net savings

### 2️⃣ Scenario Management
- Save simulations by name.
- Retrieve, update, and delete saved scenarios.

### 3️⃣ Report Generation (Email-Gated)
- Requires email before download.
- Generates and serves HTML/PDF report.
- Email recorded in `leads` collection for analytics.

### 4️⃣ Favorable ROI Logic
- Backend constants ensure automation **always shows positive ROI**.
- Bias factor `min_roi_boost_factor` amplifies savings slightly.

---

## 🧮 Example Calculation Logic

```python
labor_cost_manual = num_ap_staff * hourly_wage * avg_hours_per_invoice * monthly_invoice_volume
auto_cost = monthly_invoice_volume * automated_cost_per_invoice
error_savings = (error_rate_manual - error_rate_auto) * monthly_invoice_volume * error_cost
monthly_savings = ((labor_cost_manual + error_savings) - auto_cost) * min_roi_boost_factor

cumulative_savings = monthly_savings * time_horizon_months
net_savings = cumulative_savings - one_time_implementation_cost
payback_months = one_time_implementation_cost / monthly_savings
roi_percentage = (net_savings / one_time_implementation_cost) * 100
