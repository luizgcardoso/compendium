
# ENGENHARIA DE PROMPT

Eficiência, Controle e Escalabilidade no uso de IA.

## Boas Práticas:
- Ser específico (objetivo);
- Ser descritivo (sem deixar de ser específico);
- Reforçar o pedido;
- Atenção a ordem/organização do prompt;
- Dar uma saída alternativa para caso o modelo não encontre uma resposta;

## Fundamentos 

 **Engenharia de prompt** - a ciência de criar, estruturar e refinar comandos ou perguntas em linguagem natural para orientar LLMs .
 <br><br>Na hora de criar um prompt, pense:<br>
- *" como eu faria? "* - o que pediria para alguém (especialista) fazer...<br><br>
- *" faça o simples "*  - não complique além do necessário<br><br>
- **Dica:** Começe a partir dos modelos mais caros, pois os mais baratos vão conseguir refinar <br>

## PROMPT

Exemplo de extrutura para criação eficiente de prompt:<br><br>
        **P** - persona: Você é um especialista em...<br>
        **R** - roteiro: Ajude a construir/desenvolver...<br>
        **O** - objetivo: O objetivo é...<br>
        **M** - modelo: Quero o resultado da seguinte forma...<br>
        **P** - panorama:  (detalhadamente) Minha necessidade é ... e está inserida em um contexto... exemplos..<br>
        **T** - transformar: (intruções para refinamento da resposta)
 <br>
## Processos

* Definir a tarefa e os critérios de sucesso:
    - Desempenho e precisão (melhor modelo para o trabalho).
    - Latência (quanto tempo demora para trazer a melhor resposta).
    - Preço (orçamento).
* Desenvolver Casos de Testes:
    - casos comuns/default e edge cases.
* Prompt Inicial;
* Testar outros exemplos;
* Refinar o prompt;
* Colocar em produção;
 <br>
## Técnicas

- Arquivos Markdown (.md) para prompts bem detalhados/especificados.
    - As LLMs entendem melhor um prompt bem formatado e estruturado/organizado.

- Tag XML <Transcrição>: possibilita a atribuição de textos longos e isolando os diferentes contextos:
    * **DICA IMPORTANTE:** Inclua o arquivo antes (acima) da instruçao de analise.

    ```
    <Transcrição>
    {{TRANSCRICAO}} // texto longo ou file
    </Transcrição>
    ```
    - outro exemplo:

    ```
    >>instrucao.md

   # Contexto:
    <transcricao>
    Aqui entra o texto falado ou copiado de uma reunião, áudio ou vídeo.
    </transcricao>

    # Objetivo:
    Resuma os pontos principais do texto abaixo em formato de tópicos.
    ```
    
- Prompt do Sistema: configuração do sistema ferramenta da IA - ajuda na interpretação correta dos prompts.
- Zero Shot - Zero "Exemplos": prompt sem exemplo, e pergunta/solicitação direta;
- DSP - Directional Stimilus Prompting: é uma técnica que direciona o prompt através de estímulos (dicas, exemplos).
- Few Shot: Incluir no prompt vários exemplos para que o modelo tenha referências/estímulos (pode ser tanto exemplo positivos, quanto exemplos negativos)
- CoT (Chain-of-Thought): Cadeia de Pensamento para racíocinios lógicos mais complexos... Instruir o modelo a pensar explicitamente, passo a passo...
    - **Dica:** Usar contextos diferentes como <Thinking> para os pensamentos do modelo e <Answer> para as respostas produzidas.
- CCoT (Contrastive Chain-of-Thought): instruir a forma correta e a errada sobre como analisar/resolver algo.
- CoT Zero Shot: em modelos avançados uma simples instrução do tipo "... vamos pensar sobre isso passo a passo ..." ou "pense nisso passo a passo, com calma...", às vezes, é suficiente para que o modelo chegue a uma resposta satisfatória através da técnica de cadeia de pensamento naturalmente.

### Técnicas Avançadas:
- Self Consistency: incorporar várias CoT e instruir o modelo a comparar e analisar as respostas para decidir qual delas é a melhor.
- ToT (Tree of Thoughts): uma árvore de conhecimento com várias CoTs, permitindo ao modelo ramificar seu raciocínio em múltiplos caminhos paralelos, avaliar cada ideia e descartar caminhos errados na resolução de problemas complexos.
- SoT (Skeleton of Thought): acelera e organiza as respostas do modelo; antes de expandir detalhando a resposta definitiva, o modelo traz uma lista de possibilidades, tópicos, processo de raciocinio (brainstorm) para analise prévia.<br>
    ***Essa técnica economiza tokens e contexto!***
- GKP - Geração de Conhecimento por prompt: orientar o modelo a listar fatos ou conceitos fundamentais sobre um tema antes de executar a tarefa final, garantindo respostas mais precisas, informadas e estruturadas.
- Prompt Maiuetico: instruir o modelo a justificar a sua resposta com a finalidade de identificar possíveis erros ou falhas e para que possa melhorar a resposta.
- RAG - Geração Aumentada de Recuperação: objetiva resolver o problema de limitação do contexto, combinando bases de dados externas de conhecimento para aumentar a resposta e produzir respostas melhores.
- PAL - Linguagem Progamática Assistida: incluir técnicas de linguagem de programação ao prompt; exemplo: incluir variáveis em meio as cadeias de pensamento. 
-ReAct: instruir o modelo a raciocinar o que cada umas das ações implica antes de executá-las.

### Técnicas para evitar Alucinações:
- Configurar a ferramenta/modelso para que:
    - informe caso não saibam a resposta e não invete informações;
    - antes de processar a resposta, procurar citações no contexto/prompt;
    - regular o nível(temperatura) de criatividade do modelo (para restringir aos critérios do prompt);
    - usar a self-consistency;
<br><br>
<hr><br>

# Frameworks
### CLEAR
- **C**oncise: prompt breve e objetivo, evitando informações desnecessárias;
- **L**ogical: organizar ideias em uma sequência lógica;
- **E**xplicit: descrever o que se espera da resposta (formato, etc...);
- **A**daptive: adaptar o resultado para melhorar respostas futuras;
- **R**eflexive: refletir sobre o resultado para melhorar respostas futuras; 
     
        
        [CLEAR]

        Instruções organizadas seguindo os princípios da técnicas
        ...

        [CÓDIGO]

    

### CRISPE
- **C**apacity: definir a capacidade IA;
- **R**ole: definir o papel que a IA deve assumir;
- **I**nsight: descrever informações como background;
- **S**tatement: declarar a tarefa a ser executada/entregue;
- **P**ersonality: definir a personalidade/tom adotado pela IA; 
- **E**xperiment: definir múltiplas alternativas/abordagens ou possibiliades de resposta; 
    
        
        [CRISPE]

        [Capacity e Role]
        ...

        [Insight]
        ...

        [Statement]
        ...

        [CÓDIGO]

        [Personality]
        ...

        [Experiment]
        ...

### RACE
- **R**ole: definir o papel que o modelo deve assumir;
- **A**ction: definir a ação/tarefa que deve ser executada;
- **C**ontext: descrever o contexto/background;
- **E**xpectation/Execution: definir o formato da saída/resultado;
 
        [ROLE]

        [Role]
        ...

        [Action]
        ...

        [Context]
        ...

        [CÓDIGO]

        [Expectation]
        ...

