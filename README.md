<!DOCTYPE html>
<html lang="pl">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Generowanie tablicy liczb</title>
</head>

<body>
    <h1>Generowanie tablicy liczb</h1>
    <label for="start">Od:</label>
    <input type="number" id="start" placeholder="Wprowadź początek zakresu">
    <label for="end">Do:</label>
    <input type="number" id="end" placeholder="Wprowadź koniec zakresu">
    <button onclick="generateArray()">Generate</button>

    <p>Średnia: <span id="average"></span></p>
    <p>Liczby: <span id="numbers"></span></p>
    <p>Pierwszych 13 liczb: <span id="first-13"></span></p>

    <script>
        function createArray(start, end) {
            let array = [];
            for (let i = start; i <= end; i++) {
                array.push(i);
            }
            return array;
        }

        function calculateAverage(array) {
            let sum = array.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
            return sum / array.length;
        }

        function generateArray() {
            const start = parseInt(document.getElementById('start').value);
            const end = parseInt(document.getElementById('end').value);

            if (isNaN(start) || isNaN(end) || start > end) {
                alert("Proszę wprowadzić poprawne wartości dla zakresu.");
                return;
            }

            const numbersArray = createArray(start, end);
            const average = calculateAverage(numbersArray).toFixed(2);
            const first13 = numbersArray.slice(0, 13);

            document.getElementById('average').textContent = average;
            document.getElementById('numbers').textContent = numbersArray.join(', ');
            document.getElementById('first-13').textContent = first13.join(', ');
        }
    </script>
</body>

</html>
