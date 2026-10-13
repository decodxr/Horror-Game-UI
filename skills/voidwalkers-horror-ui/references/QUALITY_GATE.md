# QUALITY GATE · AURA IS EARNED

> Uma interface não é premium porque o agente disse que é. É premium quando a leitura, a emoção e o controle sobrevivem ao jogo em movimento.

## 01 · Evidência mínima

A avaliação visual depende de **prints reais** sempre que disponíveis:

| Estado | Desktop | Mobile landscape | Mobile portrait* |
|---|---:|---:|---:|
| HUD em gameplay noturno | ✓ | ✓ | se suportado |
| HUD em área clara / fogo | ✓ | ✓ | se suportado |
| Diálogo normal + sobrenatural | ✓ | ✓ | se suportado |
| “SIGA A LUZ” / aviso | ✓ | ✓ | se suportado |
| Inventário vazio e com itens | ✓ | ✓ | se suportado |
| Ação de sprint / interação | ✓ | ✓ | se suportado |
| 1% stamina ou bateria crítica | ✓ | ✓ | se suportado |

`*` Se orientação retrato não for suportada pelo jogo, documentar explicitamente em vez de fingir um layout funcional.

**Separar na entrega:**
- **Play executado** (evidência real, data/ambiente e captura).
- **Layout simulado** (útil, mas não certifica touch).
- **Código inspecionado** (não certifica aparência).
- **Pendente** (sem evidência).

## 02 · Rubrica 0–4 por critério

Avaliar com exemplos concretos, nunca elogios genéricos.

| Critério | 0–1 (falha) | 2 (aceitável) | 3 (forte) | 4 (excepcional) |
|---|---|---|---|---|
| Legibilidade | texto desaparece, corte, contraste baixo | legível com esforço | claro e estável | leitura imediata em todos os fundos |
| Hierarquia | informações competem | ordem parcialmente clara | prioridades claras | o olhar chega ao que importa sem ruído |
| Composição | blocos soltos/sobrepostos | alinhamento funcional | ritmo, margens e proporção intencionais | presença editorial memorável |
| Identidade | genérica / arcade | dark mode comum | assinatura reconhecível | silêncio/ruptura equilibrados e autorais |
| Feedback | valores e ações ambíguos | estados básicos | estados claros em movimento | feedback elegante e instantâneo |
| Responsividade | unusable mobile | fixture aceitável | adaptação sólida | ergonomia confirmada em touch real |
| Movimento | flash/efeito irritante | transições funcionais | motion suave e curto | ritmo narrativo expressivo, sem atrapalhar |

**Regra de aceite:** nenhum critério abaixo de 3 para “pronto para revisão estética”; para declarar “premium”, ao menos três critérios com 4, **sem** falhas de acessibilidade nem funcionalidade. Se não houver touch real, marcar Responsividade como **não verificada**, não 4.

Isso não é pontuação de arte objetiva: é um processo de decisão para evitar “ficou foda” sem critérios.

## 03 · Checklist de falhas bloqueantes

Qualquer ocorrência bloqueia conclusão:

- Atributos críticos ilegíveis em noite escura, fogueira ou fundo claro.
- Inventário bloqueia o botão de fechar, hotbar, saída por Escape ou toque.
- Diálogo encobre controles mobile essenciais ou não permite progressão.
- Avisos de objetivo somem antes de serem lidos.
- Estado de HUD difere do servidor/gameplay ou fica estático após respawn.
- Texto cortado, fora da tela ou invisível por transparência/gradiente.
- Uma nova ScreenGui é criada repetidamente por respawn.
- Fontes/assets sem permissão deixam texto ou elementos essenciais ausentes.
- Efeitos perigosos (flashes, vibrações agressivas) sem alternativa segura.
- Falha de validação de sessão, missão ou input causada pela alteração de UI.

## 04 · Crítica visual estruturada

Após cada captura, produza:

```text
TELA/ESTADO:
Problema observado:
Impacto no jogador:
Causa provável:
Mudança visual proposta:
Evidência que confirmará a correção:
Status (corrigido / pendente / bloqueado):
```

**Nunca:** “Refinei todas as telas, ficou premium.”

**Sempre:** “Em mobile landscape, o diálogo cobria Correr e usava 11 px de corpo; movi o painel, aumentei o corpo e repeti a captura sem sobreposição.”

## 05 · Direção de arte — auditoria anti-clichê

Para cada componente, perguntar:

- Há uma maneira de remover 30% dos ornamentos e aumentar a presença?
- A fenda está agregando significado ou virou logo colado em tudo?
- O horror está na tensão ou em glitches repetitivos?
- A cor transmite estado ou só enfeita?
- A interface continua distinta sem o texto “VOIDWALKERS”?
- O painel parece objeto do universo, ou modal padrão com borda cinza?
- A fonte funciona quando o jogador precisa correr?
- O único detalhe sobrenatural escolhido tem **ritmo e contexto**?
- Existe contraste suficiente para screenshot E para gameplay?
- O mobile exige menos movimento do polegar, não mais?

## 06 · Testes funcionais indispensáveis

- **HUD:** lanterna ligada/desligada, consumo, recarga, stamina sprint/esgotada, dano/cura, respawn.
- **Diálogo:** textos curtos/longos, mudança de falante, normal/sobrenatural/sistema, fila, skip, cleanup.
- **Inventário:** abrir/fechar, vazio/com itens, busca, scroll, foco, hotbar, resize.
- **Input:** PC, touch real quando disponível, gamepad se suportado.
- **Prólogo:** árvore WP_003, carro, anomalia, Luz, chegada à fogueira, transição de missão.
- **Multiplayer:** separação de falas/visões por cliente, quando testável.
- **Performance:** variação de FPS/dispositivo, criação excessiva de instâncias, listeners duplicados.
- **Assets:** log de permissões de áudio, ícones e fontes.

Não inferir que todos passaram porque as fontes compilaram.

## 07 · Entrega / changelog

Em uma entrega, produzir pelo menos:

1. Resumo do norte artístico em uma frase.
2. Capturas antes/depois (ou a causa real da ausência).
3. Tabela curta de rubricagem com evidências e lacunas.
4. Scripts/instâncias modificados.
5. Impacto em gameplay, regressões observadas e o que não foi testado.
6. Checkpoint/rollback seguindo `AGENTS.md`.
7. Declaração clara: **não publicado**, salvo autorização específica posterior.

## 08 · Quality gate para o criador

A pergunta não é apenas “isso parece lindo?”. São três:

1. **Reconhecível:** sem logotipo, parece Voidwalkers?
2. **Legível:** consigo agir em menos de um segundo mesmo com medo?
3. **Memorável:** existe um detalhe que eu nunca vi, sem virar truque?

Se duas respostas forem não, volte para a composição. **Não acrescente glow.**
