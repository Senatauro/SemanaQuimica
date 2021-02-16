getParticipando
===============

Operação para pegar dados de usuários inscritos em eventos no banco de dados.
Utiliza o parâmetro ”id” para encontrar uma informação no banco de dados.
Informação necessária para fazer a query:

- id (String)

Informações capazes de serem retornadas:

begin{itemize}
- _deleted
- _lastChangedAt
- _version
- createdAt (utilizar para saber quando o cadastro para o evento foi criado)
- evento_id { dados do evento (nome, descricao, etc...) }
- id
- participante_id { dados do participante (nome, cidade, escolaridade, etc...) }
- updatedAt


***********************
GraphQL
***********************
Definição da operação:

::

    query MyQuery {
        getParticipando(id: "idAqui"){
            _deleted
            _lastChangedAt
            _version
            createdAt
            data_cadastro
            evento_id {
            id
            }
            id
            participante_id {
            id
            }
            updatedAt
        }
    }

Exemplo de operacao:

::

    query MyQuery {
        getParticipando(id: "f6985da0-4834-49d2-a414-6efaf7c41445") {
            evento_id {
                id
                nome_curso
            }
        }
    }

    Retorno:
    {
        "data": {
            "getParticipando": {
                "_deleted": null,
                "evento_id": {
                    "id": "05b1e695-2ce7-409f-901f-8717c6c5383d",
                    "nome_evento": "nome do evento"
                }
            }
        }
    }

***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipando } from 'caminho/para/graphql/queries';

    const pesquisa = {id: "idAqui"}
    API.graphql(graphqlOperation(getParticipando, pesquisa)).then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipando } from '.../graphql/queries';

    const teste = () => {

    const pesquisa = {id: "f6985da0 -4834-49d2-a414-6efaf7c41445"};

    API.graphql(graphqlOperation(getParticipando, pesquisa)).then(function (resultado) {
        console.log(resultado) //Olhar console
        //Realizar operações necessárias aqui
    });

    return (
            <div className='teste'>
            <p>teste</p>
            </div>
        );
    }