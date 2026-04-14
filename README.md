# UpKisan

UpKisan is a static multi-page web project focused on farmer support features such as:
- Home and navigation hub
- Feature dashboard
- Weather checker
- Crop map analysis
- AI-assisted suggestions (API-based)
- Supplier/product showcase
- Contact and registration pages

## Project Structure

The project has been organized by file type for clarity and maintainability:

```text
UpKisan/
	assets/
		images/                  # All local image assets used by pages and styles
	data/
		Crop_recommendation.csv  # Crop-related dataset file
	pages/
		home.html                # Main landing page (recommended starting page)
		dashboard.html           # Feature board/navigation page
		weather.html             # Weather forecast and UI display page
		crop-analysis.html       # Map-based analysis page (Leaflet)
		ai-chatbot.html          # AI prompt/response interface
		crop-recommendation.html # Crop recommendation form + AI call flow
		suppliers.html           # Supplier/products page
		contact.html             # Contact page
		registration.html        # Registration/login form page
	styles/
		Inscad.css
		style1.css
		style3.css
	README.md
```

## How To Run

Because this is a static website, there are two simple ways to run it:

1. Open `pages/home.html` directly in a browser.
2. Or use a local static server (recommended for cleaner relative-path behavior):

```bash
# from project root
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/pages/home.html
```

## Page Flow

1. `pages/home.html` acts as the main entry page.
2. Navigation links route users to dashboard, supplier, AI chatbot, weather, registration, and contact pages.
3. `pages/dashboard.html` provides quick feature buttons to major tools.
4. Tool pages (`weather.html`, `crop-analysis.html`, `ai-chatbot.html`, `crop-recommendation.html`) execute their own page-specific logic.

## Logic Behind Key Features

### 1) Weather Module
- Implemented in `pages/weather.html`.
- Takes user location input.
- Calls a weather API endpoint and renders current/forecast weather details.
- Updates weather icon and forecast cards dynamically based on response JSON.

### 2) Crop Analysis Map
- Implemented in `pages/crop-analysis.html`.
- Uses Leaflet via CDN.
- Renders an interactive map for location-based crop-oriented insights.

### 3) AI Assistance
- Implemented in `pages/ai-chatbot.html` and `pages/crop-recommendation.html`.
- User input is composed into prompt-style requests.
- Page scripts send API calls, parse JSON responses, and display AI-generated text.

### 4) Crop Recommendation Data Logic
- `pages/crop-recommendation.html` now reads `data/Crop_recommendation.csv` at runtime.
- It parses `N`, `P`, `K`, `ph`, and `label` columns.
- It ranks rows by nearest soil-parameter match and returns the top crop label.

### 5) Supplier Showcase
- Implemented in `pages/suppliers.html`.
- Displays categorized farming products using static cards and image assets.

### 6) Registration and Contact
- Implemented in `pages/registration.html` and `pages/contact.html`.
- Form-based pages for user onboarding and communication flow.

## Notes

- The reorganization changed file locations only (structure and paths), not business logic.
- If any API-backed page does not respond, verify API keys/endpoints configured in the page scripts.
- Some image references (`F1.jpeg`, `F2.jpeg`, `F3.jpeg`) are referenced by markup but are not present in assets currently.
