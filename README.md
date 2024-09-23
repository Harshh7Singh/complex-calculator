# complex-calculator
This Complex Calculator is a feature-rich mathematical tool designed to handle a wide variety of operations, including basic arithmetic, trigonometric functions, and advanced calculations such as square roots. Using html,css and javascript

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Complex Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        .calculator {
            background-color: #333;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0,0,0,0.5);
        }
        #display {
            width: 100%;
            height: 60px;
            font-size: 24px;
            text-align: right;
            margin-bottom: 10px;
            padding: 5px;
            background-color: #eee;
            border: none;
            border-radius: 5px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 10px;
        }
        button {
            width: 100%;
            height: 50px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            opacity: 0.8;
        }
        .number, .decimal {
            background-color: #4CAF50;
            color: white;
        }
        .operator {
            background-color: #2196F3;
            color: white;
        }
        .function {
            background-color: #FF9800;
            color: white;
        }
        .clear, .equals {
            background-color: #f44336;
            color: white;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" readonly>
        <div class="buttons">
            <button class="clear" onclick="clearDisplay()">C</button>
            <button class="function" onclick="appendToDisplay('(')">(</button>
            <button class="function" onclick="appendToDisplay(')')">)</button>
            <button class="function" onclick="calculateSquareRoot()">√</button>
            <button class="function" onclick="calculatePower()">^</button>
            
            <button class="number" onclick="appendToDisplay('7')">7</button>
            <button class="number" onclick="appendToDisplay('8')">8</button>
            <button class="number" onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            <button class="function" onclick="calculateSin()">sin</button>
            
            <button class="number" onclick="appendToDisplay('4')">4</button>
            <button class="number" onclick="appendToDisplay('5')">5</button>
            <button class="number" onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
            <button class="function" onclick="calculateCos()">cos</button>
            
            <button class="number" onclick="appendToDisplay('1')">1</button>
            <button class="number" onclick="appendToDisplay('2')">2</button>
            <button class="number" onclick="appendToDisplay('3')">3</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            <button class="function" onclick="calculateTan()">tan</button>
            
            <button class="number" onclick="appendToDisplay('0')">0</button>
            <button class="decimal" onclick="appendToDisplay('.')">.</button>
            <button class="function" onclick="calculatePercentage()">%</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            <button class="equals" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            try {
                const result = eval(document.getElementById('display').value);
                document.getElementById('display').value = result;
            } catch (error) {
                document.getElementById('display').value = 'Error';
            }
        }

        function calculateSquareRoot() {
            const value = parseFloat(document.getElementById('display').value);
            if (value >= 0) {
                document.getElementById('display').value = Math.sqrt(value);
            } else {
                document.getElementById('display').value = 'Error';
            }
        }

        function calculatePower() {
            appendToDisplay('**');
        }

        function calculateSin() {
            const value = parseFloat(document.getElementById('display').value);
            document.getElementById('display').value = Math.sin(value * Math.PI / 180);
        }

        function calculateCos() {
            const value = parseFloat(document.getElementById('display').value);
            document.getElementById('display').value = Math.cos(value * Math.PI / 180);
        }

        function calculateTan() {
            const value = parseFloat(document.getElementById('display').value);
            document.getElementById('display').value = Math.tan(value * Math.PI / 180);
        }

        function calculatePercentage() {
            const value = parseFloat(document.getElementById('display').value);
            document.getElementById('display').value = value / 100;
        }
    </script>
</body>
</html>
