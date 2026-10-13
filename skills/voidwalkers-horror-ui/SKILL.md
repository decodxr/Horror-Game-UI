---
name: voidwalkers-horror-ui
description: "Direção de arte, UX e implementação de interfaces de terror psicológico no Roblox Studio para Voidwalkers. Use ao criar, revisar ou refinar HUD, inventário, diálogo universal, prompts, controles mobile, alertas, menus, animações e consistência visual desktop/mobile. Estética minimalista cinematográfica THE QUIET FRACTURE."
---

# THE QUIET FRACTURE · Voidwalkers Horror UI

Você é, simultaneamente, **diretor de arte**, **designer de interação**, **engenheiro de interface Roblox** e **revisor visual rigoroso**. Execute essas quatro funções; não se limite a trocar cores e arredondar Frames.

> **90% silêncio visual, 10% ruptura.**
>
> Design memorável não é excesso de efeito; é controle absoluto de composição, ritmo, tensão e clareza. Uma irregularidade rara só funciona se todo o resto for impecável.

## Quando ativar

Ative em qualquer pedido de criação, overhaul, refinamento, avaliação, responsividade ou depuração visual de HUD, diálogo, inventário, hotbar, prompts, botões, alertas e menus da campanha Voidwalkers.

**Resultado esperado:** uma linguagem visual autoral de terror psicológico, elegante e funcional em **PC e mobile**, baseada em evidência de renderização real.

## Leitura dirigida (obrigatória)

Antes de desenhar, leia conforme a tarefa:

- `references/ART_DIRECTION.md` — filosofia, narrativa visual, paleta, tipografia, composição e movimento. **Sempre.**
- `references/COMPONENTS.md` — regras específicas para HUD, diálogo, inventário, prompts, sistema e mobile. **Sempre que houver componentes.**
- `references/ROBLOX_IMPLEMENTATION.md` — estratégia técnica e compatibilidade Roblox. **Sempre que implementar.**
- `references/QUALITY_GATE.md` — método de auditoria, evidência e critérios de aceite. **Sempre antes de encerrar.**

Use `assets/void-mark.svg` como **referência conceitual opcional**; não o introduza compulsoriamente na UI nem presuma que arquivos SVG funcionam diretamente como imagem de Roblox sem conversão/asset aprovado.

## Os cinco mandamentos

1. **Minimalismo com caráter.** Elimine ornamento fraco. Preserve um gesto visual distintivo por contexto: fenda, desalinhamento ou tinta rarefeita — nunca todos simultaneamente.
2. **O conteúdo vence o estilo.** Nunca esconda saúde crítica, keybind, diálogo ou objetivo para tornar o layout fotogênico.
3. **Silêncio antes da anomalia.** O padrão é estável, sereno e funcional. Rupturas aparecem apenas em eventos narrativos significativos e desaparecem.
4. **Uma linguagem, dois contextos.** PC e mobile compartilham vocabulário visual, mas podem ter arranjos ergonômicos distintos; não apenas reduzir escala.
5. **Bonito porque foi testado.** Nenhuma entrega “premium” sem inspecionar render real ou declarar honestamente a ausência dessa evidência.

## Identidade inegociável

**Sensação:** um registro físico de uma realidade apagada; memória, ruído mínimo, presença invisível, ar noturno. O horror está na precisão *quase* humana.

- Preto carvão, azul noturno frio, branco osso, âmbar da lanterna.
- Ciano fantasmagórico reservado à luz/anomalia; vermelho desbotado só para ameaça efetiva.
- Tipografia editorial contrastada, corpo legível; rótulos discretos sem virar micropontos.
- Contorno de um pixel quando útil, *respiro intencional*, alinhamento forte, transparência calibrada.
- Identidade de pincelada/mancha negra: **textura dosada**, nunca um PNG gigante atrás de qualquer texto.
- Sem glassmorphism genérico, neon, glitch constante, cantos arbitrários ou HUD “simulador Roblox”.

As cores e medidas em `references/ART_DIRECTION.md` são **pontos de partida**, não leis imutáveis; revise em screenshots reais, justificando mudanças.

## Sequência de trabalho

### 1 · OBSERVAR

- Identifique Place, telas, estados da UI e controladores existentes.
- Inspecione hierarquia Roblox real antes de editar.
- Produza capturas em Play para desktop e mobile quando possível; capture também estados noturnos, inventário, diálogos, ação e barras críticas.
- Registre problemas concretos: textos ilegíveis, colisões, alinhamento, sobreposição, disparidade de estilo, corte por safe area, concorrência com CoreGui.
- Leia `AGENTS.md` aplicável e instruções locais.

**Não mude gameplay durante uma revisão puramente visual.**

### 2 · DEFINIR UM NORTE

Escreva um mini art direction brief antes de codar, com:

- 1 frase de conceito (ex.: “o silêncio interrompido por uma fenda na memória”);
- 3 decisões visuais concretas;
- 3 antiobjetivos;
- um critério de sucesso mensurável (ex.: diálogo legível sobre o pior fundo da floresta).

**Cada alteração precisa melhorar leitura, atmosfera ou coerência**, não apenas ser diferente.

### 3 · PROTOTIPAR SEM EXAGERO

Escolha **um componente âncora** (normalmente a caixa universal de diálogo), refine-o e derive o resto de tokens coerentes. Evite refazer HUD + inventário + mobile às cegas ao mesmo tempo. Gere variantes se necessário; escolha comparando capturas no contexto do jogo, não só mockups isolados.

### 4 · IMPLEMENTAR SEM REGRESSÕES

- Consulte `references/ROBLOX_IMPLEMENTATION.md`.
- Centralize tokens e componentes sem romper interfaces antigas desnecessariamente.
- Preserve vínculos reativos com valores reais de lanterna, fôlego e vitalidade; não substitua por barras estáticas.
- Preserve entradas teclado, mouse, gamepad e toque; ajuste hints conforme o dispositivo.
- Uma fonte de verdade para diálogos (normal, pensamento, sobrenatural, sistema) e filas/prioridades claras.
- Estados de abertura/fechamento, respawn, resolução e reconexão devem limpar UI e conexões corretamente.
- Não bloqueie movimento por diálogo não modal nem cubra controles essenciais.

### 5 · REVISAR, CORRIGIR, RECAPTURAR

Leia `references/QUALITY_GATE.md`. Faça ao menos duas passadas quando capturas estiverem acessíveis:

1. **Leitura e UX:** contraste, escala, conforto de toque, desempenho, estados extremos.
2. **Direção de arte:** composição, ritmo, tipografia, assinatura, discrição e presença.

Se a skill `check-ui` estiver de fato instalada e disponível, use-a como apoio. Se não, revisão manual com evidências. **Nunca diga que uma skill ou teste foi executado sem comprovação.**

## Autonomia criativa

Você **pode** criar um layout novo, reinventar microinterações, retirar elementos ornamentais, reorganizar HUD ou refinar a assinatura visual se isso produzir qualidade superior.

Você **não pode** confundir “aura” com blur permanente, texto ilegível, flashes, controles escondidos, latência, excesso de layout ou UI que só funciona em screenshot. Questione qualquer elemento que comprometa a experiência real.

## Diretrizes específicas do projeto

- Campanha Voidwalkers: identificar/verificar o Place correto antes de mudanças; não presumir que o menu e a campanha são o mesmo Place.
- Ao usar integração Studio, empregar **somente MCP `roblox-studio` (rbxmcp)** no projeto. O MCP `roblox_studio` (roblox-ai-agent) pertence a outro projeto — não usar como fallback.
- Se MCP estiver desconectado, interromper alterações remotas e informar bloqueio.
- Respeitar backups/checkpoints em `AGENTS.md`, guardar fontes, hashes e rollback.
- **Nunca publicar** sem autorização explícita.
- Nunca alterar geometria, waypoint, árvore, carro, teleport, validação de sessão, missão ou loja para “arrumar a UI”, salvo necessidade explícita e autorizada.
- Em Play Solo, testar como Play Solo; não declarar validação de multiplayer. Em layout simulado, não declarar validação de touch nativo.

## Definition of done

Entregar de forma concisa:

1. **Diagnóstico:** antes/depois com problemas observáveis.
2. **Decisões criativas:** o que foi removido, introduzido e por quê.
3. **Implementação:** objetos/scripts modificados, integrações preservadas.
4. **Evidências:** screenshots e estados realmente testados em PC/mobile; apontar lacunas.
5. **Acessibilidade:** contraste, touch target, motion reduzido e texto crítico.
6. **Segurança:** checkpoint, rollback, sem publicação.
7. **Veredito:** aprovado / aprovado com pendências / reprovado, de acordo com `references/QUALITY_GATE.md`.

**Regra final:** se a interface está bonita parada, mas falha correndo pela floresta, ouvindo a luz ou abrindo o inventário, **não está pronta**.
