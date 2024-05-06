<!DOCTYPE html>
<html>
<head>
    <title>Calculadora Científica</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
            text-align: center;
        }

        .calculator {
            width: 90%;
            max-width: 400px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        input[type="button"] {
            width: 45px;
            height: 45px;
            margin: 5px;
            font-size: 18px;
            border: 1px solid #ccc;
            border-radius: 3px;
            background-color: #f9f9f9;
            cursor: pointer;
        }

        input[type="text"] {
            width: 100%;
            height: 45px;
            margin-bottom: 10px;
            padding: 5px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 3px;
            font-size: 18px;
            text-align: right;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled><br>
        <input type="button" value="7" onclick="addToDisplay('7')">
        <input type="button" value="8" onclick="addToDisplay('8')">
        <input type="button" value="9" onclick="addToDisplay('9')">
        <input type="button" value="/" onclick="addToDisplay('/')"><br>
        <input type="button" value="4" onclick="addToDisplay('4')">
        <input type="button" value="5" onclick="addToDisplay('5')">
        <input type="button" value="6" onclick="addToDisplay('6')">
        <input type="button" value="*" onclick="addToDisplay('*')"><br>
        <input type="button" value="1" onclick="addToDisplay('1')">
        <input type="button" value="2" onclick="addToDisplay('2')">
        <input type="button" value="3" onclick="addToDisplay('3')">
        <input type="button" value="-" onclick="addToDisplay('-')"><br>
        <input type="button" value="0" onclick="addToDisplay('0')">
        <input type="button" value="." onclick="addToDisplay('.')">
        <input type="button" value="=" onclick="calculate()">
        <input type="button" value="+" onclick="addToDisplay('+')"><br>
        <input type="button" value="sin" onclick="calculateTrig('sin')">
        <input type="button" value="cos" onclick="calculateTrig('cos')">
        <input type="button" value="tan" onclick="calculateTrig('tan')">
        <input type="button" value="^" onclick="addToDisplay('^')"><br>
        <input type="button" value="sqrt" onclick="calculateSqrt()">
        <input type="button" value="log" onclick="calculateLog()">
        <input type="button" value="(" onclick="addToDisplay('(')">
        <input type="button" value=")" onclick="addToDisplay(')')">
        <input type="button" value="AC" onclick="clearDisplay()">
        <input type="button" value="←" onclick="deleteLastCharacter()">
    </div>

    <script>
        document.onkeydown = function(event) {
            event = event || window.event;
            var key = event.key || event.which || event.keyCode;
            switch (key) {
                case '0':
                    addToDisplay('0');
                    break;
                case '1':
                    addToDisplay('1');
                    break;
                case '2':
                    addToDisplay('2');
                    break;
                case '3':
                    addToDisplay('3');
                    break;
                case '4':
                    addToDisplay('4');
                    break;
                case '5':
                    addToDisplay('5');
                    break;
                case '6':
                    addToDisplay('6');
                    break;
                case '7':
                    addToDisplay('7');
                    break;
                case '8':
                    addToDisplay('8');
                    break;
                case '9':
                    addToDisplay('9');
                    break;
                case '+':
                    addToDisplay('+');
                    break;
                case '-':
                    addToDisplay('-');
                    break;
                case '*':
                    addToDisplay('*');
                    break;
                case '/':
                    addToDisplay('/');
                    break;
                case '.':
                    addToDisplay('.');
                    break;
                case '^':
                    addToDisplay('^');
                    break;
                case 'Enter':
                    calculate();
                    break;
                case 'Backspace':
                    deleteLastCharacter();
                    break;
                default:
                    break;
            }
        }

        function addToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function calculate() {
            try {
                document.getElementById('display').value = eval(document.getElementById('display').value);
            } catch (error) {
                document.getElementById('display').value = 'Error';
            }
        }

        function calculateTrig(func) {
            var value = document.getElementById('display').value;
            var result;

            switch (func) {
                case 'sin':
                    result = Math.sin(parseFloat(value));
                    break;
                case 'cos':
                    result = Math.cos(parseFloat(value));
                    break;
                case 'tan':
                    result = Math.tan(parseFloat(value));
                    break;
                default:
                    result = '';
            }

            document.getElementById('display').value = result;
        }

        function calculateSqrt() {
            var value = document.getElementById('display').value;
            var result = Math.sqrt(parseFloat(value));
            document.getElementById('display').value = result;
        }

        function calculateLog() {
            var value = document.getElementById('display').value;
            var result = Math.log(parseFloat(value));
            document.getElementById('display').value = result;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function deleteLastCharacter() {
            var currentValue = document.getElementById('display').value;
            document.getElementById('display').value = currentValue.slice(0, -1);
        }
    </script>
</body>
</html>
