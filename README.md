# Ex05 Image Carousel
## Name: SANJAY K
## Register No: 212223220094
## Date:20-09-25

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
### App.js
```
import React, { useState, useEffect } from "react";
import "./index.css";

const images = [
  "/image1.jpg",
  "/image2.jpg",
  "/image3.jpg",
  "/image4.jpg"
];

function App() {
  const [currentIndex, setCurrentIndex] = useState(0);

  // Auto-slide every 3s
  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentIndex((prev) => (prev + 1) % images.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  return (
    <div className="App">
      <h1 className="carousel-title">🌟 My Image Carousel 🌟</h1>
      <div className="carousel-box">
        <img src={images[currentIndex]} alt="carousel" />
        <div className="controls">
          <button onClick={prevImage}>⬅ Previous</button>
          <button onClick={nextImage}>Next ➡</button>
        </div>
      </div>
    </div>
  );
}

export default App;
```
### index.css
```
/* Reset & base */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #a18cd1, #fbc2eb);
  background-size: 400% 400%;
  animation: gradientMove 12s ease infinite;
}

/* Animate gradient */
@keyframes gradientMove {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.App {
  text-align: center;
  color: #fff;
}

/* Title above carousel */
.carousel-title {
  margin-bottom: 20px;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 0 4px 8px rgba(0, 0, 0, 0.6);
}

/* Carousel box */
.carousel-box {
  width: 600px;
  height: 400px;
  overflow: hidden;
  border-radius: 20px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
  position: relative;
  background: #000;
}

/* Image */
.carousel-box img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* keeps consistent size */
  border-radius: 20px;
  transition: opacity 0.6s ease-in-out, transform 0.5s ease;
}

.carousel-box img:hover {
  transform: scale(1.05);
}

/* Controls */
.controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 20px;
}

button {
  background: linear-gradient(145deg, #ffffffcc, #dddddd88);
  backdrop-filter: blur(6px);
  border: 1px solid #ffffff66;
  color: #111;
  padding: 10px 18px;
  border-radius: 12px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: bold;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease;
}

button:hover {
  background: linear-gradient(145deg, #ffffff, #eeeeee);
  transform: scale(1.1);
  box-shadow: 0 8px 20px rgba(255, 255, 255, 0.4);
}

button:active {
  transform: scale(0.95);
  box-shadow: 0 3px 10px rgba(255, 255, 255, 0.2);
}
```


## OUTPUT
<img width="1919" height="1079" alt="Screenshot 2025-09-22 114001" src="https://github.com/user-attachments/assets/976d9398-1c73-4213-91bf-886690c4b292" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
