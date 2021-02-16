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
Aplicação em GraphQL
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

***********************
Aplicação em Javascript
***********************

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipante } from 'caminho/para/graphql/queries';

    const pesquisa = {id: "idAqui"}
    API.graphql(graphqlOperation(getParticipante, pesquisa)).
    then(function (resultado) {
    //realizar operações com o resultado da pesquisa aqui
    });