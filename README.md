<!DOCTYPE html>
<html lang="eu">
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3.ariketa</title>
</head>
<body>

    <h1>JavaScript Funtzio ezberdinak Lander.P</h1>
    
    <section>
        <h2>1. Testu-Aldatzailea</h2>
        <p id="testu_aldagarria">Rafa Nadal (1986, Manacor) tenislari espainiar ospetsua da, historiako jokalaririk arrakastatsu eta diziplinatuenetakoa.
Bere 22 Grand Slam tituluengatik eta borroka-espirituagatik mundu osoan ezaguna da.</p>
        <button onclick="aldatuTestua()">Testua aldatu</button>
    </section>

    <section>
        <h2>2. Kolore Txandakatzailea</h2>
        <p id="kolore_aldagarria">Kaixo egunon, Lander deitzen naiz.</p>
        <button onclick="aldatuKolorea()">Kolorea txandakatu</button>
    </section>

    <section>
        <h2>3. Elementuen Ezkutagailua</h2>
        <p id="ezkutatu_hau">Cristiano Ronaldo (1985, Madeira) portugaldar futbolaria da, historiako jokalaririk arrakastatsu eta gol-sartzaileenetakoa.</p>
        <button onclick="txandakatuEzkutatzea()">Txandakatu</button>
    </section>

    <section>
        <h2>4. Batuketa Kalkulagailua</h2>
        <input type="number" id="zenbaki1" placeholder="Zenbakia 1"> +
        <input type="number" id="zenbaki2" placeholder="Zenbakia 2">
        <button onclick="batuketaEgin()">Batu</button>
        <p>Emaitza: <span id="emaitza4"></span></p>
    </section>
    
    <section>
        <h2>5. Zerrenda Dinamikoa</h2>
        <input type="text" id="elementu_berria" placeholder="Elementu berria idatzi">
        <button onclick="gehituElementua()">Gehitu</button>
        <ul id="zerrenda_dinamikoa"></ul>
    </section>

    <section>
        <h2>6. Klik Kontagailua</h2>
        <p>Klika kopurua: <span id="kontagailu_emaitza">0</span></p>
        <button onclick="kontatuKlik()">Klikatu</button>
    </section>

    <section>
        <h2>7. Zenbaki Asmatzearen Jokoa (1-5)</h2>
        <input type="number" id="asmatutako_zenbakia" placeholder="Zure zenbakia (1-5)">
        <button onclick="konprobatuZenbakia()">Konprobatu</button>
        <p id="joko_emaitza"></p>
    </section>
    
    <section>
        <h2>8. Atzeko Planoaren Kolore-Aldatzailea</h2>
        <button onclick="aldatuAtzekoPlanoarenKolorea()">Aldatu</button>
    </section>

    <script>
        // 🔹 Aldagai globalak
        let klikKopurua = 0;
        let zenbakiSekretua = Math.floor(Math.random() * 5) + 1;

        // 1. Testu-Aldatzailea
        function aldatuTestua() {
            const p = document.getElementById("testu_aldagarria");
            if (p.textContent === "Hau da hasierako testua") {
                p.textContent = "Testua aldatu da!";
            } else {
                p.textContent = "Carlos Alcaraz (2003, El Palmar) espainiar tenislari gaztea da, bere talentu eta indar fisikoagatik nabarmentzen dena.";
            }
        }

        // 2. Kolore Txandakatzailea
        function aldatuKolorea() {
            const p = document.getElementById("kolore_aldagarria");
            const koloreak = ["red", "blue", "green", "purple", "orange"];
            let unekoKolorea = p.dataset.kolore || 0;
            unekoKolorea = (parseInt(unekoKolorea) + 1) % koloreak.length;
            p.style.color = koloreak[unekoKolorea];
            p.dataset.kolore = unekoKolorea;
        }

        // 3. Elementuen Ezkutagailua
        function txandakatuEzkutatzea() {
            const p = document.getElementById("ezkutatu_hau");
            if (p.style.display === "none") {
                p.style.display = "block";
            } else {
                p.style.display = "none";
            }
        }

        // 4. Batuketa Kalkulagailua
        function batuketaEgin() {
            const n1 = document.getElementById("zenbaki1").value;
            const n2 = document.getElementById("zenbaki2").value;
            const emaitza = document.getElementById("emaitza4");
            const z1 = parseFloat(n1);
            const z2 = parseFloat(n2);

            if (isNaN(z1) || isNaN(z2)) {
                emaitza.textContent = "Sartu bi zenbaki, mesedez.";
            } else {
                emaitza.textContent = z1 + z2;
            }
        }

        // 5. Zerrenda Dinamikoa
        function gehituElementua() {
            const input = document.getElementById("elementu_berria");
            const zerrenda = document.getElementById("zerrenda_dinamikoa");
            const testua = input.value.trim();

            if (testua === "") return;

            const li = document.createElement("li");
            li.textContent = testua;
            zerrenda.appendChild(li);
            input.value = "";
        }

        // 6. Klik Kontagailua
        function kontatuKlik() {
            klikKopurua++;
            document.getElementById("kontagailu_emaitza").textContent = klikKopurua;
        }

        // 7. Zenbaki Asmatzearen Jokoa
        function konprobatuZenbakia() {
            const sarrera = document.getElementById("asmatutako_zenbakia");
            const emaitza = document.getElementById("joko_emaitza");
            const zenb = parseInt(sarrera.value);

            if (isNaN(zenb) || zenb < 1 || zenb > 5) {
                emaitza.textContent = "1 eta 5 arteko zenbakia sartu.";
                return;
            }

            if (zenb === zenbakiSekretua) {
                emaitza.textContent = "Zorionak! Asmatu duzu!";
                zenbakiSekretua = Math.floor(Math.random() * 5) + 1;
            } else {
                emaitza.textContent = "Ez da zuzena. Saiatu berriro!";
            }
            sarrera.value = "";
        }

        // 8. Atzeko Planoaren Kolore-Aldatzailea
        function aldatuAtzekoPlanoarenKolorea() {
            const koloreak = ["#FFCCCC", "#CCFFCC", "#CCCCFF", "#FFFFCC", "#FFCCFF"];
            const koloreBerria = koloreak[Math.floor(Math.random() * koloreak.length)];
            document.body.style.backgroundColor = koloreBerria;
        }
    </script>
</body>
</html>
