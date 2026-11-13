# Sistema de Design (Design System)
## Plataforma de Monitoramento da Educação Infantil
### Secretaria Municipal de Educação — Prefeitura de Lagoa da Canoa / AL

---

## 1. Visão Geral e Filosofia de Design

O **Sistema de Design do Monitoramento da Educação Infantil** estabelece uma linguagem visual moderna, acessível e funcional, criada especificamente para atender à realidade de coordenadores pedagógicos, diretores escolares e gestores da Secretaria de Educação.

### Princípios Fundamentais:
1. **Clareza Pedagógica Imediata:** A interface traduz dados quantitativos em diagnósticos pedagógicos rápidos (Adequado, Atenção, Prioritário), permitindo intervenções assertivas na aprendizagem infantil.
2. **Identidade Visual Tricolor Municipal:** Integração harmônica das cores oficiais da bandeira e identidade de Lagoa da Canoa (Verde, Laranja e Magenta/Rosa).
3. **Preenchimento sem Fricção:** Formulários ergonômicos, navegação intuitiva por teclado, máscaras automáticas e validações em tempo real que não atrapalham a digitação do usuário.
4. **Resolução de Conflitos por Período:** Independência matemática total do número de alunos por bimestre, evitando inconsistências históricas ou duplicidades de dados.
5. **Fidelidade Gráfica de Impressão:** Relatórios analíticos no padrão executivo A4, prontos para assinatura e arquivo documental sem necessidade de ajustes pelo usuário.

---

## 2. Tokens de Design (Design Tokens)

### 2.1 Paleta de Cores

O sistema utiliza variáveis CSS nativas aplicadas no seletor `:root`, com adaptação automática para Modo Escuro (*Dark Mode*).

#### Cores Primárias e da Marca
| Token CSS | Cor HEX | Amostra | Função / Aplicação |
| :--- | :--- | :---: | :--- |
| `--g` | `#2F7D5B` | ![#2F7D5B](https://via.placeholder.com/15/2F7D5B/000000?text=+) | Verde Municipal Primário: Botões principais, indicadores "Sim", itens concluídos |
| `--gd` | `#1F5C43` | ![#1F5C43](https://via.placeholder.com/15/1F5C43/000000?text=+) | Verde Escuro: Hover de botões, textos de confirmação e cabeçalhos |
| `--gs` | `#E4F2EA` | ![#E4F2EA](https://via.placeholder.com/15/E4F2EA/000000?text=+) | Verde Suave: Fundo de inputs "Sim", badges de sucesso, KPI primário |
| `--o` | `#F47B20` | ![#F47B20](https://via.placeholder.com/15/F47B20/000000?text=+) | Laranja Municipal: Resposta "Parcial", diagnósticos em atenção, destaques |
| `--os` | `#FFEBDA` | ![#FFEBDA](https://via.placeholder.com/15/FFEBDA/000000?text=+) | Laranja Suave: Fundo de inputs "Parcial", badges de alerta, avisos de preenchimento |
| `--p` | `#E8005F` | ![#E8005F](https://via.placeholder.com/15/E8005F/000000?text=+) | Magenta/Rosa Municipal: Resposta "Não", diagnósticos prioritários, erros |
| `--ps` | `#FDE3EC` | ![#FDE3EC](https://via.placeholder.com/15/FDE3EC/000000?text=+) | Rosa Suave: Fundo de inputs "Não", badges de pendência, caixas de erro |

#### Superfície, Texto e Neutros (Modo Claro)
| Token CSS | Cor HEX | Função / Aplicação |
| :--- | :--- | :--- |
| `--bg` | `#F1F6F2` | Fundo geral da página (off-white esverdeado suave) |
| `--sf` | `#FFFFFF` | Superfície de cartões, modais e containers de conteúdo |
| `--navy` | `#173F31` | Títulos principais (`H1`, `H2`), cabeçalhos de destaque e ênfases |
| `--ink` | `#17352A` | Texto base e corpo de texto com alto contraste |
| `--mut` | `#5E7268` | Texto secundário, legendas, placeholders e rótulos auxiliares |
| `--ln` | `#DCE7DF` | Linhas de divisão, bordas de tabelas e contornos de inputs |

#### Modo Escuro (Dark Mode)
Ativado automaticamente via `@media (prefers-color-scheme: dark)` ou atributo `[data-theme="dark"]`:
```css
:root:not([data-theme="light"]) {
  --bg: #0E1713;
  --sf: #16231D;
  --ink: #E6F0E9;
  --mut: #9BB0A3;
  --ln: #27382F;
  --g: #4FB586;
  --gd: #3FA073;
  --gs: #173626;
  --os: #3B2612;
  --ps: #3C1627;
  --navy: #E6F0E9;
  color-scheme: dark;
}
```

#### Faixa Tricolor Municipal (Assinatura Oficial)
Utilizada no topo do sistema e nos relatórios de impressão:
```css
.band {
  height: 8px;
  background: linear-gradient(90deg, #2F7D5B 0 45%, #F47B20 45% 72%, #E8005F 72%);
}
```

---

### 2.2 Tipografia

* **Família Tipográfica Principal:** `"Plus Jakarta Sans", system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif`
* **Características:** Tipografia geométrica humanista com excelente legibilidade tanto em números de telas administrativas quanto em relatórios impressos.

| Nível / Uso | Tamanho | Peso | Line-Height | Aplicação |
| :--- | :--- | :--- | :--- | :--- |
| **Display / H1** | `clamp(1.4rem, 3.4vw, 2.0rem)` | 800 (Bold) | `1.2` | Título da tela principal e saudações |
| **Card Title / H2** | `1.35rem (21.6px)` | 700 / 800 | `1.3` | Nomes de turmas, escolas e seções |
| **Subtitle / H3** | `1.05rem (16.8px)` | 700 / 800 | `1.35` | Títulos internos de cartões e tabelas |
| **Item Title / H4** | `0.95rem (15.2px)` | 600 / 700 | `1.35` | Texto dos critérios pedagógicos |
| **Body (Corpo)** | `0.92rem (14.7px)` | 500 (Regular) | `1.5` | Parágrafos e descrições gerais |
| **Inputs & Botões**| `1.05rem – 1.15rem` | 600 / 700 | `1.0` | Campos numéricos, CPF e botões |
| **Badges & Labels**| `0.74rem – 0.85rem` | 600 / 700 | `1.2` | Rótulos de campos, etiquetas de status |
| **Microcopy / Meta**| `0.65rem – 0.78rem` | 500 / 600 | `1.25` | Legendas, rodapés e notas de rodapé |

---

### 2.3 Espaçamento, Grid e Elevações

* **Escala de Espaçamento Base:** `4px`, `6px`, `8px`, `10px`, `12px`, `14px`, `16px`, `20px`, `24px`, `28px`, `36px`.
* **Largura Máxima do Container (`.wrap`):** `1080px` centralizado com `margin: 0 auto; padding: 26px 20px 56px;`.
* **Raios de Borda (*Border Radius*):**
  * `6px`: Badges e botões de incremento/decremento.
  * `8px`: Alertas em linha e botões de ação rápida.
  * `10px`: Containers de controle, inputs e botões secundários.
  * `12px`: Botões de formulário (`.btn`) e campos de texto principais.
  * `16px – 18px`: Cartões de conteúdo (`.card`, `.kpi`).
  * `20px`: Painéis principais e molduras (`.panel`, `.plate`).
  * `99px`: Pílulas de filtro (`.pills button`) e chips de estado (`.chip`).
* **Sombras (*Box Shadows*):**
  * Cartão Padrão (`.card`): `0 10px 30px -22px rgba(23, 63, 49, .4)`
  * Painel de Login (`.panel`): `0 24px 60px -30px rgba(23, 63, 49, .45)`
  * Hover em Itens Selecionáveis (`.item:hover`): `0 16px 34px -18px rgba(23, 63, 49, .5)`

---

## 3. Componentes de Interface (UI Components)

### 3.1 Botões (*Buttons*)

O sistema disponibiliza 4 padrões principais de botões:

```html
<!-- Botão Primário de Ação -->
<button class="btn">Salvar preenchimento</button>

<!-- Botão Secundário / Contorno -->
<button class="ghost">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">...</svg>
  Imprimir relatório
</button>

<!-- Botão de Ação Crítica / Perigo -->
<button class="dan">Excluir</button>

<!-- Botão de Navegação / Migalha de Pão -->
<button class="crumb">← Voltar às turmas</button>
```

#### Estados dos Botões:
* **Hover:** Transição suave de 0.15s com escurecimento (`--gd`) para botões primários e borda verde para botões `.ghost`.
* **Active:** Efeito sutil de clique (`transform: translateY(1px)`).
* **Focus Visible:** Contorno verde de acessibilidade: `outline: 3px solid var(--g); outline-offset: 2px;`.

---

### 3.2 Badges e Etiquetas de Status

Utilizados para feedback de preenchimento, etapas e situações pedagógicas.

```html
<!-- Concluído / Sucesso (Verde Suave) -->
<span class="badge">✓ Preenchida</span>
<span class="badge">✓ 15/15 alunos</span>

<!-- Em Andamento / Atenção (Laranja Suave) -->
<span class="badge w">● Parcial (1/15)</span>
<span class="badge w">⚠️ 12/15 alunos</span>

<!-- Pendente / Erro (Rosa Suave) -->
<span class="badge x">Pendente</span>
<span class="badge x">✕ 18/15 alunos</span>
```

---

### 3.3 Gestão Dinâmica de Alunos por Período

Componente projetado para permitir que cada turma tenha matrículas variáveis ao longo dos bimestres (entradas e transferências) sem causar divergências:

```html
<div class="card" style="margin-bottom:16px;padding:20px;border-radius:12px">
  <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px;margin-bottom:14px">
    <div>
      <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap">
        <h2 style="margin:0;font-size:1.35rem;font-weight:700;color:var(--navy)">Pré - teste · Pré-I</h2>
        <span class="badge" style="margin:0;background:var(--gs);color:var(--gd);font-weight:600">4º Bimestre</span>
      </div>
      <p style="margin:4px 0 0;font-size:.88rem;color:var(--mut)">ESCOLA DIVALDO SURUAGY · Acompanhamento de Desenvolvimento e Aprendizagem</p>
    </div>
    <div id="prog-badge-wrap">...</div>
  </div>

  <!-- Controle do número de alunos na turma no período -->
  <div style="background:var(--bg);border:1px solid var(--ln);border-radius:10px;padding:12px 18px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:14px">
    <div style="flex:1;min-width:240px">
      <div style="font-weight:700;font-size:.85rem;color:var(--navy);display:flex;align-items:center;gap:6px">
        Total de Alunos Matriculados no Período
      </div>
      <p style="margin:3px 0 0;font-size:.78rem;color:var(--mut);line-height:1.3">
        Caso o número de alunos desta turma tenha mudado neste período, ajuste a quantidade ao lado.
      </p>
    </div>

    <!-- Stepper Compacto -->
    <div style="display:flex;align-items:center;gap:8px;background:var(--sf);border:1px solid var(--ln);padding:4px 10px;border-radius:8px">
      <button type="button" class="ghost" style="width:30px;height:30px;padding:0;font-size:1.1rem;font-weight:700;border-radius:6px;border:1px solid var(--ln)" onclick="alterarTotalAlunos(-1)">−</button>
      <input id="turma_total" type="number" min="1" max="999" value="15" style="width:62px;height:32px;text-align:center;font-weight:700;font-size:1.15rem;border:0;background:transparent;color:var(--ink)" oninput="onTotalAlunosInput(this.value)">
      <button type="button" class="ghost" style="width:30px;height:30px;padding:0;font-size:1.1rem;font-weight:700;border-radius:6px;border:1px solid var(--ln)" onclick="alterarTotalAlunos(1)">+</button>
      <span style="font-weight:600;font-size:.85rem;color:var(--mut);margin-left:2px">alunos</span>
    </div>
  </div>
</div>
```

---

### 3.4 Linha de Indicador e Campos Tricolores (`.ind` & `.ins`)

Cada critério pedagógico é composto por:
1. Número em círculo verde (`.num`).
2. Texto do critério pedagógico com badge de conferência.
3. Três campos de preenchimento com cores semânticas pastéis (Verde = Sim, Laranja = Parcial, Rosa = Não).
4. Notificação inteligente abaixo do item (ativada apenas quando os 3 campos estão preenchidos e a soma difere do total da turma).

```html
<div class="ind" id="ind_card_i1">
  <span class="num">1</span>
  <div style="grid-column: 2">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:12px;margin-bottom:8px">
      <b style="font-weight:600;font-size:.92rem;line-height:1.35;color:var(--ink)">Identifica e escreve o próprio nome</b>
      <div id="badge_i1">
        <span class="badge" style="margin:0;background:var(--gs);color:var(--gd);font-size:.74rem">✓ 15/15 alunos</span>
      </div>
    </div>

    <!-- 3 Campos Pastel -->
    <div class="ins" style="grid-column:unset;max-width:440px">
      <div class="a">
        <label>Sim</label>
        <input type="number" min="0" data-i="i1" data-j="0" value="2" oninput="onIndInput('i1')">
      </div>
      <div class="b">
        <label>Parcial</label>
        <input type="number" min="0" data-i="i1" data-j="1" value="3" oninput="onIndInput('i1')">
      </div>
      <div class="c">
        <label>Não</label>
        <input type="number" min="0" data-i="i1" data-j="2" value="10" oninput="onIndInput('i1')">
      </div>
    </div>

    <!-- Alerta Condicional: invisível quando correto; visível apenas se houver falta/excesso com 3 campos preenchidos -->
    <div id="alert_i1" class="ind-alert" style="margin-top:8px"></div>
  </div>
</div>
```

#### Alerta Inteligente de Divergência de Alunos
Quando os três campos foram preenchidos e a soma diverge da quantidade da turma no período:

```html
<!-- Quando faltam alunos (Alerta Laranja Suave) -->
<div style="display:flex;align-items:center;gap:8px;background:var(--os);color:var(--o);padding:7px 12px;border-radius:8px;font-size:.82rem;font-weight:600;border:1px solid rgba(244,123,32,0.25)">
  <svg style="width:16px;height:16px;flex-shrink:0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>
  <span>A soma informada é <b>12</b>. Para completar a turma de <b>15 alunos</b>, faltam <b>3</b> aluno(s).</span>
</div>

<!-- Quando passa do total de alunos (Alerta Rosa/Magenta Suave) -->
<div style="display:flex;align-items:center;gap:8px;background:var(--ps);color:var(--p);padding:7px 12px;border-radius:8px;font-size:.82rem;font-weight:600;border:1px solid rgba(232,0,95,0.25)">
  <svg style="width:16px;height:16px;flex-shrink:0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
  <span>A soma informada é <b>17</b> e ultrapassou o total da turma de <b>15 alunos</b> (+<b>2</b> a mais).</span>
</div>
```

---

### 3.5 Cartões de Indicadores-Chave (KPIs)

Utilizados no topo da área administrativa e relatórios para sintetizar o estado da rede municipal:

```html
<div class="kpis">
  <div class="kpi a">
    <b>20</b>
    <small>Escolas Monitoradas</small>
  </div>
  <div class="kpi b">
    <b>45</b>
    <small>Turmas no Ano</small>
  </div>
  <div class="kpi c">
    <b>38/45</b>
    <small>Turmas Preenchidas (84%)</small>
  </div>
  <div class="kpi d">
    <b>72%</b>
    <small>Taxa "Sim" (Pleno)</small>
  </div>
</div>
```

---

### 3.6 Gráficos e Visualização de Dados

#### Barra Segmentada Tricolor (`.bar` e `.print-stacked-bar`)
Representa a proporção das respostas nos critérios consolidados:

```html
<div class="bar" title="Sim: 72% · Parcial: 18% · Não: 10%">
  <i class="s" style="width:72%" title="Sim: 72%"></i>
  <i class="pa" style="width:18%" title="Parcial: 18%"></i>
  <i class="n" style="width:10%" title="Não: 10%"></i>
</div>
```

---

## 4. Motor de Impressão e Relatórios Oficiais (A4 Print Engine)

O arquivo `impressao.html` (e `relatorio.html`) implementa a especificação oficial de documentação da Secretaria Municipal de Educação de Lagoa da Canoa.

### 4.1 Estrutura de Folha A4 Oficial

```
+-------------------------------------------------------------+
| [LOGO PREFEITURA] |  ESTADO DE ALAGOAS                       |
|                   |  PREFEITURA MUNICIPAL DE LAGOA DA CANOA  |
|                   |  SECRETARIA MUNICIPAL DE EDUCAÇÃO        |
|                   |  GERÊNCIA DE ENSINO        [PÁGINA X DE Y|
+-------------------------------------------------------------+
| ==================== FAIXA TRICOLOR ======================= |
+-------------------------------------------------------------+
| TITULO DO RELATORIO & ESCOPO DA AVALIACAO                   |
+-------------------------------------------------------------+
| METADADOS: Ano | Período | Unidade Escolar | Data/Hora      |
+-------------------------------------------------------------+
| KPIS EXECUTIVOS: Escolas | Turmas | Alunos | % Sim          |
+-------------------------------------------------------------+
| DISTRIBUIÇÃO GERAL DAS RESPOSTAS (Gráfico de barras)        |
+-------------------------------------------------------------+
| POTENCIALIDADES (Top Sim) | NECESSIDADE DE APOIO (Top Não)  |
+-------------------------------------------------------------+
| DEMONSTRATIVO POR ESCOLA OU TURMA (Tabela analítica)        |
+-------------------------------------------------------------+
| RODAPÉ INSTITUCIONAL: Sistema de Monitoramento · Pág 1 de 2 |
+-------------------------------------------------------------+
```

### 4.2 Folha 2: Matriz Analítica por Indicador BNCC
1. **Tabela Completa dos 15 Indicadores:** Exibe contagens absolutas e percentuais de `Sim`, `Parcial`, `Não`, mini-barra visual de distribuição e classificação diagnóstica (`Adequado`, `Atenção`, `Prioritário`).
2. **Caixa de Encaminhamentos e Orientações Pedagógicas:** Orientações normativas para coordenação e professores baseadas na BNCC.
3. **Assinaturas Oficiais:**
   * Coordenação Pedagógica / Direção Escolar
   * Secretaria Municipal de Educação (Gerência de Ensino)
4. **CSS de Quebra de Página:**
   ```css
   @media print {
     @page {
       size: A4 portrait;
       margin: 12mm 15mm;
     }
     .a4-sheet {
       page-break-after: always;
       box-shadow: none;
       border: none;
       width: 100%;
       padding: 0;
     }
   }
   ```

---

## 5. Regras de Lógica e Arquitetura de Dados no Design

### 5.1 Função Universal de Matrícula: `getTurmaTotal(c, pid)`
Garante que todas as tabelas, resumos, contagens e relatórios exibam o total de alunos correto por período:

```javascript
function getTurmaTotal(c, pid) {
  if (!c) return 0;
  // 1. Se tem respostas salvas no período, extrai a soma exata das respostas
  if (pid && D.rec && D.rec[c.id] && D.rec[c.id][pid]) {
    const periodRec = D.rec[c.id][pid];
    for (const iid in periodRec) {
      const v = periodRec[iid];
      if (Array.isArray(v)) {
        const s = (+v[0] || 0) + (+v[1] || 0) + (+v[2] || 0);
        if (s > 0) return s;
      }
    }
  }
  // 2. Se foi ajustado em c.totals[pid]
  if (pid && c.totals && c.totals[pid]) {
    return +c.totals[pid];
  }
  // 3. Em "Todos os períodos", pega a matrícula ativa mais recente
  if (!pid) {
    const ps = yPer(yr());
    for (let i = ps.length - 1; i >= 0; i--) {
      const pId = ps[i].id;
      if (D.rec && D.rec[c.id] && D.rec[c.id][pId]) {
        for (const iid in D.rec[c.id][pId]) {
          const v = D.rec[c.id][pId][iid];
          if (Array.isArray(v)) {
            const s = (+v[0] || 0) + (+v[1] || 0) + (+v[2] || 0);
            if (s > 0) return s;
          }
        }
      }
      if (c.totals && c.totals[pId]) return +c.totals[pId];
    }
  }
  return +c.total || 0;
}
```

### 5.2 Validação Pré-Envio (*Save Guard*)
Ao clicar em **"Salvar preenchimento"**:
1. O sistema valida se todos os critérios com preenchimento possuem exatamente `Sim + Parcial + Não == Total da Turma no Período`.
2. Em caso de divergência, impede a gravação, lista os critérios pendentes e executa **scroll suave até o primeiro item com erro**:
   ```javascript
   const firstErrEl = document.getElementById("ind_card_" + badItems[0].id);
   if (firstErrEl) firstErrEl.scrollIntoView({ behavior: "smooth", block: "center" });
   ```
3. Atualiza instantaneamente a memória local e o `localStorage` para que a tela de impressão já abra sincronizada.

---

## 6. Acessibilidade (a11y) e Usabilidade

1. **Navegação por Teclado:**
   * Usuários podem transitar rapidamente entre campos `Sim`, `Parcial` e `Não` com a tecla `Tab`.
   * Pressionar `Enter` na tela de login autentica diretamente sem exigir clique no mouse.
2. **Contraste em Conformidade com WCAG 2.1 AA:**
   * O verde escuro (`#1F5C43`) e o navy (`#173F31`) garantem taxa de contraste superior a 7:1 contra superfícies brancas.
   * O fundo suave de campos pastéis (`--gs`, `--os`, `--ps`) reduz a fadiga visual durante preenchimentos longos de até 15 critérios por turma.
3. **Prevenção de Perda de Dados:**
   * Indicador visual de gravação pendente (`#sv`).
   * Fallback em fila sequencial de requisições (`Promise chain`) que impede conflitos de concorrência com o Google Sheets.

---
*Documentação atualizada e sincronizada com o código-fonte em produção.*
