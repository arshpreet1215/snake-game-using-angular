# snake-game-using-angular
Snake changes color after eating each dot

<!DOCTYPE html>

<html lang=”en” ng-app=”snakeApp”>

<head>

    <meta charset=”UTF-8”>

    <meta name=”viewport” content=”width=device-width, initial-scale=1.0”>

    <title>Snake Game</title>

    <style>

        .game-board {

            Display: grid;

            Grid-template-columns: repeat(20, 20px);

            Grid-template-rows: repeat(20, 20px);

            Border: 1px solid black;

        }

 

        .game-board div {

            Width: 20px;

            Height: 20px;

            Border: 1px solid black;

        }

 

        .snake-body {

            Background-color: green;

        }

 

        .dot {

            Background-color: red;

        }

 

        .snake-head {

            Background-color: blue;

        }

    </style>

</head>

<body ng-controller=”snakeController as snake”>

    <div class=”game-board” ng-init=”initGameBoard()”>

        <div ng-repeat=”cell in gameBoard” ng-class=”{‘snake-body’: cell.isSnakeBody, ‘dot’: cell.isDot, ‘snake-head’: cell.isSnakeHead}” ng-click=”moveSnake(cell)”></div>

    </div>

    <script src=https://ajax.googleapis.com/ajax/libs/angularjs/1.7.9/angular.min.js></script>

    <script>

        Const app = angular.module(‘snakeApp’, []);

 

        App.controller(‘snakeController’, function() {

            This.gameBoard = [];

            This.snake = {

                Body: [{ x: 10, y: 10 }],

                Direction: ‘right’,

                Color: ‘green’

            };

            This.dot = { x: 5, y: 5 };

 

            This.initGameBoard = function() {

                For (let I = 0; I < 20; i++) {

                    For (let j = 0; j < 20; j++) {

                        This.gameBoard.push({ x: I, y: j, isSnakeBody: false, isDot: false, isSnakeHead: false });

                    }

                }

                This.gameBoard[this.snake.body[0].y * 20 + this.snake.body[0].x].isSnakeHead = true;

                This.gameBoard[this.dot.y * 20 + this.dot.x].isDot = true;

            };

 

            This.moveSnake = function(cell) {

                If (cell.isDot) {

                    This.snake.body.push({ x: cell.x, y: cell.y });

                    This.snake.color = this.getRandomColor();

                    This.placeDot();

                } else {

                    This.snake.body.shift();

                }

                This.snake.body.push({ x: cell.x, y: cell.y });

                This.updateGameBoard();

            };

 

            This.updateGameBoard = function() {

                This.gameBoard.forEach(cell => {

                    Cell.isSnakeBody = false;

                    Cell.isDot = false;

                    Cell.isSnakeHead = false;

                });

                This.snake.body.forEach(segment => {

                    This.gameBoard[segment.y * 20 + segment.x].isSnakeBody = true;

                });

                This.gameBoard[this.snake.body[0].y * 20 + this.snake.body[0].x].isSnakeHead = true;

                This.gameBoard[this.dot.y * 20 + this.dot.x].isDot = true;

            };

 

            This.placeDot = function() {

                Let x, y;

                Do {

                    X = Math.floor(Math.random() *

