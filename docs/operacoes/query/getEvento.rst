getEvento
===============
Operação para pegar dados de eventos inscritos no banco de dados.
Utiliza o parâmetro ”id” para encontrar uma informação no banco de dados.
Informação necessária para fazer a query:

- id (String)
        
Informações capazes de serem retornadas:
- _deleted
- _lastChangedAt
- _version
- createdAt
- data_inicio (AWSDate)
- descricao (String)
- em_exibicao (Boolean)
- hora_inicio (AWSTime)
- hora_fim (AWSTime)
- id (String)
- img (String)
- link_transmissao (String)
- nome_evento (String)
- nome_palestrante (String)
- repositorio (String)
- updatedAt
- tipo_evento


***********************
GraphQL
***********************
Definição da operação:

::

    query MyQuery {
        getEvento(id: "idAqui"){
            _deleted
            _lastChangedAt
            _version
            createdAt
            data_inicio
            descricao
            em_exibicao
            hora_fim
            hora_inicio
            id
            img
            link_transmissao
            nome_evento
            nome_palestrante
            repositorio
            updatedAt
            tipo_evento
        }
    }

Exemplo de operacao:

::

    query MyQuery {
        getEvento(id: "05b1e695-2ce7-409f-901f-8717c6c5383d") {
            descricao
            nome_evento
            nome_palestrante
            img
        }
    }

    Retorno:
    {
        "data": {
            "getEvento": {
            "descricao": "Evento aqui",
            "nome_evento": "nome do evento",
            "nome_palestrante": "nome do palestrante",
            "img": "link para imagem"
            }
        }
    }

***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getEvento } from 'caminho/para/graphql/queries';

    const pesquisa = {id: "idAqui"}
    API.graphql(graphqlOperation(getEvento, pesquisa)).
    then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getEvento } from '.../graphql/queries';

    const teste = () => {

    const pesquisa = {id: "05b1e695-2ce7-409f-901f-8717c6c5383d"};

    API.graphql(graphqlOperation(getEvento, pesquisa)).then(function (resultado) {
        console.log(resultado) //Olhar console
        //Realizar operações necessárias aqui
    });

    return (
            <div className='teste'>
            <p>teste</p>
            </div>
        );
    }