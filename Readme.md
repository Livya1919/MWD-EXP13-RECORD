## Exp 13 - Simulate an Asynchronous Operation Using Promises in React
## NAME: LIVYA DHARSHINI G
## REG NO: 2305001013
## Aim
To develop a React application that simulates an asynchronous student-data operation using a
JavaScript Promise, displays a loading message while the operation is in progress, and displays the
result when the Promise is fulfilled.
## Objectives
1. To understand the concept of a Promise in JavaScript.
2. To create a Promise using new Promise() .
3. To use .then() and .catch() to handle success and errors.
4. To use React's useState() hook to manage application state.
5. To display loading and result messages using conditional rendering.
## Program
```
1. App.jsx

import { useState } from "react";
import "./App.css";
function fetchStudentData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const student = {
        name: "Arun",
        department: "CSE",
        year: "III"
      };
      resolve(student);
      // To test rejection:
      // reject(new Error("Unable to fetch student data"));
    }, 3000);
  });
}
function App() {
  const [loading, setLoading] = useState(false);
  const [student, setStudent] = useState(null);
  const [error, setError] = useState("");
  const handleFetch = () => {
    setLoading(true);
    setStudent(null);
    setError("");
    fetchStudentData()
      .then((data) => {
        setStudent(data);
      })
      .catch((err) => {
        setError(err.message);
      })
      .finally(() => {
        setLoading(false);
      });
  };
  return (
    <div className="app">
      <h1>Student Data Fetch</h1>
      <button onClick={handleFetch} disabled={loading}>
        {loading ? "Fetching..." : "Fetch Student"}
      </button>
      {loading && (
        <p>Fetching student information...</p>
      )}
      {student && (
        <div className="result">
          <h2>Student Details</h2>
          <p>Student Name: {student.name}</p>
          <p>Department: {student.department}</p>
          <p>Year: {student.year}</p>
          <h3>Status: Data Loaded Successfully</h3>
        </div>
      )}
      {error && (
        <p className="error">Error: {error}</p>
      )}
    </div>
  );
}
export default App;


2. App.css

.app {
  text-align: center;
  padding: 40px;
}
button {
  padding: 12px 25px;
  background-color: blue;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: darkblue;
}
button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
.result {
  margin: 25px auto;
  padding: 20px;
  background-color: #e8f5e9;
  width: 350px;
  border-radius: 10px;
}
.error {
  color: red;
  font-weight: bold;
}

3. index.css

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
}
h1 {
color: darkblue;
}
h2 {
color: darkgreen;
}


4. main.jsx

import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";
ReactDOM.createRoot(document.getElementById("root")).render(
<React.StrictMode>
<App />
</React.StrictMode>
);
```
## Output
1. Successful Student Data Fetch

   <img width="1015" height="331" alt="13 1" src="https://github.com/user-attachments/assets/52c0eaa9-f7ec-4267-a654-6710d8516b10" />

2. Promise Rejection (Error Handling)
   
   <img width="1035" height="307" alt="13 2" src="https://github.com/user-attachments/assets/be0db249-bce7-4a36-ac07-7507f52e2b1e" />

## Result
Thus, a React application was successfully developed to simulate an asynchronous student-data
operation using JavaScript Promises. The application displayed a loading message and handled
successful completion and errors using .then() , .catch() , and .finally() .
