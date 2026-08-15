# JSX: 
<hr>
"JavaScript extendido" ... Atribui elementos (extendidos) ao JavaScript
 
    - cadeia de elementos deve ser envolvida por <React.Fragment></React.Fragment> ou apenas <></>
    - propriedades das tags (elementos) devem ser nomeadas/referenciadas em camelCase

# Componentes:
<hr>
    - auxiliam na organização do código através da componentização
    - (via de regra) quanto mais componentizado, melhor

# props (propriedades):
 - Facilitam o reúso dos elementos

# children
    - conteúdo do elemento fechado. 
    Exemplo: <br>
    ```
    <Titulo>
        Isso é o children
    </Titulo>
    ```


# Estados (states):
    - representa as características da aplicação conforme seu estado atual (state)

 ## Hooks:
        - tipo de função especial usada para controlar o estado e ciclo de vida de componentes funcionais.

 ## useState:
        - retorna array com dois valores ([estadoAtual, hook])
        - atraves da execução da função hook, todos os componentes dependentes do estado são renderizados novamente (isso garante a reatividade dos componentes funcionais)