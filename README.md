# NEXUS SOLAR — Simulador Oficial

Um simulador interativo do Sistema Solar feito **100% em HTML5 + CSS3 + JavaScript (Canvas 2D)**, com visual inspirado em interfaces de missão. Sem frameworks, sem dependências externas — só abrir e explorar.

> **Destaques**
> - Renderização 2D no `<canvas>` com projeção/rotação 3D simulada
> - Painéis flutuantes e redimensionáveis (missão, telemetria, tempo e manual)
> - Controles de visualização: órbitas, rótulos, rastros, grade, anéis, cinturões e mais
> - Elementos dinâmicos: estrelas cintilantes, galáxias, nebulosas, asteroides, Kuiper e cometas
> - Fases orbitais baseadas em **J2000** (ajuste de fase por dia atual)
> - Telemetria em tempo real (T+, alvo, dados físicos e indicadores)

---

## 🖥️ Executando localmente

1. Baixe/clon​e o projeto.
2. Abra o arquivo **`index.html`** diretamente no navegador moderno (Chrome, Edge, Firefox ou Safari).
3. Opcional: sirva via HTTP para melhor performance de assets estáticos (ex.: `npx serve .`).

> Requisitos: navegador com suporte a Canvas 2D e JavaScript ES2015+.

---

## 🎮 Controles

### Mouse
- **Arrastar**: rotaciona a câmera orbital
- **Scroll**: zoom in/out dinâmico
- **Clique**: seleciona o corpo celeste

### Teclado
- **W / A / S / D**: navegação espacial
- **Q / E**: movimento vertical
- **ESPAÇO**: pausa/retoma a simulação
- **R**: reseta a câmera

### Painéis (arrastáveis e redimensionáveis)
- **Controle da Missão**: alterna **Órbitas**, **Rótulos**, **Rastros**, **Grade**; ativa **Asteroides**, **Kuiper**, **Cometas**, **Galáxias**.
- **Escala de Observação**: `Tamanho dos Corpos` e `Distância Orbital` (sliders).
- **Câmera**: `Seguir Alvo`, `Câmera Livre`, `Vista Superior`, `Reset`.
- **Controle Temporal**: seleção de velocidade via slider **-10x…+10x**, botões rápidos e _display_ de velocidade.
- **Telemetria**: relógio **T+**, data da missão, painel do planeta-alvo e indicador de órbita estável.
- **Manual**: lembretes rápidos de mouse/teclado e notas científicas.

---

## 🧠 Como funciona (visão técnica)

- **Projeção/rotação**: funções `project3D(x,y,z)` e `rotate3D(x,y,z,rotX,rotY)` cuidam da transformação e escala por profundidade.
- **Fase orbital realista**: `initPlanetPhases()` calcula **longitude média** por corpo (base **J2000**) e aplica em `baseAngle` para iniciar cada planeta na posição astronômica aproximada do dia atual.
- **Órbitas & posições**: `calculateOrbitalPosition(body, time)` usa `orbitalPeriod`, `distance`, `timeAcceleration` e `speed` (inclui leve inclinação procedural).
- **Cenas**: geradores dedicados para **estrelas**, **galáxias**, **nebulosas**, **asteroides**, **kuiper** e **cometas**, cada um com _tweaks_ visuais e falsos volumétricos via gradientes.
- **Render loop**: `render()` compõe fundo, órbitas, cinturões, cometas e corpos, ordenando por distância, e atualiza a **telemetria**.
- **UI**: elementos HTML/CSS com tema “NEXUS/NASA”, fontes Orbitron/Roboto e _hover/active states_.

---

## ⚙️ Configurações úteis

- **Escalas**: comece em `sizeScale = 0.1` e `distanceScale = 0.1`; ajuste para imersão vs. legibilidade.
- **Desempenho**: desative **Nebulosas/Galáxias** em máquinas fracas; reduza contagens nos geradores (ex.: estrelas, asteroides).
- **Câmera**: `mode = 'free' | 'follow' | 'top'` (via botões). Suavização por `smoothing`.
- **Tempo**: `speed` e **aceleração** definem avanço do relógio da missão; valores negativos “voltam no tempo” visualmente.

---

## 🧪 Roadmap (sugestões)

- Elementos orbitais reais (excentricidade, inclinação, longitude do periélio) por planeta
- Texturas/normal maps simples para superfícies e anéis
- Pistas de rastro configuráveis por corpo
- Preferências persistidas (localStorage) e _presets_ de câmera
- Acessibilidade: alto contraste e navegação por teclado
- Modularização em ES Modules e separação de CSS/JS
- _PWA_ (instalável), _service worker_ e _screenshot_ do canvas

---

## 📁 Estrutura atual (mínima)

```
/
└── index.html   # HTML + CSS + JS integrados (single file)
```

---

## 📝 Licença

MIT — ajuste conforme necessário.

---

## 🙌 Créditos & Avisos

- Simulação didática; aproximações físicas/visuais foram adotadas para desempenho e clareza.
- Dados e termos astronômicos inspirados em fontes públicas (e.g., J2000). Marcas e estilos “NEXUS/NASA-like” são apenas estética temática para fins educacionais.
- Autor: Thaynison (Gerente de TI). Contribuições são bem-vindas.
