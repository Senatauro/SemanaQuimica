========
Operações
========
As possiveis operações que podem ser executadas na API são:

.. _op_Query:

***********************
Operações de Query
***********************

- getParticipante
- getEvento
- getParticipando
- getCertificado    (Irá retornar um PDF quando feito)
- listParticipantes
- listEventos
- listParticipandos
- listCertificados  (Irá retornar uma lista de PDFs quando feito)


.. _op_Mutation:

***********************
Operações de Mutation
***********************

- createParticipante
- createEvento
- createParticipando
- createCertificado (Utilizado somente pelo backend)
- updateParticipante
- updateEvento
- updateParticipando
- updateCertificado (Utilizado somente pelo backend)
- deleteParticipante
- deleteEvento
- deleteParticipando
- deleteCertificado (Utilizado somente pelo backend)


***********************
Funções especiais (mutation)
***********************

- enviarEmail