createParticipante
===============

Operação utilizada para criar um participante no banco de dados.
Utiliza diversos parametros para fazer a criação, dos quais alguns são obrigatórios.

Informação necessária para fazer a mutation:

- nome_evento: String!
- nome_palestrante: String!
- descricao: String!
- data_inicio: AWSDate!
- hora_inicio: AWSTime!
- hora_fim: AWSTime!
- em_exibicao: Boolean!

Informações opcionais para fazer a mutation:

- img: String
- repositorio: String
- link_transmissao: String

Informações retornadas ao realizar a mutation:

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


***********************
GraphQL
***********************
Definição da operação:

::

    mutation MyMutation {
        createEvento(input: {repositorio: "", nome_palestrante: "", nome_evento: "", link_transmissao: "", hora_inicio: "", img: "", hora_fim: "", descricao: "", data_inicio: "", em_exibicao: false}) {
            id
        }
    }

Exemplo de operacao:

::

    mutation MyMutation {
        createEvento(input: {repositorio: "", nome_palestrante: "Joao da Silva", nome_evento: "Quimica estrutural - Visualização de moleculas com ChemBio", link_transmissao: "", hora_inicio: "14:00:00", img: "", hora_fim: "15:00:00", descricao: "Uma palestra para o participante aprender a mexer com Chembio", data_inicio: "2021-06-14", em_exibicao: true}) {
            id
        }
    }


    Retorno:
    {
        "data": {
            "createEvento": {
                "id": "jae4aec6-72bd-4dba-86b5-edbafd9bf11e"
            }
        }
    }

***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { createEvento } from 'caminho/para/graphql/mutations';

    const operacao = {
        repositorio: "", 
        nome_palestrante: "", 
        nome_evento: "", 
        link_transmissao: "", 
        hora_inicio: "", 
        img: "", 
        hora_fim: "",
        descricao: "",
        data_inicio: "",
        em_exibicao: true
    }
    
    API.graphql(graphqlOperation(getParticipante, { input: operacao })).
    then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { createEvento } from '.../graphql/mutations';

    const teste = () => {

    const operacao = {
        repositorio: "", 
        nome_palestrante: "Joao da Silva", 
        nome_evento: "Quimica estrutural - Visualização de moleculas com ChemBio", 
        link_transmissao: "", 
        hora_inicio: "14:00:00", 
        img: "", 
        hora_fim: "15:00:00",
        descricao: "Uma palestra para o participante aprender a mexer com Chembio",
        data_inicio: "2021-06-14",
        em_exibicao: true
    }

    API.graphql(graphqlOperation(getParticipante, { input: operacao })).then(function (resultado) {
        console.log(resultado) //Olhar console
        //Realizar operações necessárias aqui
        console.log(resultado.id) //Nome do usuário com id acima definido
    });

    return (
            <div className='teste'>
            <p>teste</p>
            </div>
        );
    }