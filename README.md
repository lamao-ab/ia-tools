<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Attribution Outils IA — Master</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:wght@400;700&display=swap');

  :root {
    --bg: #ffffff;
    --surface: #f4f6fa;
    --border: #dde1ea;
    --accent1: #0099aa;
    --accent2: #e0284a;
    --accent3: #c48a00;
    --accent4: #7c4ddb;
    --accent5: #1a7abf;
    --accent7: #1f9e4a;
    --text: #1a1d26;
    --text-muted: #6b7280;
    --header-bg: #eef1f7;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    padding: 40px 20px 60px;
  }

  .hero { text-align: center; margin-bottom: 40px; }

  .hero::before {
    content: '';
    display: block;
    width: 180px;
    height: 2px;
    background: linear-gradient(90deg, transparent, #0099aa, #7c4ddb, transparent);
    margin: 0 auto 28px;
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(1.6rem, 4vw, 2.8rem);
    letter-spacing: -0.02em;
    line-height: 1.1;
    color: var(--text);
    margin-bottom: 10px;
  }

  .hero p { color: var(--text-muted); font-size: 0.8rem; letter-spacing: 0.08em; text-transform: uppercase; }

  .group-tabs { display: flex; gap: 10px; margin-bottom: 24px; flex-wrap: wrap; }

  .tab-btn {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.8rem;
    padding: 8px 20px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text-muted);
    cursor: pointer;
    transition: all 0.2s;
  }

  .tab-btn.active { background: #0099aa; color: #fff; border-color: #0099aa; }
  .tab-btn:hover:not(.active) { border-color: #0099aa; color: #0099aa; }

  .controls-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
    flex-wrap: wrap;
  }

  .search-wrap { position: relative; flex: 1; min-width: 200px; max-width: 400px; }

  .search-wrap input {
    width: 100%;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    color: var(--text);
    font-family: 'Space Mono', monospace;
    font-size: 0.78rem;
    padding: 10px 14px 10px 38px;
    outline: none;
    transition: border-color 0.2s;
  }

  .search-wrap input:focus { border-color: #0099aa; }
  .search-wrap input::placeholder { color: var(--text-muted); }

  .search-wrap svg {
    position: absolute; left: 12px; top: 50%;
    transform: translateY(-50%); color: var(--text-muted); pointer-events: none;
  }

  .export-btn {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.75rem;
    padding: 9px 20px;
    border-radius: 8px;
    border: 1px solid var(--accent1);
    background: rgba(0,229,200,0.1);
    color: var(--accent1);
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .export-btn:hover { background: var(--accent1); color: #000; }
  .export-btn:disabled { opacity: 0.5; cursor: not-allowed; }

  .stats { display: flex; gap: 14px; flex-wrap: wrap; margin-bottom: 24px; }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 10px 18px;
    flex: 1;
    min-width: 100px;
    text-align: center;
  }

  .stat-card .num {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.5rem;
    display: block;
  }

  .stat-card .label { font-size: 0.62rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.08em; }

  .table-wrap {
    overflow-x: auto;
    border-radius: 14px;
    border: 1px solid var(--border);
    box-shadow: 0 0 60px rgba(0,229,200,0.05);
  }

  table { width: 100%; border-collapse: collapse; font-size: 0.78rem; }

  thead tr { background: var(--header-bg); border-bottom: 2px solid var(--border); }

  thead th {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--text-muted);
    padding: 14px 16px;
    text-align: left;
    white-space: nowrap;
  }

  thead th:nth-child(1) { color: var(--text-muted); }
  thead th:nth-child(2) { color: var(--accent1); }
  thead th:nth-child(3) { color: var(--accent4); }
  thead th:nth-child(4) { color: var(--accent3); }
  thead th:nth-child(5) { color: var(--accent5); }
  thead th:nth-child(6) { color: var(--accent7); }

  tbody tr { border-bottom: 1px solid var(--border); transition: background 0.15s; }
  tbody tr:hover { background: rgba(255,255,255,0.03); }
  tbody tr:last-child { border-bottom: none; }

  td { padding: 12px 16px; vertical-align: middle; line-height: 1.5; }

  .num-cell { color: var(--text-muted); font-size: 0.68rem; }

  .student-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.82rem;
    white-space: nowrap;
    color: var(--text);
  }

  .tool-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.82rem;
    white-space: nowrap;
  }

  .cat-pill {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-size: 0.65rem;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    padding: 2px 9px;
    border-radius: 20px;
    white-space: nowrap;
    border: 1px solid;
  }

  .project-idea {
    font-size: 0.72rem;
    color: var(--text);
    max-width: 320px;
    line-height: 1.6;
    border-left: 2px solid;
    padding-left: 10px;
  }

  .group-badge {
    display: inline-block;
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.65rem;
    padding: 2px 8px;
    border-radius: 4px;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  .group-A { background: rgba(0,122,138,0.12); color: #007a8a; border: 1px solid rgba(0,122,138,0.3); }
  .group-B { background: rgba(109,52,199,0.12); color: #6d34c7; border: 1px solid rgba(109,52,199,0.3); }
</style>
</head>
<body>

<div class="hero">
  <h1>Attribution des Outils IA<br>Mini-Projets Master</h1>
  <p>43 étudiants · 2 groupes · outils IA assignés</p>
</div>

<div class="group-tabs">
  <button class="tab-btn active" data-group="all">⬡ Tous les groupes</button>
  <button class="tab-btn" data-group="A">Groupe A (21 étudiants)</button>
  <button class="tab-btn" data-group="B">Groupe B (22 étudiants)</button>
</div>

<div class="search-wrap" style="margin-bottom:20px;max-width:400px;">
    <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
      <circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/>
    </svg>
    <input type="text" id="search" placeholder="Rechercher un étudiant ou un outil...">
  </div>

<div class="stats" id="stats"></div>

<div class="table-wrap">
  <table>
    <thead>
      <tr>
        <th>N°</th>
        <th>Nom &amp; Prénom</th>
        <th>Groupe</th>
        <th>Outil IA assigné</th>
        <th>Catégorie</th>
        <th>Idée de mini-projet</th>
      </tr>
    </thead>
    <tbody id="tbody"></tbody>
  </table>
</div>

<script>
const CATEGORIES = {
  "Revue de littérature":      { color: "#007a8a", bg: "rgba(0,122,138,0.10)",    icon: "📚" },
  "Gestion des références":    { color: "#6d34c7", bg: "rgba(109,52,199,0.10)",   icon: "🗂️" },
  "Grands modèles de langage": { color: "#1266a8", bg: "rgba(18,102,168,0.10)",   icon: "🤖" },
  "Écriture & Paraphrase":     { color: "#9a6800", bg: "rgba(154,104,0,0.10)",    icon: "✍️" },
  "Traduction":                { color: "#b84f00", bg: "rgba(184,79,0,0.10)",     icon: "🌐" },
  "Présentation visuelle":     { color: "#b5006e", bg: "rgba(181,0,110,0.10)",    icon: "🎨" },
  "Génération d'images":       { color: "#8a00b8", bg: "rgba(138,0,184,0.10)",    icon: "🖼️" },
  "Transcription":             { color: "#0d7a50", bg: "rgba(13,122,80,0.10)",    icon: "🎙️" },
  "Lecture de PDF":            { color: "#c0003a", bg: "rgba(192,0,58,0.10)",     icon: "📄" },
  "Résumé de littérature":     { color: "#1a7a3a", bg: "rgba(26,122,58,0.10)",    icon: "🔬" },
  "Brainstorming":             { color: "#9a7000", bg: "rgba(154,112,0,0.10)",    icon: "💡" },
  "Grammaire & Style":         { color: "#6a1faa", bg: "rgba(106,31,170,0.10)",   icon: "📝" },
  "Détection de plagiat":      { color: "#b82020", bg: "rgba(184,32,32,0.10)",    icon: "🔍" },
};

const ASSIGNMENTS = [
  { group:"A", name:"Boutaghrout Taoufik",   tool:"Semantic Scholar",               cat:"Revue de littérature",      project:"Cartographier l'évolution d'un thème de recherche sur 10 ans à partir des citations." },
  { group:"A", name:"EL Maataouy Ilham",     tool:"Elicit",                         cat:"Revue de littérature",      project:"Comparer automatiquement les méthodologies de 20 articles sur un sujet donné." },
  { group:"A", name:"EL Allaoui Mounaim",    tool:"Zotero",                         cat:"Gestion des références",    project:"Gérer toutes les sources d'un mémoire de master et générer la bibliographie APA." },
  { group:"A", name:"Barrajjal Nabil",       tool:"ChatGPT",                        cat:"Grands modèles de langage", project:"Structurer et améliorer un plan de mémoire en plusieurs itérations conversationnelles." },
  { group:"A", name:"Chahidi Rihab",         tool:"QuillBot",                       cat:"Écriture & Paraphrase",     project:"Reformuler un résumé d'article en plusieurs niveaux de complexité pour différents publics." },
  { group:"A", name:"Abdellati Oussama",     tool:"DeepL Translator",               cat:"Traduction",                project:"Traduire un article anglais en français et évaluer la qualité avec un expert bilingue." },
  { group:"A", name:"Elaouni Abdelkarim",    tool:"Canva",                          cat:"Présentation visuelle",     project:"Concevoir un poster scientifique professionnel pour une conférence de master." },
  { group:"A", name:"Aidari Yassin",         tool:"Bing Image Creator",             cat:"Génération d'images",       project:"Créer des illustrations conceptuelles pour un article de vulgarisation scientifique." },
  { group:"A", name:"Bouchlagham Chafir",    tool:"Otter.ai",                       cat:"Transcription",             project:"Transcrire et analyser thématiquement 3 entretiens pour un mémoire qualitatif." },
  { group:"A", name:"Bounfour Ibrahim",      tool:"ChatPDF",                        cat:"Lecture de PDF",            project:"Extraire les hypothèses et résultats clés de 10 articles en interrogeant chaque PDF." },
  { group:"A", name:"Aidone Fahd",           tool:"Scite.ai",                       cat:"Résumé de littérature",     project:"Étudier la réception critique d'un article fondateur dans la littérature récente." },
  { group:"A", name:"EL Alami Souhaila",     tool:"Miro AI",                        cat:"Brainstorming",             project:"Cartographier collaborativement les concepts d'une problématique de recherche." },
  { group:"A", name:"Douiri Chahida",        tool:"Grammarly",                      cat:"Écriture & Paraphrase",     project:"Analyser et améliorer le style d'un chapitre de mémoire avec rapport de score détaillé." },
  { group:"A", name:"Taibi Asmae",           tool:"Quetext",                        cat:"Détection de plagiat",      project:"Vérifier l'originalité d'un mémoire et identifier les passages à reformuler." },
  { group:"A", name:"Akarach Amine",         tool:"Research Rabbit",                cat:"Revue de littérature",      project:"Construire la carte de citations d'un auteur phare de sa discipline." },
  { group:"A", name:"Elmahraoui Hind",       tool:"Mendeley",                       cat:"Gestion des références",    project:"Créer une bibliothèque partagée annotée pour un projet de groupe." },
  { group:"A", name:"Naciri Amine",          tool:"Claude",                         cat:"Grands modèles de langage", project:"Analyser et synthétiser 5 articles scientifiques longs pour produire une revue critique." },
  { group:"A", name:"Kabbouri Abdelmounaim", tool:"Gamma.app",                      cat:"Présentation visuelle",     project:"Transformer un résumé de mémoire en présentation visuelle en moins de 10 minutes." },
  { group:"A", name:"Agrour Chaimae",        tool:"SciSpace",                       cat:"Résumé de littérature",     project:"Expliquer et comparer les méthodologies de 5 articles à des étudiants L3." },
  { group:"A", name:"Boutastas Mohamed",     tool:"ProWritingAid",                  cat:"Grammaire & Style",         project:"Évaluer et améliorer le style académique d'un chapitre de mémoire." },
  { group:"A", name:"Belarbi Abdelmajid",    tool:"GPTZero",                        cat:"Détection de plagiat",      project:"Étudier la détectabilité de textes IA reformulés par différents outils." },
  { group:"B", name:"TAGHLAOUI YOUSSEF",     tool:"Consensus",                      cat:"Revue de littérature",      project:"Analyser la convergence/divergence de la littérature sur une hypothèse précise." },
  { group:"B", name:"AFASI SALMA",           tool:"Paperpile",                      cat:"Gestion des références",    project:"Rédiger un article collaboratif Google Docs avec gestion des sources intégrée." },
  { group:"B", name:"MAHDAOUI ALI",          tool:"Google Gemini",                  cat:"Grands modèles de langage", project:"Utiliser le mode multimodal pour analyser des graphiques d'articles scientifiques." },
  { group:"B", name:"ZAGHDOUD NABILA",       tool:"Hemingway Editor",               cat:"Écriture & Paraphrase",     project:"Réécrire une introduction de mémoire pour atteindre un score de lisibilité optimal." },
  { group:"B", name:"EL HAGOUI AYYOUB",      tool:"Google Translate",               cat:"Traduction",                project:"Comparer les traductions d'un texte spécialisé par 3 outils différents." },
  { group:"B", name:"HAOUHAOU ISSAME",       tool:"Leonardo.ai",                    cat:"Génération d'images",       project:"Produire une série visuelle cohérente pour illustrer un concept scientifique abstrait." },
  { group:"B", name:"BOUYAHYI MOHAMMED",     tool:"Fireflies.ai",                   cat:"Transcription",             project:"Analyser les dynamiques de prise de parole dans des entretiens de recherche." },
  { group:"B", name:"OU SOUH MOHAMED",       tool:"Scholarcy",                      cat:"Lecture de PDF",            project:"Générer des fiches de révision à partir d'une bibliographie de mémoire." },
  { group:"B", name:"AABID ELHOUSSAINE",     tool:"Notion AI",                      cat:"Brainstorming",             project:"Créer un wiki de projet de recherche avec génération automatique de contenu." },
  { group:"B", name:"BOUCHAYB MOHAMED",      tool:"Wordtune",                       cat:"Écriture & Paraphrase",     project:"Produire 3 versions différentes (formel, neutre, accessible) d'un même paragraphe." },
  { group:"B", name:"AANOUI FATIMA",         tool:"Reverso Context",                cat:"Traduction",                project:"Étudier les variations de terminologie scientifique dans des corpus bilingues." },
  { group:"B", name:"JALAL KHALID",          tool:"SlidesAI",                       cat:"Présentation visuelle",     project:"Générer automatiquement une présentation de 15 slides depuis un rapport PDF." },
  { group:"B", name:"BOUDLA RIDOUAN",        tool:"Ideogram",                       cat:"Génération d'images",       project:"Créer des infographies visuelles avec texte lisible pour une présentation académique." },
  { group:"B", name:"OULHAJ HASSAN",         tool:"Microsoft Teams (transcription)", cat:"Transcription",            project:"Analyser les thèmes récurrents dans les transcriptions de réunions de projet." },
  { group:"B", name:"AFENICH MONAIM",        tool:"Humata AI",                      cat:"Lecture de PDF",            project:"Comparer les résultats de plusieurs études sur un même objet de recherche." },
  { group:"B", name:"EL KAMOUNI MOHAMMED",   tool:"Explain Paper",                  cat:"Résumé de littérature",     project:"Rendre accessible un article très technique à un public non-spécialiste." },
  { group:"B", name:"DIOUANI OUMAIMA",       tool:"MindMeister",                    cat:"Brainstorming",             project:"Structurer visuellement le cadre théorique d'un mémoire en carte mentale." },
  { group:"B", name:"AAZZAB FATIMA",         tool:"Language Tool",                  cat:"Écriture & Paraphrase",     project:"Corriger un article académique en français et en anglais et comparer les erreurs." },
  { group:"B", name:"LOUCHERI CHAHRAZAD",    tool:"Scribbr",                        cat:"Détection de plagiat",      project:"Analyser l'impact de la paraphrase IA sur les scores de plagiat." },
  { group:"B", name:"EL MAHDAOUI WALID",     tool:"Microsoft Copilot",              cat:"Grands modèles de langage", project:"Automatiser la rédaction de rapports Word et la mise en forme de tableaux Excel." },
  { group:"B", name:"TAIBI CHAMA",           tool:"Google Scholar",                 cat:"Revue de littérature",      project:"Créer un dashboard de veille scientifique sur une thématique de mémoire." },
  { group:"B", name:"EL YAAKOUBI NISRIA",    tool:"Whimsical",                      cat:"Brainstorming",             project:"Modéliser le processus méthodologique d'une recherche en flowchart interactif." },
];

let activeGroup = 'all';
const tbody = document.getElementById('tbody');
const searchInput = document.getElementById('search');
const statsDiv = document.getElementById('stats');
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    activeGroup = btn.dataset.group;
    render();
  });
});

searchInput.addEventListener('input', render);

function getFiltered() {
  const q = searchInput.value.toLowerCase();
  return ASSIGNMENTS.filter(s => {
    const gm = activeGroup === 'all' || s.group === activeGroup;
    const sm = !q || s.name.toLowerCase().includes(q) || s.tool.toLowerCase().includes(q) || s.cat.toLowerCase().includes(q);
    return gm && sm;
  });
}

function renderStats(filtered) {
  statsDiv.innerHTML = '';
  [
    { num: filtered.length,                               label: 'Étudiants',  color: '#007a8a' },
    { num: filtered.filter(s => s.group === 'A').length,  label: 'Groupe A',   color: '#007a8a' },
    { num: filtered.filter(s => s.group === 'B').length,  label: 'Groupe B',   color: '#6d34c7' },
    { num: new Set(filtered.map(s => s.cat)).size,        label: 'Catégories', color: '#9a6800' },
  ].forEach(s => {
    const c = document.createElement('div');
    c.className = 'stat-card';
    c.innerHTML = `<span class="num" style="color:${s.color}">${s.num}</span><span class="label">${s.label}</span>`;
    statsDiv.appendChild(c);
  });
}

function render() {
  const filtered = getFiltered();
  renderStats(filtered);
  tbody.innerHTML = '';

  if (filtered.length === 0) {
    tbody.innerHTML = `<tr><td colspan="6" style="text-align:center;padding:40px;color:var(--text-muted)">Aucun résultat.</td></tr>`;
    return;
  }

  filtered.forEach((s, i) => {
    const cat = CATEGORIES[s.cat];
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td class="num-cell">${String(i+1).padStart(2,'0')}</td>
      <td><span class="student-name">${s.name}</span></td>
      <td><span class="group-badge group-${s.group}">Groupe ${s.group}</span></td>
      <td><span class="tool-name" style="color:${cat.color}">${s.tool}</span></td>
      <td><span class="cat-pill" style="color:${cat.color};border-color:${cat.color};background:${cat.bg}">${cat.icon} ${s.cat}</span></td>
      <td><span class="project-idea" style="border-color:${cat.color}">${s.project}</span></td>
    `;
    tbody.appendChild(tr);
  });
}

render();
</script>
</body>
</html>
