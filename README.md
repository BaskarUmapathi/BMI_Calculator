# Ex06 BMI Calculator
## Date:01.05.2025
```
NAME : BASKAR U
REG NO : 212223220013
```
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
Home.jsx
```
import React from 'react';
import { useNavigate } from 'react-router-dom';

function Home() {
  const navigate = useNavigate();
  return (
    <div className="home-container">
      <h2 className="home-title">Welcome to the BMI Calculator!</h2>
      <p className="home-description">Click the button below to calculate your Body Mass Index.</p>
      <button className="start-btn" onClick={() => navigate('/calculator')}>Start</button>
    </div>
  );
}
export default Home;
```
BMICalculator.jsx
```
import React, { useState } from 'react';

function BMICalculator() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState('');
  const [category, setCategory] = useState('');

  const calculate = () => {
    const h = height / 100;
    const b = weight / (h * h);
    setBmi(b.toFixed(2));
    if (b < 18.5) setCategory('Underweight');
    else if (b < 25) setCategory('Normal');
    else if (b < 30) setCategory('Overweight');
    else setCategory('Obese');
  };

  return (
    <div className="calculator-container">
      <h2 className="calculator-title">Calculate Your BMI</h2>
      <div className="input-container">
        <input 
          type="number" 
          placeholder="Weight (kg)" 
          value={weight} 
          onChange={(e) => setWeight(e.target.value)} 
          className="input"
        />
        <input 
          type="number" 
          placeholder="Height (cm)" 
          value={height} 
          onChange={(e) => setHeight(e.target.value)} 
          className="input"
        />
      </div>
      <button className="calculate-btn" onClick={calculate}>Calculate</button>
      {bmi && (
        <div className="result">
          <h3>Your BMI: {bmi}</h3>
          <p>Category: <strong>{category}</strong></p>
        </div>
      )}
    </div>
  );
}

export default BMICalculator;
```
k.css
```
/* Basic Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #f0f8ff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* App */
.app {
  text-align: center;
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  max-width: 500px;
  width: 100%;
}

.app-title {
  font-size: 2.5rem;
  color: #2196f3;
  margin-bottom: 20px;
}

.nav {
  margin-bottom: 30px;
}

.nav-link {
  font-size: 1rem;
  color: #4caf50;
  margin: 0 10px;
  text-decoration: none;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #2196f3;
}

/* Calculator */
.calculator-container {
  margin-top: 20px;
}

.calculator-title {
  font-size: 2rem;
  color: #333;
  margin-bottom: 15px;
}

.input-container {
  margin-bottom: 20px;
}

.input {
  width: 80%;
  padding: 10px;
  font-size: 1rem;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin: 5px;
  transition: border 0.3s;
}

.input:focus {
  border: 1px solid #2196f3;
}

.calculate-btn {
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.calculate-btn:hover {
  background-color: #45a049;
}

.result {
  margin-top: 20px;
}

.result h3 {
  font-size: 1.5rem;
  color: #333;
}

.result p {
  font-size: 1.2rem;
  color: #666;
}

/* Home */
.home-container {
  text-align: center;
}

.home-title {
  font-size: 2.5rem;
  color: #2196f3;
  margin-bottom: 15px;
}

.home-description {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

.start-btn {
  padding: 12px 25px;
  background-color: #2196f3;
  color: white;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.start-btn:hover {
  background-color: #1976d2;
}
```
App.jsx
```
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import BMICalculator from './BMICalculator';
import k from './k.css';

function App() {
  return (
    <Router>
      <div className="app">
        <h1 className="app-title">BMI Calculator</h1>
        <nav className="nav">
          <Link className="nav-link" to="/">Home</Link>
          <Link className="nav-link" to="/calculator">Calculator</Link>
        </nav>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/calculator" element={<BMICalculator />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```
## OUTPUT
![Screenshot 2025-05-16 165550](https://github.com/user-attachments/assets/ecbd831f-1a0b-4482-b28d-a799b3afaa93)
![Screenshot 2025-05-16 165607](https://github.com/user-attachments/assets/603f3f52-7559-499e-b5b8-2e8fd604af6c)
![Screenshot 2025-05-16 165628](https://github.com/user-attachments/assets/04fa9b8b-6ab5-4aac-bd76-f04b4991f5ec)

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
