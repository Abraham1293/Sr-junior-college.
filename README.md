<div class="max-w-7xl mx-auto px-4 mt-6">
    <div class="relative max-w-xl mx-auto">
        <span class="absolute inset-y-0 left-0 pl-3 flex items-center">
            <i class="fas fa-search text-gray-400"></i>
        </span>
        <input 
            type="text" 
            id="searchInput" 
            onkeyup="searchTopics()"
            placeholder="Search for topics (e.g., Matrices, Physics, Laws...)" 
            class="w-full pl-10 pr-4 py-3 rounded-xl border border-gray-200 focus:ring-2 focus:ring-indigo-500 focus:outline-none shadow-sm"
        >
    </div>
</div>
function searchTopics() {
    const query = document.getElementById('searchInput').value.toLowerCase();
    const iitGrid = document.getElementById('iit-grid');
    const ipeContainer = document.getElementById('ipe-container');
    
    const data = studyData[currentYear];

    // 1. Filter IIT Cards
    const filteredIIT = data.iit.filter(item => 
        item.sub.toLowerCase().includes(query) || 
        item.topics.some(t => t.toLowerCase().includes(query))
    );

    // 2. Filter IPE Questions
    const filteredIPE = data.ipe.map(subject => ({
        ...subject,
        sections: subject.sections.map(sec => ({
            ...sec,
            qs: sec.qs.filter(q => q.toLowerCase().includes(query))
        })).filter(sec => sec.qs.length > 0)
    })).filter(subject => subject.sections.length > 0);

    // 3. Update the UI
    updateIITUI(filteredIIT);
    updateIPEUI(filteredIPE);
}

// Helper function to render filtered IIT cards
function updateIITUI(filteredData) {
    const iitGrid = document.getElementById('iit-grid');
    if (filteredData.length === 0) {
        iitGrid.innerHTML = `<p class="col-span-full text-center text-gray-500 py-10">No IIT topics found for "${document.getElementById('searchInput').value}"</p>`;
        return;
    }
    iitGrid.innerHTML = filteredData.map((item, idx) => `
        <div class="bg-white p-8 rounded-2xl shadow-sm border border-gray-100 card-hover cursor-pointer" onclick="openIITModal(${idx})">
            <div class="w-14 h-14 bg-${item.color}-100 rounded-xl flex items-center justify-center mb-6">
                <i class="fas ${item.icon} text-${item.color}-600 text-2xl"></i>
            </div>
            <h3 class="text-xl font-bold mb-3">${item.sub}</h3>
            <div class="flex flex-wrap gap-2 mb-6">
                ${item.topics.map(t => `<span class="bg-gray-100 text-gray-600 px-2 py-1 rounded text-xs">${t}</span>`).join('')}
            </div>
        </div>
    `).join('');
}

// Helper function to render filtered IPE rows
function updateIPEUI(filteredData) {
    const ipeContainer = document.getElementById('ipe-container');
    if (filteredData.length === 0) {
        ipeContainer.innerHTML = `<p class="text-center text-gray-500 py-10">No IPE questions found matching your search.</p>`;
        return;
    }
    ipeContainer.innerHTML = filteredData.map(subject => `
        <div class="bg-white rounded-xl shadow-sm overflow-hidden mb-4">
            <div class="bg-gray-800 text-white px-6 py-4">
                <h4 class="text-lg font-bold">${subject.sub}</h4>
            </div>
            <div class="grid md:grid-cols-2 gap-0">
                ${subject.sections.map(sec => `
                    <div class="p-6 border-r border-gray-100 last:border-0">
                        <h5 class="text-indigo-600 font-bold mb-4 italic">${sec.type}</h5>
                        <ul class="space-y-3">
                            ${sec.qs.map(q => `
                                <li class="flex items-start text-sm text-gray-700">
                                    <i class="fas fa-check-circle text-green-500 mt-1 mr-3 shrink-0"></i>
                                    <span>${q}</span>
                                </li>
                            `).join('')}
                        </ul>
                    </div>
                `).join('')}
            </div>
        </div>
    `).join('');
}

# Sr-junior-college.
Free IIT preparation notes for Physics, Chemistry and Maths
<!DOCTYPE html>
<html>
<head>
<title>AM IIT Notes</title>

<style>

body{
font-family: Arial;
background:#f5f5f5;
text-align:center;
}

h1{
background:#222;
color:white;
padding:20px;
}

.notes{
background:white;
margin:20px;
padding:20px;
border-radius:10px;
box-shadow:0px 0px 10px #ccc;
}

a{
display:block;
margin:10px;
padding:10px;
background:#007BFF;
color:white;
text-decoration:none;
border-radius:5px;
}

a:hover{
background:#0056b3;
}

</style>
</head>

<body>

<h1>AM IIT Notes</h1>
<p>This notes are written by toppers and helpful for students who are preparing for jee mains/advance.</p>
<image><img src="https://image2url.com/r2/default/images/1773495382664-ddcdd2e2-be3f-4fd3-aa8d-51f1300e8bb2.jpg" alt="image" /></image>

<div class="notes">

<h2>Physics</h2>

<a href="PASTE_NOTE_LINK_HERE">Units and Measurements</a>

<a href="PASTE_NOTE_LINK_HERE">Kinematics</a>

<a href="PASTE_NOTE_LINK_HERE">Laws of Motion</a>

</div>

<div class="notes">

<h2>Chemistry</h2>

<a href="PASTE_NOTE_LINK_HERE">Atomic Structure</a>

<a href="PASTE_NOTE_LINK_HERE">Chemical Bonding</a>

<a href="PASTE_NOTE_LINK_HERE">Periodic Table</a>

</div>

<div class="notes">

<h2>Mathematics</h2>

<a href="PASTE_NOTE_LINK_HERE">Quadratic Equations</a>

<a href="PASTE_NOTE_LINK_HERE">Trigonometry</a>

<a href="PASTE_NOTE_LINK_HERE">Limits and Derivatives</a>

</div>

</body>
</html>
