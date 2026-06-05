# 🦠 Stellar Pulse 🧬

> **Stellar Pulse: Jogo Educativo de Estratégia para o Ensino de Imunologia e Epidemiologia**.
> Uma plataforma gamificada de estratégia em tempo real (RTS) desenvolvida para transformar a educação científica e combater a desinformação na saúde pública.

---

## 🔬 Sobre o Projeto

O **Stellar Pulse** surge como uma resposta criativa e tecnológica aos desafios da educação científica no cenário pós-pandêmico. O objetivo principal é preencher as lacunas no conhecimento escolar tradicional por meio da gamificação, oferecendo uma ferramenta interativa hospedada em uma plataforma web acessível. 

A missão do projeto vai além do entretenimento: ele busca democratizar o acesso ao conhecimento básico de microbiologia para grupos sub-representados nas áreas de STEM (Ciência, Tecnologia, Engenharia e Matemática). Além disso, o software funcionará como um instrumento de pesquisa empírica para validar a eficácia de jogos sérios na aprendizagem, analisando o engajamento e a retenção de dados dos estudantes quando comparados a métodos tradicionais de ensino.

---

## 🎮 Mecânicas e Foco Educacional

O núcleo do *gameplay* inspira-se em mecânicas de *Tower Defense* e estratégia em tempo real, integrando modelos de sistemas biológicos de forma precisa e desafiadora:

* **Sistemas de Defesa Orgânicos:** Divisão tática do jogo em ambientes biológicos, como a Fase 1 (Camada Epitelial/Pele) e a Fase 2 (Sistema Respiratório/Pulmões).
* **Torres com Funções Imunológicas Específicas:** Implementação de mecânicas reais, como o Insta-kill de poluentes pesados pelo *Macrófago Alveolar*, dano em área pelas *Defensinas*, lentidão por muco via *Células Caliciformes* e silenciamento de habilidades pela *IgA Secretora*.
* **Economia de ATP:** O jogador gerencia recursos de energia (ATP) vitais para a implantação de defesas, obtidos tanto pelo abate de patógenos quanto por estruturas de suporte (como *Células Dendríticas* e *Hemoglobina*).
* **Inteligência Artificial Heurística:** O jogo implementa uma IA avaliativa (O Diretor) capaz de "ler" o cenário do jogador e escolher invasores específicos para quebrar a defesa. Por exemplo, enviar o *Poluente* impenetrável caso o jogador não possua *Macrófagos Alveolares*, ou utilizar o *Alérgeno* como "isca" para forçar o gasto de habilidades.

---

## ⚙️ Arquitetura Técnica

O desenvolvimento do jogo abandonou os protótipos em Canvas/React e migrou completamente para uma infraestrutura robusta de *Game Engine*, garantindo performance quadro a quadro e escalabilidade modular:

### Engine e Lógica Principal (Godot 4)
* **Motor Gráfico e Físico:** Desenvolvimento integral na **Godot Engine** (renderizador Compatibility para suporte otimizado a WebGL/HTML5).
* **Programação em GDScript:** Lógica totalmente orientada a objetos, com forte uso de comunicação assíncrona orientada a eventos (`Signals`) para isolamento de acoplamento e nós de tempo (`Timers`) para controle de cadência das *Waves* (Ondas).
* **Movimentação Orgânica:** Substituição de matemática manual de matrizes pela utilização de nós nativos `Path2D` e `PathFollow2D`, permitindo desenhar rotas biológicas complexas, como bifurcações alveolares e vasculares.
* **Modelagem Matemática da IA:** A transição de patógenos ocorre de forma não-linear através de uma FSM (Máquina de Estados Finitos) no script de *spawn*. O algoritmo de ameaça avalia as defesas aliadas com uma ponderação similar a $f(x) = D(x) \times W_t$, somando pesos heurísticos baseados nas torres presentes no mapa (ex: contar nós no grupo `"Torres_Aliadas"` via `to_lower()`).

### Integração Web e Landing Page
* **Arquitetura Web-Embed:** A exportação do jogo em WebAssembly (`.wasm`) é distribuída via `itch.io`.
* **Interface do Site:** Construção de uma *Landing Page* autônoma em HTML/CSS/JS puro, atuando como portal educacional estático (Enciclopédia Biológica) com estética retro/Arcade, que encapsula e executa a *game engine* no centro da tela através de requisições seguras via `iframe`.

---

## 🚀 Status do Desenvolvimento

As bases práticas do projeto já superaram a etapa de idealização e estão com seus sistemas principais implementados:

* Conclusão do GDD (*Game Design Document*) com mapeamento de todas as tabelas de atributos de torres e patógenos.
* **Fase 1 (Camada Epitelial):** Concluída, com integração das defesas inatas (Mastócitos, Eosinófilos) e ameaças externas.
* **Fase 2 (Sistema Respiratório):** Implementada, incluindo o sistema de ramificação em dois caminhos (`Path_Direita` e Esquerda) e a **IA Heurística** completa com avaliação dinâmica de contra-ataques (Tuberculose, Pneumococo, Influenza).
* **Integração Web:** Site educacional responsivo concluído, com sistema dinâmico de modais para consulta da enciclopédia e integração de áudio (`AudioBus`) via player HTML5.
* Validação de conceito original apresentada no evento "Ocean Game JAM" (Samsung Ocean Manaus).

---

## 📚 Referências Bibliográficas Base

O arcabouço teórico apoia-se em estudos recentes sobre a eficácia de jogos no ensino de saúde e simulação baseada em dados:
* Análises de eficácia no ensino básico com ferramentas como o *Immuno Rush* (Machado & Carvalho, 2018) e *A Trilha da Vacina* (Azevedo et al.).
* Estratégias de aprendizagem superior atestadas pelo projeto *Hepatitis Game* (Takenami & Palácio, 2020).
* Estudos de aplicação da mecânica *Tower Defense* para a conscientização sobre resistência antibiótica (Aungst).
