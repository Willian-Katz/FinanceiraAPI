# README - Requisitos
# Aula em: Primeiro projeto com Node.js › Primeiro projeto com Node.js › Conhecendo os requisitos da aplicação

### FinApi - Financeira

### Requisitos

- [x] Deve ser possível criar uma conta
- [x] Deve ser possível buscar o extrato bancário do cliente
- [x] Deve ser possível realizar um depósito
- [x] Deve ser possível realizar um saque
- [x] Deve ser possível buscar o extrato bancário do cliente por data
- [x] Deve ser possível atualizar dados da conta do cliente
- [x] Deve ser possível obter dados da conta do cliente
- [x] Deve ser possível deletar uma conta
- [x] Deve ser possível retornar o balance

## Regras de negócio

- [x] Não deve ser possível cadastrar uma conta com CPF já existente
- [x] Não deve ser possível buscar extrato em uma conta não existente
- [x] Não deve ser possível fazer depósito em uma conta não existente
- [x] Não deve ser possível fazer saque em uma conta não existente
- [x] Não deve ser possível fazer saque quando o saldo for insuficiente
- [x] Não deve ser possível excluir uma conta não existente

#### O que estou fazendo

Chamei o metodo POST para poder criar uma conta, definindo as informações necessárias para o cadastro, e gerando uma forma de colocar esses dados no corpo como um json(utilizando chave:valor).

Na questão do ID eu utilizei uma biblioteca chamada "uuid", que irá me gerar um seguência de caracteres aleatórios para ser o identificador. Fiz um baco de dados fake, para armazenar dando um push, as informações passadas. E pra terminar dei uma resposta de retorno.

Coloquei um filtro em resposta a primeira regra de negócio, onde verifiquei o cpf que foi colocado e verificar se já existe tal armazenado, para não haver repetição de cpf, gerenado como resposta um status 400, que dará um error, e avisando que já existe este cpf.

################################

Para ser possível buscar o estrato, utilizarei o método get para essa função. Vai pegar esse cpf como parametro para o headers, encontrar esse cpf e verificar se este cpf passado é igual ao cpf encontrado. E retornara uma resposta em json o estado.

MIDWARES: É uma função que fica entre requisição(request) e entre nosso response. Ele vai verificar se existe uma conta. Existem duas formas de passar o middleware:

1- Utilizando na rota (Quando precisamos coloca-lo especificamente ou somente nessa rota);

2- Utilizando o "app.use()" (Quando precisamos coloca-lo em todas as rotas seguêncialmente).

Para ter acesso a uma constante de uma middleware, só pegar a constante, desestruturar a constante do request.

################################

Criei uma forma de depositar, utilizando o método POST, onde vamos colocar no corpo uma descrição e uma quantia, estou conferindo se existe a conta, depois crio uma constante que irá receber a descrição e quantia, mas também irá receber a data de depósito, e o tipo do deposito como crédito. Após dou um push nesses dados para o statement essa operação.