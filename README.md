<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>MINI TESTE: Qual trauma mais marca sua vida hoje?</title>
<meta name="description" content="Autoavaliação com 6 categorias de traumas emocionais (5 questões cada), pontuação e interpretação.">
<style>
  :root { --gap:14px; --radius:14px; }
  * { box-sizing: border-box; }
  body {
    margin: 0 auto; padding: 24px; max-width: 980px;
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
    line-height: 1.6; color:#111; background:#fafafa;
  }
  header { margin-bottom: 22px; }
  h1 { margin:0 0 8px; font-size: 1.7rem; line-height:1.25; }
  .lead { color:#333; margin: 0 0 12px; }
  .muted { color:#666; }
  .card {
    background:#fff; border:1px solid #e6e6e6; border-radius: var(--radius);
    padding: 18px; box-shadow: 0 1px 0 rgba(0,0,0,.03); margin-bottom: var(--gap);
  }
  .grid { display: grid; gap: var(--gap); }
  @media (min-width: 880px){ .grid-2{ grid-template-columns:1fr 1fr; } }

  .q-group header { display:flex; justify-content:space-between; align-items:baseline; margin-bottom:10px; }
  .badge { display:inline-block; padding:4px 10px; border-radius:999px; background:#f1f1f1; color:#333; font-size:.85rem; font-weight:600; }
  .question { padding: 12px; border:1px solid #eee; border-radius:12px; background:#fff; }
  .question + .question { margin-top:10px; }
  .q-title { margin:0 0 10px; font-weight:600; color:#222; }
  .options { display:flex; gap:10px; flex-wrap:wrap; }
  .options label {
    border:1px solid #ddd; border-radius:10px; padding:8px 10px; cursor:pointer;
    display:inline-flex; gap:6px; align-items:center; background:#fff;
  }
  .options input { accent-color:#111; }

  .hint { font-size:.9rem; color:#666; margin: 8px 0 0; }
  .actions { display:flex; gap:10px; flex-wrap:wrap; }
  button, .btn {
    appearance:none; border:1px solid #111; background:#111; color:#fff;
    padding:10px 14px; border-radius:10px; font-weight:700; cursor:pointer;
  }
  button.secondary, .btn.secondary { background:#fff; color:#111; }
  button:disabled { opacity:.6; cursor:not-allowed; }

  .results h2 { margin:0 0 12px; font-size:1.25rem; }
  .scores { display:grid; gap:8px; grid-template-columns: repeat(auto-fit, minmax(240px,1fr)); }
  .score-item { border:1px solid #eee; border-radius:12px; padding:12px; background:#fff; }
  .bar { height:8px; background:#eee; border-radius:8px; overflow:hidden; margin-top:6px; }
  .bar > span { display:block; height:100%; background:#111; width:0%; transition: width .35s; }
  .impact { font-size:.9rem; margin-top:6px; color:#444; }
  .callout { background:#f6f6f6; border-left:4px solid #111; padding:12px; border-radius:8px; }
  .center { text-align:center; }
  footer { margin-top:24px; font-size:.9rem; color:#666; }
  details summary { cursor:pointer; font-weight:700; }
</style>
</head>
<body>
  <header>
    <h1>MINI TESTE: Qual trauma mais marca sua vida hoje?</h1>
    <p class="lead">Autoavaliação com 6 categorias (5 afirmações por categoria). Atribua de <strong>0</strong> a <strong>3</strong> a cada afirmação: 0 (nunca) · 1 (às vezes) · 2 (frequentemente) · 3 (sempre).</p>
  </header>

  <!-- INTRODUÇÃO (seu texto, compacto com details) -->
  <section class="card">
    <details open>
      <summary>Sobre este mini teste</summary>
      <p>Este mini teste foi elaborado para ajudar você a identificar qual trauma emocional exerce maior impacto em sua vida hoje. Traumas do passado podem influenciar pensamentos, emoções e comportamentos. Ao responder com sinceridade, você ganhará clareza sobre raízes de sentimentos e reações.</p>
      <p>Interpretando os resultados por categoria (0–15): <strong>8–15</strong> impacto significativo · <strong>4–7</strong> impacto moderado · <strong>0–3</strong> impacto leve. Empates indicam feridas entrelaçadas que também merecem atenção.</p>
      <p class="muted">⚠️ Uso educativo/pastoral. Não substitui avaliação clínica.</p>
    </details>
  </section>

  <form id="formTraumas" class="grid">
    <!-- DADOS OPCIONAIS -->
    <section class="card grid grid-2">
      <div>
        <label for="nome"><strong>Nome (opcional)</strong></label>
        <input id="nome" name="nome" type="text" placeholder="Seu nome"
               style="width:100%; padding:10px; border:1px solid #ddd; border-radius:10px;">
      </div>
      <div>
        <label for="email"><strong>Email (opcional)</strong></label>
        <input id="email" name="email" type="email" placeholder="seu@email.com"
               style="width:100%; padding:10px; border:1px solid #ddd; border-radius:10px;">
      </div>
    </section>

    <!-- GRUPOS DINÂMICOS -->
    <section id="grupos" class="grid"></section>

    <!-- AÇÕES -->
    <section class="card actions">
      <button type="button" id="btnCalcular">Calcular resultado</button>
      <button type="button" class="secondary" id="btnLimpar">Limpar respostas</button>
      <button type="button" class="secondary" id="btnImprimir">Salvar/Imprimir</button>
    </section>

    <!-- RESULTADOS -->
    <section id="resultado" class="card results" hidden>
      <h2>Seus resultados</h2>
      <div class="scores" id="scores"></div>
      <div id="topTrauma" class="callout" style="margin-top:12px;"></div>
      <p class="muted" style="margin-top:12px;">
        ⚠️ Este teste é indicativo e educativo. Busque apoio pastoral e/ou profissional quando necessário.
      </p>
      <div class="center" style="margin-top:10px;">
        <a class="btn secondary" href="mailto:amadurecendoemcristo@gmail.com?subject=Quero%20ajuda%20com%20meus%20traumas">✉️ Falar com a equipe</a>
      </div>
    </section>
  </form>

  <footer class="center">
    <p>© Comunidade Amadurecendo em Cristo — Método TRANSFORMA®</p>
  </footer>

<script>
/* ========= Dados completos: 6 categorias x 5 itens ========= */
const DATA = [
  {
    cat: 'Abandono',
    descr: 'Ausência emocional/física; medo de perder quem ama; sensação de invisibilidade.',
    verse: '“Ainda que me abandonem pai e mãe, o Senhor me acolherá.” (Salmos 27:10)',
    items: [
      'Sinto um medo constante e profundo de perder as pessoas que amo.',
      'Fico ansioso(a) quando alguém demora a responder e interpreto como abandono.',
      'Já aceitei relações tóxicas/abusivas para evitar solidão.',
      'Evito me apegar para não sofrer com perda, rejeição ou separação.',
      'Necessito de constantes afirmações de amor/valor para me sentir seguro(a).'
    ]
  },
  {
    cat: 'Rejeição',
    descr: 'Exclusão, desvalorização, comparação negativa; sensação de não pertencimento.',
    verse: '“A pedra que os construtores rejeitaram tornou-se a principal pedra.” (Salmos 118:22)',
    items: [
      'Evito expor opiniões/sentimentos por medo de críticas ou rejeição.',
      'Sinto que minhas conquistas nunca são suficientes para os outros.',
      'Tenho dificuldade em acreditar/aceitar elogios sinceros.',
      'Prefiro me isolar para evitar risco de exclusão ou humilhação.',
      'Vivo me comparando e me sinto aquém de um padrão idealizado.'
    ]
  },
  {
    cat: 'Humilhação',
    descr: 'Ridicularização, vergonha pública/privada; medo de se expor e se destacar.',
    verse: '“Em ti, Senhor, busquei refúgio; nunca permitas que eu seja humilhado.” (Salmos 71:1)',
    items: [
      'Tenho medo intenso de falar em público e de ser ridicularizado(a).',
      'Faço piadas de mim mesmo(a) para me proteger de humilhações.',
      'Evito me destacar para não ser alvo de críticas ou vergonha.',
      'Guardo ressentimentos por situações em que me envergonharam.',
      'Sinto desconforto com elogios; às vezes os rejeito por me expor.'
    ]
  },
  {
    cat: 'Injustiça',
    descr: 'Tratamento desigual; favoritismos; cobranças sem reconhecimento; rigidez interna.',
    verse: '“O Senhor é justo em todos os seus caminhos.” (Salmos 145:17)',
    items: [
      'Cobro-me em excesso para evitar críticas e busco perfeição.',
      'Tenho dificuldade de perdoar injustiças ou traições.',
      'Sinto frustração profunda quando meu esforço não é reconhecido.',
      'Sou muito competitivo(a) para garantir valor e evitar injustiças.',
      'Questiono/resisto a autoridades quando as percebo parciais.'
    ]
  },
  {
    cat: 'Traição / Falta de Confiança',
    descr: 'Promessas quebradas, mentiras, segredos; dificuldade de confiar e se abrir.',
    verse: '“Maldito o homem que confia no homem...” (Jeremias 17:5) — e a confiança é restaurada em Cristo.',
    items: [
      'Preciso controlar situações/pessoas para evitar decepções.',
      'Tenho dificuldade de delegar com medo de não cumprirem o combinado.',
      'Já testei lealdade de alguém para confirmar confiança.',
      'Evito me abrir emocionalmente por medo de ser ferido(a).',
      'Evito depender de alguém para não ser decepcionado(a).'
    ]
  },
  {
    cat: 'Violência / Abuso',
    descr: 'Ameaças, agressões, medo; hipervigilância; dificuldade para relaxar.',
    verse: '“O Senhor é refúgio para os oprimidos.” (Salmos 9:9)',
    items: [
      'Vivo em estado de alerta esperando que algo ruim aconteça.',
      'Tenho dificuldade de relaxar e encontrar tranquilidade.',
      'Reajo de forma agressiva ou defensiva além do necessário.',
      'Temo que repitam comigo erros do passado e me afasto.',
      'Busco “desligar” a mente por meio de fuga/isolamento quando sobrecarregado(a).'
    ]
  }
];

// ranges de interpretação
function faixa(score) {
  if (score >= 8) return {label:'Impacto significativo (8–15)', color:'#111'};
  if (score >= 4) return {label:'Impacto moderado (4–7)', color:'#444'};
  return {label:'Impacto leve (0–3)', color:'#666'};
}

/* ========= Renderização ========= */
function renderGroups() {
  const container = document.getElementById('grupos');
  DATA.forEach(group => {
    const sec = document.createElement('section');
    sec.className = 'card q-group';
    sec.dataset.category = group.cat;
    sec.dataset.max = group.items.length * 3; // 5 x 3 = 15

    const header = document.createElement('header');
    header.innerHTML = `<div><strong>${group.cat}</strong><br><span class="muted">${group.descr}</span></div>
                        <span class="badge">0–3 por item</span>`;
    sec.appendChild(header);

    group.items.forEach((qText, idx) => {
      const qId = `${group.cat.toLowerCase()}_${idx+1}`.replace(/[^\w]+/g,'_');
      const q = document.createElement('div');
      q.className = 'question';
      q.innerHTML = `
        <p class="q-title">${qText}</p>
        <div class="options" data-name="${qId}"></div>
      `;
      sec.appendChild(q);
    });

    const hint = document.createElement('p');
    hint.className = 'hint';
    hint.textContent = 'Escala: 0 (nunca) · 1 (às vezes) · 2 (frequentemente) · 3 (sempre)';
    sec.appendChild(hint);

    container.appendChild(sec);
  });

  // Render opções 0–3
  document.querySelectorAll('.options').forEach(wrap => {
    const name = wrap.getAttribute('data-name');
    ['0','1','2','3'].forEach(val => {
      const id = name + '_' + val;
      const label = document.createElement('label');
      label.innerHTML = `<input type="radio" name="${name}" value="${val}" id="${id}"><span>${val}</span>`;
      wrap.appendChild(label);
    });
  });
}

/* ========= Cálculo ========= */
function calcular() {
  const grupos = document.querySelectorAll('.q-group');
  const scores = [];
  let faltantes = 0;

  grupos.forEach(gr => {
    const cat = gr.getAttribute('data-category');
    const max = parseInt(gr.getAttribute('data-max'),10);
    const qs = gr.querySelectorAll('.options');
    let soma = 0;

    qs.forEach(q => {
      const name = q.getAttribute('data-name');
      const marcado = gr.querySelector(`input[name="${name}"]:checked`);
      if (!marcado) faltantes++;
      soma += marcado ? parseInt(marcado.value,10) : 0;
    });

    scores.push({ cat, soma, max });
  });

  if (faltantes > 0) {
    alert('Existem questões sem resposta. Complete todas para um resultado mais preciso.');
    // Se quiser bloquear o cálculo, descomente:
    // return;
  }

  renderScores(scores);
}

function renderScores(scores) {
  const cont = document.getElementById('scores');
  cont.innerHTML = '';

  scores.forEach(s => {
    const pct = Math.max(0, Math.min(100, Math.round((s.soma / s.max) * 100)));
    const fx = faixa(s.soma);
    const item = document.createElement('div');
    item.className = 'score-item';
    item.innerHTML = `
      <div style="display:flex; justify-content:space-between; align-items:center; gap:8px;">
        <strong>${s.cat}</strong>
        <span>${s.soma} / ${s.max}</span>
      </div>
      <div class="bar"><span style="width:${pct}%"></span></div>
      <div class="impact" style="color:${fx.color}">${fx.label}</div>
    `;
    cont.appendChild(item);
  });

  const top = [...scores].sort((a,b)=>b.soma - a.soma)[0];
  const ref = DATA.find(d => d.cat === top.cat);
  const topBox = document.getElementById('topTrauma');
  topBox.innerHTML = `<strong>Maior pontuação: ${top.cat}</strong><br>
    <span class="muted">${ref?.descr || ''}</span><br>
    <em>${ref?.verse || ''}</em>`;

  document.getElementById('resultado').hidden = false;
  window.scrollTo({ top: document.getElementById('resultado').offsetTop - 12, behavior: 'smooth' });
}

/* ========= Utilidades ========= */
function limpar() {
  document.getElementById('formTraumas').reset();
  document.getElementById('resultado').hidden = true;
  document.getElementById('scores').innerHTML = '';
  document.getElementById('topTrauma').innerHTML = '';
  document.querySelectorAll('.bar > span').forEach(b => b.style.width = '0%');
}
function imprimir(){ window.print(); }

/* ========= Init ========= */
renderGroups();
document.getElementById('btnCalcular').addEventListener('click', calcular);
document.getElementById('btnLimpar').addEventListener('click', limpar);
document.getElementById('btnImprimir').addEventListener('click', imprimir);
</script>
</body>
</html>
