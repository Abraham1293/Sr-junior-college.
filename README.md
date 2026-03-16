<!DOCTYPE html>
<html>
<head>
    <title>AM IIT Notes</title>
    <style>
        body {
            font-family: Arial;
            background: #f5f5f5;
            text-align: center;
            padding-bottom: 50px;
        }

        h1 {
            background: #222;
            color: white;
            padding: 20px;
            margin-top: 0;
        }

        /* Search Bar Styling */
        .search-container {
            margin: 20px;
        }

        #searchBar {
            width: 80%;
            max-width: 400px;
            padding: 12px;
            border-radius: 25px;
            border: 1px solid #ccc;
            outline: none;
            font-size: 16px;
        }

        .notes {
            background: white;
            margin: 20px auto;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px #ccc;
            max-width: 600px;
            /* Animation for smooth appearance */
            transition: all 0.3s ease;
        }

        h2 {
            color: #333;
            border-bottom: 2px solid #007BFF;
            padding-bottom: 10px;
        }

        /* The link items we will search through */
        .note-link {
            display: block;
            margin: 10px;
            padding: 10px;
            background: #007BFF;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            transition: 0.2s;
        }

        .note-link:hover {
            background: #0056b3;
        }

        /* Helper class to hide items */
        .hidden {
            display: none !important;
        }
    </style>
</head>

<body>

    <h1>AM IIT Notes</h1>

    <div class="search-container">
        <input type="text" id="searchBar" onkeyup="searchFunction()" placeholder="Search for subjects or chapters...">
    </div>

    <div id="notes-wrapper">
        <div class="notes">
            <h2>Physics</h2>
            <a class="note-link" href="PASTE_LINK">Units and Measurements</a>
            <a class="note-link" href="PASTE_LINK">Kinematics</a>
            <a class="note-link" href="PASTE_LINK">Laws of Motion</a>
        </div>

        <div class="notes">
            <h2>Chemistry</h2>
            <a class="note-link" href="PASTE_LINK">Atomic Structure</a>
            <a class="note-link" href="PASTE_LINK">Chemical Bonding</a>
            <a class="note-link" href="PASTE_LINK">Periodic Table</a>
        </div>

        <div class="notes">
            <h2>Mathematics</h2>
            <a class="note-link" href="PASTE_LINK">Quadratic Equations</a>
            <a class="note-link" href="PASTE_LINK">Trigonometry</a>
            <a class="note-link" href="PASTE_LINK">Limits and Derivatives</a>
        </div>
    </div>

    <script>
        function searchFunction() {
            // Get the text typed in search bar
            let input = document.getElementById('searchBar').value.toLowerCase();
            
            // Get all the note sections
            let sections = document.getElementsByClassName('notes');

            for (let i = 0; i < sections.length; i++) {
                let section = sections[i];
                let links = section.getElementsByClassName('note-link');
                let sectionTitle = section.getElementsByTagName('h2')[0].innerText.toLowerCase();
                
                let sectionHasMatch = false;

                // Check if the Section Title (Physics, etc) matches
                if (sectionTitle.includes(input)) {
                    sectionHasMatch = true;
                    // Show all links in this section if title matches
                    for (let j = 0; j < links.length; j++) {
                        links[j].classList.remove('hidden');
                    }
                } else {
                    // Otherwise, check individual links
                    for (let j = 0; j < links.length; j++) {
                        if (links[j].innerText.toLowerCase().includes(input)) {
                            links[j].classList.remove('hidden');
                            sectionHasMatch = true;
                        } else {
                            links[j].classList.add('hidden');
                        }
                    }
                }

                // If nothing in this section matches, hide the whole card
                if (sectionHasMatch) {
                    section.classList.remove('hidden');
                } else {
                    section.classList.add('hidden');
                }
            }
        }
    </script>

</body>
</html>
