# COMPONENTS · Grammar of a Broken Reality

Cada componente deve pertencer à mesma família, mas **não** parecer cópia da mesma caixa preta. O sistema tem três linguagens: **instrumentos** (HUD), **registros** (inventário) e **interferências** (diálogo/anomalia).

## 01 · HUD — SURVIVAL INSTRUMENT

### Intenção

Três sinais vitais concisos como um instrumento de campo, não como painel de nave espacial.

**Informações principais:** carga da lanterna, fôlego/stamina, vitalidade. Preservar rótulos em PT-BR, valores dinâmicos e ícones somente se tiverem função.

**Composição sugerida:**

```text
VOIDWALKERS  ─╴
LANTERNA      100%  ━━━━━━━━━━░
FÔLEGO        100%  ━━━━━━━━━━░
VITALIDADE     100  ━━━━━━━━━━░
```

O exemplo é conceitual, não posição obrigatória de cada item.

### Regras

- Um único grupo principal, espaçamento vertical coerente, rótulo alinhado à esquerda e valor à direita.
- Use trilho de medição fino e contraste seguro; a leitura deve sobreviver sem cor.
- Proporção: o painel deve parecer uma pequena ferramenta na periferia, nunca o protagonista visual.
- Evitar ornamentos redundantes (ícone + texto + título + logo + barra brilhante para a mesma informação).
- Feedback por alteração de valor deve ser sutil; feedback de **risco real** pode ter 1 destaque visível.
- Health e battery abaixo de limite crítico devem aumentar legibilidade, não piscar constantemente.
- No mobile, reservar espaço para polegares e controles de movimento.

### Estados para testar

100%, 50%, 1%, 0%, dano, regeneração, lanterna desligada, spam de sprint, abertura do inventário, respawn e resolução alterada.

## 02 · DIÁLOGO UNIVERSAL — THE WITNESS PANEL

**Componente âncora da identidade.** Ele precisa funcionar em 3 segundos de leitura, não somente em screenshots.

### Estrutura

```text
       [marca tinta / etiqueta curta do falante]
       A LUZ     ─╴
       Nem tudo que você lembra aconteceu aqui.

                         [próxima fala, se interativo]
```

**Escolha gráfica:** o painel pode ter fundo carvão suave para contraste, mas o corpo da frase fica em um campo limpo. A pincelada da referência atua como **sinal de autoria no cabeçalho**, não como fundo sujo do texto inteiro.

### Tipos — MESMA BASE, diferenças intencionais

| Tipo | Identidade | Comportamento |
|---|---|---|
| `normal` | osso + grafite, nome do falante | conversa ou memória explícita |
| `thought` | assinatura silenciosa, nome opcional | reflexão breve, não bloquear controles |
| `supernatural` | halo incompleto e acento `ghost` | presença da Luz/Void; distorção excepcional, não contínua |
| `system` | sem “voz”, estrutura seca | objetivos e notificações com maior prioridade funcional |

### APIs que o agente deve considerar

Separar **conteúdo** de **renderização**. Uma fila ideal suporta parâmetros sem exigir que gameplay manipule labels diretamente:

```lua
-- Interface conceitual; adaptar à arquitetura real do projeto.
DialogueService:Show({
    kind = "supernatural",
    speaker = "A LUZ",
    text = "Nem tudo que você lembra aconteceu aqui.",
    priority = 20,
    dismiss = "timed",
    duration = 4.5,
    player = localPlayer,
})
```

Não copiar a assinatura acima cegamente: primeiro identificar os contratos já existentes. **Não criar segunda fila concorrente.**

### Modos

- **Ambiental:** texto não modal, sem tirar controle de câmera ou movimento.
- **Interativo:** exige confirmação/continuação claramente identificada e acessível.
- **Urgente:** avisos críticos priorizados sem apagar permanentemente falas importantes.

### Robustez narrativa

- Falas do prólogo/árvore WP_003 são locais, não repetidas pelo servidor.
- Em solo não inventar fala de companheiros ausentes.
- Em trio não sincronizar artificialmente todas as memórias pessoais; manter progressão cooperativa validada.
- Evitar sobreposição entre diálogo e prompt “SIGA A LUZ”.
- Quando o jogador acelera/pula fala, garantir que cleanup e conclusão narrativa continuem.
- Fim de animação não deve determinar estado crítico de missão; estado real governa UI.

### Anti-padrões

Texto cinza em painel quase preto, nome ilegível em 9 px, serifa muito fina no mobile, typewriter lento sem skip, blur pesado em todo diálogo, três barras de “energia da entidade”, piscar de palavras essenciais.

## 03 · AVISO — THE INTERRUPT

Para `SIGA A LUZ`, `NÃO OLHE PARA TRÁS` e objetivo contextual.

A janela deve ser **curta, incisiva e de alta legibilidade**. Preferir tipografia com respiro, pequeno segmento de fenda, entrada discreta e saída suave.

- O evento pode ser sobrenatural; a função do texto continua informativa.
- Deve possuir cooldown e não competir com mensagens simultâneas.
- Não cobrir centro da mira/visão por tempo prolongado.
- Para avisos repetidos, aumentar clareza, não a intensidade de flash.

**Exemplo de gradação:**
- sistema cotidiano: label discreta;
- orientação: label clara com 1 traço;
- ameaça: acento de perigo e prioridade maior, sem estrobo.

## 04 · INVENTÁRIO — FIELD ARCHIVE

O inventário é um **arquivo de achados**, não um marketplace nem uma janela vazia gigante.

### Estrutura

```text
╭────────────────────────────────────────────────────╮
│ INVENTÁRIO                  03 ITENS       [×]     │
│ ─╴                                                 │
│ [Buscar item…                             ]        │
│                                                    │
│ [Item] [Item] [Item] [    ] [    ]                  │
│                                                    │
│ ITEM SELECIONADO                                   │
│ Descrição curta; ação clara quando aplicável.      │
╰────────────────────────────────────────────────────╯
```

- O estado `Nada guardado.` precisa parecer intencional; frase breve + hierarquia, não um vazio enorme.
- Campo de busca deve ser claramente editável, com placeholder e foco perceptível.
- Hotbar e grid devem falar mesma língua, mas não necessariamente duplicar posições.
- Fechar sempre acessível com mouse, Escape e toque (quando aplicável).
- Evitar texto gigante fantasma `PROCURAR OBJETO` atrás do modal.
- Ordem de foco/seleção deve manter sentido no gamepad.
- Não esconder itens reais por reestilizar/filtrar sem manter dados.

## 05 · AÇÕES — QUIET CONTROLS

Botões de Lanterna, Inventário, Correr, interação e prompts devem formar um pequeno vocabulário de ações.

- PC: hints contextuais elegantes, controlados pelo método de input efetivo.
- Mobile: botões touch com área suficiente e distância segura do movimento/câmera, sem ser blocos enormes.
- Gamepad: display de tecla contextual correto se houver suporte.
- Diferenciar visual de ação disponível/desabilitada/pressionada.
- Não colocar controles touch sobre a caixa de diálogo.
- Não forçar etiquetas literais `F` e `'` em telas mobile.

**Direção:** peso visual cresce com relevância da ação, não com a quantidade de bordas.

## 06 · MENUS, PARTY E LOJA

Se o pedido incluir outras telas, manter a família `Quiet Fracture`, mas respeitar contexto:

- Menu/Party: hierarquia social e estados claros (liderança, pronto, participantes).
- Loja: informação e legibilidade acima de “horror”; uma compra nunca deve ser visualmente enganosa.
- Cutscene: overlays mínimos, capazes de desaparecer sem bloquear câmera ou subtítulo.
- O Place do menu é distinto do da campanha: **não alterar outro Place por inferência**.

## 07 · COMPORTAMENTO ENTRE TELAS

Não precisa forçar coordenadas idênticas. Precisa preservar:

- famílias de borda, cor, tipografia e movimento;
- semântica das mesmas ações;
- prioridades visuais;
- clareza de estados.

**Desktop widescreen:** margem generosa, HUD periférica, diálogo em largura confortável e não esticado.

**Mobile landscape:** evitar conflito com thumb zones, joystick, chat, topbar e notch; preferir caixas compactas e textos maiores em relação ao painel.

**Mobile portrait:** tratar como layout próprio se suportado; jamais comprimir widescreen até texto impossível. Se o jogo for landscape-only, informar isso explicitamente e testar o caso realmente suportado.

## 08 · REGRA DE OURO

Uma captura sem UI pode ser bonita. Uma captura com UI deve permanecer bonita — **e o jogador deve poder agir sem pensar em onde tocar**.
