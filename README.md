# dnd-party-dashboard
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>D&D Party Cheat Sheet</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: radial-gradient(circle at top, #3b0764, #0f172a 45%, #020617);
      color: #f8fafc;
      min-height: 100vh;
      padding: 24px;
    }

    .page {
      max-width: 1200px;
      margin: 0 auto;
    }

    .hero {
      background: linear-gradient(135deg, rgba(236,72,153,.18), rgba(99,102,241,.18));
      border: 1px solid rgba(255,255,255,.14);
      border-radius: 28px;
      padding: 28px;
      margin-bottom: 24px;
      box-shadow: 0 20px 60px rgba(0,0,0,.35);
    }

    .eyebrow {
      color: #f0abfc;
      text-transform: uppercase;
      letter-spacing: .16em;
      font-size: 12px;
      font-weight: 800;
      margin-bottom: 10px;
    }

    h1 {
      font-size: clamp(34px, 6vw, 72px);
      line-height: .95;
      margin-bottom: 14px;
    }

    .subtitle {
      color: #cbd5e1;
      max-width: 760px;
      font-size: 17px;
      line-height: 1.6;
    }

    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 24px;
    }

    input, button {
      border: 0;
      border-radius: 999px;
      padding: 13px 18px;
      font: inherit;
    }

    input {
      flex: 1;
      min-width: 230px;
      background: rgba(255,255,255,.92);
      color: #0f172a;
    }

    button {
      cursor: pointer;
      background: rgba(255,255,255,.12);
      color: white;
      border: 1px solid rgba(255,255,255,.18);
      font-weight: 700;
      transition: .2s ease;
    }

    button:hover, button.active {
      background: #ec4899;
      transform: translateY(-1px);
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 18px;
      margin-bottom: 28px;
    }

    .card {
      background: rgba(255,255,255,.94);
      color: #0f172a;
      border-radius: 24px;
      overflow: hidden;
      box-shadow: 0 18px 45px rgba(0,0,0,.28);
      border: 1px solid rgba(255,255,255,.2);
    }

    .card-top {
      background: linear-gradient(135deg, #111827, #4c1d95, #831843);
      color: white;
      padding: 20px;
    }

    .card h2 {
      font-size: 25px;
      margin-bottom: 6px;
    }

    .meta {
      color: #e9d5ff;
      font-size: 14px;
      margin-bottom: 12px;
    }

    .role {
      display: inline-block;
      background: rgba(255,255,255,.14);
      border: 1px solid rgba(255,255,255,.2);
      border-radius: 999px;
      padding: 7px 12px;
      font-size: 13px;
      font-weight: 800;
    }

    .card-body {
      padding: 20px;
    }

    .stat-row {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 8px;
      margin-bottom: 16px;
    }

    .stat {
      background: #f1f5f9;
      border-radius: 14px;
      padding: 10px;
      text-align: center;
    }

    .stat span {
      display: block;
      color: #64748b;
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: .08em;
      font-weight: 800;
    }

    .stat strong {
      font-size: 18px;
    }

    .section {
      margin-top: 16px;
    }

    .section h3 {
      font-size: 15px;
      text-transform: uppercase;
      letter-spacing: .08em;
      color: #581c87;
      margin-bottom: 8px;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 7px;
    }

    .tag {
      background: #ede9fe;
      color: #4c1d95;
      border-radius: 999px;
      padding: 6px 10px;
      font-size: 13px;
      font-weight: 700;
    }

    ul {
      padding-left: 18px;
      color: #334155;
      line-height: 1.55;
      font-size: 14px;
    }

    .cheat {
      background: #fff1f2;
      border-left: 5px solid #ec4899;
      padding: 14px;
      border-radius: 16px;
      color: #334155;
      line-height: 1.55;
      font-size: 14px;
    }

    .panel {
      background: rgba(255,255,255,.92);
      color: #0f172a;
      border-radius: 24px;
      padding: 22px;
      margin-bottom: 22px;
      box-shadow: 0 18px 45px rgba(0,0,0,.28);
    }

    .panel h2 {
      font-size: 28px;
      margin-bottom: 14px;
    }

    .plans {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 14px;
    }

    .plan {
      background: #f8fafc;
      border-radius: 20px;
      padding: 16px;
      border: 1px solid #e2e8f0;
    }

    .plan h3 {
      margin-bottom: 8px;
      color: #831843;
    }

    .hidden {
      display: none;
    }

    @media (max-width: 520px) {
      body {
        padding: 14px;
      }

      .hero, .panel, .card-body, .card-top {
        padding: 16px;
      }

      .stat-row {
        grid-template-columns: repeat(2, 1fr);
      }
    }
  </style>
</head>
<body>
  <main class="page">
    <section class="hero">
      <div class="eyebrow">D&D Party Dashboard</div>
      <h1>Ambush Party Cheat Sheet</h1>
      <p class="subtitle">
        A simple, clean webpage for Eilrys, Zo, Kenshi, Evangeline, and Lixie. Built for quick reference during sessions: roles, spells, strengths, and what to do in common combat situations.
      </p>
    </section>

    <section class="controls">
      <input id="search" type="text" placeholder="Search character, spell, role, skill..." />
      <button class="active" data-filter="all">All</button>
      <button data-filter="scout">Scout</button>
      <button data-filter="damage">Damage</button>
      <button data-filter="support">Support</button>
      <button data-filter="control">Control</button>
    </section>

    <section id="characters" class="grid"></section>

    <section class="panel">
      <h2>Team Ambush Plans</h2>
      <div class="plans">
        <div class="plan">
          <h3>Glow & Delete</h3>
          <ul>
            <li>Eilrys or Lixie casts Faerie Fire.</li>
            <li>Zo attacks with Sneak Attack.</li>
            <li>Evangeline bursts the priority target.</li>
            <li>Kenshi charges survivors.</li>
          </ul>
        </div>
        <div class="plan">
          <h3>Root & Shoot</h3>
          <ul>
            <li>Lixie opens with Entangle.</li>
            <li>Eilrys and Zo shoot from range.</li>
            <li>Evangeline slows or finishes enemies.</li>
            <li>Kenshi blocks escape routes.</li>
          </ul>
        </div>
        <div class="plan">
          <h3>Protect the Backline</h3>
          <ul>
            <li>Eilrys slows with Longbow or Thorn Whip.</li>
            <li>Lixie uses Thunderwave if surrounded.</li>
            <li>Evangeline flies away or uses Telekinetic shove.</li>
            <li>Kenshi intercepts the biggest threat.</li>
          </ul>
        </div>
        <div class="plan">
          <h3>Boss Focus Fire</h3>
          <ul>
            <li>Pick one target and call it out.</li>
            <li>Eilrys uses Hunter’s Mark.</li>
            <li>Zo attacks when Sneak Attack is available.</li>
            <li>Everyone avoids spreading damage too thin.</li>
          </ul>
        </div>
      </div>
    </section>

    <section class="panel">
      <h2>What to Study First</h2>
      <ul>
        <li><strong>Action economy:</strong> Action, Bonus Action, Movement, Reaction.</li>
        <li><strong>Concentration:</strong> only one concentration spell at a time.</li>
        <li><strong>Stealth and surprise:</strong> how ambushes actually begin.</li>
        <li><strong>Cover:</strong> half cover, three-quarters cover, full cover.</li>
        <li><strong>Conditions:</strong> restrained, prone, grappled, invisible, frightened, charmed.</li>
        <li><strong>Target priority:</strong> casters, archers, fast enemies, then bulky melee enemies.</li>
      </ul>
    </section>
  </main>

  <script>
    const party = [
      {
        name: "Eilrys Winterpath",
        player: "Chila",
        species: "Wood Elf",
        classLevel: "Ranger 1",
        role: "Tactical Support Sniper",
        type: "scout control support damage",
        ac: 16,
        hp: 13,
        init: "+4",
        passive: 15,
        vibe: "Scout • Skirmisher • Control • Emergency Heal",
        skills: ["Stealth +6", "Perception +5", "Survival +5", "Insight +5", "Investigation +4", "Nature +4"],
        actions: ["Longbow +6, 1d8+4 piercing, Slow", "Thorn Whip +5, pull enemy", "Hunter’s Mark for single-target damage", "Faerie Fire for ambush advantage", "Guidance before important checks"],
        cheat: "Open with Faerie Fire if there are multiple enemies. Use Hunter’s Mark for one big threat. Stay at range, use cover, slow enemies, and protect the backline."
      },
      {
        name: "Zion / Zo",
        player: "Tabba",
        species: "Human",
        classLevel: "Rogue 1",
        role: "Scout & Skill Specialist",
        type: "scout damage",
        ac: 15,
        hp: 11,
        init: "+6",
        passive: 18,
        vibe: "Perception Monster • Face • Trap Finder • Sneak Attack",
        skills: ["Perception +8", "Persuasion +7", "Acrobatics +6", "Insight +6", "Survival +6", "Animal Handling +6"],
        actions: ["Light Crossbow +6", "Shortsword +6", "Daggers with Nick", "Sneak Attack +1d6", "Alert initiative swap"],
        cheat: "Scout with Eilrys. Start hidden when possible. Attack enemies near allies to trigger Sneak Attack. You are the party’s eyes and social specialist."
      },
      {
        name: "Kenshi of the Kuro Ryu Clan",
        player: "Umar",
        species: "Black Dragonborn",
        classLevel: "Ranger 1",
        role: "Frontline Striker",
        type: "damage control",
        ac: 16,
        hp: 12,
        init: "+2",
        passive: 14,
        vibe: "Greatsword • Shock Trooper • Breath Weapon • Pressure",
        skills: ["Athletics +6", "Insight +4", "Perception +4", "Stealth +4", "Nature +1"],
        actions: ["Greatsword +6, 2d6+4 slashing", "Acid Breath Weapon", "Zephyr Strike", "Hunter’s Mark", "Longbow backup"],
        cheat: "Wait for control spells, then charge the dangerous target. You hit hard, but you are not an immortal tank. Use Zephyr Strike to reposition safely."
      },
      {
        name: "Evangeline",
        player: "Nina",
        species: "Fairy",
        classLevel: "Wizard 1",
        role: "Arcane Damage & Utility",
        type: "damage control support",
        ac: 12,
        hp: 9,
        init: "+2",
        passive: 12,
        vibe: "Flying Wizard • Burst Damage • Telekinetic Control",
        skills: ["Arcana +6", "Deception +4", "Medicine +4", "Sleight of Hand +4", "Investigation +4"],
        actions: ["Magic Missile", "Chromatic Orb", "Ray of Frost", "Mage Armor", "Telekinetic shove", "Comprehend Languages"],
        cheat: "Cast Mage Armor before danger. Stay away from melee. Use Magic Missile for reliable finishing damage and Ray of Frost to slow threats."
      },
      {
        name: "Lixie",
        player: "Amanda",
        species: "Fairy",
        classLevel: "Druid 1",
        role: "Support Controller",
        type: "support control scout",
        ac: 14,
        hp: 12,
        init: "+3",
        passive: 24,
        vibe: "Healing Word • Entangle • Goodberry • Nature Magic",
        skills: ["Passive Perception 24", "Passive Investigation 22", "Insight +6", "Survival +6", "Stealth +5", "Athletics +5"],
        actions: ["Entangle", "Healing Word", "Thunderwave", "Goodberry", "Fog Cloud", "Absorb Elements", "Detect Magic"],
        cheat: "Open with Entangle when enemies group up. Healing Word is the emergency pick-up button. Use Goodberry before travel and Detect Magic in suspicious places."
      }
    ];

    const container = document.getElementById("characters");
    const search = document.getElementById("search");
    const buttons = document.querySelectorAll("button[data-filter]");
    let activeFilter = "all";

    function render() {
      const q = search.value.toLowerCase();
      container.innerHTML = "";

      party
        .filter(c => activeFilter === "all" || c.type.includes(activeFilter))
        .filter(c => JSON.stringify(c).toLowerCase().includes(q))
        .forEach(c => {
          const card = document.createElement("article");
          card.className = "card";
          card.innerHTML = `
            <div class="card-top">
              <h2>${c.name}</h2>
              <p class="meta">${c.player} • ${c.species} • ${c.classLevel}</p>
              <span class="role">${c.role}</span>
            </div>
            <div class="card-body">
              <p><strong>${c.vibe}</strong></p>
              <div class="stat-row">
                <div class="stat"><span>AC</span><strong>${c.ac}</strong></div>
                <div class="stat"><span>HP</span><strong>${c.hp}</strong></div>
                <div class="stat"><span>Init</span><strong>${c.init}</strong></div>
                <div class="stat"><span>Passive</span><strong>${c.passive}</strong></div>
              </div>
              <div class="section">
                <h3>Best Skills</h3>
                <div class="tags">${c.skills.map(s => `<span class="tag">${s}</span>`).join("")}</div>
              </div>
              <div class="section">
                <h3>Core Actions</h3>
                <ul>${c.actions.map(a => `<li>${a}</li>`).join("")}</ul>
              </div>
              <div class="section">
                <h3>Cheat Sheet</h3>
                <div class="cheat">${c.cheat}</div>
              </div>
            </div>
          `;
          container.appendChild(card);
        });
    }

    search.addEventListener("input", render);

    buttons.forEach(btn => {
      btn.addEventListener("click", () => {
        buttons.forEach(b => b.classList.remove("active"));
        btn.classList.add("active");
        activeFilter = btn.dataset.filter;
        render();
      });
    });

    render();
  </script>
</body>
</html>