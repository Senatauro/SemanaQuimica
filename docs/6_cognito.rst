========
Cognito
========
Cognito é a API utilizada para realizar operações que tem haver com estado de usuário.

Tipos de Operações
--------

Para este projeto iremos utilizar 5 tipos de operações:

- Sign-up (cadastrar)
- Sign-in (entrar)
- Sign-out (sair)
- Forgot password (esqueci minha senha)


.. _Query:

***********************
Query
***********************

Queries são operações que realizam buscas no banco de dados, retornando resultados encontrados dado os parâmetros enviados.

Queries podem ser categorizadas em 3 tipos padrões:

- Get: Retorna 1 elemento dado um parâmetro(Geralmente ID) enviado
- List: Retorna uma lista, que pode ser paginada, com todos os elementos
- Sync: Sincroniza dados armazenados offline com dados online

Destes 3 tipos iremos utilizar somente o Get e o List.

.. _Mutation:

***********************
Mutation
***********************

Mutation são operações que realizam funções únicas ou mudanças no banco de dados, adicionando, removendo ou alterando informações dado os parâmetros enviados.

Mutation podem ser categorizadas em 3 tipos padrões:

- Create: Cria um elemento no banco de dados com os dados enviados
- Update: Atualiza um elemento já existente no banco de dados dado um parâmetro(Geralmente ID) e dados enviados
- Delete: Deleta um elemento existente no banco de dados dado um parâmetro(Geralmente ID)