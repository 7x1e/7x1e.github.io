<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7x1e</title>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #000;
            color: #fff;
            font-family: 'Fira Code', monospace;
            overflow: hidden;
        }
        #title {
            position: absolute;
            top: 20px;
            font-size: 3em;
            color: #fff;
        }
        #counter {
            font-size: 4em;
            margin-bottom: 20px;
        }
        #graph {
            width: 80%;
            height: 200px;
            border: 1px solid #fff;
            position: relative;
            overflow: hidden;
        }
        .bar {
            position: absolute;
            bottom: 0;
            width: 1px;
            background: linear-gradient(to top, red, orange, yellow, green, blue, indigo, violet);
        }
    </style>
</head>
<body>
    <div id="title">7x1e</div>
    <div id="counter">1</div>
    <div id="graph"></div>
    <script>
        const counterElement = document.getElementById('counter');
        const graphElement = document.getElementById('graph');
        let count = 1;
        let bars = [];

        function updateCounter() {
            count++;
            counterElement.textContent = count;
            addBar();
        }

        function addBar() {
            const bar = document.createElement('div');
            bar.className = 'bar';
            bar.style.height = `${(Math.sin(count / 10) * 100 + 100)}px`; // Example function for height
            bar.style.left = `${(count % graphElement.clientWidth)}px`;
            graphElement.appendChild(bar);
            bars.push(bar);

            // Remove old bars to prevent memory issues
            if (bars.length > graphElement.clientWidth) {
                graphElement.removeChild(bars.shift());
            }
        }

        setInterval(updateCounter, 20); // Update every 20ms for a faster graph
    </script>
</body>
</html>
