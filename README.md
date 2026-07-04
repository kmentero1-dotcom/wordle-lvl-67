# wordle-lvl-67
just answer the game

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Wordle</title>
<style>
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background: #121213;
    color: white;
}
h1 { margin-top: 20px; }
.grid {
    display: grid;
    grid-template-columns: repeat(6, 60px);
    gap: 5px;
    justify-content: center;
    margin-top: 20px;
}
.tile {
    width: 60px;
    height: 60px;
    border: 2px solid #3a3a3c;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    text-transform: uppercase;
}
.correct { background: #538d4e; }
.present { background: #b59f3b; }
.absent { background: #3a3a3c; }
input {
    margin-top: 20px;
    padding: 10px;
    font-size: 18px;
    text-transform: uppercase;
}
button {
    padding: 10px 20px;
    font-size: 16px;
    margin-left: 10px;
}
</style>
</head>
<body>

<h1>Wordle</h1>
<p>Guess the 6-letter word</p>

<div id="board"></div>

<input id="guess" maxlength="6">
<button onclick="submitGuess()">Enter</button>

<script>
const answer = "DATEME";
const board = document.getElementById("board");

for (let i = 0; i < 6 * 6; i++) {
    let tile = document.createElement("div");
    tile.className = "tile";
    board.appendChild(tile);
}

let currentRow = 0;

function submitGuess() {
    const guess = document.getElementById("guess").value.toUpperCase();
    if (guess.length !== 6) return;

    const start = currentRow * 6;
    const tiles = document.getElementsByClassName("tile");

    for (let i = 0; i < 6; i++) {
        tiles[start + i].textContent = guess[i];

        if (guess[i] === answer[i]) {
            tiles[start + i].classList.add("correct");
        } else if (answer.includes(guess[i])) {
            tiles[start + i].classList.add("present");
        } else {
            tiles[start + i].classList.add("absent");
        }
    }

    if (guess === answer) {
        setTimeout(() => alert("Go on a date with me?"), 300);
    }

    currentRow++;
    document.getElementById("guess").value = "";
}
</script>

</body>
</html>
