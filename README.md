#  Vírus Hunter 

> **Vírus Hunter: Jogo Educativo de Estratégia para o Ensino de Imunologia e Epidemiologia**[cite: 1].
> Uma plataforma gamificada desenvolvida para transformar a educação científica e combater a desinformação na saúde pública por meio da estratégia em tempo real[cite: 1].

---

##  Sobre o Projeto

O **Vírus Hunter** surge como uma resposta criativa e tecnológica aos desafios da educação científica no cenário pós-pandêmico[cite: 1]. O objetivo principal é preencher as lacunas no conhecimento escolar tradicional por meio da gamificação, oferecendo uma ferramenta interativa e acessível via navegador web[cite: 1]. 

A missão do projeto vai além do entretenimento: ele busca democratizar o acesso ao conhecimento básico de microbiologia para grupos sub-representados nas áreas de STEM (Ciência, Tecnologia, Engenharia e Matemática)[cite: 1]. Além disso, o software funcionará como um instrumento de pesquisa empírica para validar a eficácia de jogos sérios na aprendizagem, analisando o engajamento e a retenção de dados dos estudantes quando comparados a métodos tradicionais de ensino[cite: 1].

---

##  Mecânicas e Foco Educacional

O núcleo do *gameplay* inspira-se no gênero *Tower Defense*, integrando modelos de sistemas biológicos de forma precisa e desafiadora:

* **Estratégia *Single-Player* Focada na Defesa:** Ao contrário de jogos assimétricos, o jogador atua exclusivamente no comando do sistema imunológico. O desafio consiste em alocar defesas ativas e passivas estrategicamente para conter hordas sucessivas de patógenos invasores controlados pelo sistema.
* **Sistemas de Defesa Orgânicos:** Divisão tática do jogo em ambientes biológicos, como a Fase 1 (Camada Epitelial/Pele) e a Fase 2 (Sistema Respiratório/Pulmões). As regras de combate mimetizam dados reais de patógenos e componentes imunológicos[cite: 1].
* **Torres com Funções Imunológicas Específicas:** Implementação de mecânicas baseadas na biologia real, como o *Insta-kill* de poluentes pesados pelo Macrófago Alveolar, dano em área pelas Defensinas, controle de grupo (lentidão) por muco via Células Caliciformes e silenciamento de habilidades pela IgA Secretora.
* **Economia Metabolica (ATP):** O jogador gerencia recursos de energia vitais para a implantação de defesas, obtidos tanto pela reciclagem de patógenos abatidos quanto por estruturas biológicas de suporte (como Células Dendríticas e Hemoglobina).
* **Inteligência Artificial Heurística:** O jogo implementa uma IA capaz de "ler" o cenário montado pelo jogador e escolher invasores específicos para quebrar a defesa[cite: 1]. Por exemplo, a IA enviará o Poluente impenetrável caso o jogador não possua Macrófagos Alveolares, ou utilizará o Alérgeno como "isca" para forçar o gasto de habilidades.

---

##  Arquitetura Técnica

O desenvolvimento do jogo baseou-se na construção de uma infraestrutura robusta de *Game Engine*, garantindo performance e escalabilidade modular:

### Engine e Lógica Principal (Godot 4.3)
* **Motor Gráfico e Físico:** Desenvolvimento integral na **Godot Engine**, utilizando o renderizador *Compatibility* para garantir suporte otimizado e leveza em navegadores (WebGL/HTML5).
* **Programação em GDScript:** Lógica baseada em Programação Orientada a Objetos, com forte uso de comunicação assíncrona orientada a eventos (`Signals`) para isolamento de acoplamento, e nós de tempo (`Timers`) para controle de cadência das ondas (*Waves*).
* **Movimentação Orgânica:** Utilização de nós nativos `Path2D` e `PathFollow2D` em substituição à matemática manual de matrizes, permitindo desenhar rotas biológicas complexas de invasão (ex: bifurcações alveolares e vasculares).
* **Modelagem Matemática da IA:** A tomada de decisão dos patógenos ocorre de forma não-linear através de uma Máquina de Estados Finitos (FSM) no script de *spawn*. O algoritmo de ameaça avalia as defesas aliadas com uma ponderação similar a $f(x) = D(x) \times W_t$, somando pesos heurísticos baseados nas torres presentes no mapa no momento exato do cálculo.

### Integração Web e Interface
* **Arquitetura Web-Embed:** A exportação do jogo em WebAssembly (`.wasm`, `.pck`) é processada em um *player* HTML5 e distribuída online (via plataformas como `itch.io` ou hospedagem local/GitHub Pages).
* **Portal Educacional (Frontend):** Construção de uma *Landing Page* autônoma em HTML/CSS/JS puro com estética *Arcade*/Pixel Art. O site atua como uma Enciclopédia Biológica interativa, que encapsula e executa a *game engine* no centro da tela através de requisições seguras via `iframe`, permitindo a consulta paralela de dados científicos.

---

##  Status do Desenvolvimento

O projeto superou a etapa de idealização e encontra-se em produção ativa, com seus sistemas principais implementados e validados:

* Conclusão do GDD (*Game Design Document*) com o mapeamento completo das tabelas de atributos de defesa e patógenos[cite: 1].
* **Fase 1 (Camada Epitelial):** Totalmente funcional, com integração das defesas inatas (Macrófagos Residentes, Mastócitos, Eosinófilos) contra ameaças externas de entrada.
* **Fase 2 (Sistema Respiratório):** Implementada com sistema avançado de ramificação de caminhos (`Path_Direita` e Esquerda) e integração da IA Heurística dinâmica focada em contra-ataques específicos (Tuberculose, Pneumococo, Influenza e Poluentes).
* **Integração Web:** Site educacional responsivo finalizado, incluindo o sistema dinâmico de modais para consulta do banco de dados biológico e sistema integrado de áudio via HTML.
* Validação de conceito original apresentada no evento "Ocean Game JAM", realizado no Samsung Ocean Manaus[cite: 1].

---

##  Referências Bibliográficas Base

O arcabouço teórico do **Vírus Hunter** apoia-se em estudos acadêmicos recentes sobre a eficácia de jogos no ensino em saúde e ciências[cite: 1]:
* **Immuno Rush:** MACHADO, C. T.; CARVALHO, A. *Immuno Rush: análise de um serious game sobre Imunologia*. Revista Tecnologias na Educação, v. 10, n. 25, julho de 2018[cite: 1].
* **A Trilha da Vacina:** AZEVEDO, I. M. F. et al. *A Trilha da Vacina: o uso da gamificação como abordagem estratégica para a construção do conhecimento em Imunologia na educação básica*[cite: 1].
* **Gamificação no Ensino Superior de Saúde:** TAKENAMI, I.; PALÁCIO, M. A. V. *Hepatitis Game: integração da gamificação como estratégia de aprendizagem no ensino superior em saúde*. UNIVASF, 2020[cite: 1].
* **Mecânica Tower Defense e Educação:** AUNGST, M. T. *Gamification of Antibiotic Education - Tower Defense Anyone?*[cite: 1].
