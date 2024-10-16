# Modelando um sistema bancário em POO com Python

O sistema reproduzido permite gerenciar contas bancárias, incluindo a criação de clientes e contas, realização de transações como depósitos e saques, e a visualização de extratos. O sistema utiliza programação orientada a objetos (POO) para organizar o código em classes que representam diferentes entidades e funcionalidades. O código ainda demonstra o uso de conceitos fundamentais da POO como herança, polimorfismo e abstração. 

## Funcionamento dos sistema

O sistema funciona através de um menu interativo no terminal, no qual o usuário pode criar clientes, contas, realizar saques, depósitos e consultar extratos. Inicialmente o usuário necessita criar um novo cliente Pessoa Física. Após a criação do usuário, deve-se criar uma conta corrente associada ao cliente. Finalizada as etapas de criação do usuário e conta, o usuário pode realizar depósitos e saques, que seram registrados no hitórico da conta e ao consultar o extrato, todas as transações realizadas são exibidas.

## Conceitos aplicados

### Herança 

A Herança permite que uma classe herde atributos e metodos de outra classe. No projeto, temos a classe cliente como classe base e a classe **PessoaFisica** que herda de **Cliente**. Isso significa que PessoaFisica pode reutilizar e especializar os métodos e atributos de **Cliente**.

<div aling="center">
<img src="https://github.com/FredericoSander/Modelando_o_sistema_bancario_em_POO_com_Python/blob/main/Imagens/Heran%C3%A7a.png">
</div>

A classe PessoaFisica herda de cliente e além de reutilizar o construtor de Cliente com **super()** ela adiciona novos atributos como cpf, nome e data_nascimento.

### Polimorfismo

Polimorfismo refere-se à capacidade de diferentes classes de fornecerem diferentes implementações de um mesmo método. No projeto, isso é demonstrado pelo método **sacar** das classes **Conta** e **ContaCorrente**.

<div aling="center">
<img src="https://github.com/FredericoSander/Modelando_o_sistema_bancario_em_POO_com_Python/blob/main/Imagens/Polimorfismo.png">
</div>

Embora tanto **Conta** quanto **ContaCorrente** possuam um método sacar, a implementação na **ContaCorrente** é especializada para incluir verificações adicionais, como limite de saques e valores.

### Abstração

Abstração se refere à ocultação de detalhes internos e à apresentação de uma interface limpa para o usuário. No projeto, isso é implementado com o uso de classes abstratas através do módulo **abc** (Abstract Base Classes).

<div aling="center">
<img src="https://github.com/FredericoSander/Modelando_o_sistema_bancario_em_POO_com_Python/blob/main/Imagens/Abstrata.png">
</div>

A classe **Transacao** é abstrata, definindo o método abstrato registrar, que deve ser implementado pelas classes concretas **Saque** e **Deposito**. Isso força as subclasses a fornecerem sua própria implementação específica.

## Estrutura do Projeto e Classes

### Cliente

A classe cliente representa um cliente genérico do programa. Ela contém um endereço e uma lista de contas associadas ao cliente. A classe possui como atributo o **endereco** do cliente e as **contas** e os métodos  **realizar_transacao** e o método **adicionar_conta**.

### PessoaFisica

A classe PessoaFisica representa um PessoaFisica especifica do programa. Ela herda os atributos da classe cliente e adciona atributos especificos para clientes fisicos como **cpf**, **nome** , **data_nascimento** e implementa o método **__str__()** que retorna uma string representando o nome do cliente.

### Conta

A classe **Conta**, representa uma conta bancária genérica. Ela contém informações como saldo, agência da conta, número da conta e histórico de transações. Como atributos da classe, foram adicionados o **_saldo** como privado, **_agencia**, **_numero_conta**, **_cliente**, **_historico**. Como métodos foram adicionados **sacar**, que realizar o saque e **depositar**, para realizar depósitos.

### Conta Corrente 

A classe **ContaCorrente** herda os atributos e métodos da classe **conta** e adiciona outros atributos como **limite**, que concede um crédito a conta corrente criada e **limite_saques**, que atribui um quantidade máxima de saques a serem realizados (não foi especificado se o período de restrição será diário, semanal ou mensal).

### Historico

A classe **Historico**, armazena todas as transações realizadas em uma conta. A esta classe foram adicionados os atributos **_transacoes** que recebe uma lista das transações realizadas. A classe **Historico** ainda recebeu o método **adicionar_trasancao(transacao)** que adiciona cada nova transação realizada.

### Transacao(Abstrata)

A Classe **transacao** trata-se de uma classe abstrata que define uma interface de uma trasanção. A classe implementa o método abstrato **registrar(conta)** que deve se implementado pelas suas subclasses.

### Saque e Deposito

As classes **saque** e **deposito** herdam os métodos da classe **transacao** e implementam a lógica específica para saques e depósitos. As classes possuem o atributo **valor** e impelementam o método **registrar(conta)**.

## Conclusão
Este projeto é uma reprodução do Desafio de Projeto 'Modelando o Sistema Bancário em POO com Python', com o objetivo de demonstrar os princípios da Programação Orientada a Objetos em Python, aplicando conceitos como herança, polimorfismo e abstração. A utilização desses conceitos possibilita a criação de um sistema flexível e extensível, capaz de simular operações básicas. Futuras funcionalidades podem ser implementadas para expandir o projeto, como a criação de um cliente jurídico, conta poupança, conta investimentos, função de transferência, entre outras.