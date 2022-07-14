# hello-php

OBJETIVO: Esse documento tem como objetivo detalhar as regras de negócio necessárias para a implementação do teste técnico para desenvolvedor back end na CredPago.

CENÁRIO: A empresa Aluguel Agora realiza a intermediação de contratos de aluguel entre inquilinos e imobiliárias. Uma das funcionalidades que o sistema do Aluguel Agora utiliza para isso é a análise de crédito, que valida informações financeiras do cliente para a possível aprovação automática do contrato de locação. Seguem os requisitos dessa funcionalidade do backend do sistema:

O payload enviado pelo front contêm as seguintes informações:

* Nome do cliente (texto);
* CPF do cliente (somente números);
* Endereço do cliente, contendo rua, número, cidade, estado, (texto) e CEP (apenas números);
* Faixa salarial do cliente (número decimal);
* Informação se o cliente está com seu CPF negativado (verdadeiro ou falso);
* Valor do limite disponível em seu cartão de crédito (número decimal);
* Valor do aluguel ao qual o cliente está fazendo o contrato (número decimal);

O backend deve ser criado em Laravel, sendo uma API Restful que receberá os dados do front através de uma requisição, as processará e retornará o resultado da análise de crédito. As regras de negócio são as seguintes:

Todo cliente inicia sua análise com 100 (cem) pontos, sendo essa a maior pontuação possível dentro do sistema. Conforme se apresentem os seguintes cenários, essa pontuação é calculada da seguinte forma:

Caso o valor do aluguel ultrapasse 30% do salário , sua pontuação deve ser decrescida em 20%.
Caso o cliente esteja com seu CPF negativado, sua pontuação deve ser decrescida em 30%.
Caso as duas regras acima retornem como verdadeiras, a análise de crédito deve retornar como "Reprovada" e sua pontuação deve decrescida pelas duas regras acima.
Caso o limite disponível no cartão do cliente não seja maior ou igual ao valor mensal de aluguel, sua pontuação deve ser decrescida em 15%.
Caso o cliente já tenha realizada uma análise de crédito anterior que tenha sido reprovada, sua pontuação deve ser decrescida em 10% da pontuação de sua análise anterior.
A análise só deve retornar como "Aprovada" caso tenha somado 60 pontos ou mais após as validações supracitadas.
