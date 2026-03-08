<html>
    <head>
        <style>
            body, html {
                margin: 0;
                padding: 0;
                width: 100%;
                height: 100%;
                background: #000;
            }
            #container {
                width: 100%;
                height: 100%;
                position: relative;
            }
            #fullscreen-btn {
                position: absolute;
                top: 15px;
                right: 15px;
                z-index: 999;
                padding: 12px 24px;
                background: #0064ff;
                color: white;
                border: none;
                cursor: pointer;
                border-radius: 4px;
                font-family: sans-serif;
                font-weight: bold;
                box-shadow: 0px 4px 10px rgba(0,0,0,0.3);
            }
        </style>
    </head>
    <body>
        <div id="container">
            <button id="fullscreen-btn" onclick="goFullscreen()">Play Fullscreen</button>
            <div id="game" style="width:100%;height:100%;"></div>
        </div>

        <script>
            EJS_player = "#game";
            EJS_core = "gba";
            EJS_gameName = "PkmnRadicalRed";
            EJS_color = "#0064ff";
            EJS_startOnLoaded = true;
            EJS_pathtodata = "https://cdn.emulatorjs.org/stable/data/";
            EJS_gameUrl = "Pokemon - FireRed Version (USA, Europe) (patched).gba";

            function goFullscreen() {
                const elem = document.getElementById("container");
                if (elem.requestFullscreen) {
                    elem.requestFullscreen();
                } else if (elem.webkitRequestFullscreen) {
                    elem.webkitRequestFullscreen();
                } else if (elem.msRequestFullscreen) {
                    elem.msRequestFullscreen();
                }
            }

            // Detects when the screen changes to hide or show the button
            document.addEventListener('fullscreenchange', handleFSChange);
            document.addEventListener('webkitfullscreenchange', handleFSChange);
            document.addEventListener('msfullscreenchange', handleFSChange);

            function handleFSChange() {
                const btn = document.getElementById('fullscreen-btn');
                const isFS = document.fullscreenElement || document.webkitFullscreenElement || document.msFullscreenElement;
                btn.style.display = isFS ? 'none' : 'block';
            }
        </script>
        <script src="https://cdn.emulatorjs.org/stable/data/loader.js"></script>
    </body>
</html>
