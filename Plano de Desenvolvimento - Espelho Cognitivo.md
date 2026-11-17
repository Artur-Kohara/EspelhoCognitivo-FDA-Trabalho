# Plano de Desenvolvimento — Extensão "Espelho Cognitivo"

**Disciplina:** Fundamentos do Desenvolvimento e da Aprendizagem (PED0058) — UnB  
**Turma:** 01 — 2/2026  
**Natureza do produto:** Técnica Aplicada (Atividade em grupo — 50 pontos) + Seminário Temático  
**Prazo estimado:** 1 semana (7 dias)  
**Dificuldade:** Média  
**Versão:** 1.0 — 17/11/2026

---

## 1. Visão geral

O **Espelho Cognitivo** é uma extensão de navegador que cria uma **pausa intencional de cerca de 10 segundos** no momento em que o estudante abre o ChatGPT. Antes de digitar a primeira mensagem, um micro-check-in pergunta qual é a intenção daquele acesso — **entender um conceito**, **revisar algo já feito** ou **terminar uma tarefa rapidamente** — e, a partir da resposta, devolve uma **pequena reflexão** que convida a um uso mais consciente da IA.

Não há banco de dados, estatísticas, contas de usuário nem sistemas complexos. O valor do produto está justamente na **simplicidade**: um gesto breve de consciência antes da interação automatizada.

> **Princípio de design:** interromper o uso automático *sem bloquear* o estudo. A extensão é um espelho, não um bloqueio — sempre é possível fechá-la e seguir em frente.

---

## 2. Contexto e justificativa

A proposta nasceu de uma pesquisa realizada pelo grupo sobre **como o uso de IA tem impactado o cotidiano de estudo de estudantes universitários**. O diagnóstico que motivou o produto é o da **automatização do recorrer à IA**: abrir o ChatGPT deixou de ser uma decisão e passou a ser um reflexo, especialmente em momentos de pressa, dúvida ou tarefa pendente.

Na disciplina, essa discussão se conecta diretamente a:

- **Objetivos gerais:** compreender as dimensões cognitiva, afetivo-emocional e social do desenvolvimento e reconhecer os aspectos éticos e políticos na formação de educadores;
- **Unidade 3 — Temáticas e perspectivas atuais:** educação, diversidade, corpo, decolonialidade e interseccionalidade, ampliadas pelo debate contemporâneo sobre tecnologia, subjetividade e autoria;
- **Critérios de avaliação:** domínio das teorias e postura crítica e sensível às questões do campo.

Assim, a extensão funciona como uma **técnica aplicada em sala de aula**: um artefato concreto que materializa conceitos abstratos (metacognição, autorregulação, autoria) e pode ser usado pelo professor como disparador de discussão ética sobre o uso de IA na formação de educadores.

---

## 3. Fundamentação teórica (síntese para o seminário)

| Eixo teórico | O que fundamenta no produto | Autores de referência |
|---|---|---|
| **Metacognição e autorregulação da aprendizagem** | O check-in leva o estudante a nomear sua intenção *antes* de agir — monitoramento e planejamento do próprio processo de aprendizagem. | Flavell e Zimmerman (referências complementares); Luria e Piaget (bibliografia da disciplina) |
| **Construção ativa do conhecimento** | A reflexão incentiva explicar com as próprias palavras, comparar e verificar, em vez de apenas receber a resposta pronta. | Piaget — *Epistemologia Genética* |
| **Mediação e zona de desenvolvimento proximal** | A IA é reposicionada como mediação que deve ser integrada ao processo do estudante, não como substituição do seu esforço. | Vygotsky — *Psicologia Pedagógica* |
| **Subjetividade, autonomia e autoria** | A pausa é um gesto ético: impede que a produção do texto seja inteiramente delegada, preservando a voz e a responsabilidade do estudante. | Vygotsky, Wallon; eixo ético da ementa |
| **Dimensão afetivo-emocional** | O tom da interface é acolhedor e curioso, nunca punitivo — o intervalo é de acolhimento, não de cobrança. | Wallon — *Objetivos e Métodos da Psicologia* |

> **Nota acadêmica:** Flavell e Zimmerman não constam na bibliografia básica do plano de ensino e devem ser tratados como **leituras complementares**, com referência explícita e validação pelo grupo/professores. Piaget, Vygotsky, Wallon e Luria fazem parte da bibliografia da disciplina e devem ser a espinha dorsal da fundamentação. Todas as citações e paráfrases seguem as normas do plano de ensino (com autoria, fonte e data de acesso quando aplicável).

---

## 4. Objetivos

### Geral
Criar uma extensão de navegador simples que interrompa o uso reflexo da IA e convide o estudante a reconhecer sua intenção antes de interagir, fortalecendo autonomia e autoria no processo de aprendizagem.

### Específicos
1. Exibir automaticamente um micro-check-in de ~10 s ao abrir o ChatGPT.
2. Oferecer três intenções claras e mutuamente exclusivas.
3. Apresentar uma reflexão curta, personalizada para cada intenção selecionada.
4. Permitir dispensar a interface a qualquer momento, sem impedir o uso da ferramenta.
5. Executar localmente, sem coleta de dados, servidores ou credenciais.
6. Documentar o produto e preparar a apresentação para o seminário (técnica aplicada + reflexão crítica).

---

## 5. Escopo

### MVP (obrigatório — ChatGPT)
- Extensão compatível com **Manifest V3** (Chrome/Edge).
- Injeção de um *overlay* na página do ChatGPT (`chatgpt.com` e `chat.openai.com`).
- Check-in com 3 opções + reflexão correspondente.
- Botão de fechar e botão "Entendi, seguir" ao final da reflexão.
- Arquitetura 100% local: `manifest.json` + HTML + CSS + JavaScript.

### Stretch goal (se houver tempo — dias 6 e 7)
- Adaptação para **Claude** (`claude.ai`) e **Gemini** (`gemini.google.com`) via novos *match patterns* e ajustes de posicionamento/seletores.
- Prefixo de configuração único para os três provedores.

### Explicitamente fora de escopo
- Banco de dados, analytics, login, sincronização entre dispositivos.
- Histórico de check-ins, gráficos, métricas de uso.
- Bloqueio do ChatGPT, temporizadores punitivos ou notificações push.
- Publicação na Chrome Web Store (a entrega é o código-fonte + demonstração).

---

## 6. Requisitos

### Funcionais
| ID | Requisito |
|---|---|
| RF-01 | Ao carregar uma página do ChatGPT, o overlay aparece em até 1 segundo. |
| RF-02 | O overlay apresenta a pergunta: "Qual é o seu objetivo agora?" e 3 botões. |
| RF-03 | Uma barra de progresso visual sugere o intervalo de ~10 s (meta de leitura, não bloqueio). |
| RF-04 | Ao selecionar uma opção, exibe a reflexão correspondente e um botão de conclusão. |
| RF-05 | O botão "Fechar" dispensa o overlay imediatamente em qualquer etapa. |
| RF-06 | Durante a mesma sessão/aba, o check-in não reaparece ao trocar de conversa (SPA). |
| RF-07 | A extensão não interfere no campo de texto nem nos controles do ChatGPT. |

### Não funcionais
| ID | Requisito |
|---|---|
| RNF-01 | Sem permissões de rede; nenhum dado enviado para fora do navegador. |
| RNF-02 | Interface acessível: contraste mínimo 4.5:1, navegação por teclado, foco visível, `aria-live` na reflexão. |
| RNF-03 | Layout responsivo (desktop e janela estreita), com `z-index` alto o suficiente para sobressair ao layout do ChatGPT. |
| RNF-04 | Código legível e comentado, pensado para ser apresentado em sala. |
| RNF-05 | Instalação via "Carregar descompactada" em `chrome://extensions`, sem build. |

---

## 7. Design da experiência e fluxo do usuário

```
[Abre o ChatGPT]
        ↓
[Overlay aparece — pergunta + 3 opções + barra de ~10 s]
        ↓
[Estudante clica em uma intenção]
        ↓
[Reflexão curta aparece (mesmo overlay, troca de conteúdo)]
        ↓
[Botão "Entendi, seguir" → overlay desaparece]
        ↓
[Estudante interage com o ChatGPT normalmente]
```

**Decisões de UX:**
- O overlay é **central e compacto**, com fundo levemente escurecido — visível, mas não invasivo.
- O fechamento é sempre possível (botão "×" e tecla `Esc`).
- A barra de progresso é **informativa**, não impeditiva: se o estudante responder em 3 s, a reflexão aparece na hora.
- A reflexão usa **segunda pessoa e tom convidativo** ("Que tal...?", "O que você...?"), nunca imperativo punitivo.
- O tempo total alvo (~10 s) é validado no teste com colegas (dia 5).

### Conteúdo das reflexões (proposta inicial)

| Intenção escolhida | Reflexão exibida |
|---|---|
| **Entender um conceito** | "Ótimo. Peça exemplos e, depois, tente explicar com as suas próprias palavras. É nesse esforço que o conceito se torna seu." |
| **Revisar algo que já fez** | "Compare a resposta da IA com o que você produziu. O que acrescentou? O que você manteria — ou mudaria — por ser seu?" |
| **Terminar rapidamente** | "A pressa é real. Antes de copiar, registre uma linha do que você decidiu: assim a autoria do processo continua sendo sua." |

> As reflexões devem ser revisadas coletivamente no dia 1 para garantir coerência com a fundamentação e com o tom acolhedor definido no eixo afetivo-emocional.

---

## 8. Arquitetura e tecnologias

| Camada | Tecnologia / arquivo | Papel |
|---|---|---|
| Manifesto | `manifest.json` | Declara versão MV3, permissões mínimas, *host permissions* e content script. |
| Injeção | `content.js` | Detecta a página, cria o DOM do overlay, gerencia estados e eventos. |
| Apresentação | `style.css` | Estilos do overlay, animação da barra, responsividade e acessibilidade. |
| Estrutura | `index.html` (template) | Modelo opcional do marcação injetada (ou HTML criado via `innerHTML` no content script). |
| Persistência leve | `sessionStorage` (opcional) | Evita reaparecer ao trocar de conversa na mesma aba — sem dados pessoais. |
| Ícone | `assets/icon.svg` | Identidade visual simples do produto. |

**Permissões mínimas:** `activeTab` e `scripting` (ou apenas `content_scripts` declarado com *matches*, sem permissões extras). Nada de `storage` persistente, `tabs` amplo ou acesso a sites externos.

### Estrutura de pastas sugerida

```
espelho-cognitivo/
├── manifest.json
├── content.js
├── style.css
├── assets/
│   └── icon.svg
├── docs/
│   ├── fundamentacao.md
│   └── roteiro-seminario.md
└── README.md   # como instalar, como testar, equipe, referências
```

---

## 9. Cronograma — 1 semana

| Dia | Foco | Atividades principais | Entrega do dia |
|---|---|---|---|
| **1** | Fundamentação & design | Fechar o diagnóstico da pesquisa; revisar as 3 reflexões; esboçar o fluxo em papel/Figma; dividir tarefas do grupo. | Fluxo validado + textos das reflexões |
| **2** | Estrutura & interface | Criar `manifest.json`, template HTML e `style.css`; posicionar o overlay sobre o ChatGPT; ajustar contraste e responsividade. | Overlay estático aparecendo na página |
| **3** | Lógica & interação | Implementar `content.js`: estados (pergunta → reflexão), eventos dos botões, barra de ~10 s, `Esc`/fechar, controle de reaparição na SPA. | Check-in funcional de ponta a ponta |
| **4** | Refinamento & testes técnicos | Testar em Chrome/Edge; corrigir `z-index`, foco por teclado, `aria-live`; conferir que o campo do ChatGPT continua utilizável; testar instalação via "Carregar descompactada". | MVP estável |
| **5** | Teste com usuários & ajustes | Aplicar o check-in em 3–5 colegas; cronometrar o tempo médio (~10 s); perguntar clareza das reflexões e incômodo da interrupção; ajustar textos/tempo. | Relato de testes + ajustes aplicados |
| **6** | Stretch goal | Adicionar *match patterns* para Claude e Gemini; ajustar posicionamento se o layout dos sites divergir. Se não der tempo, registrar como trabalho futuro. | Compatibilidade ampliada (ou decidido adiar) |
| **7** | Documentação & seminário | Finalizar `README.md`, `fundamentacao.md` e roteiro; gravar vídeo demo curto; preparar slides com problema → técnica → fundamentação → demonstração → discussão ética. Enviar o produto. | Pacote completo para entrega |

**Marco de risco:** se algo atrasar, o **MVP (dia 4)** é a prioridade inegociável. O stretch goal dos dias 6–7 é descartável sem prejuízo da avaliação.

---

## 10. Divisão de tarefas sugerida (grupo)

> Ajustar conforme o tamanho real do grupo. A lógica de junto com a fundamentação evita "código sem teoria".

- **Subgrupo A — Conteúdo e teoria:** diagnóstico da pesquisa, reflexões, fundamentação, roteiro do seminário e referências.
- **Subgrupo B — Interface:** HTML/CSS, identidade visual, acessibilidade e responsividade.
- **Subgrupo C — Lógica e testes:** `content.js`, manifest, testes técnicos e testes com colegas.
- **Todos:** revisão coletiva nos dias 1, 5 e 7; apresentação no seminário.

---

## 11. Entregáveis (alinhados à avaliação da disciplina)

1. **Produto (técnica aplicada):** pasta da extensão com código-fonte e README de instalação.
2. **Demonstração:** vídeo curto (1–2 min) ou live mostrando a extensão em ação no ChatGPT.
3. **Documento de fundamentação:** síntese das seções 2 e 3, com referências em ABNT.
4. **Seminário temático:** apresentação conectando a técnica às unidades da disciplina e ao debate ético sobre IA, subjetividade, autonomia e autoria.
5. **Relato de testes com usuários:** evidência de que o produto foi experimentado e ajustado (reforça o critério de postura crítica e sensível).

---

## 12. Critérios de sucesso

- [ ] A extensão instala e aparece corretamente ao abrir o ChatGPT.
- [ ] O check-in + reflexão leva, em média, ~10 s no teste com colegas.
- [ ] É possível fechar/pular sem travar o uso da ferramenta.
- [ ] Nenhum dado é coletado ou enviado.
- [ ] A interface é legível, navegável por teclado e funciona em janela estreita.
- [ ] A fundamentação cita corretamente Piaget, Vygotsky e Wallon (bibliografia da disciplina) e sinaliza leituras complementares.
- [ ] A apresentação articula produto, teoria e ética — não apenas demonstra a ferramenta.
- [ ] Tudo entregue no prazo previsto.

---

## 13. Riscos e mitigação

| Risco | Impacto | Mitigação |
|---|---|---|
| O layout do ChatGPT muda e o overlay quebra | Médio | Usar posicionamento `fixed` independente de seletores internos; testar no dia 4. |
| O overlay é percebido como incômodo | Médio | Manter fechamento fácil, tom acolhedor e validar com colegas no dia 5. |
| A reflexão soa "moralizante" | Alto | Revisar os textos no dia 1 com o eixo afetivo-emocional de Wallon; preferir convites a imperativos. |
| Atraso no stretch goal (Claude/Gemini) | Baixo | Tratar como extensão opcional; o MVP já atende à avaliação. |
| Falta de clareza nas referências | Médio | Separar bibliografia básica da disciplina e complementares; validar com os professores. |
| Extensão reaparece ao trocar de conversa | Baixo | Usar `sessionStorage` como controle de sessão (dia 3). |

---

## 14. Trabalhos futuros (fora deste plano)

- Versões para Claude e Gemini consolidadas em um único manifesto.
- Preferência "não mostrar hoje" via `localStorage` (ainda sem servidor).
- Reflexões sazonais (ex.: período de prova) escritas pelos próprios estudantes.
- Tradução para inglês e estudio de uso em outras disciplinas.
- Pesquisa qualitativa sobre o efeito da pausa na autoria das produções — possível desdobramento em monografia.

---

## 15. Referências (base — completar em ABNT na entrega)

- Dessen, M. A., & Costa Jr., A. L. (Orgs.). (2005). *A ciência do desenvolvimento humano: Tendências atuais e perspectivas futuras*. Artmed.
- Luria, A. R. (1990). *Desenvolvimento cognitivo*. Ícone.
- Piaget, J. (1992). *Os seis estudos em Psicologia*. Forense Universitária.
- Vygotsky, L. S. (2001). *Psicologia pedagógica*. Martins Fontes.
- Wallon, H. (1963). *Objetivos e métodos da psicologia*. Editorial Estampa.
- Gratiot-Alfandéry, H. (2010). *Henri Wallon*. Fundação Joaquim Nabuco, Editora Massangana.

**Complementares (validar com a equipe docente):**
- Flavell, J. H. (1979). Metacognition and cognitive monitoring. *American Psychologist, 34*(10), 906–911.
- Zimmerman, B. J. (2002). Becoming a self-regulated learner. *Theory into Practice, 41*(2), 64–70.

> Consultas a sites e documentação técnica (ex.: Chrome Extensions — Manifest V3) devem registrar o endereço e a data de acesso, conforme as normas do plano de ensino.

---

**Próximo passo imediato:** validar o fluxo e os textos das reflexões (dia 1) e criar a estrutura inicial da extensão (`manifest.json`, `content.js`, `style.css`) na pasta do projeto.
