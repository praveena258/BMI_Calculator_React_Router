# Ex06 BMI Calculator
## Date: 

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
bmi.js
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [result, setResult] = useState("");
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    const h = height / 100;
    const bmi = (weight / (h * h)).toFixed(2);

    setResult(bmi);

    if (bmi < 18.5) {
      setCategory("Underweight");
    } else if (bmi < 24.9) {
      setCategory("Normal");
    } else if (bmi < 29.9) {
      setCategory("Overweight");
    } else {
      setCategory("Obese");
    }
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>

      <input
        type="number"
        placeholder="Enter height in cm"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
      />

      <input
        type="number"
        placeholder="Enter weight in kg"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
      />

      <button onClick={calculateBMI}>Calculate</button>

      <h2>BMI: {result}</h2>
      <h2>{category}</h2>
    </div>
  );
}

export default App;
```
bmi.css
```
body {
  margin: 0;
  font-family: Arial;
  background: lightgray;
}

.container {
  text-align: center;
  margin-top: 100px;
}

input {
  display: block;
  margin: 10px auto;
  padding: 10px;
  width: 250px;
}

button {
  padding: 10px 20px;
  background: blue;
  color: white;
  border: none;
}
```


## OUTPUT
<img width="1919" height="1075" alt="image" src="https://github.com/user-attachments/assets/853e8dba-449f-44c8-9ef9-f17fa04da679" />
<img width="1919" height="1046" alt="image" src="https://github.com/user-attachments/assets/2f51eaa6-b0f6-43eb-a536-63f1f00857de" />




## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
