<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Atividade Interativa — Endereçamento de Armazém | SENAI</title>
<style>
  body{
    font-family:'Segoe UI',Roboto,Arial;
    background:linear-gradient(180deg,#0b1220 0%,#111e35 100%);
    color:#eef6ff;
    margin:0;padding:0;
  }
  header{
    background:#c00a0a;
    color:#fff;
    padding:16px 20px;
    display:flex;align-items:center;gap:14px;
  }
  header img{height:50px;}
  header h1{font-size:20px;margin:0;line-height:1.2;}
  .container{max-width:1050px;margin:0 auto;padding:20px;}
  h2{margin-top:0;color:#e0f0ff;}
  .card{background:#13243f;padding:18px;border-radius:12px;margin-bottom:20px;
        box-shadow:0 6px 18px rgba(0,0,0,.4);}
  label{font-size:14px;color:#b7d0ec;margin-bottom:4px;display:block;}
  input[type=text]{width:100%;padding:8px;border-radius:6px;border:1px solid #234a72;
                   background:#09192d;color:#d8f4ff;margin-bottom:10px;}
  table{width:100%;border-collapse:collapse;margin-top:10px;}
  th,td{border:1px solid rgba(255,255,255,.1);padding:8px;text-align:center;}
  th{background:#1b345c;color:#dff6ff;}
  td input{width:90%;text-align:center;background:#07172b;color:#d9f3ff;
           border:1px solid rgba(255,255,255,.1);border-radius:4px;}
  .btn{background:#c00a0a;border:none;color:white;padding:8px 14px;font-weight:700;
       border-radius:6px;cursor:pointer;}
  .btn-alt{background:#15803d;}
  .btn-blue{background:#2563eb;}
  .btn-red{background:#ef4444;}
  .result{margin-top:12px;padding:10px;border-radius:8px;background:#0d223d;color:#aef0db;}
  textarea{width:100%;height:150px;background:#0a1a2e;color:#d6efff;border:1px solid rgba(255,255,255,.1);
           border-radius:8px;padding:10px;resize:vertical;}
  footer{background:#0b1220;color:#a0b8cc;font-size:13px;padding:12px;text-align:center;}
</style>
</head>
<body>
<header>
  <img src="https://www.senairs.org.br/sites/default/files/styles/scale_sm/public/logos/avatares_sistema_fiergs_senai_cor.png?itok=fu" alt="SENAI">
  <div>
    <h1>Atividade Prática — Endereçamento de Armazém</h1>
    <div style="font-size:14px;opacity:.9;">Assistente de operações em Logística (EAD) — Prof. Luiz Eduardo Peixoto</div>
  </div>
</header>

<div class="container">
  <div class="card">
    <label>Nome do Aluno:</label>
    <input id="aluno" type="text" placeholder="Digite seu nome completo..." />
  </div>

<div class="card">
    <h2>🧭 Lógica de Endereçamento (instrucional)</h2>
    <div class="explain">
      <strong>Resumo:</strong><br>
      <ul>
        <li><strong>Corredores A/B</strong>: destinados a produtos de <em>alto giro</em> (acesso rápido).</li>
        <li><strong>Corredores C/D</strong>: produtos de <em>giro médio/baixo</em>.</li>
        <li><strong>Níveis</strong>: <em>01</em> para itens grandes/pesados, <em>02</em> para médios, <em>03</em> para pequenos/levos.</li>
        <li><strong>Módulos</strong>: agrupamento por categoria: <em>01=Fixadores, 02=Ferramentas, 03=EPIs, 04=Acessórios</em>.</li>
        <li><strong>Vãos A–D</strong>: posições laterais dentro do módulo (variam sem alterar a lógica).</li>
      </ul>
      <p class="small">O objetivo da atividade é fazer com que o aluno justifique o endereço escolhido a partir das características do produto (tamanho, peso, giro e categoria).</p>
    </div>
  </div>

  <div class="card">
    <h2>📦 Produtos e Parâmetros (use para decidir o endereço)</h2>
    <table>
      <thead>
        <tr><th>Produto</th><th>Tamanho</th><th>Peso</th><th>Giro</th><th>Categoria</th></tr>
      </thead>
      <tbody id="parametros">
      </tbody>
    </table>
    <p class="small" style="margin-top:8px">Use essas informações para aplicar a lógica acima ao preencher os endereços.</p>
  </div>

  <div class="card">
    <h2>🧭 Modo Desafio</h2>
    <p style="font-size:14px;color:#b8cde0">Cada tentativa gera novos endereços aleatórios. Preencha os campos corretamente segundo a estrutura <strong>Corredor-Módulo-Nível-Vão</strong> (ex: <code>B-02-01-A</code>).</p>
    <button class="btn" id="gerar">🔄 Gerar Desafio</button>

    <table id="tabela" style="display:none;">
      <thead>
        <tr>
          <th>Produto</th>
          <th>Corredor</th>
          <th>Módulo</th>
          <th>Nível</th>
          <th>Vão</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>

    <div style="margin-top:12px;display:flex;gap:10px;">
      <button class="btn-alt" id="verificar" style="display:none;">✅ Verificar Respostas</button>
      <button class="btn-red" id="limpar" style="display:none;">🧹 Limpar</button>
      <button class="btn-blue" id="baixar" style="display:none;">📄 Baixar Relatório</button>
    </div>
    <div id="resultado" class="result" style="display:none;"></div>
  </div>

  <div class="card">
    <h2>📋 Feedback / Avaliação do Professor</h2>
    <textarea id="feedback" placeholder="Comente sobre a padronização dos endereços, lógica de agrupamento e coerência com o WMS..."></textarea>
    <p style="font-size:13px;color:#aac6dd"></p>
  </div>
</div>

<footer>
  SENAI — Serviço Nacional de Aprendizagem Industrial • Atividade EAD Logística<br>
  Referências: material "Logística de Armazenagem" (endereçamento hierárquico e sinalização de áreas). 
</footer>

<script>
  // Produtos com parâmetros
  const produtos = [
    {nome:"Parafuso 4x20", tamanho:"Pequeno", peso:"Leve", giro:"Alto", categoria:"Fixador"},
    {nome:"Porca M6", tamanho:"Pequeno", peso:"Leve", giro:"Alto", categoria:"Fixador"},
    {nome:"Arruela lisa 1/4", tamanho:"Pequeno", peso:"Leve", giro:"Alto", categoria:"Fixador"},
    {nome:"Chave de fenda", tamanho:"Médio", peso:"Leve", giro:"Médio", categoria:"Ferramenta"},
    {nome:"Martelo de borracha", tamanho:"Médio", peso:"Médio", giro:"Médio", categoria:"Ferramenta"},
    {nome:"Alicate universal", tamanho:"Médio", peso:"Médio", giro:"Médio", categoria:"Ferramenta"},
    {nome:"Luvas de proteção", tamanho:"Médio", peso:"Leve", giro:"Alto", categoria:"EPI"},
    {nome:"Caixa organizadora", tamanho:"Grande", peso:"Leve", giro:"Baixo", categoria:"Acessório"}
  ];

  const tabela = document.getElementById("tabela");
  const corpo = tabela.querySelector("tbody");
  const gerar = document.getElementById("gerar");
  const verificar = document.getElementById("verificar");
  const limpar = document.getElementById("limpar");
  const baixar = document.getElementById("baixar");
  const resultado = document.getElementById("resultado");
  const parametrosTbody = document.getElementById("parametros");

  // preencher tabela de parâmetros
  function renderParametros() {
    parametrosTbody.innerHTML = "";
    produtos.forEach(p => {
      const tr = document.createElement("tr");
      tr.innerHTML = `<td>${p.nome}</td>
                      <td class="param-cell">${p.tamanho}</td>
                      <td class="param-cell">${p.peso}</td>
                      <td class="param-cell">${p.giro}</td>
                      <td class="param-cell">${p.categoria}</td>`;
      parametrosTbody.appendChild(tr);
    });
  }
  renderParametros();

  // lógica de mapeamento
  function corredorPorGiro(giro) {
    if (giro === "Alto") return ["A","B"];
    return ["C","D"];
  }
  function nivelPorTamanhoPeso(tamanho, peso) {
    // preferência: se grande OU pesado => 01, se médio => 02, se pequeno e leve =>03
    if (tamanho === "Grande" || peso === "Pesado") return "01";
    if (tamanho === "Médio" || peso === "Médio") return "02";
    return "03";
  }
  function moduloPorCategoria(cat) {
    const map = {"Fixador":"01","Ferramenta":"02","EPI":"03","Acessório":"04"};
    return map[cat] || "04";
  }

  function gerarVao() {
    const v = ["A","B","C","D"];
    return v[Math.floor(Math.random()*v.length)];
  }

  // Gera um endereço coerente com a lógica do produto (usado como gabarito)
  function gerarEnderecoCoerente(p) {
    const corredoresPossiveis = corredorPorGiro(p.giro);
    const corredor = corredoresPossiveis[0]; // por padrão escolhe a primeira (pode randomizar se preferir)
    const modulo = moduloPorCategoria(p.categoria);
    const nivel = nivelPorTamanhoPeso(p.tamanho, p.peso);
    const vao = gerarVao();
    return `${corredor}-${modulo}-${nivel}-${vao}`;
  }

  // opcional: se preferir variar corredor entre os possíveis
  function gerarEnderecoCoerenteAleatorio(p) {
    const corredoresPossiveis = corredorPorGiro(p.giro);
    const corredor = corredoresPossiveis[Math.floor(Math.random() * corredoresPossiveis.length)];
    const modulo = moduloPorCategoria(p.categoria);
    const nivel = nivelPorTamanhoPeso(p.tamanho, p.peso);
    const vao = gerarVao();
    return `${corredor}-${modulo}-${nivel}-${vao}`;
  }

  let gabarito = [];

  gerar.addEventListener("click", () => {
    corpo.innerHTML = "";
    gabarito = [];
    produtos.forEach(p => {
      // gere gabarito coerente (use a versão aleatória ou fixa conforme desejar)
      const end = gerarEnderecoCoerenteAleatorio(p);
      gabarito.push(end);
      const linha = document.createElement("tr");
      linha.dataset.gabarito = end;
      linha.dataset.params = JSON.stringify(p);
      linha.innerHTML = `
        <td>${p.nome}</td>
        <td><input maxlength="1" placeholder="A"></td>
        <td><input maxlength="2" placeholder="01"></td>
        <td><input maxlength="2" placeholder="01"></td>
        <td><input maxlength="1" placeholder="A"></td>
      `;
      corpo.appendChild(linha);
    });
    tabela.style.display = "table";
    verificar.style.display = limpar.style.display = baixar.style.display = "inline-block";
    resultado.style.display = "none";
  });

  // avalia uma linha: retorna checks, feedback e se é exata
  function avaliarLinha(linha) {
    const p = JSON.parse(linha.dataset.params);
    const inputs = Array.from(linha.querySelectorAll("input")).map(i => i.value.trim().toUpperCase());
    // preencher com valores padrão quando vazio para evitar erro de padStart
    const corredorInput = (inputs[0] || "");
    const moduloInput = (inputs[1] || "").padStart(2,"0");
    const nivelInput = (inputs[2] || "").padStart(2,"0");
    const vaoInput = (inputs[3] || "");

    const resposta = `${corredorInput}-${moduloInput}-${nivelInput}-${vaoInput}`;
    const correto = linha.dataset.gabarito;

    // o gabarito coerente esperado (lista de corredores possíveis + módulo + nível)
    const corredoresEsperados = corredorPorGiro(p.giro); // array
    const moduloEsperado = moduloPorCategoria(p.categoria); // string "01" etc
    const nivelEsperado = nivelPorTamanhoPeso(p.tamanho, p.peso); // string "01"/"02"/"03"

    const checks = {
      corredorOk: corredoresEsperados.includes(corredorInput),
      moduloOk: (moduloInput === moduloEsperado),
      nivelOk: (nivelInput === nivelEsperado),
      vaoOk: (["A","B","C","D"].includes(vaoInput))
    };

    const exata = (resposta === correto);
    const logicaOk = checks.corredorOk && checks.moduloOk && checks.nivelOk && checks.vaoOk;

    // montar feedback detalhado
    let feedback = "";
    if (exata) {
      feedback = "Endereço exato (igual ao gabarito). Excelente.";
    } else {
      if (!checks.corredorOk) {
        feedback += `Corredor incorreto — giro "${p.giro}" pede ${corredoresEsperados.join(" ou ")}. `;
      } else {
        feedback += `Corredor válido (${corredorInput}). `;
      }
      if (!checks.moduloOk) {
        feedback += `Módulo incorreto — categoria "${p.categoria}" pede módulo ${moduloEsperado}. `;
      } else {
        feedback += `Módulo válido (${moduloInput}). `;
      }
      if (!checks.nivelOk) {
        feedback += `Nível incorreto — tamanho/peso pedem ${nivelEsperado}. `;
      } else {
        feedback += `Nível válido (${nivelInput}). `;
      }
      if (!checks.vaoOk) {
        feedback += `Vão inválido — escolha A, B, C ou D.`;
      } else {
        feedback += `Vão (${vaoInput}).`;
      }
    }

    return { resposta, correto, exata, logicaOk, checks, feedback };
  }

  // botão verificar: aplica avaliação por linha, pinta e calcula nota
  verificar.addEventListener("click", () => {
    let acertosExatos = 0;
    let total = 0;
    corpo.querySelectorAll("tr").forEach(linha => {
      total++;
      const res = avaliarLinha(linha);

      // pintar linha: verde = exata, amarelo = lógica ok, vermelho = incorreta
      if (res.exata) {
        linha.style.background = "rgba(0,255,150,0.12)";
        acertosExatos++;
      } else if (res.logicaOk) {
        linha.style.background = "rgba(255,235,59,0.08)"; // amarelo suave
      } else {
        linha.style.background = "rgba(255,0,0,0.08)";
      }

      // mostrar feedback inline (se já não houver célula, criar)
      let celFeedback = linha.querySelector(".feedback-cell");
      if (!celFeedback) {
        celFeedback = document.createElement("td");
        celFeedback.className = "feedback-cell";
        celFeedback.colSpan = 1; // não quebra layout — vamos inserir após a última célula
        celFeedback.style.textAlign = "left";
        celFeedback.style.fontSize = "12px";
        celFeedback.style.paddingLeft = "10px";
        linha.appendChild(celFeedback);
      }
      celFeedback.textContent = res.feedback;
    });

    const nota = total ? Math.round((acertosExatos / total) * 100) : 0;
    resultado.style.display = "block";
    resultado.innerHTML = `<strong>Nota automática (exatas):</strong> ${nota}/100<br>${acertosExatos} respostas exatas de ${total}.<br><em>Linhas em amarelo seguem a lógica mas não batem com o gabarito exato.</em>`;
  });

  limpar.addEventListener("click", () => {
    corpo.querySelectorAll("input").forEach(i => i.value = "");
    corpo.querySelectorAll("tr").forEach(l => l.style.background = "transparent");
    // remover feedback cells adicionadas
    corpo.querySelectorAll(".feedback-cell").forEach(c => c.remove());
    resultado.style.display = "none";
  });

  baixar.addEventListener("click", () => {
    const nome = document.getElementById("aluno").value || "Aluno";
    const fb = document.getElementById("feedback").value || "(sem feedback)";
    let rel = `Relatório de Atividade - Endereçamento de Armazém (SENAI)\nAluno: ${nome}\n\n`;
    rel += "Produto | Endereço Gabarito | Resposta do Aluno | Observação\n";
    rel += "------------------------------------------------------------\n";
    corpo.querySelectorAll("tr").forEach(l => {
      const ins = l.querySelectorAll("input");
      const resposta = `${(ins[0].value||"").toUpperCase()}-${(ins[1].value||"").padStart(2,"0")}-${(ins[2].value||"").padStart(2,"0")}-${(ins[3].value||"").toUpperCase()}`;
      const obs = l.querySelector(".feedback-cell") ? l.querySelector(".feedback-cell").textContent : "";
      rel += `${l.cells[0].textContent} | ${l.dataset.gabarito} | ${resposta} | ${obs}\n`;
    });
    rel += `\nFeedback do Professor:\n${fb}\n\nAssinatura: ____________________________`;

    const blob = new Blob([rel], {type:'text/plain'});
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url; a.download = `${nome}_enderecamento.txt`;
    a.click(); URL.revokeObjectURL(url);
  });
</script>
</body>
</html>
