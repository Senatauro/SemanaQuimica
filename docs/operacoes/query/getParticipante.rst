getParticipante
===============

Operação para pegar dados de usuários inscritos no banco de dados.
Utiliza o parâmetro "id" para encontrar uma informação no banco de dados. 
Informação necessária para fazer a query:

- id (String)

Informações capazes de serem retornadas:

- _deleted
- _lastChangedAt
- _version
- createdAt
- curso (String)
- escolaridade (Int)
- estuda_ufrj (Boolean)
- genero (Int)
- id (String)
- nome (String)
- participando_id (String) { ... } //Informações de em quais eventos o participante esta inscrito
- periodo (Int)
- telefone (String)
- universidade (String)
- updatedAt


***********************
GraphQL
***********************
Definição da operação:

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

Exemplo de operacao:

::

    query MyQuery {
        getParticipante(id: "3b53c11a-761a-4a6f-abcd-b2f24c9a198c") {
            nome
            telefone
            universidade
            updatedAt
        }
    }

    Retorno:
    {
        "data": {
            "getParticipante": {
            "nome": "Daniel Sant' Anna Andrade",
            "telefone": "+5521 26919368",
            "universidade": "UFRJ",
            "updatedAt": "2021-02-10T19:06:06.264Z"
            }
        }
    }

***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipante } from 'caminho/para/graphql/queries';

    const pesquisa = {id: "idAqui"}
    API.graphql(graphqlOperation(getParticipante, pesquisa)).
    then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipante } from '.../graphql/queries';

    const teste = () => {

    const pesquisa = {id: "3b53c11a-761a-4a6f-abcd-b2f24c9a198c"};

    API.graphql(graphqlOperation(getParticipante, pesquisa)).then(function (resultado) {
        console.log(resultado) //Olhar console
        //Realizar operações necessárias aqui
        console.log(resultado.nome) //Nome do usuário com id acima definido
    });

    return (
            <div className='teste'>
            <p>teste</p>
            </div>
        );
    }