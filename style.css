const gridSize = 25;
const grid = document.getElementById('grid');
const scoreDisplay = document.getElementById('score');
const gameOverDisplay = document.getElementById('game-over');
const restartButton = document.getElementById('restart');

let snake = [{x: 10, y: 10}];
let food = {x: 15, y: 15};
let direction = {x: 0, y: 0};
let score = 0;
let gameRunning = true;

function createGrid() {
    for (let i = 0; i < gridSize * gridSize; i++) {
        const cell = document.createElement('div');
        cell.classList.add('cell');
        grid.appendChild(cell);
    }
}

function getCell(x, y) {
    return grid.children[y * gridSize + x];
}

function draw() {
    // Clear grid
    for (let cell of grid.children) {
        cell.classList.remove('snake', 'food');
    }
    // Draw snake
    snake.forEach(segment => {
        getCell(segment.x, segment.y).classList.add('snake');
    });
    // Draw food
    getCell(food.x, food.y).classList.add('food');
}

function moveSnake() {
    const head = {x: snake[0].x + direction.x, y: snake[0].y + direction.y};
    snake.unshift(head);
    if (head.x === food.x && head.y === food.y) {
        score++;
        scoreDisplay.textContent = `Punteggio: ${score}`;
        generateFood();
    } else {
        snake.pop();
    }
}

function generateFood() {
    do {
        food.x = Math.floor(Math.random() * gridSize);
        food.y = Math.floor(Math.random() * gridSize);
    } while (snake.some(segment => segment.x === food.x && segment.y === food.y));
}

function checkCollision() {
    const head = snake[0];
    if (head.x < 0 || head.x >= gridSize || head.y < 0 || head.y >= gridSize) {
        return true;
    }
    for (let i = 1; i < snake.length; i++) {
        if (head.x === snake[i].x && head.y === snake[i].y) {
            return true;
        }
    }
    return false;
}

function gameLoop() {
    if (!gameRunning) return;
    moveSnake();
    if (checkCollision()) {
        gameRunning = false;
        gameOverDisplay.style.display = 'block';
        return;
    }
    draw();
}

function changeDirection(event) {
    if (!gameRunning) return;
    const key = event.key;
    if (key === 'ArrowUp' && direction.y === 0) {
        direction = {x: 0, y: -1};
    } else if (key === 'ArrowDown' && direction.y === 0) {
        direction = {x: 0, y: 1};
    } else if (key === 'ArrowLeft' && direction.x === 0) {
        direction = {x: -1, y: 0};
    } else if (key === 'ArrowRight' && direction.x === 0) {
        direction = {x: 1, y: 0};
    }
}

function restartGame() {
    snake = [{x: 10, y: 10}];
    direction = {x: 0, y: 0};
    score = 0;
    scoreDisplay.textContent = `Punteggio: ${score}`;
    gameRunning = true;
    gameOverDisplay.style.display = 'none';
    generateFood();
    draw();
}

document.addEventListener('keydown', changeDirection);
restartButton.addEventListener('click', restartGame);

createGrid();
generateFood();
draw();
setInterval(gameLoop, 200);
