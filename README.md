# Poetry-book

<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>কবিতার বই</title>
  <link rel="stylesheet" href="style.css" />
  <style>
    body {
  font-family: 'Siyam Rupali', sans-serif;
  background-color: #fefdfb;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  background-color: #8e44ad;
  color: white;
  padding: 20px;
  text-align: center;
}

#search {
  margin-top: 10px;
  padding: 8px;
  width: 80%;
  max-width: 400px;
  border-radius: 5px;
  border: none;
}

main {
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.poem-card {
  background-color: #f1e9ff;
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 15px;
  margin: 10px;
  width: 250px;
  cursor: pointer;
  transition: transform 0.2s ease;
}

.poem-card:hover {
  transform: scale(1.03);
}

footer {
  text-align: center;
  background-color: #8e44ad;
  color: white;
  padding: 15px;
  margin-top: 20px;
}

.modal {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background-color: rgba(0,0,0,0.6);
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 30px;
  border-radius: 10px;
  width: 90%;
  max-width: 600px;
  position: relative;
}

#close-btn {
  position: absolute;
  top: 10px; right: 15px;
  font-size: 22px;
  cursor: pointer;
}

  </style>
</head>
<body>
  <header>
    <h1>📖 কবিতার বই</h1>
    <input type="text" id="search" placeholder="কবিতার নাম লিখুন..." />
  </header>

  <main id="poem-list">
    <!-- কবিতা এখানে JavaScript দিয়ে আসবে -->
  </main>

  <div id="poem-modal" class="modal">
    <div class="modal-content">
      <span id="close-btn">&times;</span>
      <h2 id="modal-title"></h2>
      <p id="modal-body"></p>
    </div>
  </div>

  <footer>
    <p> &copy; ২০২৫ - শাহরিয়া সবুজ শিশির| সমস্ত অধিকার সংরক্ষিত</p>
  </footer>

  <script src="script.js">
    const poems = [
  {
    title: "আমার সোনার বাংলা",
    content: `আমার সোনার বাংলা, আমি তোমায় ভালবাসি।
চিরদিন তোমার আকাশ, তোমার বাতাস, আমার প্রাণে বাজায় বাঁশি॥`
  },
  {
    title: "বিদায়",
    content: `শেষ দেখার সেই ক্ষণ এল
চোখের জলে কথা বলল
বিদায় বন্ধু, থাকো ভালো,
মনের গভীরে তুমি রবে আলো।`
  },
  {
    title: "নবজাগরণ",
    content: `আলো জ্বালাও হৃদয় মাঝে,
জেগে ওঠো নতুন সাজে।
ভবিষ্যতের স্বপ্ন চোখে,
এসো সবাই মিলি এক পথে।`
  }
];

const poemList = document.getElementById("poem-list");
const searchInput = document.getElementById("search");
const modal = document.getElementById("poem-modal");
const modalTitle = document.getElementById("modal-title");
const modalBody = document.getElementById("modal-body");
const closeBtn = document.getElementById("close-btn");

function displayPoems(filter = "") {
  poemList.innerHTML = "";
  poems
    .filter(poem => poem.title.includes(filter))
    .forEach((poem, index) => {
      const card = document.createElement("div");
      card.className = "poem-card";
      card.innerHTML = `<h3>${poem.title}</h3>`;
      card.onclick = () => showPoem(index);
      poemList.appendChild(card);
    });
}

function showPoem(index) {
  modal.style.display = "flex";
  modalTitle.textContent = poems[index].title;
  modalBody.textContent = poems[index].content;
}

closeBtn.onclick = () => {
  modal.style.display = "none";
};

window.onclick = e => {
  if (e.target === modal) {
    modal.style.display = "none";
  }
};

searchInput.addEventListener("input", () => {
  const value = searchInput.value.trim();
  displayPoems(value);
});

displayPoems(); // Initial Load
    
  </script>

