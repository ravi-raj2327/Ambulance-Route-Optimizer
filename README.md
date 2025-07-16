# Ambulance-Route-Optimizer
Overview
The Ambulance Route Optimizer is a web-based application designed to calculate and visualize the optimal route for an ambulance navigating through a city road network. It uses Dijkstra's algorithm to find the shortest path between two nodes, factoring in road types, traffic conditions, and road closures. The application provides an interactive interface with a control dashboard and a dynamic canvas for route visualization, built using HTML, JavaScript, p5.js, and Tailwind CSS.
Features

Graph Configuration: Choose predefined graph complexities (Easy, Moderate, Complex) or input custom graph data with vertices, edges, weights, road types, and coordinates.
Interactive Controls: Select source and destination nodes via dropdowns or by clicking on the canvas, adjust traffic intensity, simulate rush hour, or close roads randomly.
Dynamic Visualization: Displays the road network with color-coded edges (green for smooth, yellow for moderate, red for high traffic, gray for closed roads) and animates the ambulance along the optimal route.
Theming: Toggle between light and dark modes for better visibility.
Event Logging: Tracks user actions like graph loading, route calculation, and road closures in a log panel.
Save/Load: Save custom graph configurations to local storage and load them on startup.
Help Guide: Provides instructions and a sample input format (accessible via the commented-out modal in the code).

Prerequisites

A modern web browser (e.g., Chrome, Firefox, Edge).
Internet connection for loading external libraries (p5.js, Tailwind CSS, LottieFiles, Lucide).
No server-side setup is required as the application runs entirely in the browser.

Installation

Clone or Download: Obtain the source code (e.g., save the provided index.html).
Host Locally: Place the index.html file in a directory and open it in a web browser. Alternatively, use a local server (e.g., python -m http.server or VS Code's Live Server).
Dependencies: The application automatically loads the following libraries via CDN:
p5.js (https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.2/p5.min.js)
Tailwind CSS (https://cdn.tailwindcss.com)
LottieFiles (https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js)
Lucide Icons (https://unpkg.com/lucide@latest/dist/umd/lucide.js)
Google Fonts (Poppins)



Usage

Select Graph Complexity:
Choose from predefined graphs ("Easy", "Moderate", "Complex") or select "Custom" to input your own graph data.
Custom input format:V E
src dest weight road_type
...
x y
...

Example:5 6
0 1 5 arterial
1 2 10 arterial
2 3 15 local
0 2 20 highway
1 4 8 arterial
4 3 7 arterial
100 100
300 150
500 200
200 400
400 350




Load Graph: Click "Load Graph" to initialize the road network.
Set Source/Destination:
Use dropdowns or click nodes on the canvas to select the starting point (source) and destination.


Adjust Traffic:
Use the traffic slider to scale edge weights (0.5x to 2x).
Click "Rush Hour" to simulate increased traffic on non-highway roads (1.5x multiplier).
Click "Road Closure" to randomly set an edge weight to infinity (simulating a closed road).


Find Route: Click "Find Optimal Route" to compute the shortest path using Dijkstra's algorithm. The route is displayed on the canvas with a moving ambulance animation.
Additional Features:
Toggle "Show Closed Roads" to display closed roads in gray.
Toggle "Show Alternate Paths" (not fully implemented in the provided code).
Use "Reset" to revert to the default easy graph and reset traffic settings.
Toggle between light and dark themes using the "Toggle Theme" button.


Navigation:
Drag the canvas to pan.
Scroll to zoom in/out (0.5x to 2x).


Logs: View recent actions (e.g., graph loaded, route calculated) in the log panel.

File Structure

index.html: The main application file containing HTML, CSS, and JavaScript.
No additional files are required as all dependencies are loaded via CDN.

Implementation Details

Graph Representation: Uses an adjacency list to store the graph, with each edge containing source, destination, weight, and road type (arterial, highway, local).
Algorithm: Implements Dijkstra's algorithm with a priority queue to find the shortest path based on edge weights adjusted for traffic.
Visualization: p5.js renders the graph with nodes as circles, edges as color-coded lines, and the optimal path as a dashed green line with an animated ambulance.
UI: Tailwind CSS for responsive styling, glassmorphism effects, and a clean control dashboard. Lucide icons and Lottie animations enhance the interface.
Interactivity: Supports canvas dragging, zooming, and node selection via clicks. Toast notifications provide feedback on actions.

Limitations

Static Data: The application uses predefined or user-input graphs without real-time traffic data integration.
No Persistent Storage: Graphs are saved to localStorage, which is browser-specific and limited in capacity.
Basic Error Handling: Invalid inputs may cause errors, with toast notifications for feedback.
Commented Modal: The help modal is currently commented out in the code but can be uncommented for additional user guidance.
Single Edge Closure: The "Road Closure" feature closes only one random edge at a time.

Future Improvements

Integrate real-time traffic data via APIs (e.g., Google Maps API).
Allow multiple road closures and dynamic reopening.
Enhance the help modal with interactive tutorials.
Add support for weighted road types (e.g., highways prioritized over local roads).
Implement alternate path visualization for comparison.

Troubleshooting

Graph Not Loading: Ensure the custom input follows the correct format (vertices, edges, edge details, coordinates).
Canvas Not Rendering: Check browser compatibility and ensure p5.js is loaded correctly.
No Path Found: Verify that the source and destination nodes are connected and no critical roads are closed (infinite weight).
Performance Issues: For large graphs, reduce the number of nodes/edges or optimize the priority queue.

License
This project is open-source and available under the MIT License.
