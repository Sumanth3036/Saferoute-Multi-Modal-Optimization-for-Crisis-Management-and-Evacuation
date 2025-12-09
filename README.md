# Smart Disaster Management – Run Guide

Python project with two entry points:
- `main.py`/`hello.py`: FastAPI service that serves earthquake and flood predictions using pre-trained models (`Earthquake_Model.pkl`, `Flood_Model.pkl`).
- `app1.py`: Streamlit prototype for interactive prediction and map display (expects extra CSV datasets that are not bundled).

## Project structure
- `main.py`, `hello.py` – FastAPI APIs for predictions.
- `earthquake.py` – training script that fits models and writes `Earthquake_Model.pkl` and `Flood_Model.pkl`.
- `app1.py` – Streamlit UI (needs `earthquake_prediction_data.csv` and `flood_prediction_data.csv`, not in repo).
- `*.pkl`, `*.csv` – model artifacts and sample data used by the API/training.

## Prerequisites
- Python 3.10+ recommended.
- Install dependencies:
  - With a venv (PowerShell): `python -m venv .venv; .\.venv\Scripts\Activate.ps1; pip install -r requirements.txt`
  - Or globally: `pip install -r requirements.txt`

## Running the FastAPI service
1. Open a terminal in `project (2)/project`.
2. Ensure model/data files sit in this folder:
   - `Earthquake_Model.pkl`
   - `Flood_Model.pkl`
   - `encoded_flood_data_with_waterlevel.csv`
3. Update the hard-coded absolute paths in `main.py` (and `hello.py` if you use it) so they are relative to the project folder, e.g. replace the current `joblib.load(...)` paths with:
   ```python
   BASE_DIR = Path(__file__).parent
   earthquake_model = joblib.load(BASE_DIR / "Earthquake_Model.pkl")
   flood_model = joblib.load(BASE_DIR / "Flood_Model.pkl")
   flood_data_path = BASE_DIR / "encoded_flood_data_with_waterlevel.csv"
   ```
4. Start the server: `uvicorn main:app --reload --host 127.0.0.1 --port 8000`
5. Test health: GET `http://127.0.0.1:8000/` should return a message.

### Sample request bodies
- Earthquake (to `/prediction`):
```json
{
  "data": {
    "prediction_type": "earthquake",
    "depth": 10.5,
    "magType": "ml",
    "nst": 25,
    "gap": 45.0,
    "dmin": 0.1,
    "rms": 0.9,
    "horizontalError": 1.2,
    "depthError": 0.7,
    "magError": 0.05,
    "magNst": 15
  }
}
```
- Flood (to `/prediction`):
```json
{
  "data": {
    "prediction_type": "flood",
    "latitude": 8.52,
    "longitude": 76.94,
    "daily_rainfall": 60,
    "river_water_level": 6,
    "soil_moisture_content": 35,
    "elevation": 50,
    "slope": 12,
    "construction_activity_encoded": 1,
    "population_density_x_encoded": 2,
    "dams_reservoirs_encoded": 1,
    "drainage_system_encoded": 1,
    "population_density_y_encoded": 2,
    "wind_speed": 20,
    "agricultural_activity_encoded": 1
  }
}
```
Responses include predicted category/magnitude, precautions, and derived metrics.

## Streamlit prototype (`app1.py`)
1. Place the missing datasets `earthquake_prediction_data.csv` and `flood_prediction_data.csv` alongside the script (not provided here).
2. Run: `streamlit run app1.py`
3. Use the sidebar to choose Earthquake/Flood, enter features, and view the map for nearest safe camps (`earthquake_safe_camps.csv`, `flood_safe_camps.csv`).

## Training models
- Script: `python earthquake.py`
- Requires the CSVs `filtered_earthquake_india.csv` and `encoded_flood_data_with_waterlevel.csv` in the same folder.
- Outputs updated `Earthquake_Model.pkl` and `Flood_Model.pkl`.

## Notes & troubleshooting
- If you see `FileNotFoundError`, verify file names/locations and adjust the paths in the scripts to be relative (see step 3 above).
- If `scikit-learn` complains about pickle incompatibility, retrain with `earthquake.py` under your current Python/sklearn version.
- CORS is open in the API (`allow_origins=["*"]`); tighten before production use.

## Screenshots
Place your images in the repo (e.g., `docs/screenshots/`) and link them here. Suggested captions for the provided captures:
- Contact form submission showing submitted name/number/lat/long/audio attachment.
- <img width="948" height="675" alt="Screenshot 2024-12-04 152235" src="https://github.com/user-attachments/assets/cecbe78e-ffa8-4e17-85e7-ccbeba9d8024" />
- Streamlit “Get In Touch” form with location buttons, recorder controls, and blank map.
- <img width="280" height="429" alt="Screenshot 2025-03-16 231929" src="https://github.com/user-attachments/assets/9c44622c-4634-4d33-a8fe-198fedf9011b" />
- Route map view with directions and markers to the nearest safe camp.
- <img width="385" height="215" alt="Screenshot 2025-03-16 232049" src="https://github.com/user-attachments/assets/24ed03cc-f5a2-475a-ae3f-a512bb3c6e8a" />


