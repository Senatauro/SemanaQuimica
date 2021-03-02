createParticipante
===============

Operação utilizada para criar um participante no banco de dados.
Utiliza diversos parametros para fazer a criação, dos quais alguns são obrigatórios.

Informação necessária para fazer a mutation:

- nome: String!
- telefone: String!
- email: String!
- genero: Int!              #1 - M; 2 - F; 3 - NB; 4 - O
- escolaridade: Int!        #1 - Ens. Med.; 2 - Grad; 3 - Pós; 4 - Outro
- estuda_ufrj: Boolean!     #1 - Sim; 2 - Não
- cidade: String!
- estado: String!

Informações opcionais para fazer a mutation:

- curso: String
- universidade: String
- periodo: Int

Informações retornadas ao realizar a mutation:

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

    mutation MyMutation {
        createParticipante(input: {cidade: "", curso: "", email: "", escolaridade: 1, estado: "", estuda_ufrj: false, genero: 1, nome: "", periodo: 1, telefone: "", universidade: ""}) {
            id
        }
    }

Exemplo de operacao:

::

    mutation MyMutation {
        createParticipante(input: {cidade: "Jataí", curso: "Ciências da computação", email: "cgsste@hotmail.com", escolaridade: 2, estado: "Goiás", estuda_ufrj: false, genero: 1, nome: "Carlos Gabriel Silva Stedilee", periodo: 8, telefone: "64992438948", universidade: "Universidade Federal de Goiás"}) {
            id
        }
    }


    Retorno:
    {
        "data": {
            "createParticipante": {
                "id": "fee4aec6-72bd-4dba-86b5-edbafd9bf11e"
            }
        }
    }

***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { createParticipante } from 'caminho/para/graphql/mutations';

    const operacao = {
        cidade: "",
        email: "",
        curso: "",
        escolaridade: 1,
        estado: "", 
        estuda_ufrj: false,
        genero: 1,
        nome: "",
        periodo: 1,
        telefone: "",
        universidade: ""
    }
    
    API.graphql(graphqlOperation(getParticipante, { input: operacao })).
    then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { getParticipante } from '.../graphql/mutations';

    const teste = () => {

    const operacao = {
        cidade: "Jataí",
        email: "cgsste@hotmail.com",
        curso: "Ciências da computação",
        escolaridade: 2,
        estado: "Goiás",
        estuda_ufrj: false,
        genero: 1,
        nome: "Carlos Gabriel Silva Stedile",
        periodo: 8, 
        telefone: "64992438948",
        universidade: "Universidade Federal de Goiás"
    };

    API.graphql(graphqlOperation(getParticipante, { input: operacao })).then(function (resultado) {
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