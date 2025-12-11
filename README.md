# e-Funktionen
Alles über e-Funktionen
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>E-Funktionen – Interaktive Lernseite</title>

    <!-- Design -->
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f3f4f6;
        }
        header {
            background: #2563eb;
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 26px;
        }
        nav {
            background: #1e40af;
            padding: 10px;
            display: flex;
            gap: 20px;
        }
        nav a {
            color: white;
            text-decoration: none;
            font-weight: bold;
        }
        .container {
            max-width: 1000px;
            margin: auto;
            padding: 20px;
            background: white;
        }
        h2 {
            margin-top: 40px;
            color: #1e3a8a;
        }
        .formula {
            background: #eef2ff;
            padding: 10px;
            border-left: 3px solid #6366f1;
            margin: 15px 0;
        }
        .task {
            background: #f9fafb;
            border: 1px solid #e5e7eb;
            padding: 10px;
            margin-top: 10px;
        }
        .solution {
            display: none;
            background: #dbeafe;
            padding: 10px;
            margin-top: 5px;
        }
        button {
            margin-top: 5px;
            padding: 6px 12px;
        }
    </style>

    <!-- MathJax -->
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async
        src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

<body>

<header>
    Interaktive Lernseite: Die e-Funktion
</header>

<nav>
    <a href="#definition">Definition</a>
    <a href="#eigenschaften">Eigenschaften</a>
    <a href="#interaktiv">Interaktive Grafik</a>
    <a href="#aufgaben">Aufgaben</a>
</nav>

<div class="container">

    <!-- Definition -->
    <h2 id="definition">1. Definition</h2>
    <p>
        Die wichtigste Exponentialfunktion ist die <strong>e-Funktion</strong>:
    </p>
    <p class="formula">
        \( f(x) = e^x \)
    </p>
    <p>
        Sie ist besonders, weil:
    </p>
    <ul>
        <li>ihre Ableitung gleich der Funktion ist</li>
        <li>sie in Naturwissenschaften überall vorkommt</li>
        <li>sie besonders leicht zu rechnen ist</li>
    </ul>

    <!-- Eigenschaften -->
    <h2 id="eigenschaften">2. Eigenschaften</h2>
    <ul>
        <li>Definitionsbereich: \( \mathbb{R} \)</li>
        <li>Wertebereich: \( (0, \infty) \)</li>
        <li>streng monoton wachsend</li>
        <li>kein Schnittpunkt mit der x-Achse</li>
    </ul>

    <h3>Ableitung</h3>
    <p class="formula">
        \( (e^x)' = e^x \)
    </p>

    <h3>Allgemeine e-Funktion</h3>
    <p class="formula">
        \( f(x) = a \cdot e^{bx} \)
    </p>

    <ul>
        <li>\(a\) = Streckung/Stauchung</li>
        <li>\(b\) = Wachstum oder Zerfall</li>
    </ul>

    <!-- Interaktive Grafik -->
    <h2 id="interaktiv">3. Interaktive Grafik – Parameter verändern</h2>

    <p>Verändere die Parameter, um die Wirkung auf den Graphen zu sehen:</p>

    <label>a: <input type="range" id="a" min="-5" max="5" step="0.1" value="1"></label>
    <br>
    <label>b: <input type="range" id="b" min="-5" max="5" step="0.1" value="1"></label>

    <canvas id="plot" width="700" height="350" style="border:1px solid #ccc; margin-top:20px;"></canvas>

    <script>
        function draw() {
            const a = parseFloat(document.getElementById("a").value);
            const b = parseFloat(document.getElementById("b").value);
            const c = document.getElementById("plot");
            const ctx = c.getContext("2d");

            ctx.clearRect(0,0,c.width,c.height);

            // Koordinatensystem
            ctx.strokeStyle = "#888";
            ctx.beginPath();
            ctx.moveTo(350, 0);
            ctx.lineTo(350, 350);
            ctx.moveTo(0, 175);
            ctx.lineTo(700, 175);
            ctx.stroke();

            // Graph
            ctx.strokeStyle = "black";
            ctx.beginPath();

            let first = true;
            for (let x = -10; x <= 10; x += 0.1) {
                const y = a * Math.exp(b * x);
                const px = 350 + x * 20;
                const py = 175 - y * 20;

                if (first) {
                    ctx.moveTo(px, py);
                    first = false;
                } else {
                    ctx.lineTo(px, py);
                }
            }

            ctx.stroke();
        }

        document.getElementById("a").oninput = draw;
        document.getElementById("b").oninput = draw;

        draw();
    </script>

    <!-- Aufgaben -->
    <h2 id="aufgaben">4. Aufgaben</h2>

    <div class="task">
        <strong>Aufgabe 1:</strong><br>
        Bestimme die Ableitung von  
        \( f(x) = 3e^{2x} \).
        <br>
        <button onclick="toggle('s1')">Lösung anzeigen</button>
        <div id="s1" class="solution">
            \( f'(x) = 6e^{2x} \)
        </div>
    </div>

    <div class="task">
        <strong>Aufgabe 2:</strong><br>
        Löse die Gleichung  
        \( e^{x} = 5 \).
        <br>
        <button onclick="toggle('s2')">Lösung anzeigen</button>
        <div id="s2" class="solution">
            \( x = \ln(5) \)
        </div>
    </div>

    <div class="task">
        <strong>Aufgabe 3:</strong><br>
        Eine Population wächst nach \( f(x) = 100e^{0{,}4x} \).  
        Wie groß ist sie nach 3 Stunden?
        <br>
        <button onclick="toggle('s3')">Lösung anzeigen</button>
        <div id="s3" class="solution">
            \( f(3) = 100e^{1{,}2} \approx 332{,}01 \)
        </div>
    </div>

    <script>
        function toggle(id){
            const el = document.getElementById(id);
            el.style.display = el.style.display === "block" ? "none" : "block";
        }
    </script>

</div>
</body>
</html>