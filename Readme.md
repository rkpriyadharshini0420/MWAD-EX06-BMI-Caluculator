## Ex06 BMI Calculator
### Date: 11-11-2025
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
App.jsx:
```
import React from 'react'
import { Routes, Route, Link } from 'react-router-dom'
import Home from './components/Home'
import BMICalculator from './components/BMICalculator'

function App() {
  return (
    <div className="App">
      <nav>
        <Link to="/">Home</Link> | <Link to="/calculator">BMI Calculator</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/calculator" element={<BMICalculator />} />
      </Routes>
    </div>
  )
}

export default App

```
App.css:
```
body {
  font-family: Arial, sans-serif;
  background-color: #f4f7fa;
  margin: 0;
  padding: 0;
  text-align: center;
}

nav {
  background-color: #007bff;
  padding: 10px;
}

nav a {
  color: white;
  margin: 0 10px;
  text-decoration: none;
}

button {
  background-color: #28a745;
  border: none;
  color: white;
  padding: 8px 12px;
  margin-top: 10px;
  border-radius: 5px;
  cursor: pointer;
}

input {
  margin: 5px;
  padding: 5px;
}

.result {
  margin-top: 15px;
  background: white;
  display: inline-block;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 0 5px #ccc;
}

```
BMICalculator.jsx
```
import React, { useState } from 'react'

function BMICalculator() {
  const [weight, setWeight] = useState('')
  const [height, setHeight] = useState('')
  const [bmi, setBmi] = useState(null)
  const [category, setCategory] = useState('')

  const calculateBMI = () => {
    if (weight && height) {
      const h = height / 100 // convert cm to m
      const result = (weight / (h * h)).toFixed(2)
      setBmi(result)

      if (result < 18.5) setCategory('Underweight')
      else if (result >= 18.5 && result < 24.9) setCategory('Normal weight')
      else if (result >= 25 && result < 29.9) setCategory('Overweight')
      else setCategory('Obesity')
    }
  }

  return (
    <div className="bmi-calculator">
      <h2>BMI Calculator</h2>

      <div>
        <label>Weight (kg): </label>
        <input type="number" value={weight} onChange={(e) => setWeight(e.target.value)} />
      </div>

      <div>
        <label>Height (cm): </label>
        <input type="number" value={height} onChange={(e) => setHeight(e.target.value)} />
      </div>

      <button onClick={calculateBMI}>Calculate</button>

      {bmi && (
        <div className="result">
          <h3>Your BMI: {bmi}</h3>
          <p>Category: {category}</p>
        </div>
      )}
    </div>
  )
}

export default BMICalculator
```
Home.jsx
```
import React from 'react'
import { Link } from 'react-router-dom'

function Home() {
  return (
    <div className="home">
      <h1>Welcome to BMI Calculator</h1>
      <p>Click below to calculate your BMI.</p>
      <Link to="/calculator">
        <button>Go to Calculator</button>
      </Link>
    </div>
  )
}

export default Home
```
## OUTPUT



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
