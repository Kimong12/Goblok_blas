<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Hans uji coba</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
      background-image: url('bot3.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }
    #game-container {
      background-color: ;
      padding: 10px;
      border-radius: 10px;
      margin: 20px auto;
      width: fit-content;
    }#grid {
  display: grid;
  grid-template-columns: repeat(10, 30px);
  grid-template-rows: repeat(10, 30px);
  gap: 2px;
  margin: 20px;
  position: relative;
}

.cell {
  width: 30px;
  height: 30px;
  background-color: #000;
  border: 1px solid black;
  box-shadow: inset 0 0 5px gold;
  transition: background-color 0.2s ease;
}

.filled {
  background-color: var(--block-color, #007bff) !important;
}

#blocks {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 20px;
}

.block {
  display: grid;
  grid-template-columns: repeat(3, 20px);
  grid-template-rows: repeat(3, 20px);
  gap: 2px;
  background-color: transparent;
  touch-action: none;
}

.block-cell {
  width: 20px;
  height: 20px;
  background-color: var(--block-color, #444);
  border-radius: 4px;
}

  </style>
</head>
<body>
  <h1>-</h1>
  <div id="game-container">
    <div id="blocks"></div>
    <div id="grid"></div>
    <p id="score">Score: 0</p>
  </div>
  <script>
    const grid = document.getElementById("grid");
    const blocksContainer = document.getElementById("blocks");
    const scoreDisplay = document.getElementById("score");
    let score = 0;
    const gridCells = [];
    for (let i = 0; i < 100; i++) {
      const cell = document.createElement("div");
      cell.classList.add("cell");
      grid.appendChild(cell);
      gridCells.push(cell);
    }const blockShapes = [
  [[1, 1, 1]],
  [[1], [1], [1]],
  [[1, 1], [1, 0]],
  [[1, 1], [0, 1]],
  [[1, 1], [1, 1]]
];

const colors = ["#e74c3c", "#8e44ad", "#3498db", "#27ae60", "#f39c12", "#d35400", "#1abc9c"];

function createBlock(shape) {
  const block = document.createElement("div");
  block.classList.add("block");
  const color = colors[Math.floor(Math.random() * colors.length)];
  block.style.setProperty('--block-color', color);
  block.dataset.shape = JSON.stringify(shape);

  shape.forEach((row, y) => {
    row.forEach((val, x) => {
      if (val) {
        const cell = document.createElement("div");
        cell.classList.add("block-cell");
        cell.style.gridRowStart = y + 1;
        cell.style.gridColumnStart = x + 1;
        block.appendChild(cell);
      }
    });
  });

  block.addEventListener("touchstart", onTouchStart);
  blocksContainer.appendChild(block);
}

function generateBlocks() {
  blocksContainer.innerHTML = "";
  for (let i = 0; i < 3; i++) {
    const shape = blockShapes[Math.floor(Math.random() * blockShapes.length)];
    createBlock(shape);
  }
}

let activeBlock = null;
let offsetX = 0;
let offsetY = 0;

function onTouchStart(e) {
  const original = e.currentTarget;
  activeBlock = original.cloneNode(true);
  activeBlock.style.position = "absolute";
  activeBlock.style.zIndex = 1000;
  activeBlock.style.setProperty('--block-color', original.style.getPropertyValue('--block-color'));
  document.body.appendChild(activeBlock);
  offsetX = e.touches[0].clientX - original.getBoundingClientRect().left;
  offsetY = e.touches[0].clientY - original.getBoundingClientRect().top;
  moveBlock(e);

  document.addEventListener("touchmove", moveBlock);
  document.addEventListener("touchend", onTouchEnd);
}

function moveBlock(e) {
  if (!activeBlock) return;
  activeBlock.style.left = (e.touches[0].clientX - offsetX) + "px";
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Hans uji coba</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
      background-image: url('bot3.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }
    #game-container {
      background-color: ;
      padding: 10px;
      border-radius: 10px;
      margin: 20px auto;
      width: fit-content;
    }#grid {
  display: grid;
  grid-template-columns: repeat(10, 30px);
  grid-template-rows: repeat(10, 30px);
  gap: 2px;
  margin: 20px;
  position: relative;
}

.cell {
  width: 30px;
  height: 30px;
  background-color: #000;
  border: 1px solid black;
  box-shadow: inset 0 0 5px gold;
  transition: background-color 0.2s ease;
}

.filled {
  background-color: var(--block-color, #007bff) !important;
}

#blocks {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 20px;
}

.block {
  display: grid;
  grid-template-columns: repeat(3, 20px);
  grid-template-rows: repeat(3, 20px);
  gap: 2px;
  background-color: transparent;
  touch-action: none;
}

.block-cell {
  width: 20px;
  height: 20px;
  background-color: var(--block-color, #444);
  border-radius: 4px;
}

  </style>
</head>
<body>
  <h1>-</h1>
  <div id="game-container">
    <div id="blocks"></div>
    <div id="grid"></div>
    <p id="score">Score: 0</p>
  </div>
  <script>
    const grid = document.getElementById("grid");
    const blocksContainer = document.getElementById("blocks");
    const scoreDisplay = document.getElementById("score");
    let score = 0;
    const gridCells = [];
    for (let i = 0; i < 100; i++) {
      const cell = document.createElement("div");
      cell.classList.add("cell");
      grid.appendChild(cell);
      gridCells.push(cell);
    }const blockShapes = [
  [[1, 1, 1]],
  [[1], [1], [1]],
  [[1, 1], [1, 0]],
  [[1, 1], [0, 1]],
  [[1, 1], [1, 1]]
];

const colors = ["#e74c3c", "#8e44ad", "#3498db", "#27ae60", "#f39c12", "#d35400", "#1abc9c"];

function createBlock(shape) {
  const block = document.createElement("div");
  block.classList.add("block");
  const color = colors[Math.floor(Math.random() * colors.length)];
  block.style.setProperty('--block-color', color);
  block.dataset.shape = JSON.stringify(shape);

  shape.forEach((row, y) => {
    row.forEach((val, x) => {
      if (val) {
        const cell = document.createElement("div");
        cell.classList.add("block-cell");
        cell.style.gridRowStart = y + 1;
        cell.style.gridColumnStart = x + 1;
        block.appendChild(cell);
      }
    });
  });

  block.addEventListener("touchstart", onTouchStart);
  blocksContainer.appendChild(block);
}

function generateBlocks() {
  blocksContainer.innerHTML = "";
  for (let i = 0; i < 3; i++) {
    const shape = blockShapes[Math.floor(Math.random() * blockShapes.length)];
    createBlock(shape);
  }
}

let activeBlock = null;
let offsetX = 0;
let offsetY = 0;

function onTouchStart(e) {
  const original = e.currentTarget;
  activeBlock = original.cloneNode(true);
  activeBlock.style.position = "absolute";
  activeBlock.style.zIndex = 1000;
  activeBlock.style.setProperty('--block-color', original.style.getPropertyValue('--block-color'));
  document.body.appendChild(activeBlock);
  offsetX = e.touches[0].clientX - original.getBoundingClientRect().left;
  offsetY = e.touches[0].clientY - original.getBoundingClientRect().top;
  moveBlock(e);

  document.addEventListener("touchmove", moveBlock);
  document.addEventListener("touchend", onTouchEnd);
}

function moveBlock(e) {
  if (!activeBlock) return;
  activeBlock.style.left = (e.touches[0].clientX - offsetX) + "px";
  activeBlock.style.top = (e.touches[0].clientY - offsetY) + "px";
}

function onTouchEnd(e) {
  const dropX = e.changedTouches[0].clientX;
  const dropY = e.changedTouches[0].clientY;
  const gridRect = grid.getBoundingClientRect();

  const shape = JSON.parse(activeBlock.dataset.shape);
  let col = Math.floor((dropX - gridRect.left) / 32);
  let row = Math.floor((dropY - gridRect.top) / 32);

  col = Math.max(0, col);
  row = Math.max(0, row);

  let canPlace = true;

  shapeLoop:
  for (let y = 0; y < shape.length; y++) {
    for (let x = 0; x < shape[y].length; x++) {
      if (shape[y][x]) {
        const i = (row + y) * 10 + (col + x);
        if (row + y >= 10 || col + x >= 10 || !gridCells[i] || gridCells[i].classList.contains("filled")) {
          canPlace = false;
          break shapeLoop;
        }
      }
    }
  }

  if (canPlace) {
    for (let y = 0; y < shape.length; y++) {
      for (let x = 0; x < shape[y].length; x++) {
        if (shape[y][x]) {
          const i = (row + y) * 10 + (col + x);
          gridCells[i].classList.add("filled");
          gridCells[i].style.setProperty('--block-color', activeBlock.style.getPropertyValue('--block-color'));
          gridCells[i].style.backgroundColor = activeBlock.style.getPropertyValue('--block-color');
        }
      }
    }
    score += 10;
    clearLines();
    generateBlocks();
  }

  if (activeBlock) activeBlock.remove();
  activeBlock = null;
  document.removeEventListener("touchmove", moveBlock);
  document.removeEventListener("touchend", onTouchEnd);
}

function clearLines() {
  for (let r = 0; r < 10; r++) {
    let fullRow = true;
    for (let c = 0; c < 10; c++) {
      if (!gridCells[r * 10 + c].classList.contains("filled")) {
        fullRow = false;
        break;
      }
    }
    if (fullRow) {
      for (let c = 0; c < 10; c++) {
        gridCells[r * 10 + c].classList.remove("filled");
        gridCells[r * 10 + c].style.backgroundColor = "#000";
      }
      score += 50;
    }
  }
  scoreDisplay.textContent = "POIN INGET KOMTOL: " + score;
}

generateBlocks();

  </script>
</body>
</html>￼Enter  activeBlock.style.top = (e.touches[0].clientY - offsetY) + "px";
}

function onTouchEnd(e) {
  const dropX = e.changedTouches[0].clientX;
  const dropY = e.changedTouches[0].clientY;
  const gridRect = grid.getBoundingClientRect();

  const shape = JSON.parse(activeBlock.dataset.shape);
  let col = Math.floor((dropX - gridRect.left) / 32);
  let row = Math.floor((dropY - gridRect.top) / 32);

  col = Math.max(0, col);
  row = Math.max(0, row);

  let canPlace = true;

  shapeLoop:
  for (let y = 0; y < shape.length; y++) {
    for (let x = 0; x < shape[y].length; x++) {
      if (shape[y][x]) {
        const i = (row + y) * 10 + (col + x);
  if (row + y >= 10 || col + x >= 10 || !gridCells[i] || gridCells[i].classList.contains("filled")) {
          canPlace = false;
          break shapeLoop;
        }
      }
    }
  }

  if (canPlace) {
    for (let y = 0; y < shape.length; y++) {
      for (let x = 0; x < shape[y].length; x++) {
        if (shape[y][x]) {
          const i = (row + y) * 10 + (col + x);
          gridCells[i].classList.add("filled");
          gridCells[i].style.setProperty('--block-color', activeBlock.style.getPropertyValue('--block-color'));
          gridCells[i].style.backgroundColor = activeBlock.style.getPropertyValue('--block-color');
        }
      }
    }
    score += 10;
    clearLines();
    generateBlocks();
  }

  if (activeBlock) activeBlock.remove();
