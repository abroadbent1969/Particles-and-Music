Interactive 3D MandelbulbThis project is an interactive 3D visualization of the Mandelbulb fractal, created using Three.js and the Web Audio API. The fractal dynamically responds to audio input, with individual points morphing based on audio frequency data, and features interactive controls for rotation and zooming.Table of ContentsFeatures (#features)
Prerequisites (#prerequisites)
Installation (#installation)
Usage (#usage)
File Structure (#file-structure)
How It Works (#how-it-works)
Customization (#customization)
Known Issues (#known-issues)
License (#license)

Features3D Mandelbulb Visualization: Renders a point cloud representation of the Mandelbulb fractal.
Audio Reactivity: Points morph based on the frequency data of uploaded audio files, with dynamic amplitude adjustments.
Interactive Controls:Mouse drag to rotate the fractal.
Mouse wheel to zoom in and out.
Upload and play/pause audio files to influence the fractal's movement.

Dynamic Color Cycling: Colors shift over time based on normalized distances from the fractal's center.
Global Movement: The fractal moves smoothly in a circular pattern.
Responsive Design: Adjusts to window resizing and includes a modern UI with styled controls.

PrerequisitesA modern web browser (e.g., Chrome, Firefox, Edge) with WebGL support.
Internet access to load the Three.js library from a CDN (or a local copy of Three.js).
Audio files in a supported format (e.g., MP3, WAV) for audio-reactive features.

InstallationClone or Download the Repository:Clone this repository or download the HTML file.
Ensure the file is named index.html or update references accordingly.

Serve the File:Due to browser security restrictions (e.g., CORS for audio files), you need to serve the file via a web server. You can use one of the following methods:Local Development Server:Using Node.js: Install http-server with npm install -g http-server, then run http-server in the project directory and navigate to http://localhost:8080.
Using Python: Run python -m http.server 8000 in the project directory and navigate to http://localhost:8000.

VS Code: Use the Live Server extension.

Alternatively, deploy to a hosting service like GitHub Pages or Netlify.

Dependencies:The project uses the Three.js library, loaded via CDN (three.min.js). Ensure internet access or replace the CDN link with a local copy of Three.js.

UsageOpen index.html in a web browser via a local or remote server.
Load an Audio File:Click the "Load Audio File" button and select an audio file (e.g., MP3, WAV).
The "Play Audio" button will be enabled after loading.

Control the Audio:Click "Play Audio" to start playback and enable audio-reactive morphing.
Click again to pause (button toggles to "Pause Audio").

Interact with the Fractal:Rotate: Click and drag the mouse to rotate the Mandelbulb.
Zoom: Use the mouse wheel to zoom in and out (clamped between 0.5 and 10 units).

Observe Visual Effects:The fractal moves in a smooth circular pattern.
Colors cycle dynamically based on normalized distances.
Points morph individually based on audio frequency data (or a base amplitude when no audio is playing).

File Structure

project-directory/
└── index.html  # Main HTML file containing HTML, CSS, and JavaScript

index.html: Contains the HTML structure, CSS styles, and JavaScript logic for rendering the Mandelbulb, handling audio, and enabling interactivity.
Three.js: Loaded via CDN (https://threejs.org/build/three.min.js). No local files are required unless you choose to host Three.js locally.

How It WorksMandelbulb Calculation:The Mandelbulb is computed by sampling a 3D grid (from -size to size with a given resolution) and applying the Mandelbulb formula with a specified power (default: 12) and iterations (default: 12).
Points that remain bounded after iterations are added to the point cloud.

Three.js Rendering:A BufferGeometry stores vertex positions, colors, original positions, and normalized distances.
A PointsMaterial with vertex colors and additive blending creates a glowing effect.
The scene is rendered with a PerspectiveCamera and WebGLRenderer.

Audio Reactivity:The Web Audio API (AudioContext, AnalyserNode) processes uploaded audio files.
Frequency data (getByteFrequencyData) is used to adjust the morph amplitude of individual points.

