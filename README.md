# THE QUIET FRACTURE
### Voidwalkers Horror UI — an agent skill for cinematic psychological-horror interfaces

> **O horror não grita na interface. Ele aparece quando algo perfeitamente organizado deixa de fazer sentido.**

Uma skill de direção de arte e engenharia de UI para o **Voidwalkers** (Roblox). Não é um pacote de HUD pronta, nem uma coleção de efeitos neon: é um método de criação, implementação e revisão para desenhar interfaces que parecem pertencer à realidade quebrada do jogo.

**Assinatura:** **90% silêncio visual · 10% ruptura.**

### O que ela entrega

- **Direção de arte autoral:** tipografia editorial, composição assimétrica controlada, espaços vazios intencionais, tinta e fraturas discretas.
- **Componentes concretos:** HUD de sobrevivência, diálogos universais, inventário, prompts, objetivos, controles mobile e estados de ameaça.
- **Sistema visual verificável:** tokens sugeridos, estados, motion, regras de contraste e anti-padrões.
- **Implementação responsável em Roblox:** arquitetura reutilizável, compatibilidade PC/mobile, separação de apresentação e lógica, performance.
- **Quality gate:** ciclo capturar → criticar → corrigir → recapturar; evidências de Play, pendências explicitadas.

## Instale no Codex

No terminal:

```sh
npx skills add decodxr/Horror-Game-UI --skill voidwalkers-horror-ui
```

Selecione **Codex** e a opção global se quiser ter a skill disponível em qualquer projeto. Reinicie/retome o Codex depois da instalação:

```sh
codex resume --last
```

Na conversa com o Codex:

```text
Use $voidwalkers-horror-ui para dirigir uma revisão premium da UI da campanha
Voidwalkers. Inspecione o estado real pelo MCP roblox-studio, capture em Play,
refine em ciclos e preserve todos os sistemas de gameplay. Não publique.
```

**Importante:** a skill fornece instruções; não instala modelos no Roblox Studio, não altera Places e não garante que MCP ou Play estejam conectados. Seu agente continua responsável por verificar as ferramentas disponíveis e registrar testes realmente executados.

## Estrutura

```text
skills/
└── voidwalkers-horror-ui/
    ├── SKILL.md                       # Orquestração e padrões obrigatórios
    ├── references/
    │   ├── ART_DIRECTION.md           # A estética e a assinatura Voidwalkers
    │   ├── COMPONENTS.md              # HUD, diálogos, inventário e prompts
    │   ├── ROBLOX_IMPLEMENTATION.md   # Engenharia e adaptação PC/mobile
    │   └── QUALITY_GATE.md            # Critérios, capturas e revisão
    └── assets/
        └── void-mark.svg              # Símbolo vetorial conceitual (opcional)
```

## Filosofia: THE QUIET FRACTURE

A interface deve ser tão precisa e discreta que a *menor alteração intencional* provoque tensão. A personalidade não vem de 15 bordas, 40 partículas ou letras ilegíveis. Vem do ritmo, do silêncio, do acabamento, do contraste e de um único detalhe impossível.

**Menos UI. Mais presença.**

## Segurança criativa

- Preservar gameplay, HUD reativa, inventário, cutscenes, Party e sessões.
- Validar visualmente em desktop e mobile. Layout simulado **não** equivale a toque real.
- Não publicar, não modificar outros Places, não afirmar sucesso de testes não feitos.
- No projeto Voidwalkers, usar somente o MCP `roblox-studio` autorizado; não usar `roblox_studio` de outro projeto como fallback.
- Referência visual não é permissão para copiar identidades, assets ou fontes proprietários de terceiros.

## Status

**Skill V2 — primeira edição.** A qualidade final depende do diagnóstico, execução e revisão de cada implementação.

*Concebida para preservar a aura, não para substituí-la por efeitos.*
