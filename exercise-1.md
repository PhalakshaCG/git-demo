# Exercise 1: Add a Small Feature

## Step 1: Add a New Feature
1. Open the project in your code editor.
2. Locate the main Express app file (e.g., `index.js`).
3. Add a new feature to show the image for current weather condition. 
Replace line 25 with:
```
    <p>Condition: <img src="${weatherData.current.condition.icon}" alt="Weather Icon" style="height: 5mm;"> ${weatherData.current.condition.text}</p>
```

---

## Step 2: Stage and Commit Your Changes
1. Stage the changes:
   ```bash
   git add .
   ```
2. Commit the changes:
   ```bash
   git commit -m "feat: Add image for weather condition"
   ```
---

## Next Steps
The `main` branch will be updated with another feature by the instructor. Once that is done, proceed to the `exercise-2.md` file for the next part of the demo.
