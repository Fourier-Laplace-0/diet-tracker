# diet-tracker
# 🍛 AI-Powered Indian Diet Tracker

A lightweight, intelligent web application designed to track daily nutrition and water intake. Built with Vanilla JavaScript, HTML, and CSS, this tracker uses a custom AI proxy to parse natural language food entries—specifically optimized for Indian vegetarian diets—and instantly calculates your daily macronutrients.

## ✨ Features

* **🤖 AI Food Logging:** Forget manual databases. Just type what you ate (e.g., "2 paneer uttapam" or "3 roti, 1 bowl dal"), and the AI handles the macro breakdown based on standard Indian mess preparations.
* **🔒 Secure Access Layer:** Features a master passcode overlay to keep your personal diet logs private. 
* **📊 Visual Macro Dashboard:** Track your Calories, Protein, Carbs, Fat, and Fiber. Features dynamic progress bars with color-coded status indicators (Yellow = Under, Green = On Target, Red = Over).
* **🎯 Editable Goals:** Click on any macro goal (e.g., 2600 Kcal) to edit it on the fly. The app immediately recalculates your progress.
* **⏱️ Quick History Chips:** The app remembers your 10 most recent entries per meal category. Click a history chip to instantly re-populate the input field.
* **💧 Hydration Tracking:** A simple, dedicated counter for tracking daily glasses of water.
* **💾 Local Persistence:** All daily data, custom goals, water counts, and meal histories are saved seamlessly to your browser's `localStorage`.

## 🛠️ Technologies Used

* **Frontend:** HTML5, CSS3, Vanilla JavaScript
* **Backend API:** Connects via `fetch` to a Cloudflare Worker proxy (`gemini-diet-proxy`) which handles the AI model generation securely.
* **Storage:** Browser `localStorage` API

## 🚀 Getting Started

Because this application runs primarily on the client side, there is no heavy build step required. 

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Fourier-Laplace-0/diet-tracker.git](https://github.com/Fourier-Laplace-0/diet-tracker.git)
    ```
2.  **Open the application:**
    Simply double-click the `index.html` file to open it in any modern web browser.
    
    *Alternatively, serve it locally:*
    ```bash
    # If using Python 3
    python -m http.server 8000
    ```
    Then navigate to `http://localhost:8000`.

## 🧠 How it Works

1. **Authentication:** On load, the app checks `localStorage` for a passcode. If none is found, the UI is locked behind an authentication overlay.
2. **AI Processing:** When a meal is submitted, the frontend sends a prompt containing strict parsing rules to the Cloudflare Worker proxy. The prompt strictly instructs the AI to return data in a pure JSON format.
3. **Data Rendering:** The returned JSON (containing Kcal, P, C, F, Fib) is parsed, pushed to the daily state, and the UI dashboard is re-rendered to reflect the new totals and progress bar percentages.
