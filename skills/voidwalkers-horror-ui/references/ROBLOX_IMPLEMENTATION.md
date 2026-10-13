# ROBLOX IMPLEMENTATION · Engineering Without Breaking the Horror

Este documento é um guia para quem implementa a estética no Roblox. **Não presume APIs internas, hierarquias ou nomes de controladores que não foram inspecionados.**

## 01 · Inspeção antes do primeiro write

1. Confirmar Place correto e modo Edit/Play no Roblox Studio.
2. Ler as instruções locais/AGENTS.md; verificar backups existentes e estratégia de rollback.
3. Identificar PlayerGui/StarterGui, scripts que geram UI dinamicamente, ScreenGuis duplicadas, módulos de inventário, valores reativos e input.
4. Mapear dependências de lanterna, stamina, vida, quest, diálogos do prólogo, interação, hotbar e respawn.
5. Conferir se screenshots representam **estado atual do Studio**, não pacote entregue anteriormente.
6. Alterar um subsistema por vez e comparar visualmente.

## 02 · Tools e escopo do projeto

- Use apenas o MCP **`roblox-studio`** (rbxmcp) autorizado para o Voidwalkers.
- **Nunca** usar o MCP `roblox_studio` do outro projeto `roblox-ai-agent` como fallback.
- Quando MCP desconectado: relatar o bloqueio e preparar patch local, sem afirmar integração.
- Não publicar o jogo. Não editar Place do menu se a tarefa é só campanha.
- Manter lógica de progressão/servidores reservados e atribuição de sessões intacta; estética é camada de apresentação.
- Não escrever operações destrutivas sobre assets sem checkpoint e consentimento.

## 03 · Arquitetura preferida

Estruture a UI em **tema**, **componentes** e **binders** de estado, com contratos reais existentes. Exemplo conceitual:

```text
ReplicatedStorage/
  Shared/
    UITheme                    -- tokens e semântica
    UIComponents/              -- factories reutilizáveis, se couber
StarterPlayerScripts/
  UI/
    HUDController              -- consumo de estado de gameplay
    DialoguePresenter          -- exibição de fila existente
    PromptPresenter
    InventoryPresenter
```

**Não criar automaticamente essa hierarquia.** Descubra qual já existe e refatore com o menor número de mudanças. Priorize módulos reutilizáveis sem clonar controladores ativos.

### Tema como dados

Exemplo de constantes LuaU (valores iniciais, ajuste após captura real):

```lua
local Theme = {
    Colors = {
        Void = Color3.fromRGB(7, 11, 13),
        Carbon = Color3.fromRGB(16, 23, 25),
        Ash = Color3.fromRGB(30, 40, 41),
        Bone = Color3.fromRGB(231, 228, 218),
        Mist = Color3.fromRGB(174, 185, 182),
        Ghost = Color3.fromRGB(136, 201, 197),
        Lantern = Color3.fromRGB(218, 193, 139),
        Wound = Color3.fromRGB(138, 76, 81),
    },
    Radius = { Subtle = 3, Card = 5 },
    Motion = { Fast = 0.18, Enter = 0.28, Anomaly = 0.55 },
}
return Theme
```

Não tornar um módulo de tokens dependente de render, input ou servidor.

## 04 · Layout responsivo sem fantasia

- Preferir `UDim2` baseado em zonas relativas + limites mínimos/máximos verificados no viewport.
- `UIScale`, `UIListLayout`, `UIPadding`, `UITextSizeConstraint`, `UIAspectRatioConstraint` são opções; escolher conscientemente para cada caso, e verificar efeitos combinados.
- **Não** usar somente `Scale` indiscriminado: texto/target pode encolher de forma inacessível.
- `AutomaticSize` pode ajudar conteúdo dinâmico; verificar com quebra de texto, tamanho máximo e diálogo multilinha.
- Respeitar áreas seguras e topbar/CoreGui conforme os mecanismos disponíveis na versão do Studio, sem assumir que desabilitar inset é solução.
- Não criar touchscreen gigante sobre o joystick nativo ou área de câmera.
- Revisar semântica e input com `UserInputService`, `ContextActionService` e/ou controladores já usados no projeto; não instalar teclas duplicadas.
- Alterações de resolução/orientação devem recalcular layout onde preciso.
- Testar fonte/tamanho em texto PT-BR mais longo, não apenas "OK".

## 05 · Input e acessibilidade

**PC:** teclado + mouse; gamepad se o jogo tiver suporte real.

**Mobile:** confirmar tap/touch real além do emulador/layout fixture. Botões usados continuamente requerem área tocável confortável. Não sobrepor zona do polegar direito.

**Crítico:** rotular informações de vida, bateria e ações sem depender apenas de cor ou movimento.

**Movimento reduzido:** desligar tremor, glitch e micro-oscilação, mantendo estado visual final e narrativa legíveis.

**Foco:** fechar inventário com `Esc`/botão, respeitar seleção de campos de texto e gamepad; não roubar teclado durante digitação.

## 06 · Diálogo e eventos locais

- Reusar a fonte de verdade do sistema universal de diálogo.
- Preferir um apresentador `LocalScript` para UI particular e sinais de estado validados pelo servidor quando afetarem progressão.
- Áudio/legenda de memórias diferentes devem respeitar audiência do evento.
- Em conexão perdida, respawn, teleporte, encerramento da cena: limpar tweens, eventos, blur, etiquetas e instâncias temporárias.
- `Typewriter` é estética opcional; não prender gameplay nem tornar skip inacessível.
- Diálogos concorrentes devem ter prioridade/fila ou regra de substituição clara.
- Mudança visual de texto não deve ser tratada como prova de conclusão de missão.

## 07 · Performance e ciclo de vida

- Não instanciar nova ScreenGui ou UIGradient por frame.
- Não criar novas Tween instâncias em loop de atualização de stamina se o alvo mudou irrelevante.
- Desconectar listeners ao destruir UI e não multiplicar binds após respawn.
- Evitar `Heartbeat` para layout estático; atualizar por sinais de mudança e resize quando disponível.
- Otimizar gradientes, blur e texturas para aparelhos fracos; objetos decorativos só se tiverem ganho estético real.
- Evitar efeitos que dependam de fontes/assets externos sem confirmar permissões, disponibilidade e fallback.
- Não mover scripts de gameplay só por conveniência de temas.

## 08 · Patch seguro

Faça mudança incremental:

```text
inspecionar -> preservar fonte + hash -> alterar -> verificar sintaxe
-> Play -> screenshot -> comparar -> corrigir -> checkpoint
```

Se o Studio MCP não oferecer Play real, relatar como teste pendente e fornecer passos manuais. Não usar logs de compilação como substituto de experiência visual.

## 09 · Por que "UI bonita" falha

Um layout pode estar perfeito em 1548×614 e ilegível no celular. Outro funciona na floresta escura com lanterna cheia, mas desaparece sobre fogueira brilhante. Outro parece premium até a barra cair para 1% e o número ser cortado.

**Teste interações e extremos**. Beleza sem robustez é um mockup, não uma interface de jogo.
