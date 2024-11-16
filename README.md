<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number System Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 400px;
            width: 100%;
        }

        h1 {
            margin-bottom: 20px;
            font-size: 24px;
            color: #333;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }

        input, select, button {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-bottom: 10px;
        }

        button {
            background-color: #007BFF;
            color: white;
            cursor: pointer;
            border: none;
        }

        button:hover {
            background-color: #0056b3;
        }

        #result {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Number System Converter</h1>
        <div class="form-group">
            <label for="inputValue">Enter a Number:</label>
            <input type="text" id="inputValue" placeholder="Enter number">
        </div>
        <div class="form-group">
            <label for="fromBase">From Base:</label>
            <select id="fromBase">
                <option value="10">Decimal</option>
                <option value="2">Binary</option>
                <option value="8">Octal</option>
                <option value="16">Hexadecimal</option>
            </select>
        </div>
        <div class="form-group">
            <label for="toBase">To Base:</label>
            <select id="toBase">
                <option value="10">Decimal</option>
                <option value="2">Binary</option>
                <option value="8">Octal</option>
                <option value="16">Hexadecimal</option>
            </select>
        </div>
        <button onclick="convertNumber()">Convert</button>
        <h2 id="result">Result: </h2>
    </div>
    <script>
        function convertNumber() {
            const inputValue = document.getElementById("inputValue").value;
            const fromBase = parseInt(document.getElementById("fromBase").value);
            const toBase = parseInt(document.getElementById("toBase").value);
            const resultElement = document.getElementById("result");

            // Check if the input is valid
            try {
                // Convert the input to decimal
                const decimalValue = parseInt(inputValue, fromBase);
                if (isNaN(decimalValue)) {
                    throw new Error("Invalid input for the selected base.");
                }

                // Convert decimal to the target base
                let convertedValue;
                switch (toBase) {
                    case 2:
                        convertedValue = decimalValue.toString(2);
                        break;
                    case 8:
                        convertedValue = decimalValue.toString(8);
                        break;
                    case 16:
                        convertedValue = decimalValue.toString(16).toUpperCase();
                        break;
                    case 10:
                        convertedValue = decimalValue.toString(10);
                        break;
                    default:
                        convertedValue = "Invalid base!";
                }

                resultElement.textContent = `Result: ${convertedValue}`;
            } catch (error) {
                resultElement.textContent = `Error: ${error.message}`;
            }
        }
    </script>
</body>
</html>
