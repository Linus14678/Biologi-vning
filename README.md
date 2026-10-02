<!DOCTYPE html>
<html lang="sv">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Cellbiologi – begreppsövning</title>
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);--bg:#f3f6f4;--card:#fff;--ink:#16221d;--mute:#5d6e66;--line:#d3ddd8;--acc:#0f6b57;--accink:#fff;--ok:#1f8a4c;--mid:#b7791f;--bad:#c0392b;--sel:#dcefe8}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#101815;--card:#18231f;--ink:#e6efeb;--mute:#93a69d;--line:#2c3d36;--acc:#4cc3a2;--accink:#06231b;--ok:#4cc38a;--mid:#e0a84a;--bad:#ee7b6d;--sel:#1f3a31}}
:root[data-theme="dark"]{--bg:#101815;--card:#18231f;--ink:#e6efeb;--mute:#93a69d;--line:#2c3d36;--acc:#4cc3a2;--accink:#06231b;--ok:#4cc38a;--mid:#e0a84a;--bad:#ee7b6d;--sel:#1f3a31}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:17px/1.5 "Segoe UI",system-ui,sans-serif}
main{max-width:640px;margin:0 auto;padding:20px 16px 48px}
h1{font:700 26px/1.2 Georgia,"Times New Roman",serif;margin:8px 0 6px}
p{margin:0 0 14px;color:var(--mute)}
.card{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:20px}
.chips{display:flex;flex-wrap:wrap;gap:8px;margin:14px 0}
.chip{border:1px solid var(--line);background:var(--card);color:var(--ink);border-radius:999px;padding:8px 14px;font:inherit;font-size:15px;cursor:pointer}
.chip[aria-pressed="true"]{background:var(--sel);border-color:var(--acc);font-weight:600}
button{font:inherit}
.btn{background:var(--acc);color:var(--accink);border:0;border-radius:10px;padding:12px 20px;font-weight:600;cursor:pointer}
.btn.alt{background:transparent;color:var(--ink);border:1px solid var(--line)}
button:focus-visible,textarea:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.row{display:flex;gap:10px;flex-wrap:wrap;margin-top:14px}
.bar{height:6px;background:var(--line);border-radius:3px;overflow:hidden;margin-bottom:6px}
.bar i{display:block;height:100%;background:var(--acc);width:0;transition:width .25s}
.meta{display:flex;justify-content:space-between;color:var(--mute);font-size:14px;margin-bottom:14px}
.term{font:700 30px/1.2 Georgia,serif;margin:4px 0 14px;overflow-wrap:anywhere}
textarea{width:100%;min-height:96px;border:1px solid var(--line);border-radius:10px;background:var(--bg);color:var(--ink);padding:12px;font:inherit;resize:vertical}
.facit{margin-top:14px;padding:14px;border-left:4px solid var(--acc);background:var(--sel);border-radius:0 10px 10px 0}
.facit b{display:block;margin-bottom:4px}
.g{flex:1;min-width:110px;border:2px solid;background:transparent;border-radius:10px;padding:10px;font-weight:600;cursor:pointer}
.g.ok{color:var(--ok);border-color:var(--ok)}.g.mid{color:var(--mid);border-color:var(--mid)}.g.bad{color:var(--bad);border-color:var(--bad)}
.big{font:700 44px/1 Georgia,serif}
.miss{margin:12px 0 0;padding:0;list-style:none}
.miss li{padding:8px 0;border-top:1px solid var(--line)}
.miss span{color:var(--mute);font-size:15px}
.lst{margin:8px 0 18px;padding:0;list-style:none}.lst li{display:flex;gap:10px;justify-content:space-between;align-items:center;padding:8px 0;border-top:1px solid var(--line)}.lst small{color:var(--mute);display:block;font-size:14px;line-height:1.35}.g.alls{background:var(--bad);color:var(--card);border-color:var(--bad)}.mv{display:flex;flex-direction:column;gap:6px;flex:none}.mini{border:1px solid var(--line);background:transparent;color:var(--ink);border-radius:8px;padding:6px 10px;font-size:14px;cursor:pointer;flex:none}
h2{font:700 20px Georgia,serif;margin:20px 0 0}
[hidden]{display:none!important}
</style>
</head>
<body>
<main>
<section id="start">
  <h1>Cellbiologi – begreppsövning</h1>
  <p>Skriv ungefär en mening om vad begreppet betyder. Jämför sedan med facit och bedöm dig själv ärligt.</p>
  <div class="card">
    <b>Välj områden</b>
    <div class="chips" id="chips"></div>
    <b>Vilka begrepp?</b>
    <div class="chips" id="modes"></div>
    <div class="chips"><button class="chip" id="shuf" aria-pressed="true">Blanda ordningen</button></div>
    <div class="row"><button class="btn" id="go">Starta</button><button class="btn alt" id="lbtn">Mina listor</button></div>
  </div>
</section>

<section id="quiz" hidden>
  <div class="bar"><i id="pb"></i></div>
  <div class="meta"><span id="cat"></span><span id="cnt"></span></div>
  <div class="card">
    <div class="term" id="term"></div>
    <textarea id="ans" placeholder="Skriv din förklaring här…" aria-label="Din förklaring"></textarea>
    <div class="row"><button class="btn" id="show">Visa facit</button><button class="btn alt" id="skip">Hoppa över</button></div>
    <div id="fb" hidden>
      <div class="facit"><b>Facit</b><span id="def"></span></div>
      <p style="margin:14px 0 0">Hur gick det?</p>
      <div class="row" style="margin-top:8px">
        <button class="g ok" data-s="1">Kan det</button>
        <button class="g mid" data-s="2">Delvis</button>
        <button class="g bad" data-s="0">Kan inte</button>
        <button class="g alls" data-s="3">Kan inte alls</button>
      </div>
    </div>
  </div>
</section>

<section id="end" hidden>
  <h1>Klart!</h1>
  <div class="card">
    <div class="big" id="score"></div>
    <p id="sum" style="margin-top:8px"></p>
    <ul class="miss" id="miss"></ul>
    <div class="row"><button class="btn" id="redo">Öva på de som inte satt</button><button class="btn alt" id="home">Börja om</button></div>
  </div>
</section>
<section id="lists" hidden>
  <h1>Mina listor</h1>
  <p>Sparas i den här webbläsaren. Sortera om genom att trycka på en pil-knapp vid ett begrepp.</p>
  <div class="row" style="margin:0 0 8px"><button class="btn alt" id="lback">Tillbaka</button><button class="btn alt" id="reset">Nollställ allt</button></div>
  <div id="lbox"></div>
</section>
</main>

<script>
const RAW = `Cellbiologi|Organell|Strukturell del inuti en cell med en särskild uppgift, t.ex. cellkärna eller mitokondrie.
Cellbiologi|Cellmembran|Tunt hölje av fosfolipider och proteiner runt cellen som styr vad som tar sig in och ut.
Cellbiologi|Cytoplasma/cellplasma|Geléartad massa inuti cellen, utanför kärnan, där organellerna ligger och många reaktioner sker.
Cellbiologi|Cellskelett|Nätverk av proteintrådar som ger cellen form och stöd och möjliggör transport och rörelse.
Cellbiologi|Flagell|Lång piskliknande utskott som får en cell att simma, t.ex. spermiecellens svans.
Cellbiologi|Cilier|Många korta hårliknande utskott som rör cellen eller vätskan runt den, t.ex. i luftrören.
Cellbiologi|Cellkärna|Organell som innehåller cellens DNA och styr cellens funktioner och delning.
Cellbiologi|Endoplasmatiskt nätverk (ER)|Membransystem: skrovligt ER (med ribosomer) tillverkar proteiner, slätt ER bildar lipider och bryter ner gifter.
Cellbiologi|Ljusreaktion|Första steget i fotosyntesen, i tylakoidmembranen: ljus används för att bilda ATP och NADPH och vatten spjälkas så att syrgas bildas.
Cellbiologi|Kolfixering|Koldioxid binds och byggs in i organiska molekyler (glukos) i Calvincykeln.
Cellbiologi|Mitokondrie|Cellens kraftverk där cellandningen sker och det mesta av ATP bildas.
Cellbiologi|Mörkerreaktion|Calvincykeln i stroma, där ATP och NADPH från ljusreaktionen används för att bygga glukos av koldioxid.
Cellbiologi|Ribosomer|Tillverkar proteiner utifrån mRNA; sitter fria i cytoplasman eller på ER.
Cellbiologi|Golgiapparaten|Tar emot, modifierar, sorterar och paketerar proteiner i vesiklar för transport.
Cellbiologi|Lysosom|Blåsa med nedbrytande enzymer som tar hand om skadade organeller, avfall och intagen näring.
Cellbiologi|Kloroplast|Organell i växtceller och alger där fotosyntesen sker.
Cellbiologi|Klorofyll|Grönt pigment i kloroplasten som fångar upp ljusenergi.
Cellbiologi|Tylakoid|Säckformade membran i kloroplasten där ljusreaktionen sker; staplade bildar de grana.
Cellbiologi|Stroma|Vätskan i kloroplasten runt tylakoiderna, där mörkerreaktionen (Calvincykeln) sker.
Cellbiologi|Vakuol|Stor vätskefylld blåsa i växtceller som lagrar vatten och ämnen och håller uppe turgortrycket.
Cellbiologi|Cellvägg|Stel yta utanför cellmembranet hos växter (cellulosa), svampar (kitin) och bakterier; ger stöd och skydd.
Cellbiologi|Kitin|Starkt kolhydrat som bygger svampars cellväggar och insekters skal.
Cellundersökning|Mikroskop|Instrument som förstorar så att man kan se celler och deras delar; ljusmikroskop eller elektronmikroskop.
Cellundersökning|Centrifug|Snurrar prover snabbt så att tyngre delar sjunker och cellens delar kan separeras.
Cellundersökning|Suspension|Blandning där små partiklar svävar i en vätska, t.ex. söndrigt cellmaterial i buffert.
Cellundersökning|Supernatant|Vätskan ovanpå botten (pelleten) efter centrifugering.
Cellundersökning|Pellet|Det tyngre fasta materialet som samlas i botten av röret efter centrifugering.
Cellundersökning|Radioaktiv märkning|Ämne märks med en radioaktiv isotop så att man kan följa var det hamnar och vad det används till i cellen.
Undersöka bakterier|Agar|Geléämne från alger som används som näringsunderlag för att odla bakterier.
Undersöka bakterier|Petriskål|Grund rund skål med lock där bakterier odlas på agar.
Undersöka bakterier|Platinaögla/ympnål|Verktyg för att överföra bakterier; steriliseras i låga före och efter användning.
Undersöka bakterier|Autoklavera|Sterilisera med het vattenånga under tryck, ca 121 °C.
Undersöka bakterier|Antiseptiskt|Ämne som dödar eller hämmar mikroorganismer på levande vävnad, t.ex. handsprit.
Undersöka bakterier|Sterilisera|Döda alla mikroorganismer, även sporer, på ett föremål eller i ett medium.
Undersöka bakterier|Rackla|Stryka ut bakterier i mönster på agarplatta så att enskilda kolonier växer fram.
Membran och transport|Cellmembranens uppbyggnad|Dubbelt lager av fosfolipider med inlagrade proteiner och kolesterol som kan röra sig (flytande mosaikmodell).
Membran och transport|Fosfolipider|Lipider med ett hydrofilt huvud och två hydrofoba fettsyrasvansar; bygger upp membranet.
Membran och transport|Hydrofil|Vattenälskande; löser sig i vatten eller dras till vatten.
Membran och transport|Hydrofob|Vattenavstötande; blandas inte med vatten.
Membran och transport|Diffusion|Partiklar förflyttar sig spontant från högre till lägre koncentration.
Membran och transport|Koncentrationsgradient|Skillnad i koncentration av ett ämne mellan två områden, vilket driver diffusion.
Membran och transport|Osmos|Diffusion av vatten genom ett semipermeabelt membran, mot sidan med mest löst ämne.
Membran och transport|Transportproteiner|Proteiner i membranet som hjälper ämnen som inte kan passera fritt att ta sig över.
Membran och transport|Bärarprotein|Binder ett ämne och ändrar form så att ämnet förs över membranet.
Membran och transport|Kanalproteiner|Proteiner med en kanal som släpper igenom specifika joner eller vatten.
Membran och transport|Aktiv transport|Transport mot koncentrationsgradienten som kräver energi (ATP), t.ex. natrium-kaliumpumpen.
Membran och transport|Passiv transport|Transport längs koncentrationsgradienten utan energitillförsel, t.ex. diffusion och osmos.
Membran och transport|Endocytos|Cellen tar in ämnen när membranet snörs in till en vesikel.
Membran och transport|Exocytos|Cellen släpper ut ämnen när en vesikel smälter samman med cellmembranet.
Cellskelett och rörelse|Aktintrådar|Tunna proteintrådar som ger cellen form och rörelse och som samverkar med myosin vid muskelkontraktion.
Cellskelett och rörelse|Mikrotubuli|Ihåliga rör av tubulin; bildar delningsspolen, bygger cilier och flageller och fungerar som transportspår.
Cellskelett och rörelse|Intermediära trådar|Starka, stabila proteintrådar som ger mekanisk hållfasthet och förankrar organeller.
Cellskelett och rörelse|Motorprotein|Protein som använder ATP för att röra sig längs cellskelettet och transportera last eller skapa rörelse.
Cellskelett och rörelse|Myosin|Motorprotein som drar i aktintrådar och orsakar muskelkontraktion.
Cellskelett och rörelse|Troponin|Protein på aktintråden som binder kalcium och får tropomyosin att lämna myosinets bindningsställen.
Cellskelett och rörelse|Tropomyosin|Protein som i vila täcker myosinets bindningsställen på aktin så att muskeln inte drar ihop sig.
Cellskelett och rörelse|Dynein|Motorprotein som rör sig längs mikrotubuli och får cilier och flageller att böja sig.
Cellskelett och rörelse|Kemotaxis|Rörelse hos en cell eller organism mot eller bort från ett kemiskt ämne.
Signalering och muskler|Signalsubstans|Molekyl som skickas från en cell och binder till receptorer på en annan cell, t.ex. hormon eller neurotransmittor.
Signalering och muskler|Receptor|Protein som binder en specifik signalsubstans och utlöser ett svar i cellen.
Signalering och muskler|Hjärtmuskelcell|Tvärstrimmig, ofrivillig och förgrenad muskelcell i hjärtat med många mitokondrier.
Signalering och muskler|Glatt muskulatur|Ofrivillig muskulatur utan tvärstrimmor i t.ex. tarmar och blodkärl; långsam och uthållig.
Signalering och muskler|Tvärstrimmig skelettmuskulatur|Viljestyrd muskulatur fäst vid skelettet som ser strimmig ut på grund av sarkomererna.
Signalering och muskler|Muskelfiber|Lång flerkärnig muskelcell fylld av fibriller.
Signalering och muskler|Myoglobin|Syrebindande protein i muskelceller som lagrar syre.
Signalering och muskler|Hemoglobin|Syrebindande protein i röda blodkroppar som transporterar syre i blodet.
Signalering och muskler|Fibriller|Trådar (myofibriller) i muskelfibern som består av aktin och myosin ordnade i sarkomerer.
Signalering och muskler|Sarkomer|Muskelns minsta sammandragande enhet, mellan två Z-skivor, med aktin- och myosintrådar.
Signalering och muskler|Röda fibrer|Långsamma, uthålliga muskelfibrer med mycket myoglobin och mitokondrier; aerob förbränning.
Signalering och muskler|Vita fibrer|Snabba muskelfibrer med lite myoglobin som får energi anaerobt och tröttas snabbt.
Mikroorganismer|Prokaryota celler|Celler utan cellkärna och membranomgivna organeller; DNA ligger fritt i cytoplasman, t.ex. bakterier.
Mikroorganismer|Arkéer|Encelliga prokaryoter som skiljer sig från bakterier och ofta lever i extrema miljöer.
Mikroorganismer|Gramfärgning|Färgmetod som delar in bakterier i grampositiva (lila) och gramnegativa (rosa) utifrån cellväggens uppbyggnad.
Mikroorganismer|Plasmid|Liten cirkulär DNA-molekyl utanför bakteriens kromosom, ofta med t.ex. resistensgener.
Mikroorganismer|Koloni|Synlig grupp av identiska bakterier som vuxit fram ur en enda cell på agar.
Mikroorganismer|Fotoautotrof|Bygger organiskt material av koldioxid med ljus som energikälla (fotosyntes).
Mikroorganismer|Heterotrof|Får både energi och kol från organiskt material som andra organismer bildat.
Mikroorganismer|Kemoautotrof|Får energi från oorganiska ämnen och bygger organiskt material av koldioxid.
Mikroorganismer|Kocker|Runda bakterier.
Mikroorganismer|Baciller|Stavformade bakterier.
Mikroorganismer|Spiriller|Spiralformade bakterier.
Mikroorganismer|Grampositiv|Bakterie med tjock cellvägg som behåller den lila färgen vid gramfärgning.
Mikroorganismer|Gramnegativ|Bakterie med tunn cellvägg och yttre membran som tappar den lila färgen och blir rosa/röd.
Mikroorganismer|Gramvariabla|Bakterier som ibland färgas som grampositiva och ibland som gramnegativa, t.ex. beroende på ålder eller förhållanden.
Mikroorganismer|Gramneutrala|Bakterier som inte färgas tydligt av gramfärgning, ofta på grund av en annorlunda cellvägg.
Mikroorganismer|Pili|Tunna utskott på bakterier som används för fastsättning och utbyte av DNA.
Mikroorganismer|Endosporer|Tåliga vilostadier som vissa bakterier bildar inuti sig och som överlever värme, torka och kemikalier.
Virus|Bakteriofag|Virus som angriper och förökar sig i bakterier.
Virus|Kapsel|Skyddande proteinhölje (kapsid) runt virusets arvsmassa.
Virus|Virus|Icke-cellulär partikel av arvsmassa i proteinhölje som bara kan föröka sig inuti en värdcell.
Virus|Värdspecifik|Viruset kan bara infektera vissa arter eller celltyper som har rätt receptorer.
Virus|Retrovirus|RNA-virus som skriver om sitt RNA till DNA med omvänt transkriptas, t.ex. HIV.
Virus|Lytisk cykel|Viruset förökar sig direkt i värdcellen som sedan sprängs så att nya virus frisätts.
Virus|Lysogen cykel|Virusets DNA byggs in i värdens DNA och ligger vilande och kopieras när cellen delar sig.
Virus|Lyseras|Cellen sprängs och dör så att innehållet, t.ex. nya virus, släpps ut.
Virus|Omvänt transkriptas|Enzym som skriver om RNA till DNA.
Virus|Knoppning|Nya virus lämnar cellen genom att snöra av sig med en bit av cellmembranet som hölje.
Virus|Provirus|Virus-DNA som är inbyggt i värdcellens arvsmassa (kallas profag hos bakterier).`;

const ALL = RAW.split("\n").map(l => { const [c,t,d] = l.split("|"); return {c,t,d}; });
const CATS = [...new Set(ALL.map(x => x.c))];
const $ = id => document.getElementById(id);
const K = "cellbio-v1";
let mem = {};
try { mem = JSON.parse(localStorage.getItem(K)) || {}; } catch (e) { mem = {}; }
const save = () => { try { localStorage.setItem(K, JSON.stringify(mem)); } catch (e) {} };
const st = x => mem[x.t] === 1 ? "kan" : mem[x.t] === 2 ? "delvis" : mem[x.t] === 0 ? "kanej" : mem[x.t] === 3 ? "alls" : "ny";
const LBL = {alls:"Kan inte alls", kanej:"Kan inte", delvis:"Delvis", kan:"Kan det", ny:"Ej övade"}, VAL = {alls:3, kanej:0, delvis:2, kan:1};
const MODES = [["all","Alla"],["ny","Ej övade"],["alls","Kan inte alls"],["kanej","Kan inte"],["delvis","Delvis"],["kan","Kan det"]];
let chosen = new Set(CATS), shuffle = true, mode = "all", deck = [], i = 0, res = [];

CATS.forEach(c => {
  const b = document.createElement("button");
  b.className = "chip"; b.textContent = c; b.setAttribute("aria-pressed", "true");
  b.onclick = () => { chosen.has(c) ? chosen.delete(c) : chosen.add(c); b.setAttribute("aria-pressed", chosen.has(c)); };
  $("chips").appendChild(b);
});
function drawModes(){
  $("modes").innerHTML = "";
  MODES.forEach(([m,l]) => {
    const n = m === "all" ? ALL.length : ALL.filter(x => st(x) === m).length;
    const b = document.createElement("button");
    b.className = "chip"; b.textContent = l + " (" + n + ")"; b.setAttribute("aria-pressed", mode === m);
    b.onclick = () => { mode = m; drawModes(); };
    $("modes").appendChild(b);
  });
}
$("shuf").onclick = e => { shuffle = !shuffle; e.target.setAttribute("aria-pressed", shuffle); };

function show(id){ ["start","quiz","end","lists"].forEach(s => $(s).hidden = s !== id); if (id === "start") drawModes(); window.scrollTo(0,0); }
function start(items){
  deck = items.slice();
  if (shuffle) for (let k = deck.length - 1; k > 0; k--) { const j = Math.floor(Math.random()*(k+1)); [deck[k],deck[j]] = [deck[j],deck[k]]; }
  i = 0; res = []; show("quiz"); card();
}
function card(){
  const q = deck[i];
  $("term").textContent = q.t; $("cat").textContent = q.c; $("cnt").textContent = (i+1) + " / " + deck.length;
  $("pb").style.width = (i / deck.length * 100) + "%";
  $("ans").value = ""; $("fb").hidden = true; $("show").hidden = false; $("skip").hidden = false; $("ans").readOnly = false;
  $("ans").focus();
}
function reveal(){
  $("def").textContent = deck[i].d; $("fb").hidden = false; $("show").hidden = true; $("skip").hidden = true; $("ans").readOnly = true;
}
function grade(s){ mem[deck[i].t] = s; save(); res[i] = s; next(); }
function next(){ i++; i < deck.length ? card() : finish(); }
function finish(){
  $("pb").style.width = "100%"; show("end");
  const graded = res.filter(g => g !== undefined).length, kan = res.filter(g => g === 1).length;
  $("score").textContent = (graded ? Math.round(kan / graded * 100) : 0) + " %";
  const c = v => res.filter(g => g === v).length;
  $("sum").textContent = c(1) + " kan det, " + c(2) + " delvis, " + c(0) + " kan inte, " + c(3) + " kan inte alls. Sparat i dina listor.";
  const weak = deck.filter((_, k) => res[k] !== undefined && res[k] !== 1);
  $("miss").innerHTML = "";
  weak.forEach(w => { const li = document.createElement("li"); li.innerHTML = "<b></b><br><span></span>"; li.firstChild.textContent = w.t; li.lastChild.textContent = w.d; $("miss").appendChild(li); });
  $("redo").hidden = !weak.length; $("redo").onclick = () => start(weak);
}
$("go").onclick = () => {
  const items = ALL.filter(x => chosen.has(x.c) && (mode === "all" || st(x) === mode));
  if (items.length) start(items); else alert("Inga begrepp matchar ditt val.");
};
$("show").onclick = reveal; $("skip").onclick = next; $("home").onclick = () => show("start");
document.querySelectorAll(".g").forEach(b => b.onclick = () => grade(+b.dataset.s));
$("ans").addEventListener("keydown", e => { if (e.key === "Enter" && (e.ctrlKey || e.metaKey) && !$("show").hidden) reveal(); });

function drawLists(){
  const box = $("lbox"); box.innerHTML = "";
  ["alls","kanej","delvis","kan","ny"].forEach(s => {
    const l = LBL[s];
    const items = ALL.filter(x => st(x) === s);
    const h = document.createElement("h2"); h.textContent = l + " (" + items.length + ")"; box.appendChild(h);
    const ul = document.createElement("ul"); ul.className = "lst";
    items.forEach(x => {
      const li = document.createElement("li"), d = document.createElement("div"), b = document.createElement("b"), sm = document.createElement("small");
      b.textContent = x.t; sm.textContent = x.d; d.append(b, sm); li.appendChild(d);
      const mv = document.createElement("div"); mv.className = "mv";
      ["alls","kanej","delvis","kan"].filter(t => t !== s).forEach(t => {
        const m = document.createElement("button"); m.className = "mini";
        m.textContent = "→ " + LBL[t];
        m.onclick = () => { mem[x.t] = VAL[t]; save(); drawLists(); };
        mv.appendChild(m);
      });
      li.appendChild(mv);
      ul.appendChild(li);
    });
    box.appendChild(ul);
  });
}
let armed = false;
$("reset").onclick = e => {
  if (!armed) { armed = true; e.target.textContent = "Säker? Tryck igen"; return; }
  armed = false; e.target.textContent = "Nollställ allt"; mem = {}; save(); drawLists();
};
$("lbtn").onclick = () => { drawLists(); show("lists"); };
$("lback").onclick = () => show("start");
drawModes();
</script>
</body>
</html>
