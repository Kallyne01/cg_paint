# 📋 Divisão de Tarefas - Projeto Paint OpenGL

Para não sobrecarregar ninguém, a implementação prática foi dividida entre todos os 5 membros da equipe. Cada um ficará responsável por um módulo/arquivo lógico do sistema. 

**Isac e João** já realizaram o trabalho fundamental da arquitetura inicial (`Estruturas.h`), e agora se juntam à implementação prática para dividirmos os módulos.

---

### 1. Módulo de Inicialização, Core OpenGL e Eventos
**Responsável:** 👨‍💻 **ANDRE LUCAS CAVALCANTI COSTA SOUZA**
**O que fará:**
* Construir o esqueleto do `main.c` e iniciar as configurações da janela (`glutInit`, etc).
* Capturar os eventos primários de mouse (`glutMouseFunc`, `glutMotionFunc`) e teclado (`glutKeyboardFunc`).
* Criar a lógica de Interface (menu ou atalhos) para trocar as ferramentas (alterar o `ModoFerramenta` atual e a cor/espessura selecionada).
* Conectar os eventos do usuário com as funções dos outros módulos.

### 2. Módulo de Transformações Geométricas
**Responsável:** 👩‍💻 **KALLYNE LOPES TAVEIRA**
**O que fará:**
* Ser a responsável pela Álgebra Linear do projeto. Implementar as lógicas usando a struct `Matriz3x3`.
* Implementar a função de **Translação** (arrastar e soltar).
* Implementar a função de **Rotação** (em relação ao centro do objeto, ou origem para pontos).
* Implementar a função de **Escala** (em relação ao centro do objeto).
* Implementar a função de **Reflexão** (Eixos X, Y e Origem).
* Implementar a função de **Cisalhamento**.

### 3. Módulo de Renderização, Seleção e Exclusão
**Responsável:** 👨‍💻 **FELIPE DE SOUZA FERREIRA LIMA**
**O que fará:**
* Implementar a função `desenharCena(...)`, que irá percorrer a `CenaGrafica` e enviar os vértices para a placa de vídeo usando as primitivas corretas (`GL_POINTS`, `GL_LINES`, `GL_POLYGON`).
* Aplicar as cores e espessuras na hora do desenho, destacando os objetos que estiverem com `selecionado = 1`.
* Implementar os algoritmos de **Seleção de Objetos** (calcular se o clique do mouse colidiu com as coordenadas do ponto, reta ou polígono).
* Lógica da borracha: Implementar a função `excluirObjetosSelecionados`.

### 4. Módulo de Criação de Primitivas
**Responsável:** 👨‍💻 **ISAC PEIXOTO COSTA** *(+ Crédito Arquitetura)*
**O que fará:**
* Implementar as funções que transformam os cliques do mouse em objetos gravados na memória.
* Implementar `adicionarPonto`.
* Implementar `adicionarReta` (lidando com o clique inicial e o clique final).
* Implementar `adicionarPoligono` (gerenciar a adição de vértices temporários até que o usuário feche o polígono).

### 5. Módulo de Persistência (Arquivos) e Animação
**Responsável:** 👨‍💻 **JOAO EDSON DE SOUSA** *(+ Crédito Arquitetura)*
**O que fará:**
* **Persistência:** Implementar as funções `salvarCena` e `carregarCena`. A ideia é usar funções de arquivo do C (`fopen`, `fread`, `fwrite`) para guardar e ler os bytes da nossa grande struct `CenaGrafica` em um arquivo binário (ex: `cena.dat`).
* **Animação:** Configurar a função `glutTimerFunc` para criar um loop contínuo independente. Com base nas propriedades da struct `EstadoAnimacao`, a animação irá modificar automaticamente os vértices ou os ângulos dos objetos da cena.
