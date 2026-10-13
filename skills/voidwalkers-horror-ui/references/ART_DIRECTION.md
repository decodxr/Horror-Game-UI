# ART DIRECTION · THE QUIET FRACTURE

> A floresta está quieta. A interface também. Até que um detalhe contradiz a realidade.

## 01 · Conceito: a estética da memória quebrada

A interface não é um dashboard tecnológico. É um **vestígio**: uma camada de sinais humanos tentando catalogar o que não deveria existir.

Três qualidades simultâneas:

1. **Precisão editorial:** tipografia, alinhamentos, espaço negativo, ritmo.
2. **Matéria imperfeita:** tinta interrompida, borda com falha, marca de registro quase apagada.
3. **Presença anômala:** raras alterações perceptuais que desafiam a expectativa, nunca impedem leitura crítica.

**Contraste narrativo:** gameplay normal = estável, quase silencioso; encontro com o Void = uma anomalia localizada. Se tudo pulsa, nada assusta.

## 02 · A assinatura visual (não um template)

### Gesto A — THE SEAM (a fenda)

Uma linha fina, deliberadamente incompleta, separa nome e conteúdo, ou sinaliza um estado de ameaça. Às vezes pode parecer deslocada por 1–2 px *como escolha estilística*. Nunca comprometer hitboxes ou texto.

**Boa utilização:** pequeno traço lateral de uma caixa de diálogo, uma abertura no retângulo de um objetivo, um canto interrompido no inventário.

**Ruim:** colocar uma linha em todos os componentes até parecer grade industrial.

### Gesto B — ECHO INK (tinta ecoada)

A referência original de pincelada preta vira **uma mancha curta e irregular**, aplicada somente à assinatura de diálogos ou passagens narrativas. Use leve imperfeição, mantendo uma área sólida por trás das letras.

**Boa utilização:** etiqueta do nome do falante em diálogo decisivo; marca discreta atrás de uma palavra-chave.

**Ruim:** textura de pincel ocupando 50% da tela ou uma silhueta com fundo branco incorporado.

### Gesto C — THE WITNESS (observação)

Um indicador minúsculo, quase como uma marca de registro analógico ou um halo interrompido, pode assinalar presença da Luz/entidade. Um único ponto de brilho, não um ícone em tudo.

**Boa utilização:** prefixo de diálogo sobrenatural ou aviso excepcional.

**Ruim:** marca de espírito ao lado de saúde, lanterna, inventário e todos os botões.

## 03 · Paleta proposta (tokens base)

**Valores sugeridos para iniciar protótipo; contraste deve ser validado no ambiente real.**

| Token | Hex | Uso |
|---|---|---|
| `night-void` | `#070B0D` | Fundo quase preto, overlays |
| `carbon` | `#101719` | Planos principais |
| `ash` | `#1E2829` | Superfícies secundárias |
| `bone` | `#E7E4DA` | Texto principal |
| `mist` | `#AEB9B6` | Texto secundário |
| `ghost` | `#88C9C5` | Luz, presença anômala, seleção rara |
| `lantern` | `#DAC18B` | Carga de lanterna, recurso |
| `wound` | `#8A4C51` | Perigo real, nunca decoração gratuita |
| `divider` | `#53615E` | Traços e contornos em baixa opacidade |

### Regra de distribuição

Acentos cromáticos são raros. **95% da estrutura visual deve usar neutros e tipografia**; cor informa estado, não preenche espaço vazio.

HUD de vitalidade e fôlego precisam ficar distinguíveis mesmo sem depender exclusivamente de cor (rótulo, valor, forma). É possível usar amarelo da lanterna, azul-petróleo para fôlego e neutro/branco para vitalidade. Não transformar o trio em semáforo.

Texto pequeno nunca deve usar `mist` excessivamente transparente sobre `carbon`: **cinza visível não significa legível**.

## 04 · Tipografia editorial, sem elitismo ilegível

**Contraste de papéis**, não mistura aleatória de fontes.

- **Voz narrativa / títulos raros:** serif editorial sóbria, com alto caráter; verificar disponibilidade/licença entre fontes Roblox existentes. Se a família não existir, usar uma alternativa suportada e documentar a substituição.
- **UI funcional:** sans serena, eficiente, espaçamento calibrado.
- **Dados / percentuais / keybinds:** números muito legíveis, alinhados de forma tabular quando possível.

### Hierarquia por função

| Papel | Direção |
|---|---|
| Nome do falante | pequeno mas reconhecível, tracking controlado, peso superior ao metadado |
| Diálogo | leitura confortável no pior fundo, quebra de linha natural |
| HUD | rótulo pequeno e firme; valor mais presente; número próximo do atributo |
| Aviso | título curto com ar, mais presença que tamanho |
| Inventário | título editorial contido, busca claramente interativa |
| Botão touch | texto/ícone inconfundível no movimento |

**Não obrigar caixa alta em texto longo; não reduzir corpo para “ficar chique”.**

## 05 · Espaço negativo como instrumento

A região principal da tela pertence à floresta e ao jogador. Interface recua para as bordas e ocupa o mínimo necessário, exceto momentos explicitamente modais.

### Regra da periferia

- HUD de sobrevivência compacto na borda inferior/esquerda com margens consistentes.
- Mensagem narrativa no terço inferior, acima dos controles essenciais.
- Objetivo excepcional breve em faixa discreta mais acima.
- Hotbar, prompts, botão de interação e touch não devem competir pela mesma área.
- Inventário aberto pode escurecer o fundo, mas não transformar tudo em um retângulo indistinguível.

Na dúvida, **remover uma moldura** costuma ajudar mais do que adicionar uma sombra.

## 06 · Movimento com respiração, nunca espetáculo vazio

Microanimações recomendadas como referência, ajustáveis após Play:

| Contexto | Direção | Faixa sugerida |
|---|---|---|
| HUD revelando estado | fade curto, mínimo deslocamento | ~160–260 ms |
| Diálogo entrando | opacidade e leve elevação, easing suave | ~220–350 ms |
| Aviso “SIGA A LUZ” | inscrição breve, fixação, dissolução | ~250–450 ms entrada |
| Manifestação anômala | uma falha curta, localizada; silêncio depois | ~350–900 ms |
| Inventário | presença consistente, sem bounce | ~200–320 ms |

- Não ativar motion/repetições a cada alteração de 1% da barra.
- Nunca usar tremor de tela para avisos rotineiros.
- Evitar flashes, estrobos, efeitos que dependam de FPS e efeitos permanentes de blur.
- Oferecer caminho sem animação agressiva quando motion reduzido estiver habilitado.
- O conteúdo importante deve continuar disponível quando animações forem puladas.

## 07 · Estado e narrativa

**Normal:** UI estável, neutra, fiel.

**Percepção da Luz:** um pequeno acento `ghost`, sem trocar a HUD inteira de cor.

**Memória contraditória:** um detalhe da linha/seam desloca-se, com cautela; preservar significado do texto.

**Perigo:** contraste aumenta; acento `wound` somente em dano/ameaça concreta.

**Transição para Backrooms:** permitir mudança de atmosfera, mas preservar identidade de componentes, ergonomia e informações críticas.

A interface participa da narrativa sem mentir sobre estado vital ou keybinds.

## 08 · Proibições estéticas

Não usar para produzir “aura”:

- gradientes arco-íris, holografia, neon sem justificativa;
- fontes dramáticas minúsculas, serifa frágil para HUD de emergência;
- menu gigante permanente com fundo preto;
- 8 retângulos com a mesma borda competindo na mesma tela;
- distorção/glitch em toda fala da Luz;
- símbolos ocultistas genéricos, runas aleatórias, caveiras decorativas;
- animações de `SPRINT` berrantes ou botões mobile “arcade”;
- “muito transparente” a ponto de fundir-se com o cenário.

## 09 · Teste editorial de assinatura

Remova a palavra “VOIDWALKERS” de um screenshot. Ainda é possível reconhecer uma família visual coerente pelo espaço, pela tipografia e pela fenda? Se não, a UI depende demais do logotipo.

A aura vem da **restrição consistente**.
