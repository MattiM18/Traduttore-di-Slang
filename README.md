<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">


<title>Traduttore di Slang Online | Traduci Slang Inglese</title>
<meta name="description" content="Traduttore di slang inglese in italiano. Traduci oltre 200 slang online facilmente e rapidamente.">
<meta name="keywords" content="slang, traduttore slang, inglese italiano, traduzione slang online, slang moderno, dizionario slang">
<meta name="author" content="Tuo Nome">


<meta property="og:title" content="Traduttore di Slang Online">
<meta property="og:description" content="Traduci oltre 200 slang inglesi in italiano in modo semplice e veloce.">
<meta property="og:type" content="website">
<meta property="og:url" content="https://tuo-username.github.io/traduttore-slang/">
<meta property="og:image" content="URL_immagine_preview.png">

<style>
* { box-sizing: border-box; margin:0; padding:0; }
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background:#f0f0f5; color:#333; min-height:100vh; display:flex; flex-direction:column; transition:0.3s;}
body.dark { background:#1e1e2f; color:#f0f0f5; }
header { background:#4CAF50; color:white; padding:25px 0; text-align:center; font-size:2em; font-weight:bold; box-shadow:0 4px 10px rgba(0,0,0,0.2); }
main { flex:1; display:flex; justify-content:center; align-items:flex-start; padding:30px 10px; }
.card { background:rgba(255,255,255,0.95); border-radius:15px; padding:25px 20px; max-width:500px; width:100%; box-shadow:0 8px 20px rgba(0,0,0,0.15); transition:0.3s;}
body.dark .card { background:rgba(30,30,47,0.95);}
input { width:100%; padding:12px 15px; margin-bottom:15px; border-radius:8px; border:1px solid #ccc; font-size:16px;}
body.dark input { background:#333; color:#f0f0f5; border:1px solid #555;}
input:focus { outline:none; border-color:#4CAF50; box-shadow:0 0 5px #4CAF50;}
.btn { padding:12px 18px; font-size:16px; border:none; border-radius:8px; cursor:pointer; margin-right:10px; margin-bottom:10px; transition:all 0.2s;}
.btn:hover { transform:translateY(-2px); box-shadow:0 4px 10px rgba(0,0,0,0.2);}
.btn.translate { background-color:#4CAF50; color:white;}
.btn.translate:hover { background-color:#45a049;}
.btn.theme { background-color:#555; color:white;}
.btn.theme:hover { background-color:#777;}
#result { margin-top:20px; font-size:18px; min-height:24px;}
#suggestions, #history { margin-top:15px; font-size:16px; text-align:left;}
#suggestions div, #history div { cursor:pointer; padding:8px 10px; border-radius:8px; margin-bottom:5px; transition:all 0.2s;}
#suggestions div:hover, #history div:hover { background-color:#e0e0e0;}
body.dark #suggestions div:hover, body.dark #history div:hover { background-color:#444;}
#counter { margin-top:15px; font-size:16px; font-weight:bold;}
footer { text-align:center; padding:15px 0; background:#f9f9f9; font-size:14px; color:#555; box-shadow:0 -2px 10px rgba(0,0,0,0.05);}
body.dark footer { background:#111; color:#ccc;}
#adsense { margin:20px 0; text-align:center;}
@media(max-width:600px){ .card{padding:20px 15px;} .btn{width:100%; margin-right:0;} }
</style>
</head>
<body>

<header>Traduttore di Slang</header>

<main>
<div class="card">
<input type="text" id="slangInput" placeholder="Scrivi uno slang..." oninput="showSuggestions()">
<div>
<button class="btn translate" onclick="translateSlang()">Traduci</button>
<button class="btn theme" onclick="toggleTheme()">Tema Scuro / Chiaro</button>
</div>

<div id="result"></div>
<div id="counter">Traduzioni effettuate: 0</div>

<div id="adsense">

</div>

<div id="suggestions"><strong>Suggerimenti:</strong></div>
<div id="history"><strong>Storico parole tradotte:</strong></div>
</div>
</main>

<footer>© 2025 Traduttore di Slang • Creato da [Tuo Nome]</footer>

<script>
let count = 0;
let history = [];

const slangDictionary = {
"rizz":"fascino, carisma",
"bet":"ok, d'accordo",
"gyat":"espressione di eccitazione",
"bussin":"molto buono, delizioso",
"lewk":"stile memorabile, look",
"goat":"il migliore di tutti i tempi",
"fomo":"paura di perdersi qualcosa",
"rent-free":"nella testa di qualcuno senza sforzo",
"sus":"sospetto",
"pookie":"tesoro, amorevole termine affettuoso",
"tfw":"quel sentimento quando…",
"delulu":"delirante, illuso",
"beige flag":"abitudine bizzarra ma non negativa",
"mother":"donna famosa molto stimata",
"lit":"fantastico, eccitante",
"flex":"mettersi in mostra, mostrare orgoglio",
"ghost":"sparire, ignorare qualcuno",
"salty":"arrabbiato, risentito",
"lowkey":"in modo discreto, segreto",
"highkey":"in modo evidente, apertamente",
"shade":"critica velata",
"extra":"esagerato, drammatico",
"thirsty":"desideroso di attenzione",
"slay":"fare qualcosa in modo eccellente",
"clap back":"rispondere con forza",
"stan":"fan accanito",
"vibe":"atmosfera, sensazione",
"receipts":"prove, screenshot",
"woke":"socialmente consapevole",
"cap":"bugia",
"no cap":"davvero, non sto mentendo",
"pog":"fantastico, entusiasmante",
"simp":"persona che fa troppo per piacere a qualcuno",
"mood":"stato d’animo",
"rip":"riposa in pace / disastro",
"smh":"scuotere la testa",
"tbh":"a dire il vero",
"imo":"secondo me",
"irl":"nella vita reale",
"idk":"non lo so",
"brb":"torno subito",
"lol":"ridere ad alta voce",
"lmao":"ridere moltissimo",
"rofl":"rotolare dal ridere",
"omg":"oh mio dio",
"jomo":"gioia di perdersi qualcosa",
"bae":"amore, dolce metà",
"wyd":"cosa stai facendo?",
"otp":"coppia preferita",
"af":"molto, estremamente",
"lit af":"molto fantastico",
"drag":"criticare pesantemente",
"fire":"fantastico, eccellente",
"bomb":"molto buono",
"shook":"scioccato",
"snatched":"perfetto, incredibile",
"fam":"amico, fratello (famiglia stretta)",
"gucci":"tutto ok, bene",
"hundo p":"100%, assolutamente",
"cheugy":"fuori moda",
"drama":"conflitto, problema",
"fit":"outfit",
"squad":"gruppo di amici",
"vibe check":"controllo dell’umore",
"yolo":"si vive una volta",
"rekt":"distrutto, sconfitto",
"troll":"provocatore online",
"noob":"principiante",
"poggers":"fantastico (gaming)",
"gg":"bel gioco",
"ikr":"lo so, vero?",
"and I oop":"esclamazione di sorpresa / imbarazzo",
"sksksk":"esclamazione divertita / imbarazzata",
"clout":"influenza, popolarità",
"slaps":"molto buono (es. canzone)",
"hype":"entusiasmo",
"drip check":"controllo dello stile",
"big yikes":"grande imbarazzo",
"canceled":"escluso, bocciato socialmente",
"whip":"auto",
"litty":"molto eccitante",
"capper":"bugiardo",
"plug":"contatto utile (per risorse)",
"flexin":"mettersi in mostra",
"vibin":"godersi l’atmosfera",
"mood af":"stato d’animo intenso",
"snacc":"persona molto attraente",
"dripped out":"vestito con stile",
"main character":"protagonista della scena",
"weird flex":"vanto strano",
"ok boomer":"risposta ironica a persona anziana",
"simping":"essere troppo remissivo per qualcuno",
"ratioed":"messaggio con più risposte negative che positive",
"deadass":"seriamente",
"no chill":"senza autocontrollo",
"big oof":"grande sbaglio / imbarazzo",
"thicc":"corpulento/a in modo attraente",
"glow up":"trasformazione positiva",
"zaddy":"uomo attraente, sicuro di sé",
"sheesh":"esclamazione di sorpresa o ammirazione",
"shady":"sospetto, losco",
"drama queen":"persona che esagera sempre",
"banger":"canzone molto forte / buona",
"slay queen":"persona che eccelle (soprattutto donne)",
"drip drip":"stile molto evidente",
"big brain":"molto intelligente",
"clout chaser":"chi cerca popolarità a tutti i costi",
"spill tea":"raccontare pettegolezzi",
"sip tea":"ascoltare pettegolezzi",
"okurrr":"esclamazione di approvazione",
"main character energy":"energia da protagonista",
"weird flex but ok":"vanto strano, ma va bene",
"straight fire":"davvero eccellente",
"snatched edges":"acconciatura perfetta",
"sheeeesh":"sorpresa/magnifico",
"yeeting":"lanciare qualcosa con forza",
"cap no cap":"non sto mentendo",
"big mad":"molto arrabbiato",
"tight":"fantastico",
"queen energy":"energia potente e dominante",
"king energy":"energia maschile dominante",
"soft":"tenero, emotivo",
"hard":"difficile, serio",
"chefs kiss":"gesto di qualcosa perfetto (delizioso)",
"receipts ready":"prove pronte",
"mood vibes":"vibrazioni di stato d’animo",
"vibe check failed":"controllo dell’umore fallito",
"bussin hard":"davvero delizioso",
"snacc alert":"persona super attraente",
"extra af":"molto esagerato",
"litty titty":"molto eccitante / esilarante",
"sus moment":"momento molto sospetto",
"glow up queen":"trasformazione impressionante di una donna",
"drip king":"uomo con stile super elegante",
"big mood":"stato d’animo molto forte",
"mood check":"controllo dell’umore",
"hundo":"100%",
"the ick":"repulsione improvvisa per qualcuno",
"touch grass":"prendersi una pausa dai social",
"npc":"persona senza opinioni forti",
"tradwife":"moglie tradizionale (nel senso social)",
"lewk":"look audace e memorabile",
"iski":"termine virale, può essere usato per dire ‘cool’",
"nyeh":"suono sarcastico, come ‘meh’ ironico",
"zoomer":"giovane della Generazione Z",
"boomer":"persona più anziana, spesso usato ironicamente",
"rizzed":"essere carismatici",
"vaxxed":"vaccinato",
"unvaxxed":"non vaccinato",
"gaslight":"manipolare psicologicamente",
"clapback":"risposta pungente",
"finna":"sto per",
"spill":"raccontare pettegolezzi",
"wheeze":"ridere tantissimo",
"oof":"reazione a dolore o errore",
"finesse":"gestire qualcosa con abilità",
"hangry":"arrabbiato perché affamato",
"crippling":"che soffoca (es. ansia)",
"swole":"muscoloso",
"juiced":"molto entusiasta / caricamento energetico",
"dripped":"vestito con stile",
"moot":"discutibile, irrilevante",
"hit different":"dare un’emozione unica",
"main plot":"tema principale della vita (ironico)",
"simp city":"luogo metaforico dove regna il simpismo",
"mood board":"idea stilistica / emozionale",
"big brain play":"mossa intelligente",
"curve":"rifiutare qualcuno in modo elegante",
"throw shade":"criticare velatamente",
"zaza":"marijuana (slang)",
"drama llama":"persona che esagera i problemi",
"bounce":"andarsene",
"no capper":"chi è sinceramente serio",
"spill the barz":"raccontare rap / rime",
"big oof energy":"forte sensazione di sbaglio / imbarazzo",
"dawg":"amico / fratello",
"lowkey sad":"tristezza discreta",
"highkey mad":"molto arrabbiato",
"yw":"you’re welcome",
"fyp":"for you page (TikTok)",
"clout god":"persona con tantissima popolarità",
"suspect":"sospetto / poco affidabile",
"on god":"sul serio / giuro",
"big drip":"stile molto evidente",
"juice":"potere / influenza",
"brownie points":"punti di favore",
"simp nation":"popolazione di simp",
"vax":"vaccinare / vaccino",
"flex king":"re del vanto",
"soft life":"vita calma, senza stress",
"hard reset":"ricominciare da zero",
"wack":"scadente / brutto",
"amaze":"incredibile",
"amp":"elettrizzato / carico",
"caught lackin":"essere sorpresi impreparati",
"shooketh":"ancora più scioccato",
"sippin":"bere (slang, es. gossip)",
"no smoke":"nessun problema / conflitto",
"smoked":"sconfitto",
"canceled culture":"cultura della cancellazione",
"deadass real":"veramente serio",
"clapback king":"re delle risposte taglienti",
"gaslight queen":"persona che manipola molto",
"simp wave":"ondata di simpismo",
"vibeland":"luogo / mentalità di vibrazioni buone",
"big rizz":"grandissimo fascino",
"shake it off":"scuotersi di dosso (critiche)",
"throw hands":"litigare fisicamente (slang)",
"receipts cop":"chi raccoglie prove",
"no lies detected":"nessuna bugia rilevata",
"key bounce":"saluto (rap slang)",
"bring the receipts":"mostra le prove",
"mood swing":"oscillazione d’umore",
"hypebeast":"persona ossessionata dallo streetwear",
"fit pic":"foto dell’outfit",
"clean fit":"outfit perfetto",
"dirty drip":"stile pulito ma appariscente",
"on beat":"sul tempo, in ritmo",
"off beat":"fuori tempo",
"no cap zone":"zona di verità assoluta",
"fake flex":"vantarsi di qualcosa non così impressionante",
"sleep on it":"riflettere su qualcosa prima di decidere",
"clout monster":"persona che fa qualsiasi cosa per popolarità",
"vibe shift":"cambio di atmosfera",
"mood lifter":"cosa che rialza il morale",
"ego check":"controllo dell’ego",
"drip god":"dio dello stile",
"juice lord":"signore dell’influenza",
"king drip":"stile reale",
"queen drip":"stile regale",
"vibe lord":"signore delle vibrazioni",
"no cap bro":"fratello, davvero non sto mentendo",
"big w":"grande vittoria",
"big L":"grande sconfitta",
"sauce":"stile, qualità",
"saucy":"molto stiloso / con carisma",
"poof":"sparire improvvisamente",
"salty af":"molto risentito",
"litty again":"di nuovo incredibile",
"rizz up":"aumentare il fascino",
"finesse king":"re della furbizia",
"hundo down":"completamente sicuro",
"juice up":"aumentare l’influenza / energia",
"mood boosted":"stato d’animo migliorato",
"shake it":"scrollarsi di dosso",
"big shade":"critica pesante",
"lowkey win":"vittoria discreta",
"highkey win":"vittoria evidente",
"simp daddy":"simp potente",
"simp queen":"donna che fa troppo",
"drip daddy":"uomo molto stiloso",
"drip queen":"donna di grande stile",
"gaslight king":"uomo manipolatore",
"no lie":"senza mentire",
"no cap moment":"momento di verità assoluta",
"sauce lord":"signore dello stile",
"sauce god":"dio dello stile",
"vibe god":"dio delle vibrazioni"
};


function translateSlang(){
    const input = document.getElementById("slangInput").value.toLowerCase().trim();
    const result = document.getElementById("result");
    if(slangDictionary[input]){
        result.textContent = slangDictionary[input];
        addHistory(input);
        count++;
        document.getElementById("counter").textContent = "Traduzioni effettuate: " + count;
    } else {
        result.textContent = "Slang non trovato!";
    }
}

function addHistory(word){
    if(!history.includes(word)){
        history.push(word);
        const hDiv = document.getElementById("history");
        const div = document.createElement("div");
        div.textContent = word + " → " + slangDictionary[word];
        div.onclick = ()=>{ document.getElementById("slangInput").value=word; translateSlang(); };
        hDiv.appendChild(div);
    }
}

function showSuggestions(){
    const input = document.getElementById("slangInput").value.toLowerCase();
    const sugDiv = document.getElementById("suggestions");
    sugDiv.innerHTML="<strong>Suggerimenti:</strong>";
    if(input.length>0){
        Object.keys(slangDictionary).forEach(word=>{
            if(word.startsWith(input)){
                const div=document.createElement("div");
                div.textContent = word + " → " + slangDictionary[word];
                div.onclick = ()=>{ document.getElementById("slangInput").value=word; translateSlang(); };
                sugDiv.appendChild(div);
            }
        });
    }
}

function toggleTheme(){
    document.body.classList.toggle("dark");
}
</script>

</body>
</html>
