#  Vírus Hunter 

> **Vírus Hunter: Jogo Educativo de Estratégia para o Ensino de Imunologia e Epidemiologia**.
> Uma plataforma gamificada de estratégia em tempo real (RTS) desenvolvida para transformar a educação científica e combater a desinformação na saúde pública.

---

##  Sobre o Projeto

O **Vírus Hunter** surge como uma resposta criativa e tecnológica aos desafios da educação científica no cenário pós-pandêmico. O objetivo principal é preencher as lacunas no conhecimento escolar tradicional por meio da gamificação, oferecendo uma ferramenta interativa e acessível via navegador web. 

A missão do projeto vai além do entretenimento: ele busca democratizar o acesso ao conhecimento básico de microbiologia para grupos sub-representados nas áreas de STEM (Ciência, Tecnologia, Engenharia e Matemática). Além disso, o software funcionará como um instrumento de pesquisa empírica para validar a eficácia de jogos sérios na aprendizagem, analisando o engajamento e a retenção de dados dos estudantes quando comparados a métodos tradicionais de ensino.

---

##  Mecânicas e Foco Educacional

O núcleo do *gameplay* inspira-se em mecânicas de *Tower Defense* e estratégia em tempo real, integrando modelos matemáticos para simular processos biológicos de forma precisa:

* **Jogabilidade Assimétrica:** Os jogadores podem assumir papéis opostos, controlando ativamente agentes de defesa do sistema imunológico ou liderando a invasão de patógenos virais.
* **Dados Científicos Reais:** As regras de combate e interação mimetizam dados reais de patógenos e componentes imunológicos, evidenciando como combatentes específicos atuam contra invasores determinados.
* **Inteligência Artificial Heurística:** O jogo implementa um sistema de IA capaz de adaptar a dificuldade ao desempenho do jogador, explicando de forma orgânica conceitos-chave como mutação viral e resposta imune adaptativa.
* **Saúde Única (*One Health*):** O *design* conecta o micro (corpo humano) ao macro (desafios transnacionais), ilustrando conceitos epidemiológicos complexos como taxas de contágio, imunidade coletiva e os perigos da resistência a antibióticos.

---

##  Arquitetura Técnica

O desenvolvimento foi estruturado em duas etapas estratégicas para garantir rápida validação metodológica seguida de otimização de performance:

### Prototipagem Ágil & Validação Web (Atual)
Focada em testar balanceamento e lógica educacional rapidamente através de uma arquitetura web híbrida:
* **UI/HUD:** Utilização de React para renderização de interfaces estáticas e interativas (como menus e cards educativos) combinada com a responsividade do CSS/Tailwind.
* **Core Loop (Motor):** Renderização frame-a-frame (60 FPS) gerenciada puramente pela Canvas API com `requestAnimationFrame`, evitando sobrecarga no DOM.
* **Gestão de Estado:** Uso estratégico de `useRef` para dados de alta frequência (posição de projéteis e inimigos) e `useState` apenas para atualizações visuais da interface.
* **Design Orientado a Dados:** Balanceamento de atributos encapsulado em constantes JSON (`TOWER_TYPES`, `ENEMY_TYPES`) para ajustes finos independentes do código principal.
* **Matemática Manual:** Implementação do zero de sistemas de colisão circular (distância Euclidiana), física de projéteis e algoritmo de *pathfinding* através de arrays de coordenadas.

### Migração e Produção (Futuro)
Portabilidade para a **Godot Engine 4.3**, focada em escalar o projeto utilizando ferramentas nativas de composição de Nós:

| Componente | Transição Planejada |
| :--- | :--- |
| **Estrutura** | Migração de React Components para Cenas independentes instanciadas dinamicamente (`.tscn`). |
| **Linguagem** | Conversão de lógica JavaScript para GDScript, aproveitando a similaridade sintática. |
| **Movimentação** | Substituição da matemática vetorial manual por nós nativos `Path2D` e `PathFollow2D`. |
| **Colisão** | Implementação de `Area2D` com captura de sinais (`body_entered`, `body_exited`) para detecção de alcance. |
| **Dados** | Evolução de objetos JSON para *Custom Resources* (`.tres`) manipuláveis via inspetor. |
| **Áudio e UI** | Integração de mixagem dinâmica via *AudioBus* e uso de *Control Nodes* (VBoxContainer) nativos. |

---

##  Status do Desenvolvimento

As bases teóricas e práticas do projeto já estão em andamento. Até o momento, as seguintes etapas foram concluídas:

* Realização do levantamento bibliográfico voltado a *serious games* e gamificação educacional.
* Estudo aprofundado de metodologias de criação de jogos digitais, incluindo o *framework* MDA e elaboração do GDD (*Game Design Document*).
* Finalização da fase de pré-produção (idealização e prototipagem).
* Início ativo da produção com desenvolvimento do código e implementação lógica.
* Validação de conceito com a participação oficial da equipe no evento "Ocean Game JAM", realizado no Samsung Ocean Manaus.

---

##  Referências Bibliográficas Base

O arcabouço teórico do **Vírus Hunter** apoia-se em estudos recentes sobre a eficácia de jogos no ensino de saúde:
* Análises de eficácia no ensino básico com ferramentas como o *Immuno Rush* (Machado & Carvalho, 2018) e *A Trilha da Vacina* (Azevedo et al.).
* Estratégias de aprendizagem superior atestadas pelo projeto *Hepatitis Game* (Takenami & Palácio, 2020).
* Estudos de aplicação da mecânica *Tower Defense* para a conscientização sobre resistência antibiótica (Aungst).
