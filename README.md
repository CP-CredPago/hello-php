
# hello-php

#### Objetivo do documento: 
Detalhar as regras de negócio necessárias para a implementação do teste técnico para desenvolvedor backend na CredPago.

#### Problemática: 
A empresa Aluguel Agora realiza a intermediação de contratos de aluguel entre inquilinos e imobiliárias. Uma das funcionalidades que o sistema do Aluguel Agora utiliza para isto é a análise de crédito, que analisa informações financeiras do cliente para tomar a decisão de aprovação do contrato de locação. Você, como desenvolvedor da companhia deverá construir a nova versão deste motor de crédito.

#### Requisitos:
Deverá ser construída uma API RESTful, utilizando o framework PHP Laravel em sua versão mais recente. A PHP utilizado também deverá ser a versão mais recente, preferencialmente conteinerizado em Docker.
O Código deverá ser disponibilizado como um repositório público no GitHub.

O principal endpoint da aplicação deverá receber os seguintes parâmetros:
| Parâmetro |Tipo de dado |Formato  |
|--|--|--|
| Nome | varchar(75) | Texto plano |
| CPF | varchar(14) | xxx.xxx.xxx-xx  |
| Negativado | boolean | true ou false |
| Salário | float | xxxx.yy |
| Limite do cartão | float | xxxx.yy |
| Valor do Aluguel | float | xxxx.yy |
| Rua | varchar(120) | Texto plano |
| número | int | x |
| Municipio | varchar(75) | texto plano |
| Unidade Federativa | varchar(2) | AA |
| CEP | varchar(9) | xxxxx-xxx |




Todo cliente inicia sua análise com 100 (cem) pontos, sendo essa a maior pontuação possível dentro do sistema. As regras devem ser executadas na seguinte ordem:

* Caso o valor do aluguel ultrapasse 30% do salário , sua pontuação deve ser decrescida em 20%.
* Caso o cliente esteja com seu CPF negativado, sua pontuação deve ser decrescida em 30%.
* Caso as duas regras acima retornem como verdadeiras, a análise de crédito deve retornar como "Reprovada" e sua pontuação deve decrescida pelas duas regras acima.
* Caso o limite disponível no cartão do cliente não seja maior ou igual ao valor mensal de aluguel, sua pontuação deve ser decrescida em 15%.
* Caso o cliente já tenha realizada uma análise de crédito anterior que tenha sido reprovada, sua pontuação deve ser decrescida em 10% da pontuação de sua análise anterior.

A análise só deve retornar como "Aprovada" caso tenha somado 60 pontos ou mais após as validações supracitadas.

#### Teste de Mesa 
// Colocar exemplos de payloads e respostas

#### Diferenciais: 
Os requisitos a seguir são opcionais, as suas realizações não são obrigatórias, mas contam como pontos positivos na avaliação. Lembrando que, caso escolha realiza-los, as implementações devem ser completas.
 * 100% de cobertura com testes unitários
 * Documentação em Swagger
 * Documentação em formato de Collection do Postman ou Insomnia
 * API hospedada em uma cloud pública (AWS, GCP, Digital Ocean, Azure, Contabo, e semelhantes)
 * Disponibilizar configuração em ambiente utilizando docker-compose.
 * Ser aderente a OWASP Top Ten ([OWASP Top Ten | OWASP Foundation](https://owasp.org/www-project-top-ten/))
 * 
