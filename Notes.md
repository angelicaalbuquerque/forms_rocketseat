## Forms

### O que são

A tag form no HTML é a maneira mais tradicional de interagir com o usuário da aplicação e é incrível o que é possível com esse elemento.

Servem para capturar dados de entrada (input) do usuário, ou seja, para ter interação com a aplicação. Também controles, como play e pause.

Para ir além do entendimento de formulários, é preciso dominar:

- estilização;
- validação;
- controles customizados;
- javascript.

## Estrutura

### Forms

O primeiro passo é definir a tag `form`, elemento que definirá um formulário. Essa tag é um container que terá elementos para o formulário.

Seus atributos básicos são action (para onde o formulário será submetido) e o method (POST e GET). Em tempo, se o action ficar vazio, significa que será enviado para mesma página. Se o method ficar vazio, entende-se que é GET.

Post e Get == verbos HTTP que servem para indicar como os dados estão trafegando. GET aparecem na URL e POST ficam mais escondidos.

```html
<form action="" method=""></form>
```

### Fieldset e legend

Dentro de formulários, precisamos agrupar as informações. Essa tarefa, de agrupamento de campos que tenham o mesmo propósito, é feita pelo `<fieldset>`, que é mais semântico e melhor interpretado pelos leitores de tela, sendo assim um ótimo aliado da acessibilidade.

Atributos especiais:

- disabled
  - desabilita todos os elementos internos;
  - não serão enviados os dados do fieldset ao submeter o formulário.
- form
  - o ID de um formulário ao qual esse fieldset pertence;
  - não precisa estar dentro do formulário, se colocarmos esse atributo e o ID correto.
- name
  - nome do grupo

O `<fieldset>` sempre virá acompanhado de uma tag `<legend>`, que é o nome do agrupamento que vai aparecer na tela e será o primeiro elemento dentro do `<fieldset>`.

Exemplo:

```html
<form id="contato" action="" method=""></form>

<fieldset form="contato" name="inputs-de-contato">
  <legend>Contato</legend>

  <label>Nome</label>
  <input type="text" />
</fieldset>
```

### Label

Essa tag serve para associar e identificar uma (ou mais) tags de entrada de dados.

É ótima para a acessibilidade, até mesmo pela possibilidade de clicar para mudar o foco da entrada de dados.

```html
<label>
  Nome:
  <input type="text" />
  Razão Social:
  <input type="text" />
</label>
```

Caso eu queira colocar o input fora do label, é necessário utilizar o atributo "for" para fazer a conexão entre este label e a tag de entrada de dados. Essa conexão é feita via id do input.

```html
<label for="nome">Nome: </label> <input id="nome" type="text" />
```

Essa forma funciona com elementos específicos, como: button, input (not hidden), meter, output, progress, select e textarea.

### Button

Button representa um botão.

Primariamente, é usado para enviar formulários, mas também tem outros usos e é estilizado pelo user agent (navegador), mas, claro, pode-se usar CSS para alterá-lo.

Atributos comuns:

- type
  - submit (enviar o formulário)
  - reset (limpar o formulário)
  - button (alguns navegadores entendem que o button também envia o formulário)
- autofocus (primeiro autofocus, elemento fica focado)
- disabled (botão visível, mas desabilitado)
- name (nome do button)
- value (usado junto ao name, opcionalmente, para quando submeter o formulário o valor ser recebido dentro de algo que tenha aquele name)
- form (linka a um formulário qualquer)

Exemplos:

```html
<button type="submit">Enviar</button>
```

```html
<button autofocus>Enviar</button>
```

```html
<button disabled>Enviar</button>
```

```html
<form>
  <input type="text" value="Pesquisar..." />
  <button type="reset">Limpar</button>
</form>
```

```html
<form action="" id="meu-form"></form>

<button type="submit" form="meu-form">Enviar</button>
```

### Datalist

## Tags de Entrada de Dados
