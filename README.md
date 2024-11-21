<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eco-Friendly Travel & Live Impact Tracker</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        /* General Styling */
        ::-webkit-scrollbar {
            display: none;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e6f5f1;
            color: #333;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Header Styling */
        header {
            background-color: #1c6758;
            color: white;
            padding: 20px 0;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            background-image: url("2.webp");
        }

        header h1 {
            font-size: 36px;
            letter-spacing: 2px;
        }

        header p {
            font-size: 18px;
            margin-top: 10px;
        }

        /* Navigation Bar */
        nav {
            display: flex;
            justify-content: center;
            background-color: #158f77;
            padding: 15px;
            position: sticky;
            top: 70px;
            z-index: 90;
            background-image: url("2.webp");
        }

        nav a {
            text-decoration: none;
            color: white;
            margin: 0 15px;
            font-size: 18px;
            transition: color 0.3s ease-in-out;
        }

        nav a:hover {
            color: #ffd700;
        }

        /* Section Styling */
        section {
            padding: 60px 20px;
            text-align: center;
            background-color: #f0fdfc;
        }

        h2 {
            font-size: 32px;
            color: #1c6758;
            margin-bottom: 40px;
            position: relative;
        }

        h2::after {
            content: '';
            width: 60px;
            height: 4px;
            background-color: #ffd700;
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }

        /* Tips List Styling */
        ul {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
        }

        li {
            background-color: white;
            width: 300px;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        li:hover {
            transform: translateY(-10px);
        }

        li img {
            border-radius: 8px;
            width: 50px;
            height: 50px;
            margin-bottom: 10px;
        }

        li h3 {
            font-size: 20px;
            margin-bottom: 10px;
            color: #1c6758;
        }

        li p {
            font-size: 16px;
            color: #666;
        }

        /* Impact Tracker Section */
        .tracker,
        .eco-actions,
        .community-impact {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
        }

        .impact-summary {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
        }

        .impact-box {
            text-align: center;
        }

        .impact-label {
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 1.2rem;
        }

        .impact-box p {
            font-size: 1.4rem;
            color: #4CAF50;
        }

        /* Map Section */
        #map {
            height: 600px;
            width: 100%;
        }

        /* Button Styles */
        button {
            background-color: #4CAF50;
            color: white;
            font-size: 1rem;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 10px;
        }

        button:hover {
            background-color: #45a049;
        }

        /* Footer Styling */
        footer {
            text-align: center;
            padding: 20px;
            background-color: #1c6758;
            color: white;
            position: relative;
            bottom: 0;
            width: 100%;
            background-image: url("2.webp");
        }

        footer p {
            font-size: 16px;
            letter-spacing: 1px;
        }

        footer a {
            color: white;
            text-decoration: none;
            margin: 0 10px;
        }

        footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>

<body>

    <!-- Header -->
    <header>
        <h1>Eco-Friendly Travel Tips & Impact Tracker</h1>
        <p>Explore the world while preserving the environment!</p>
    </header>

    <!-- Navigation -->
    <nav>
        <a href="#tips">Tips</a>
        <a href="#carbon-emission">Carbon Emission Calculator</a>
        <a href="#tracker">Live Impact Tracker</a>
        <a href="#map">Eco-Friendly Map</a>
        <a href="#about">About Us</a>
        <a href="#contact">Contact</a>
    </nav>

    <!-- Tips Section -->
    <section id="tips">
        <h2>15 Tips for Sustainable Travel</h2>
        <ul>
            <li>
                <img src="15.jpg" alt="Tip 1">
                <h3>Pack Light</h3>
                <p>A lighter bag means less fuel consumption during travel.</p>
            </li>
            <li>
                <img src="3.webp" alt="Tip 2">
                <h3>Use Public Transport</h3>
                <p>Opt for buses, trains, or bikes instead of taxis and rental cars.</p>
            </li>
            <!-- Additional tips would go here -->
        </ul>
    </section>

    <!-- Carbon Emission Section -->
    <section id="carbon-emission" style="background-color: #dff3f1; padding: 60px 20px;">
        <h2>Calculate Your Travel's Carbon Emissions</h2>
        <div class="container">
            <div class="form-group">
                <label for="departure">Departure City:</label>
                <input type="text" id="departure" placeholder="e.g., New York">
            </div>
            <div class="form-group">
                <label for="arrival">Arrival City:</label>
                <input type="text" id="arrival" placeholder="e.g., London">
            </div>
            <button onclick="getCarbonFootprint()">Calculate Emissions</button>
        </div>
        <div class="output" id="output"></div>
    </section>

    <!-- Live Impact Tracker Section -->
    <section id="tracker">
        <h2>Your Live Eco-Friendly Impact</h2>
        <div class="tracker">
            <h2>Your Impact</h2>
            <div class="impact-summary">
                <div class="impact-box">
                    <p class="impact-label">CO2 Saved (kg):</p>
                    <p id="co2-saved">0</p>
                </div>
                <div class="impact-box">
                    <p class="impact-label">Trees Planted:</p>
                    <p id="trees-planted">0</p>
                </div>
                <div class="impact-box">
                    <p class="impact-label">Eco-Friendly Trips:</p>
                    <p id="eco-trips">0</p>
                </div>
            </div>
        </div>
        <div class="eco-actions">
            <h2>Make an Eco-Friendly Choice</h2>
            <button id="train-btn">Choose Train</button>
            <button id="green-hotel-btn">Choose Green Hotel</button>
        </div>
        <div class="community-impact">
            <h2>Community Impact</h2>
            <div class="impact-summary">
                <div class="impact-box">
                    <p class="impact-label">Total CO2 Saved (kg):</p>
                    <p id="community-co2-saved">0</p>
                </div>
                <div class="impact-box">
                    <p class="impact-label">Total Trees Planted:</p>
                    <p id="community-trees-planted">0</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Eco-Friendly Destinations Map Section -->
    <section id="map" style="padding: 60px 20px;">
        <h2>Explore Eco-Friendly Destinations</h2>
        <div id="map"></div>
    </section>

    <!-- About Us Section -->
    <section id="about" style="background-color: #e0f7e6; padding: 60px 20px;">
        <h2>About Us</h2>
        <p>We are committed to making travel more sustainable by encouraging eco-friendly choices for all travelers. Join us on the journey toward a greener planet!</p>
    </section>

    <!-- Contact Section -->
    <section id="contact" style="padding: 60px 20px;">
        <h2>Contact</h2>
        <p>For inquiries or partnerships, email us at info@ecotravel.com</p>
    </section>

    <!-- Footer -->
    <footer>
        <p>©️ 2024 Eco-Friendly Travel. All rights reserved.</p>
    </footer>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script src="https://unpkg.com/leaflet.markercluster/dist/leaflet.markercluster.js"></script>
    <script src="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.js"></script>

    <script>
        // Carbon Footprint Calculation
        function getCarbonFootprint() {
            const departure = document.getElementById("departure").value;
            const arrival = document.getElementById("arrival").value;

            if (!departure || !arrival) {
                alert("Please enter both departure and arrival cities.");
                return;
            }

            // Simple simulation of carbon footprint for example purposes
            const carbonEmission = Math.floor(Math.random() * 500 + 100); // random emission value

            document.getElementById("output").innerHTML = `
                <p>Your carbon footprint for this trip is approximately ${carbonEmission} kg of CO2.</p>
            `;
        }

        // Impact Tracker Actions
        document.getElementById("train-btn").addEventListener("click", function() {
            updateImpact(0.5, 1, 1); // example values for train trip
        });

        document.getElementById("green-hotel-btn").addEventListener("click", function() {
            updateImpact(0.2, 0.5, 1); // example values for choosing a green hotel
        });

        // Update Impact Tracker Values
        function updateImpact(co2Saved, treesPlanted, ecoTrips) {
            const currentCO2 = parseFloat(document.getElementById("co2-saved").innerText);
            const currentTrees = parseFloat(document.getElementById("trees-planted").innerText);
            const currentTrips = parseFloat(document.getElementById("eco-trips").innerText);

            document.getElementById("co2-saved").innerText = (currentCO2 + co2Saved).toFixed(1);
            document.getElementById("trees-planted").innerText = (currentTrees + treesPlanted).toFixed(1);
            document.getElementById("eco-trips").innerText = (currentTrips + ecoTrips).toFixed(0);
        }

        // Initialize the map
        const map = L.map('map').setView([51.505, -0.09], 2); // Default center (lat, lon) for global view

        // Set up the map tile layer (using OpenStreetMap)
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        // Eco-friendly destinations (example data)
        const ecoDestinations = [
            {
                name: "Green Hotel Paris",
                coordinates: [48.8566, 2.3522],
                certification: "Green Key Certified",
                description: "A sustainable hotel with energy-efficient amenities.",
                link: "https://example.com/green-hotel-paris"
            },
            {
                name: "Eco Lodge Tokyo",
                coordinates: [35.6762, 139.6503],
                certification: "EarthCheck Certified",
                description: "Eco-friendly lodge with water conservation practices.",
                link: "https://example.com/eco-lodge-tokyo"
            },
            {
                name: "Solar Camp Costa Rica",
                coordinates: [9.7489, -83.7534],
                certification: "LEED Platinum",
                description: "A solar-powered eco-camp immersed in nature.",
                link: "https://example.com/solar-camp-costa-rica"
            }
        ];

        // Create a marker cluster group to handle multiple markers efficiently
        const markers = L.markerClusterGroup();

        // Add the eco-destination markers
        ecoDestinations.forEach(dest => {
            const marker = L.marker([dest.coordinates[0], dest.coordinates[1]])
                .bindPopup(`
                    <h3>${dest.name}</h3>
                    <p><strong>Certification:</strong> ${dest.certification}</p>
                    <p><strong>Description:</strong> ${dest.description}</p>
                    <a href="${dest.link}" target="_blank">Learn more</a>
                `)
                .addTo(markers);
        });

        // Add the markers to the map
        map.addLayer(markers);

        // Optional: Add a geocoder control for searching locations by name
        L.Control.Geocoder.nominatim().addTo(map);

    </script>
</body>

</html>
