<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AM IIT Notes | Premium Portal</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #6366f1; /* Indigo */
            --primary-hover: #4f46e5;
            --bg: #0f172a; /* Deep Navy */
            --card-bg: #1e293b;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --glass: rgba(255, 255, 255, 0.03);
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg);
            color: var(--text-main);
            margin: 0;
            padding-bottom: 100px;
            line-height: 1.6;
        }

        header {
            padding: 60px 20px;
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            border-bottom: 1px solid rgba(255,255,255,0.1);
            margin-bottom: 40px;
        }

        h1 {
            font-size: 2.5rem;
            font-weight: 700;
            letter-spacing: -1px;
            margin: 0;
            background: linear-gradient(to right, #818cf8, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        p.subtitle {
            color: var(--text-muted);
            margin-top: 10px;
        }

        /* Modern Search Bar */
        .search-container {
            position: sticky;
            top: 20px;
            z-index: 100;
            margin-bottom: 40px;
        }

        #searchBar {
            width: 90%;
            max-width: 500px;
            padding: 16px 25px;
            border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.1);
            background: rgba(30, 41, 59, 0.8);
            backdrop-filter: blur(10px);
            color: white;
            font-size: 16px;
            outline: none;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        #searchBar:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.2);
            width: 95%;
        }

        /* Grid Layout for Notes */
        #notes-wrapper {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .notes {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.05);
            text-align: left;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }

        .notes:hover {
            transform: translateY(-5px);
            border-color: rgba(99, 102, 241, 0.4);
        }

        h2 {
            font-size: 1.25rem;
            margin-top: 0;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* Premium Link Styling */
        .note-link {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 12px 0;
            padding: 14px 18px;
            background: var(--glass);
            color: var(--text-main);
            text-decoration: none;
            border-radius: 12px;
            font-weight: 500;
            font-size: 0.95rem;
            transition: all 0.2s ease;
        }

        .note-link:hover {
            background: var(--primary);
            transform: scale(1.02);
        }

        .note-link::after {
            content: '→';
            opacity: 0.5;
        }

        /* Utility */
        .hidden {
            display: none !important;
        }

        @media (max-width: 600px) {
            h1 { font-size: 1.8rem; }
            .notes { padding: 20px; }
        }
    </style>
</head>
<body>

    <header>
        <h1>AM IIT Notes</h1>
        <p class="subtitle">Ultimate Resource for JEE Aspirants</p>
    </header>

    <div class="search-container">
        <input type="text" id="searchBar" onkeyup="searchFunction()" placeholder="Search subjects, topics, or chapters...">
    </div>

    <div id="notes-wrapper">
        <div class="notes">
            <h2><span>⚛️</span> Physics</h2>
            <a class="note-link" href="#">Units and Measurements</a>
            <a class="note-link" href="#">Kinematics</a>
            <a class="note-link" href="#">Laws of Motion</a>
            <a class="note-link" href="#">Work, Energy & Power</a>
        </div>

        <div class="notes">
            <h2><span>🧪</span> Chemistry</h2>
            <a class="note-link" href="#">Atomic Structure</a>
            <a class="note-link" href="#">Chemical Bonding</a>
            <a class="note-link" href="#">Periodic Table</a>
            <a class="note-link" href="#">Thermodynamics</a>
        </div>

        <div class="notes">
            <h2><span>📐</span> Mathematics</h2>
            <a class="note-link" href="#">Quadratic Equations</a>
            <a class="note-link" href="#">Trigonometry</a>
            <a class="note-link" href="#">Limits and Derivatives</a>
            <a class="note-link" href="#">Complex Numbers</a>
        </div>
    </div>

    <script>
        function searchFunction() {
            const input = document.getElementById('searchBar').value.toLowerCase();
            const sections = document.querySelectorAll('.notes');

            sections.forEach(section => {
                const links = section.querySelectorAll('.note-link');
                const title = section.querySelector('h2').innerText.toLowerCase();
                let hasMatch = title.includes(input);

                links.forEach(link => {
                    const text = link.innerText.toLowerCase();
                    if (text.includes(input) || hasMatch) {
                        link.classList.remove('hidden');
                        if (text.includes(input)) hasMatch = true;
                    } else {
                        link.classList.add('hidden');
                    }
                });

                section.style.display = hasMatch ? "block" : "none";
            });
        }
    </script>

</body>
</html>
