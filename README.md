# Ex06 BMI Calculator
## Date: 10-11-2025

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM

BMIcalc.jsx

```jsx

import { useState } from "react";

export default function Calculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (!weight || !height) return;
    const hInMeters = height / 100;
    const bmiValue = (weight / (hInMeters * hInMeters)).toFixed(1);
    setBmi(bmiValue);
    categorizeBMI(bmiValue);
  };

  const categorizeBMI = (bmi) => {
    let category = "";
    if (bmi < 18.5) category = "Underweight";
    else if (bmi < 24.9) category = "Normal weight";
    else if (bmi < 29.9) category = "Overweight";
    else category = "Obesity";
    setCategory(category);
  };

  return (
    <div className="calculator-container">
      <h2>BMI Calculator</h2>

      <div className="input-group">
        <input
          type="number"
          placeholder="Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
        <input
          type="number"
          placeholder="Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
        <button onClick={calculateBMI}>Calculate BMI</button>
      </div>

      {bmi && (
        <div className="result">
          <p>Your BMI: <strong>{bmi}</strong></p>
          <p>Category: {category}</p>
        </div>
      )}
    </div>
  );
}

```


Home.jsx

```jsx

import { Link } from "react-router-dom";

export default function Home() {
  return (
    <div className="home-container">
      <h1>Welcome to the BMI Calculator</h1>
      <Link to="/calculator">Go to Calculator</Link>
    </div>
  );
}

```


App.jsx

```jsx

import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import "./App.css";
import Home from "./Home";
import Calculator from "./BMIcalc";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/calculator">Calculator</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/calculator" element={<Calculator />} />
      </Routes>
    </Router>
  );
}

export default App;

```

## OUTPUT

<img width="1919" height="1140" alt="image" src="https://github.com/user-attachments/assets/49bd5927-809c-45d9-9947-55d4eeb0b942" />

<img width="1919" height="1140" alt="image" src="https://github.com/user-attachments/assets/72f8943a-227c-4fe0-bdc3-41243fa39c64" />

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
