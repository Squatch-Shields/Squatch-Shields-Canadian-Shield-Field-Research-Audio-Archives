Welcome to the official GitHub repository for Squatch Shields, a specialized cryptozoology and bioacoustic field research initiative operating in the rugged terrain of Northern Ontario (Mattawa and North Bay region).
​🌲 About the Project
​Squatch Shields is dedicated to empirical field research, nocturnal audio tracking, and granite-shield sign collection. This repository houses the source code for our offline-ready research hub and public information portal.
​Key Features Included:
​Bioacoustic Evidence Vault: Interactive audio player simulation featuring raw nocturnal wood knocks and vocalization recordings.
​Privacy-First Regional Map: An interactive map utilizing dark minimalist vector tiles (CartoDB Dark Matter) to display general survey sectors without exposing micro-coordinates or terrain features to public satellite imagery.
​Secure Encounter Reporting Form: Detailed intake mechanism for Class A (visuals), Class B (audio/vocalizations), and Class C (sign/trackway) reports.
​Community & Events: Information on the Northern Ontario Sasquatch Festival and direct links to our social channels.
​🚀 Live Website
​Once hosted via GitHub Pages, the site can be accessed live at:
https://<your-github-username>.github.io/squatch-shields/
​🛠️ Local Development & Offline Use
​To run or test this website locally on your computer or tablet:
​Clone or download this repository.
​Ensure the main file is named index.html.
​Double-click index.html to open it directly in any modern web browser.
​© 2026 Squatch Shields Research Initiative. All Rights Reserved.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Squatch Shields | Bioacoustic & Field Research Hub</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Leaflet CSS for Privacy-First Map -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        forest: {
                            900: '#061a10',
                            800: '#0a2316',
                            700: '#113824',
                            600: '#1b4d32',
                        },
                        amberGlow: '#f59e0b',
                    }
                }
            }
        }
    </script>
    <style>
        #map { height: 450px; border-radius: 0.75rem; }
        /* Custom Dark Tile Filter for Leaflet */
        .leaflet-layer, .leaflet-control-zoom-in, .leaflet-control-zoom-out, .leaflet-control-attribution {
            filter: invert(100%) hue-rotate(180deg) brightness(95%) contrast(90%);
        }
    </style>
</head>
<body class="bg-forest-900 text-gray-200 font-sans antialiased selection:bg-amberGlow selection:text-forest-900">

    <!-- Navigation Bar -->
    <nav class="bg-forest-800/90 backdrop-blur-md border-b border-forest-700 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 rounded-full bg-forest-600 flex items-center justify-center border border-amberGlow/40">
                        <i class="fa-solid fa-paw text-amberGlow text-lg"></i>
                    </div>
                    <span class="font-bold text-xl tracking-wider text-white">SQUATCH <span class="text-amberGlow">SHIELDS</span></span>
                </div>
                <div class="hidden md:flex items-center space-x-6 text-sm font-medium">
                    <a href="#audio" class="hover:text-amberGlow transition">Audio Logs</a>
                    <a href="#map-section" class="hover:text-amberGlow transition">Sector Map</a>
                    <a href="#report" class="hover:text-amberGlow transition text-amberGlow font-semibold"><i class="fa-solid fa-triangle-exclamation mr-1"></i> Report Encounter</a>
                    <a href="#contact" class="hover:text-amberGlow transition">Connect</a>
                </div>
                <!-- Social Icons Header -->
                <div class="flex items-center space-x-4 text-lg">
                    <a href="https://youtube.com" target="_blank" class="text-gray-400 hover:text-red-500 transition" title="YouTube"><i class="fab fa-youtube"></i></a>
                    <a href="https://twitter.com" target="_blank" class="text-gray-400 hover:text-amberGlow transition" title="X / Twitter"><i class="fab fa-x-twitter"></i></a>
                    <a href="mailto:contact@squatchshields.com" class="text-gray-400 hover:text-amberGlow transition" title="Email"><i class="fa-solid fa-envelope"></i></a>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="relative bg-gradient-to-b from-forest-800 to-forest-900 py-20 px-4 text-center border-b border-forest-700">
        <div class="max-w-4xl mx-auto space-y-6">
            <span class="inline-block bg-forest-700 text-amberGlow text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-widest border border-amberGlow/30">
                Northern Ontario Field Research
            </span>
            <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight text-white">
                Uncompromising <span class="text-amberGlow">Cryptozoology</span> & Bioacoustics
            </h1>
            <p class="text-lg sm:text-xl text-gray-300 max-w-2xl mx-auto leading-relaxed">
                Documenting nocturnal activity across the Canadian Shield. Utilizing clip microphones, digital night vision, and rigorous audio analysis away from public tourism channels.
            </p>
            <div class="flex justify-center gap-4 pt-4">
                <a href="#audio" class="bg-amberGlow hover:bg-amber-600 text-forest-900 font-bold px-6 py-3 rounded-lg shadow-lg transition flex items-center gap-2">
                    <i class="fa-solid fa-headphones"></i> Listen to Audio Logs
                </a>
                <a href="#report" class="bg-forest-700 hover:bg-forest-600 text-white font-semibold px-6 py-3 rounded-lg border border-forest-600 transition">
                    Submit a Report
                </a>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 space-y-16">

        <!-- Audio Logs Section -->
        <section id="audio" class="bg-forest-800/60 rounded-2xl p-6 sm:p-8 border border-forest-700 shadow-xl">
            <div class="flex items-center justify-between mb-6">
                <div>
                    <h2 class="text-2xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-wave-square text-amberGlow"></i> Bioacoustic Evidence Vault
                    </h2>
                    <p class="text-sm text-gray-400 mt-1">Recorded nocturnal audio captures from the Canadian Shield granite ridges.</p>
                </div>
                <span class="text-xs bg-forest-700 text-gray-300 px-3 py-1 rounded-md">24-Bit / 96kHz Raw Files</span>
            </div>

            <!-- Audio Player Widget -->
            <div class="bg-forest-900/90 rounded-xl p-6 border border-forest-700 space-y-4">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                    <div>
                        <span id="track-title" class="text-lg font-bold text-white">Track 01: Mattawa Ridge Wood Knock Series</span>
                        <p id="track-meta" class="text-xs text-amberGlow mt-0.5">Recorded: October 2025 • Elevation: 340m • Granitic Hardwood Ridge</p>
                    </div>
                    <div class="flex items-center space-x-3">
                        <button onclick="switchTrack(0)" class="px-3 py-1 text-xs rounded bg-forest-700 hover:bg-forest-600 text-white">Track 1</button>
                        <button onclick="switchTrack(1)" class="px-3 py-1 text-xs rounded bg-forest-700 hover:bg-forest-600 text-white">Track 2</button>
                    </div>
                </div>

                <!-- Simulated Spectrogram Waveform -->
                <div class="h-20 bg-forest-800 rounded-lg flex items-center justify-center relative overflow-hidden px-2 border border-forest-700/50">
                    <div class="absolute inset-0 flex items-center justify-around opacity-40">
                        <div class="w-1 h-12 bg-amberGlow animate-pulse"></div>
                        <div class="w-1 h-8 bg-amberGlow"></div>
                        <div class="w-1 h-16 bg-amberGlow"></div>
                        <div class="w-1 h-10 bg-amberGlow animate-pulse"></div>
                        <div class="w-1 h-14 bg-amberGlow"></div>
                        <div class="w-1 h-6 bg-amberGlow"></div>
                        <div class="w-1 h-12 bg-amberGlow"></div>
                        <div class="w-1 h-18 bg-amberGlow animate-pulse"></div>
                        <div class="w-1 h-10 bg-amberGlow"></div>
                        <div class="w-1 h-14 bg-amberGlow"></div>
                    </div>
                    <span id="player-status" class="z-10 text-xs font-mono text-amberGlow bg-forest-900/80 px-3 py-1 rounded border border-amberGlow/30">Ready to Play</span>
                </div>

                <!-- Playback Controls -->
                <div class="flex items-center justify-between pt-2">
                    <div class="flex items-center space-x-4">
                        <button id="play-btn" onclick="togglePlay()" class="w-12 h-12 rounded-full bg-amberGlow text-forest-900 flex items-center justify-center hover:bg-amber-500 transition shadow-lg">
                            <i id="play-icon" class="fa-solid fa-play text-lg ml-0.5"></i>
                        </button>
                        <div>
                            <div id="time-display" class="text-xs font-mono text-gray-300">0:00 / 0:42</div>
                        </div>
                    </div>
                    <div class="text-xs text-gray-400">
                        <i class="fa-solid fa-shield-halved text-amberGlow mr-1"></i> Audio fingerprint protected.
                    </div>
                </div>
            </div>
        </section>

        <!-- Privacy-First Map Section -->
        <section id="map-section" class="bg-forest-800/60 rounded-2xl p-6 sm:p-8 border border-forest-700 shadow-xl">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-white flex items-center gap-2">
                    <i class="fa-solid fa-map-location-dot text-amberGlow"></i> Regional Sector & Activity Map
                </h2>
                <p class="text-sm text-gray-400 mt-1">General regional tracking sectors. Micro-coordinates and exact clearings are heavily masked to protect research zones from public intrusion.</p>
            </div>
            <!-- Leaflet Map Container -->
            <div id="map" class="border border-forest-700 shadow-inner"></div>
            <div class="mt-4 flex flex-wrap gap-4 text-xs text-gray-400 items-center justify-between">
                <span class="flex items-center gap-2"><span class="w-3 h-3 rounded-full bg-amberGlow inline-block"></span> Active Survey Sector</span>
                <span>Base Map: CartoDB Dark Vector (Zero Satellite Exposure)</span>
            </div>
        </section>

        <!-- Sasquatch Encounter Report Form Section -->
        <section id="report" class="bg-forest-800/60 rounded-2xl p-6 sm:p-8 border border-forest-700 shadow-xl">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-white flex items-center gap-2">
                    <i class="fa-solid fa-file-shield text-amberGlow"></i> Secure Encounter Reporting Form
                </h2>
                <p class="text-sm text-gray-400 mt-1">Submit classified witness details, audio logs, or sign evidence for direct review by the Squatch Shields research team.</p>
            </div>

            <form onsubmit="handleReportSubmit(event)" class="space-y-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Classification Type -->
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Encounter Classification *</label>
                        <select id="report-class" required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white focus:border-amberGlow focus:outline-none">
                            <option value="">Select Classification...</option>
                            <option value="Class A">Class A — Direct Visual Sighting w/ Physical Details</option>
                            <option value="Class B">Class B — Audio / Vocalization / Wood Knocks</option>
                            <option value="Class C">Class C — Sign / Trackway / Hair / Nest Structure</option>
                        </select>
                    </div>
                    <!-- Date -->
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Date of Encounter *</label>
                        <input type="date" required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white focus:border-amberGlow focus:outline-none">
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- General Region -->
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">General Region / Watershed *</label>
                        <input type="text" placeholder="e.g., Mattawa River Sector, North Bay Outskirts" required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white placeholder-gray-500 focus:border-amberGlow focus:outline-none">
                    </div>
                    <!-- Terrain Type -->
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Terrain Type</label>
                        <input type="text" placeholder="e.g., Canadian Shield granite ridge, mixed cedar swamp" class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white placeholder-gray-500 focus:border-amberGlow focus:outline-none">
                    </div>
                </div>

                <!-- Detailed Description -->
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Detailed Narrative & Observations *</label>
                    <textarea rows="5" placeholder="Describe timestamps, behaviors, audio characteristics, or structural anomalies observed..." required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white placeholder-gray-500 focus:border-amberGlow focus:outline-none"></textarea>
                </div>

                <!-- Contact Info -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Your Name / Pseudonym *</label>
                        <input type="text" placeholder="e.g., Field Researcher" required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white placeholder-gray-500 focus:border-amberGlow focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Contact Email (Kept Strictly Confidential) *</label>
                        <input type="email" placeholder="researcher@domain.com" required class="w-full bg-forest-900 border border-forest-700 rounded-lg p-3 text-white placeholder-gray-500 focus:border-amberGlow focus:outline-none">
                    </div>
                </div>

                <div class="flex justify-end">
                    <button type="submit" class="bg-amberGlow hover:bg-amber-600 text-forest-900 font-bold px-8 py-3 rounded-lg shadow-lg transition">
                        Submit Secure Report
                    </button>
                </div>
            </form>
            <div id="form-success" class="hidden mt-4 p-4 bg-forest-700/80 border border-amberGlow text-amberGlow rounded-lg text-center font-medium">
                Report logged successfully. Thank you for contributing to the Squatch Shields research database.
            </div>
        </section>

        <!-- Northern Ontario Sasquatch Festival Section -->
        <section class="bg-forest-800/60 rounded-2xl p-6 sm:p-8 border border-forest-700 shadow-xl flex flex-col md:flex-row items-center justify-between gap-8">
            <div class="space-y-4 max-w-2xl">
                <span class="text-xs bg-forest-700 text-amberGlow px-3 py-1 rounded-full uppercase tracking-widest border border-amberGlow/30">Annual Event</span>
                <h2 class="text-3xl font-extrabold text-white">Northern Ontario Sasquatch Festival</h2>
                <p class="text-gray-300 text-sm leading-relaxed">
                    Co-organized to bring together regional researchers, historians, and enthusiasts. Featuring speaker panels, fieldcraft workshops, wood-carving competitions, and audio evidence exhibitions at Samuel de Champlain Provincial Park and the Ecology Centre.
                </p>
            </div>
            <div class="bg-forest-900 p-6 rounded-xl border border-forest-700 text-center space-y-3 min-w-[260px]">
                <div class="text-amberGlow font-bold text-lg"><i class="fa-solid fa-calendar-days mr-2"></i> Upcoming Season</div>
                <div class="text-xs text-gray-300">Workshops & Vendor Registration Open</div>
                <a href="#contact" class="inline-block bg-forest-700 hover:bg-forest-600 text-white font-semibold text-xs px-4 py-2 rounded-lg transition border border-forest-600">
                    Inquire About Festival
                </a>
            </div>
        </section>

        <!-- Connect / Socials Section -->
        <section id="contact" class="bg-forest-800/60 rounded-2xl p-6 sm:p-8 border border-forest-700 shadow-xl text-center space-y-6">
            <h2 class="text-2xl font-bold text-white">Connect with Squatch Shields</h2>
            <p class="text-sm text-gray-400 max-w-xl mx-auto">Follow our field research expeditions, upcoming YouTube channel launches, and podcast appearances across Northern Ontario.</p>
            <div class="flex justify-center gap-6 text-2xl">
                <a href="https://youtube.com" target="_blank" class="w-12 h-12 rounded-xl bg-forest-900 border border-forest-700 flex items-center justify-center text-gray-300 hover:text-red-500 hover:border-red-500/50 transition"><i class="fab fa-youtube"></i></a>
                <a href="https://twitter.com" target="_blank" class="w-12 h-12 rounded-xl bg-forest-900 border border-forest-700 flex items-center justify-center text-gray-300 hover:text-amberGlow hover:border-amberGlow/50 transition"><i class="fab fa-x-twitter"></i></a>
                <a href="https://instagram.com" target="_blank" class="w-12 h-12 rounded-xl bg-forest-900 border border-forest-700 flex items-center justify-center text-gray-300 hover:text-pink-400 hover:border-pink-400/50 transition"><i class="fab fa-instagram"></i></a>
                <a href="mailto:contact@squatchshields.com" class="w-12 h-12 rounded-xl bg-forest-900 border border-forest-700 flex items-center justify-center text-gray-300 hover:text-amberGlow hover:border-amberGlow/50 transition"><i class="fa-solid fa-envelope"></i></a>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-forest-900 border-t border-forest-800 py-8 text-center text-xs text-gray-500 space-y-2">
        <p>&copy; 2026 Squatch Shields Research. All rights reserved. Maintained offline for private research coordination.</p>
        <p class="text-gray-600">North Bay, Ontario &bull; Canadian Shield Field Investigations</p>
    </footer>

    <!-- Leaflet JS Script -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
    <script>
        // Initialize Privacy-First Map (CartoDB Dark Matter Tiles)
        const map = L.map('map').setView([46.31, 79.45], 10); // Centered generally near North Bay / Mattawa region

        L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors &copy; <a href="https://carto.com/attributions">CARTO</a>',
            subdomains: 'abcd',
            maxZoom: 14
        }).addTo(map);

        // Generalized Sector Markers (Concealing exact micro-locations)
        const sectors = [
            { lat: 46.315, lng: 79.452, title: "Sector Alpha: Mattawa Ridge Zone", desc: "Multiple audio captures of wood knocks and high-frequency vocalizations along granitic ridge." },
            { lat: 46.280, lng: 79.320, title: "Sector Beta: Shield Watershed", desc: "Trackway sign reported in cedar swamp perimeter. Passive monitoring station active." },
            { lat: 46.390, lng: 79.510, title: "Sector Gamma: Northern Corridor", desc: "Night vision thermal anomalies and sit-and-listen audio logs recorded." }
        ];

        sectors.forEach(sector => {
            L.circleMarker([sector.lat, sector.lng], {
                radius: 8,
                fillColor: "#f59e0b",
                color: "#ffffff",
                weight: 1.5,
                opacity: 1,
                fillOpacity: 0.8
            }).addTo(map).bindPopup(`<div style="color:#0a2316; font-family: sans-serif;"><strong style="font-size:14px;">${sector.title}</strong><p style="margin-top:4px; font-size:12px;">${sector.desc}</p></div>`);
        });

        // Audio Player Simulation Logic
        let isPlaying = false;
        let currentTrack = 0;
        const tracks = [
            { title: "Track 01: Mattawa Ridge Wood Knock Series", meta: "Recorded: October 2025 • Elevation: 340m • Granitic Hardwood Ridge", time: "0:42" },
            { title: "Track 02: Unidentified Vocalization / Whoop", meta: "Recorded: August 2025 • Perimeter: Shield Wetland Sector", time: "0:28" }
        ];

        function togglePlay() {
            isPlaying = !isPlaying;
            const icon = document.getElementById('play-icon');
            const status = document.getElementById('player-status');
            if (isPlaying) {
                icon.className = "fa-solid fa-pause text-lg";
                status.textContent = "Playing Audio Stream...";
                status.classList.add("text-green-400");
            } else {
                icon.className = "fa-solid fa-play text-lg ml-0.5";
                status.textContent = "Paused";
                status.classList.remove("text-green-400");
            }
        }

        function switchTrack(index) {
            currentTrack = index;
            isPlaying = false;
            document.getElementById('play-icon').className = "fa-solid fa-play text-lg ml-0.5";
            document.getElementById('track-title').textContent = tracks[index].title;
            document.getElementById('track-meta').textContent = tracks[index].meta;
            document.getElementById('time-display').textContent = `0:00 / ${tracks[index].time}`;
            document.getElementById('player-status').textContent = "Ready to Play";
        }

        function handleReportSubmit(event) {
            event.preventDefault();
            document.getElementById('form-success').classList.remove('hidden');
            event.target.reset();
        }
    </script>
</body>
</html>
