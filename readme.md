# Tic Tac Toe Game

### Project online using GitHub Pages [here](https://stefanopuloz.github.io/Tic-Tac-Toe-Game/)

Tic Tac Toe Game is one page application of the well known two player game. As game itself has fairly simple logic main focus of this project has been UI and adittional features like replays.

Features:

- Fully functional two player Tic Tac Toe game mechanics
- Customizable player names
- Game timer and score
- Save and Load options
- Replay feature for every finished game with all of the standard user controls applied
- All games are automatically saved for later view in replay options

## Logic and Code

Game logic is not complicated here, especially if done using simple double array 3x3, completed whole logic in javascript, made html table and just proceeded from there with UI. 
I did not want to do that and I created divs, connected them with js and moved forward. It is certanly worse approach but I did it to explore what kind of problems I would encounter and to practice DOM manipulation.

First and most obvios downside is code maintenance. As game mechanics and UI mechanics are not clearly separated, making any changes on both ends of the code is made unecessary complicated and time consuming as even UI change could potentially brake the app. 

Second is reusabillity. This is not something that is easily done here as nature of setup dictates that all things are closley entwined and apart from copying the whole project parts of it are very hard to separate. Altough, lack of pure functions can be artributed to my inexpirience in time of writing this project.

So how is it setup?

All divs are labeld with ids. When player clicks on an empty div object is created and pushed in to array with all relevant info:

    function drawMove(cell) {
        moveHistory[gameInfo.turn] = {
            cell: cell,
            sign: currentSign,
            turn: gameInfo.turn + 1,
            playerName: currentPlayer
        };
        tableCheck[cell] = currentSign;
        document.getElementById(`cell${cell}`).classList.add(`sign${currentSign}`);
    };

UI is updated with a corresponding sign class and after it is checked to see if there are any 3 same signs in a row diganollay, vertically and horizontally. If there are, winner is declared and players are free to start another game. First player becomes second and vice versa, colors are changed to indicate who is 'X' and who is 'O', timer is reset, score updated and game is saved in Game Log section avilable to be viewed as a replay.

tableCheck global array serves for checking if there is winner.

If game is not finished Save option becomes avilable. When game is saved it can be loaded and everything is loaded including player names, colors and turns.

Method for changing player colors and names:

    function modifyPlayersAndColors(reset = false) {
        if (!reset && firstPlayer === player1Name) {
            firstPlayer = player2Name;

            player1Color.forEach((element) => element.style.color = '#00b400');
            player2Color.forEach((element) => element.style.color = 'red');
        } else {
            if (!reset) {
                firstPlayer = player1Name;
            };

            player1Color.forEach((element) => element.style.color = 'red');
            player2Color.forEach((element) => element.style.color = '#00b400');
        };
    };

Reset is set to false. If method is called with true parametar it indicates reset is needed and default colors are made. No name changes are made.

## Technologies

Vanilla javascript, css and html. No back end. Local storage is used for storing data.

### Created by Stefan Deak