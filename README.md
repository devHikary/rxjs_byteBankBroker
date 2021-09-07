# Angular e RxJS: Programação reativa

Curso da plataforma Alura

Instrutor: **Álvaro Camillo Neto**

Nesse curso será desenvolvido uma interface  para aplicativo Byte Bank Broker para explorar os recursos da biblioteca RxJS.

## 🛠️ Abrir e rodar o projeto

- Clonar o projeto
- Entrar na pasta api e instalar as dependências com `npm i`
- Rodar o comando `npm start`
- Entrar na pasta byte-bank-broker e instalar as dependências com `npm i`
- Rodar o comando `ng serve -o`

## ✔️ Técnicas e tecnologias utilizadas

### Aula 1

- Criar uma interface

```tsx
ng generate interface acoes/modelo/acoes
```

- Criar um serviço

```tsx
ng g service acoes/acoes
```

- Quando queremos um **único valor** de forma imperativa utilizamos uma **função**
- Quando queremos uma **coleção de valores** de forma imperativa utilizamos um **iterator**
- Forma reativa → precisamos esperar uma requisição
- Quando queremos um **único valor** de forma reativa utilizamos uma Promise
- Quando queremos uma **coleção de valores** de forma reativa utilizamos um Observable
- Observable representa uma coleção de eventos ou valores que ocorrem no tempo.

### Aula 2

- O operador `pluck` não recebe uma função, ele recebe uma **string**, que é o nome da propriedade que eu quero extrair do objeto que eu estou recebendo.

```tsx
pluck('payload'),
```

- `unsubscribe` → garantimos que a subscrição que fizemos no `ngOnInit()` seja corretamente finalizada quando o componente sair da memória.
- $ é um convenção da comunidade pra indicar que é um `observable`.
- Com o Async pipe, o Angular irá se inscrever nesse `Observable`, passar o seu conteúdo para a variável Ações e quando o componente for encerrado, o framework cuida para fazer o Unsubscribe do Observable.
- `Observable` tem a sua iniciação lazy, ou seja, a requisição só foi feita no momento que o nosso componente abriu-se, se inicializou, e o pipe async fez o `subscribe`. E é nesse momento do `subscribe` que acontece a requisição API.

### Aula 3

- `SwitchMap` → usado para o controle de ação do fluxo.
- Desejamos alternar o fluxo de dados vindos do evento de digitação para o fluxo de dados da requisição do HTTP.
- `Merge` → junta dois ou mais `Observable` em um só fluxo.

### Aula 4

- `filter()` vai receber uma função que passada o valor do fluxo, a função retorna um valor booleano. Se o valor retornado for verdadeiro, o fluxo segue para a próxima fase.
- `debounceTime()` → recebe, apenas, um valor numérico que representa a quantidade de milissegundos que o fluxo deve esperar. E ele emite para o próximo operador o último valor que foi gerado nesse intervalo.
- `distinctUntilChanged()` → o operador compara o valor digitado com o valor anterior, se for igual ele não faz a requisição.