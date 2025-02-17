# The Last Conquest - Interactive Storytelling Website

## Overview

"The Last Conquest" is an interactive storytelling website designed to immerse users in a digital graphic novel experience. This project uses HTML, CSS, and JavaScript (with Three.js for 3D effects) to create an engaging journey of a warrior’s rise and fall, showcasing the themes of strength, sacrifice, and realization. The website features smooth scroll-based navigation, cinematic animations, background music, and parallax effects for a richer storytelling experience.

## Features

- **Interactive Storyline**: The story progresses through various chapters with smooth transitions.
- **Parallax Effect**: Background elements create depth during scrolling, adding an immersive touch.
- **Speech Bubbles**: Handwritten-style dialogues appear with smooth fade-in and motion effects.
- **Golden Button**: A glowing button used to navigate through the story.
- **Background Music**: A radio-style toggle to control the background music.
- **3D Sword Animation**: A rotating 3D sword displayed using Three.js, adding a dynamic effect to the website.
- **Responsive Design**: The site is fully responsive and adapts to various screen sizes.

## Installation

To run this project locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/the-last-conquest.git
    ```

2. Navigate to the project directory:
    ```bash
    cd the-last-conquest
    ```

3. Open `index.html` in your browser.

## Project Structure

- `index.html`: The main HTML file containing the website structure and content.
- `style.css`: The CSS file containing all the styles, including animations, layout, and visual effects.
- `script.js`: The JavaScript file handling story navigation, animations, background music control, and 3D elements.
- `assets/`: Directory containing necessary assets like the 3D model (`sword.glb`) and background music (`music.mp3`).

## Code

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Last Conquest</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <canvas id="swordCanvas"></canvas>
    <div class="story" id="story">
        <div class="frame active" id="frame1">
            <h2>The Beginning</h2>
            <p>A warrior rises to conquer the world, driven by ambition and courage.</p>
        </div>
        <div class="frame" id="frame2">
            <h2>The Glory</h2>
            <p>Victories pile up, and glory shines brighter than the sun.</p>
        </div>
        <div class="frame" id="frame3">
            <h2>The Sacrifice</h2>
            <p>With power comes loss. Friends and loved ones fade away.</p>
        </div>
        <div class="frame" id="frame4">
            <h2>The Realization</h2>
            <p>At the end of all conquests, he stands alone, the world at his feet, but his soul empty.</p>
        </div>
    </div>
    <button id="nextButton">Next</button>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r141/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@google/model-viewer/dist/model-viewer.min.js"></script>
    <script src="script.js"></script>
</body>
</html>

```
### "styles.css

```css
/* 🔥 General Styles */
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@600&family=Poppins:wght@300;400;600&display=swap');

body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  color: white;
  background: #000;
  overflow-x: hidden;
}

/* ⚡ Smooth Scroll Effect */
html {
  scroll-behavior: smooth;
}

/* 🎭 Parallax Sections */
.parallax {
  position: relative;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  background-size: cover;
  background-attachment: fixed;
  background-position: center;
  transition: background 1s ease-in-out;
  filter: brightness(90%);
}

.content {
  background: rgba(0, 0, 0, 0.7);
  padding: 30px;
  border-radius: 12px;
  max-width: 65%;
  border: 2px solid rgba(255, 215, 0, 0.6);
  box-shadow: 0px 0px 15px rgba(255, 215, 0, 0.4);
}

h1, h2 {
  font-size: 2.8rem;
  text-transform: uppercase;
  font-family: 'Cinzel', serif;
  color: gold;
  text-shadow: 2px 2px 10px rgba(255, 223, 0, 0.8);
}

p {
  font-size: 1.2rem;
  line-height: 1.6;
}

/* 📜 Side Panel Navigation */
.side-panel {
  position: fixed;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.8);
  padding: 10px;
  border-radius: 12px;
  box-shadow: 0px 0px 15px rgba(255, 215, 0, 0.5);
}

.side-panel ul {
  list-style: none;
  padding: 0;
}

.side-panel ul li {
  margin: 12px 0;
}

.side-panel ul li a {
  display: block;
  padding: 12px;
  color: white;
  text-decoration: none;
  font-size: 1.5rem;
  transition: 0.3s;
  font-family: 'Cinzel', serif;
}

.side-panel ul li a:hover {
  color: gold;
  text-shadow: 0px 0px 10px rgba(255, 215, 0, 0.8);
}

/* ⚔️ Glowing Golden Button */
button {
  background: linear-gradient(45deg, gold, darkgoldenrod);
  color: black;
  border: none;
  padding: 12px 25px;
  font-size: 1.4rem;
  cursor: pointer;
  border-radius: 8px;
  transition: 0.4s;
  box-shadow: 0px 0px 15px rgba(255, 215, 0, 0.5);
}

button:hover {
  background: gold;
  transform: scale(1.1);
  box-shadow: 0px 0px 25px rgba(255, 215, 0, 0.9);
}

/* 🎵 Music Control */
#music-control {
  position: fixed;
  top: 10px;
  right: 20px;
  background: rgba(0, 0, 0, 0.8);
  padding: 10px;
  border-radius: 10px;
}

#music-control label {
  margin-right: 10px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

/* 🗨️ Speech Bubble Styling */
.speech-bubble {
  position: relative;
  background: rgba(255, 255, 255, 0.9);
  color: black;
  padding: 15px;
  border-radius: 10px;
  font-size: 1.2rem;
  font-weight: 600;
  font-family: 'Cinzel', serif;
  max-width: 60%;
}

.speech-bubble::after {
  content: "";
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  border-width: 10px;
  border-style: solid;
  border-color: white transparent transparent transparent;
}

/* 🌌 Parallax Effect Enhancement */
.parallax:hover {
  filter: brightness(100%);
  transform: scale(1.02);
  transition: all 0.8s ease-in-out;
}
```

```script.js
let currentFrame = 1;
const totalFrames = 4;
const nextButton = document.getElementById('nextButton');

nextButton.addEventListener('click', () => {
    document.getElementById(`frame${currentFrame}`).classList.remove('active');
    currentFrame++;
    if (currentFrame > totalFrames) currentFrame = 1;
    document.getElementById(`frame${currentFrame}`).classList.add('active');
});

// Three.js Scene Setup
const canvas = document.getElementById('swordCanvas');
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
camera.position.z = 3;

const renderer = new THREE.WebGLRenderer({ canvas, alpha: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
scene.add(ambientLight);

const directionalLight = new THREE.DirectionalLight(0xffffff, 1);
directionalLight.position.set(5, 5, 5);
scene.add(directionalLight);

const loader = new THREE.GLTFLoader();
loader.load('assets/sword.glb', (gltf) => {
    const sword = gltf.scene;
    sword.scale.set(0.5, 0.5, 0.5);
    scene.add(sword);

    function animate() {
        requestAnimationFrame(animate);
        sword.rotation.y += 0.01;
        renderer.render(scene, camera);
    }
    animate();
});

window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
});
```
