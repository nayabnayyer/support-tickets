# 🎫 Support Ticket Dashboard

A lightweight internal helpdesk tool built with Python and Streamlit. Create tickets, edit their status in a live table, and track resolution trends through auto-updating charts — all in one page.

![Python](https://img.shields.io/badge/Python-3.7+-blue?style=flat-square&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.0+-red?style=flat-square&logo=streamlit&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-1.0+-purple?style=flat-square&logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 📸 What It Does

| Feature | Description |
|---|---|
| ➕ Create tickets | Submit new issues with a priority level |
| ✏️ Edit live | Double-click any cell to update status or priority |
| 📊 Auto charts | Bar and pie charts update the moment you edit the table |
| 📈 KPI metrics | Open tickets, first response time, avg resolution time |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- pip

### Installation

```bash
# Clone the repo
git clone https://github.com/your-username/support-tickets.git
cd support-tickets

# Install dependencies
pip install streamlit pandas numpy altair

# Run the app
streamlit run tickets.py
```

Open your browser at `http://localhost:8501`.

---

## 🕹️ How to Use

**Adding a ticket**
1. Scroll to the **Add a ticket** section
2. Describe the issue and set a priority (High / Medium / Low)
3. Hit **Submit** — the ticket appears at the top of the table instantly

**Editing tickets**
- Double-click any **Status** or **Priority** cell to change it via dropdown
- Sort the table by clicking any column header
- Charts at the bottom update automatically as you edit

**Reading the stats**
- **Ticket status per month** — grouped bar chart showing Open / In Progress / Closed over time
- **Current ticket priorities** — donut chart of High / Medium / Low breakdown

---

## 🧠 How It Works

On first load, 100 fake tickets are generated and stored in `st.session_state` so they persist across reruns:

```python
if "df" not in st.session_state:
    st.session_state.df = generate_fake_tickets()
```

New tickets submitted via the form are prepended to the dataframe:

```python
st.session_state.df = pd.concat([df_new, st.session_state.df], axis=0)
```

The editable table uses Streamlit's `st.data_editor`, which returns the live-edited dataframe directly into the Altair charts — no refresh needed.

---

## 📁 Project Structure

```
support-tickets/
│
├── tickets.py     # Entire app — one file
└── README.md      # You're reading this
```

---

## 🔭 Future Ideas

- Connect to a real database (SQLite / PostgreSQL)
- Assign tickets to team members
- Filter and search the ticket table
- Email notifications on ticket updates
- Authentication so only your team can access it

---

## 👩‍💻 Author

**Nayab Nayyer**  
[GitHub](https://github.com/your-username) · [LinkedIn](https://linkedin.com/in/your-profile)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
