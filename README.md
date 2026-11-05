<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Point Guard Elite</title>

<style>
:root {
    --pink: #ff4fa3;
    --red: #ff3157;
    --purple: #9b5cff;
    --dark: #100b1b;
    --card: #20152f;
    --text: #fff;
    --muted: #c8bdd8;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    color: var(--text);
    background:
        radial-gradient(circle at 10% 10%, #76245d 0, transparent 35%),
        radial-gradient(circle at 90% 90%, #452080 0, transparent 40%),
        linear-gradient(135deg, #100b1b, #24102e);
    min-height: 100vh;
    padding: 20px;
}

header {
    text-align: center;
    padding: 35px 10px;
}

header h1 {
    font-size: clamp(28px, 5vw, 48px);
    font-weight: 900;
    background: linear-gradient(90deg, #ff4fa3, #ff3157, #a66bff);
    -webkit-background-clip: text;
    color: transparent;
}

header p {
    color: var(--muted);
    margin-top: 10px;
}

.container {
    max-width: 1100px;
    margin: auto;
}

.progress-box {
    background: rgba(255,255,255,.06);
    border: 1px solid rgba(255,255,255,.1);
    border-radius: 18px;
    padding: 20px;
    margin-bottom: 25px;
}

.progress-bar {
    background: #382746;
    height: 12px;
    border-radius: 20px;
    overflow: hidden;
    margin-top: 12px;
}

.progress-fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #ff4fa3, #ff3157, #9b5cff);
    transition: width .3s;
}

.days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 10px;
    margin-bottom: 25px;
}

.day-btn {
    border: 1px solid rgba(255,255,255,.15);
    border-radius: 14px;
    padding: 15px 5px;
    color: white;
    cursor: pointer;
    background: #24172f;
    font-weight: bold;
    transition: .2s;
}

.day-btn:hover {
    transform: translateY(-3px);
}

.day-btn.active {
    box-shadow: 0 0 20px rgba(255,79,163,.35);
    border: 2px solid white;
}

.day-btn small {
    display: block;
    margin-top: 7px;
    font-size: 11px;
    opacity: .8;
}

.day-0 { background: linear-gradient(135deg,#ff4fa3,#ff3157); }
.day-1 { background: linear-gradient(135deg,#ff3157,#a52a82); }
.day-2 { background: linear-gradient(135deg,#a52a82,#9b5cff); }
.day-3 { background: linear-gradient(135deg,#9b5cff,#5837ba); }
.day-4 { background: linear-gradient(135deg,#e83e87,#7e38d8); }
.day-5 { background: linear-gradient(135deg,#ff3157,#8a43ff); }
.day-6 { background: linear-gradient(135deg,#5b286d,#301b50); }

.content {
    background: rgba(255,255,255,.045);
    border: 1px solid rgba(255,255,255,.1);
    border-radius: 22px;
    padding: 25px;
}

.day-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;
    margin-bottom: 20px;
}

.day-header h2 {
    font-size: 28px;
}

.tag {
    background: rgba(255,79,163,.15);
    border: 1px solid rgba(255,79,163,.4);
    padding: 8px 12px;
    border-radius: 30px;
    font-size: 12px;
}

.session {
    margin-top: 25px;
}

.session h3 {
    font-size: 20px;
    margin-bottom: 15px;
}

.exercise {
    background: #20152f;
    border: 1px solid rgba(255,255,255,.08);
    padding: 16px;
    border-radius: 14px;
    margin-bottom: 10px;
}

.exercise-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
}

.exercise strong {
    font-size: 15px;
}

.exercise p {
    color: var(--muted);
    font-size: 13px;
    line-height: 1.6;
    margin-top: 8px;
}

.exercise select {
    background: #352344;
    color: white;
    border: 1px solid #754b8c;
    border-radius: 8px;
    padding: 8px;
    max-width: 140px;
}

.meals {
    background: linear-gradient(135deg,rgba(255,79,163,.12),rgba(155,92,255,.12));
    border: 1px solid rgba(255,79,163,.25);
    border-radius: 18px;
    padding: 20px;
    margin-top: 25px;
}

.meals h3 {
    margin-bottom: 15px;
}

.meal {
    margin-bottom: 13px;
    line-height: 1.6;
    font-size: 14px;
}

.meal strong {
    color: #ff85c0;
}

button.action {
    border: none;
    border-radius: 12px;
    padding: 13px 18px;
    font-weight: bold;
    cursor: pointer;
    color: white;
    margin-top: 15px;
}

.cannot {
    background: linear-gradient(90deg,#ff3157,#a52a82);
}

.reset {
    background: #39264d;
    border: 1px solid #74558f !important;
}

.off {
    background: linear-gradient(135deg,#9b5cff,#392064);
    padding: 25px;
    border-radius: 15px;
    line-height: 1.8;
}

.notice {
    font-size: 12px;
    color: var(--muted);
    margin-top: 20px;
    line-height: 1.7;
}

#reasonModal {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,.8);
    align-items: center;
    justify-content: center;
    padding: 20px;
    z-index: 10;
}

.modal {
    width: 100%;
    max-width: 450px;
    background: #21152f;
    border: 1px solid #a34bd6;
    border-radius: 20px;
    padding: 25px;
}

.modal h3 {
    margin-bottom: 15px;
}

.modal textarea {
    width: 100%;
    min-height: 110px;
    padding: 12px;
    border-radius: 10px;
    background: #120b1d;
    border: 1px solid #67447e;
    color: white;
    margin: 15px 0;
}

.modal button {
    padding: 12px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-weight: bold;
}

@media(max-width:700px) {
    body { padding: 12px; }
    .days { grid-template-columns: repeat(4,1fr); }
    .content { padding: 15px; }
    .exercise-top { flex-direction: column; align-items: flex-start; }
    .exercise select { max-width: 100%; }
}
</style>
</head>

<body>

<div class="container">

<header>
    <h1>POINT GUARD ELITE</h1>
    <p>Basketball Performance Program · Become a Complete Point Guard</p>
</header>

<div class="progress-box">
    <div style="display:flex;justify-content:space-between;gap:10px">
        <strong>Progression hebdomadaire</strong>
        <span id="progressText">0%</span>
    </div>
    <div class="progress-bar">
        <div class="progress-fill" id="progressFill"></div>
    </div>
    <p style="color:var(--muted);font-size:12px;margin-top:10px" id="progressCount">
        0 exercices terminés
    </p>
</div>

<div class="days" id="days"></div>

<div class="content" id="content"></div>

<p class="notice">
    Programme indicatif de préparation physique. Adapte les charges à ta forme,
    à ton calendrier de matchs et aux consignes de ton coach.
    Les repas sont des exemples généraux, pas un plan nutritionnel médical.
</p>

</div>

<div id="reasonModal">
    <div class="modal">
        <h3>Pourquoi tu ne peux pas t'entraîner ?</h3>
        <p style="color:var(--muted);font-size:13px">
            La raison est obligatoire pour enregistrer cet empêchement.
        </p>
        <textarea id="reasonInput" placeholder="Ex : blessure, études, manque de temps..."></textarea>
        <div style="display:flex;gap:10px">
            <button onclick="closeModal()" style="background:#39264d;color:white">Annuler</button>
            <button onclick="saveReason()" style="background:linear-gradient(90deg,#ff4fa3,#9b5cff);color:white">Confirmer</button>
        </div>
    </div>
</div>

<script>
const data = [
{
day:"Lundi",focus:"Explosivité + finition",basket:"09:00 – 10:30",gym:"15:00 – 16:15",
b:[
["09:00","Échauffement","12 min : mobilité, activation, jogging et déplacements défensifs."],
["09:12","Ball handling","3 × 45 s par main : dribbles bas, crossovers, between-the-legs, behind-the-back. Repos 30 s."],
["09:25","Accélérations","5 × 10 m + 4 changements de direction. Repos 60–90 s."],
["09:40","Finition au cercle","4 × 5 par côté : main droite et gauche, lay-up et reverse."],
["10:00","Finition après contact contrôlé","3 × 4 par côté. Protéger la balle, équilibre, finition."],
["10:15","Lancers francs","5 × 2 tirs. Routine identique."],
["10:25","Retour au calme","5 min."]
],
g:[
["15:00","Échauffement","10 min vélo léger, mobilité et séries progressives."],
["15:10","Squat","4 × 4–5. Charge maîtrisée, repos 2–3 min."],
["15:27","Soulevé de terre roumain","3 × 6. Repos 2 min."],
["15:40","Fentes arrière","3 × 6 par jambe."],
["15:55","Mollets debout","3 × 10–12."],
["16:05","Pallof press","3 × 10 par côté."],
["16:12","Retour au calme","3 min."]
],
food:[
["Petit-déjeuner","Œufs, pain complet, fruit, lait ou yaourt."],
["Déjeuner","Poulet, riz, légumes, huile d'olive."],
["Collation","Banane + yaourt ou sandwich."],
["Dîner","Poisson, pommes de terre, légumes." ]
]
},
{
day:"Mardi",focus:"Tir + haut du corps",basket:"10:00 – 11:30",gym:"15:30 – 16:45",
b:[
["10:00","Échauffement","10 min : mobilité, dribble et tirs proches."],
["10:10","Form shooting","5 spots × 8 tirs proches."],
["10:25","Tir après dribble","5 spots × 5 tirs après dribble main droite et gauche."],
["10:45","Tir en sortie d'écran imaginaire","5 spots × 4 tirs : curl, reject et pop."],
["11:00","Tir à 3 points","5 spots × 5 tirs. Qualité avant volume."],
["11:15","Lancers francs","10 tirs en routine complète."],
["11:22","Conditionnement technique","6 × 15 s dribble rapide + 45 s récupération."],
["11:28","Retour au calme","2 min."]
],
g:[
["15:30","Échauffement","10 min rameur léger et activation épaules."],
["15:40","Développé couché","4 × 5. Repos 2 min."],
["15:55","Tractions","4 × 5–8. Assistance si nécessaire."],
["16:10","Développé incliné haltères","3 × 8."],
["16:22","Rowing poulie","3 × 8–10."],
["16:35","Face pulls","3 × 12–15."],
["16:42","Gainage","2 × 45 s."]
],
food:[
["Petit-déjeuner","Flocons d'avoine, lait, banane, beurre de cacahuète."],
["Déjeuner","Pâtes, viande maigre, légumes."],
["Collation","Fruit + fromage blanc."],
["Dîner","Omelette, pain complet, salade."]
]
},
{
day:"Mercredi",focus:"Jambes + création",basket:"09:00 – 10:30",gym:"15:00 – 16:00",
b:[
["09:00","Échauffement","12 min : mobilité, appuis et dribble."],
["09:12","Dribble sous pression","4 × 45 s : protéger la balle, changer de rythme."],
["09:25","Lecture du défenseur","3 × 5 : attaque closeout, hésitation, recul."],
["09:40","Pull-up mi-distance","5 spots × 4 tirs."],
["10:00","Floater","4 × 5 par côté."],
["10:15","Pick-and-roll","4 × 3 lectures : pénétration, pull-up, passe simulée."],
["10:25","Lancers francs","5 min."]
],
g:[
["15:00","Échauffement","10 min vélo et mobilité."],
["15:10","Trap-bar deadlift","3 × 4. Charge modérée, technique stricte."],
["15:25","Split squat","3 × 6 par jambe."],
["15:40","Hip thrust","3 × 8."],
["15:50","Leg curl","2 × 10."],
["15:57","Mobilité","3 min."]
],
food:[
["Petit-déjeuner","Pain complet, œufs, fruit."],
["Déjeuner","Riz, poulet, légumes."],
["Collation","Smoothie lait, banane, avoine."],
["Dîner","Saumon ou sardines, quinoa, légumes."]
]
},
{
day:"Jeudi",focus:"Récupération active",basket:"10:00 – 10:40",gym:"16:00 – 16:30",
b:[
["10:00","Marche ou vélo léger","8 min, effort facile."],
["10:08","Ball handling détente","10 min, sans fatigue."],
["10:18","Tirs de proximité","15 min : 30–50 tirs sans forcer."],
["10:33","Mobilité","7 min : hanches, chevilles, thorax."]
],
g:[
["16:00","Mobilité guidée","10 min : hanches, chevilles, épaules."],
["16:10","Stabilité et équilibre","2 × 30 s par jambe."],
["16:18","Respiration","7 min."],
["16:25","Fin","Pas de charge lourde, pas de sprint."]
],
food:[
["Petit-déjeuner","Yaourt, avoine, fruits."],
["Déjeuner","Couscous avec légumes et poulet."],
["Collation","Fruit + poignée de noix."],
["Dîner","Soupe, œufs, pain complet."]
]
},
{
day:"Vendredi",focus:"Vitesse + défense",basket:"09:00 – 10:30",gym:"15:00 – 16:15",
b:[
["09:00","Échauffement","12 min : course progressive, appuis et mobilité."],
["09:12","Accélérations","5 × 10 m + 4 × 15 m. Récupération complète."],
["09:27","Déplacements défensifs","5 × 15 s : stance, slides, closeout."],
["09:42","Closeout + réaction","4 × 4 répétitions."],
["09:55","Tirs après sprint","5 séries : sprint court, réception, 2 tirs."],
["10:15","1 contre 1 limité","6 × 15 s, repos 45–60 s."],
["10:27","Lancers francs","3 × 2."]
],
g:[
["15:00","Échauffement","10 min."],
["15:10","Sauts sur box bas","3 × 4. Réception silencieuse."],
["15:20","Presse à cuisses","3 × 6, charge modérée."],
["15:32","Leg curl","3 × 8."],
["15:42","Développé militaire haltères","3 × 6–8."],
["15:55","Rowing poitrine appuyée","3 × 8."],
["16:07","Gainage latéral","2 × 30 s de chaque côté."]
],
food:[
["Petit-déjeuner","Avoine, lait, fruit."],
["Déjeuner","Poulet, pâtes, légumes."],
["Collation","Banane, yaourt."],
["Dîner — CHEAT MEAL","Burger maison + frites au four ou pizza. Repas plaisir, sans culpabilité."]
]
},
{
day:"Samedi",focus:"Scoring + conditionnement",basket:"10:00 – 11:30",gym:"15:30 – 16:30",
b:[
["10:00","Échauffement","12 min : mobilité et tirs proches."],
["10:12","Combo dribble + attaque","4 × 45 s : crossover, hesitation, accélération."],
["10:25","Tir en mouvement","5 spots × 4 tirs après déplacement."],
["10:45","Finition variée","3 × 4 : reverse, euro-step, floater, main faible."],
["11:00","Séquence meneur","5 séries : dribble, changement de rythme, tir ou finition."],
["11:15","Lancers francs","10 tirs, noter le résultat."],
["11:25","Retour au calme","5 min."]
],
g:[
["15:30","Échauffement","10 min."],
["15:40","Goblet squat","3 × 8."],
["15:50","Dumbbell bench press","3 × 8."],
["16:00","Lat pulldown","3 × 8."],
["16:10","Farmer carry","3 × 20 m."],
["16:20","Mobilité","10 min."]
],
food:[
["Petit-déjeuner","Œufs, pain, fruit."],
["Déjeuner","Riz, poisson, légumes."],
["Collation","Smoothie fruit + yaourt."],
["Dîner","Poulet, patates douces, salade."]
]
},
{
day:"Dimanche",focus:"OFF — repos complet",basket:"Repos",gym:"Repos",off:true,
b:[
["Toute la journée","Repos sportif","Pas d'entraînement structuré. Marche douce facultative."],
["Au besoin","Récupération","Hydratation, repas réguliers, sommeil et détente."]
],
g:[
["Toute la journée","Repos","Aucune séance de musculation."],
["Optionnel","Mobilité légère","Uniquement si cela te fait du bien."]
],
food:[
["Petit-déjeuner","Pancakes maison, fruit, yaourt."],
["Déjeuner","Repas familial équilibré."],
["Collation","Fruit, noix ou yaourt."],
["Dîner","Poisson ou poulet, féculent, légumes."]
]
}
];

let active = 0;
let pendingDay = null;

function getStore() {
    return JSON.parse(localStorage.getItem("pgElite") || "{}");
}

function saveStore(store) {
    localStorage.setItem("pgElite", JSON.stringify(store));
}

function renderDays() {
    const days = document.getElementById("days");

    days.innerHTML = data.map((d,i)=>`
        <button class="day-btn day-${i} ${i===active?'active':''}"
                onclick="selectDay(${i})">
            ${d.day}
            <small>${d.off?'OFF':d.focus}</small>
        </button>
    `).join("");
}

function selectDay(i) {
    active = i;
    renderDays();
    renderContent();
}

function renderExercises(arr, dayIndex, type) {
    const store = getStore();

    return arr.map((e,i)=>{
        const k = `${dayIndex}-${type}-${i}`;
        const entry = store[k] || {};
        const status = entry.status || "";

        return `
        <div class="exercise">
            <div class="exercise-top">
                <strong>${e[0]} — ${e[1]}</strong>

                <select onchange="setStatus('${k}',this.value)">
                    <option value="" ${status===""?"selected":""}>À faire</option>
                    <option value="fait" ${status==="fait"?"selected":""}>Fait ✓</option>
                    <option value="pasfait" ${status==="pasfait"?"selected":""}>Pas fait ✗</option>
                </select>
            </div>

            <p>${e[2]}</p>

            ${entry.status==="pasfait" && entry.reason
                ? `<p style="color:#ff85c0">Raison : ${escapeHTML(entry.reason)}</p>`
                : ""}
        </div>
        `;
    }).join("");
}

function escapeHTML(str) {
    return String(str).replace(/[&<>"']/g, function(m) {
        return {
            "&":"&amp;",
            "<":"&lt;",
            ">":"&gt;",
            '"':"&quot;",
            "'":"&#039;"
        }[m];
    });
}

function setStatus(k,value) {
    const store = getStore();

    if(value === "pasfait") {
        pendingDay = k;
        document.getElementById("reasonInput").value =
            store[k]?.reason || "";
        document.getElementById("reasonModal").style.display = "flex";
        return;
    }

    store[k] = {status:value,reason:""};
    saveStore(store);
    renderContent();
    updateProgress();
}

function closeModal() {
    document.getElementById("reasonModal").style.display = "none";
    pendingDay = null;
    renderContent();
}

function saveReason() {
    const reason = document.getElementById("reasonInput").value.trim();

    if(!reason) {
        alert("Tu dois obligatoirement donner une raison.");
        return;
    }

    const store = getStore();
    store[pendingDay] = {
        status:"pasfait",
        reason:reason
    };

    saveStore(store);
    closeModal();
    renderContent();
    updateProgress();
}

function renderFood(arr) {
    return arr.map(m=>`
        <div class="meal">
            <strong>${m[0]}</strong><br>
            ${m[1]}
        </div>
    `).join("");
}

function renderContent() {
    const d = data[active];

    let html = `
        <div class="day-header">
            <div>
                <div style="color:#ff85c0;font-size:12px;font-weight:bold">
                    MODULE ${active+1} / 7
                </div>
                <h2>${d.day}</h2>
                <p style="color:var(--muted);margin-top:7px">${d.focus}</p>
            </div>
            <span class="tag">${d.off?"JOUR OFF":"PROGRAMME DU JOUR"}</span>
        </div>
    `;

    if(d.off) {
        html += `
        <div class="off">
            <h3>🧘 Journée de récupération</h3>
            <p>Ton corps progresse aussi pendant le repos.</p>
            <p>Pas de musculation ni de basket structuré.</p>
            <p>Priorité : sommeil, hydratation et alimentation régulière.</p>
        </div>
        `;
    } else {
        html += `
        <div class="tag">🏀 BASKET : ${d.basket}</div>
        <div class="session">
            <h3>Entraînement basket</h3>
            ${renderExercises(d.b,active,"b")}
        </div>

        <div style="margin:25px 0;padding:15px;background:#2d1a3c;border-radius:14px">
            <strong>⏸️ Pause entre les séances</strong>
            <p style="color:var(--muted);font-size:13px;margin-top:8px">
                Déjeuner, hydratation, repos et récupération.
                Garde au moins 4 heures entre les entraînements.
            </p>
        </div>

        <div class="tag">🏋️ SALLE : ${d.gym}</div>
        <div class="session">
            <h3>Entraînement musculation</h3>
            ${renderExercises(d.g,active,"g")}
        </div>
        `;
    }

    html += `
        <div class="meals">
            <h3>🍽️ Nutrition du jour</h3>
            ${renderFood(d.food)}
        </div>

        <button class="action cannot" onclick="openReasonForDay()">
            Je ne peux pas faire aujourd'hui
        </button>

        <button class="action reset" onclick="resetDay()">
            Réinitialiser cette journée
        </button>
    `;

    document.getElementById("content").innerHTML = html;
}

function openReasonForDay() {
    pendingDay = `${active}-absence`;
    document.getElementById("reasonInput").value = "";
    document.getElementById("reasonModal").style.display = "flex";
}

function resetDay() {
    if(!confirm("Réinitialiser les statuts de cette journée ?")) return;

    const store = getStore();

    Object.keys(store).forEach(k=>{
        if(k.startsWith(active+"-")) delete store[k];
    });

    saveStore(store);
    renderContent();
    updateProgress();
}

function updateProgress() {
    const store = getStore();

    let total = 0;
    let done = 0;

    data.forEach((d,i)=>{
        ["b","g"].forEach(type=>{
            d[type].forEach((e,j)=>{
                total++;
                if(store[`${i}-${type}-${j}`]?.status==="fait") done++;
            });
        });
    });

    const percent = Math.round(done/total*100);

    document.getElementById("progressFill").style.width = percent+"%";
    document.getElementById("progressText").textContent = percent+"%";
    document.getElementById("progressCount").textContent =
        done+" exercices terminés sur "+total;
}

renderDays();
renderContent();
updateProgress();
</script>

</body>
</html>
