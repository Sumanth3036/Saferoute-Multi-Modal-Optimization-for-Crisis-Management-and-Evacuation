# SafeRoute: Multi-Modal Optimization for Crisis Management and Evacuation

SafeRoute is an integrated disaster management system designed to enhance response efficiency during crises like floods and earthquakes. By leveraging machine learning, geospatial technologies, and multi-modal route optimization, the project provides real-time safe route guidance, predicts disaster severity, and facilitates efficient resource allocation to minimize casualties and damages.

## 🚀 Objective

The primary goal of this project is to create a unified solution for disaster management that:
- **Predicts** the impact of floods and earthquakes using trained machine learning models.
- **Optimizes** evacuation and supply routes using a multi-modal approach (roadways, airways, waterways).
- **Provides** a user-friendly interface for civilians to report their location, receive alerts, and get safe route suggestions.
- **Enhances** real-time decision-making for disaster response teams by allocating resources effectively.

## ✨ Key Features

- **Dual Disaster Models:** Earthquake (92.60% accuracy) and Flood (91.88% accuracy).
- **Multi-Modal Routing:** Uses A*, Dijkstra, and Floyd-Warshall algorithms.
- **Real-Time Alerts:** Weather + GPS integration with dynamic safe zones.
- **Interactive UI:** Map-based view, safe route display, and warnings.
- **Resource Allocation:** Redistribution of supplies from low-risk to high-risk zones.

---

# 🖼️ Screenshots  
(Add your screenshots in the placeholders below)

### 🔹 Homepage  
`![Homepage](screenshots/homepage.png)`

### 🔹 Disaster Prediction Interface  
`![Prediction Interface](screenshots/prediction_interface.png)`

### 🔹 Safe Route Visualization (Map)  
`![Safe Route](screenshots/safe_route.png)`

### 🔹 Resource Allocation Dashboard  
`![Resource Allocation](screenshots/resource_allocation.png)`

---

## 📜 Publication

Presented at the **International Conference on Smart Systems for Applications in Electrical Sciences (ICSSES-2025)**  
**Venue:** Siddaganga Institute of Technology (SIT), Tumakuru  
**Dates:** March 21–22, 2025  

- **Paper Title:** *SafeRoute: Multi-Modal Optimization for Crisis Management and Evacuation*  
- **Presented By:** Sumanth Ponugupati  

---

## 🛠️ Tech Stack & Methodology

- **Backend:** FastAPI  
- **Machine Learning:** Python, Pandas, Scikit-learn  
- **Geospatial Analysis:** OSMnx, Folium  
- **Frontend:** HTML, CSS, JavaScript  
- **Algorithms:** Logistic Regression, A*, Dijkstra, Floyd-Warshall  

---

## ⚙️ Setup & Installation

1. **Clone the repository**
    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    cd your-repository-name
    ```

2. **Create and activate a virtual environment**
    ```bash
    # Windows
    python -m venv venv
    .\venv\Scripts\activate

    # macOS/Linux
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

---

## ▶️ How to Run

1. **Start the backend server**
    ```bash
    uvicorn main:app --reload
    ```

2. **Open the frontend**
    - Launch `index.html` in a browser.

---

## 👥 Authors

- **Sumanth Ponugupati**  
- **Teja Sai Yallamelli**

---

## 📞 Contact

For inquiries or collaboration:  
📧 **bl.en.u4eac22079@bl.students.amrita.edu**
