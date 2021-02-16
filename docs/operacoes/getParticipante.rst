getParticipante
===============

Operação para pegar dados de usuários inscritos no banco de dados.
Utiliza o parâmetro "id" para encontrar uma informação no banco de dados. 
Informação necessária para fazer a query:

- id (String)

Informações capazes de serem retornadas:

- deleted
- lastChangedAt
- version
- createdAt
- curso (String)
- escolaridade (Int)
- estuda_ufrj (Boolean)
- genero (Int)
- id (String)
- nome (String)
- participando\_id (String) { ... } //Informações de em quais eventos o participante esta inscrito
- periodo (Int)
- telefone (String)
- universidade (String)
- updatedAt

.. _ex_GetParticipante:

***********************
Exemplo de GraphQL
***********************

::

    query MyQuery {
        getParticipante(id: "idAqui"){
            _deleted
            _lastChangedAt
            _version
            createdAt
            curso
            escolaridade
            estuda_ufrj
            genero
            id
            nome
            participando_id {
            ...
            }
            periodo
            telefone
            universidade
            updatedAt
        }
    }