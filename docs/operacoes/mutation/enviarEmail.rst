enviarEmail
===============

Operação utilizada para enviar uma mensagem para um determinado e-mail dado o assunto selecionado.
Utiliza diversos parametros para montar o e-mail, dos quais todos são obrigatórios.

Informação necessária para fazer a mutation:

- assunto: String!
- tipo: Int!        #0 - inscrição; 1 - outros
- nome: String!
- mensagem: String!
- email: String!

Informações retornadas ao realizar a mutation:

- enviado: Boolean

Caso o retorno seja false irá enviar um e-mail de maneira automatica para o administrador do backend


***********************
GraphQL
***********************
Definição da operação:

::

    mutation MyMutation {
        enviarEmail(input: {assunto: "", tipo: 1, nome: "", mensagem: "", email: ""}) {
            enviado
        }
    }


Exemplo de operacao:

::

    mutation MyMutation {
        enviarEmail(input: {assunto: "Teste", tipo: 1, nome: "Carlos", mensagem: "Mensagem de teste", email: "cgsste@hotmail.com"}) {
            enviado
        }
    }



    Retorno:
    {
        "data": {
            "enviado": {
                "id": true
            }
        }
    }



***********************
Aplicação em Javascript
***********************
Definição da operação:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { enviarEmail } from 'caminho/para/graphql/mutations';

    const operacao = {
        assunto: "",
        tipo: 0,
        nome: "",
        mensagem: "",
        email: ""
    }

    API.graphql(graphqlOperation(getParticipante, { input: operacao })).
    then(function (resultado) {
        //realizar operações com o resultado da pesquisa aqui
    });

Exemplo de operacao:

::

    import Amplify, { API, graphqlOperation } from 'aws-amplify';
    import { enviarEmail } from '.../graphql/mutations';

    const teste = () => {

    const operacao = {
        assunto: "Assunto de teste",
        tipo: 0,
        nome: "Carlos Gabriel",
        mensagem: "Enviando mensagem de teste",
        email: "cgsste@hotmail.com"
    }

    API.graphql(graphqlOperation(enviarEmail, { input: operacao })).then(function (resultado) {
        console.log(resultado) //Olhar console
        //Realizar operações necessárias aqui
    });

    return (
            <div className='teste'>
            <p>teste</p>
            </div>
        );
    }