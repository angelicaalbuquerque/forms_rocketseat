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

É tag estrutural para os formulários. Fornece ao usuário uma lista de valores como sugestão a uma tag `<input>`.

Os valores são sugestivos e não obrigatórios.
Os usuários podem selecionar um dos valores ou colocar um calor diferente da sugestão.

```html
<input type="text" list="fruitsdata" placeholder="Escolha uma fruta" />

<datalist id="fruitsdata">
  <option>apple</option>
  <option>banana</option>
  <option>mango</option>
  <option>orange</option>
  <option>cherry</option>
</datalist>
```

O valor `id` de um `<datalist>` é muito importante, pois o atributo `list` recebe esse `id` de um `<datalist>` residente no mesmo documento:

```html
<input type="color" list="colorsdata" />

<datalist id="colorsdata">
  <option>##FF0000</option>
  <option>#00FF00</option>
  <option>#0000FF</option>
</datalist>
```

#### Tipos de input suportados

- text;
- search;
- url;
- tel;
- email;
- date;
- month;
- week;
- time;
- datetime-local;
- number;
- range;
- color.

Os valores de datalist que não são compatíveis com o tipo do `<input>` não serão apresentados.

#### Tipos de input NÃO suportados

- hidden;
- password;
- checkbox;
- radio;
- file;
- qualquer tipo de button.

Para verificar a compatibilidade com o browser, pode-se pesquisar no endereço [http://caniuse.com](http://caniuse.com).

## Tags de Entrada de Dados

### Input

Uma das tags mais usadas em formulários, a tag `input` aceita os mais diversos tipos de dados. Apesar disso, por ter um elevado número de combinações, é uma das tags mais poderosas e complexas.

Atributos comuns de controle:

- type (define o tipo do input e é obrigatório);
- name;
- id.

#### Input atributos comuns

_[quase todos = alguns tipos de campos não vão aceitá-los]_

**Autocomplete**: Automaticamente vai completar uma informação que já foi utilizada algumas vezes antes. No caso abaixo, o e-mail seria autocompletado.

```html
<input type="text" autocomplete="email" />
```

**Autofocus**: Automaticamente o elemento vai ser focado, vai receber o cursor piscando. É permitido apenas um por página porque o navegador vai pegar apenas o primeiro para focar.

```html
<input type="text" autofocus />
```

**Disabled**: Atributo que vai deixar um campo desabilitado.

```html
<input type="text" disabled />
```

**Readonly** _(quase todos)_: Somente exibe para leitura o campo. A diferença para o disabled é que o disabled, além de ser só para leitura, fica com aspecto opaco.

```html
<input type="text" value="texto" readonly />
```

**Value**: Valor "padrão" escrito no campo input.

```html
<input type="text" value="pesquisar" />
```

**form** _(quase todos)_: linka o input com algum formulário, caso o formulário esteja fora. Por exemplo, tem-se um input que você gostaria de deixar em outro lugar da sua página, mas enviar os dados, gostaria de enviar com as informações desse formulário.

**name**: Para enviar esses dados para um outro formulário, é necessário utilizar um outro atributo, chamado name. Sem ele no input, teremos problemas ao resgatar esses dados do input em outro momento, como no backend.

```html
<form id="meu-form">
  <input type="email" name="email" form="meu-form" />
</form>
```

**required** _(quase todos)_: Significa que o campo específico é obrigatório de preenchimento para ser enviado. Pode ser utilizado em mais de um campo.

```html
<input type="email" required />
```

**placeholder** _(quase todos)_: Utilizados em campos específicos, como: password, searh, tel, text e url.

```html
<input type="password" placeholder="Digite sua senha" />
```

#### Placeholder com Label

O label serve para a acessibilidade. Se a pessoa tem a necessidade do leitor de tela, o leitor sabe que esse label/for tem a ver com o input e-mail.

Então, mesmo tendo um placeholder objetivo, o label é importante ser usado.

```html
<label for="email">E-mail</label>
<input type="email" placeholder="Digite seu e-mail" />
```

### Password

Com `<input type="password">`, podemos colocar senhas de maneiras mais seguração na aplicação, uma vez que esse tipo cria uma máscara para esconder o que é digitado no campo -- lembrando sempre que o estilo da apresentação do campo é aplicado pelo User Agent, caso não existe nenhuma personalização para o mesmo.

#### Atributos

- minlength / maxlength <br>
  O número mínimo e máximo de caracteres para este campo.<br><br>
- size <br>
  "Maneira visual" de apresentar número aceitável de caracteres que esse campo deve conter.<br><br>
- pattern <br>
  Expressão regular para validar o que está sendo digitado no campo. Altamente recomendado para o uso de um padrão de segurança alto de senhas. Por exemplo: senhas que contenham caracteres hexadecimais (de 0 a 9, de A a F), com o limite de no mínimo 4 caracteres e no máximo 8 caracteres.<br>
  Ou seja, o pattern é poderoso por usar expressões regulares para executar essa validação: `pattern="[0-9a-fA-F]{4,8}"`
  <br><br>
- placeholder<br>
  Mostra um exemplo do texto a ser digitado no campo.<br><br>
- readonly / disabled<br>
  Atributo booleano indicando se o campo está habilitado ou não.<br><br>
- required<br>
  Campo obrigatório.
- inputmode<br>
  Poderá alterar o uso do teclado em smartphones. Por exemplo: queremos que o cliente só adicione número, para isso, usamos: `inputmode="numeric"`.<br><br>
- autocomplete<br>
  Quando on: permite a sugestão de new-password ou current-password (se já tiver senha cadastrada). Quando off: desabilita a opção de autocompletar. Já utilizando "new-password" o navegador poderá sugerir uma nova senha ao usuário.

Exemplo:

```html
<form action="">
  <input type="password"
  minlength="4"
  maxlength="8"
  size="8"
  pattern="[0-9a-fA-F]{4,8}"
  title="Coloque HEX no mínimo com 4 caracteres e no máximo 8 caracteres"
  placeholder="Digite sua senha"
  inputmode="numeric"
  autocomplete="on"
  >
  <button type="submit">
</form>
```

### Email

Usando `<input type="email">`, espera-se que o usuário digitel um e-mail. O valor digitado será validado se é referente a um e-mail.

#### Atributos

- placeholder;
- readonly / disabled;
- value;
- required;
- multiple (campo receberá 1 ou mais e-mails, separados por vírgulas);
- minlength / maxlength (valor mínimo/máximo que o campo conterá);
- size (valor numério indicando quantos carecteres esse campo deveria conter, modificando o tamnanho do campo para o usuário);
- pattern (uso de expressão regular para validar o campo, uma sequência de caracteres que serão aceitos e usados para validar se está compatível com a sequência de carecteres. Exemplo: o usuário só poderá colocar e-mail de domínio específico: `pattern=[.+@nomedosite\.com\.br`);
- list (o `id` de uma tag `<datalist>` que está no mesmo documento, contendo uma lista de valores pré-definidos como sugestão para o usuário. Os valores do `<datalist>` que não forem compatíveis com o campo, não serão apresentados como sugestão).

```html
<form action="">
  <datalist id="emails">
    <option>email1@nomedosite.com.br</option>
    <option>email2@nomedosite.com.br</option>
    <option>email3@nomedosite.com.br</option>
  </datalist>

  <input
    type="email"
    placeholder="E-mail"
    required
    multiple
    size="25"
    title="Somente e-mails nomedosite.com.br serão aceitos"
    pattern=".+@nomedosite\.com\.br"
    list="emails"
  />
  <button type="submit">Enviar</button>
</form>
```

### URL

O tipo de input URL espera que o usuário digite uma URL e valida se o valor digitado é compatível.

```html
<input type="url" />
```

Seus atributos são:

- placeholder;
- value;
- readonly / disabled;
- required;
- minlength/maxlength;
- size;
- pattern (validação com a expressão regular. Exemplo: usuário só poderá colocar domínio ".com.br" -- `pattern=".*\.com\.br\/.*` -- a leitura de `.\*` é "qualquer caractere múltiplas vezes);
- list;
- spellcheck (habilita a verificação ortográfica para este input -- se não atribuo true ou false, ele puxa do elemento parent e alguns navegadores já vão deixar habilitados como padrão).

```html
<datalist id="urlsdata">
  <option>https://meusite.com.br</option>
  <option>https://seusite.com.br</option>
  <option>https://qualquersite.com.br</option>
</datalist>

<form action="">
  <input
    type="url"
    placeholder="http://example.com.br"
    pattern=".*\.com\.br.*"
    title="Somente domínios '.com.br' serão aceitos"
    required
    size="30"
    list="urlsdata"
    spellcheck="false"
  />
  <button type="submit">Enviar</button>
</form>
```

### File

```html
<input type="file" />
```

Com esse tipo, o usuário pode escolher um ou mais arquivos para anexar ao formulário e enviar.

Seus atributos são:

- value (contém o arquivo a ser enviado);
- accept (descreve quais tipos de arquivos são aceitos, como: .doc, .pdf, audio/\*, image/png, .png) - vai enviar somente um valor, mesmo se for múltiplo;
- files (lista de arquivo ou arquivos) - onde vai ter a lista dos múltiplos arquivos ainda que se envie somente um;
- multiple (permite envio de múltiplos arquivos, é uma chave boolean. Se não tivesse o multiple, só conseguiria enviar um arquivo por vez).

Para enviar os arquivos, o formulário deverá utilizar o método POST e o atribuo `enctype` como "multipart/form-data". Isso é usado SOMENTE no tipo file.

```html
<form action="">
  <input
    type="file"
    accept="image/*"
    multiple
    method="POST"
    enctype="multipart/form-data"
  />
</form>
<button type="submit">Enviar</button>
```

### Color

É uma interface para selecionar cor, ou seja, é um color picker.

Seus atributos são:

- value (RGB)
  - se a cor for inválida/errada, o preto será exibido, bem como se nenhum value for setado.
- list
  - O id de uma tag `<datalist>` que está no mesmo documento. Irá conter uma lista de valores pré-definidos para ajudar o usuário.

```html
<datalist id="colorssdata">
  <option>#0000FF</option>
  <option>#550226</option>
  <option>#457601</option>
</datalist>

<form action="">
  <input type="color" value="#FF0254" list="colorssdata" />
</form>
```

A tag color não está disponível ao IE e outros navegadores no Android, como Chrome e Firefox.

### Checkbox

São caixinhas que podem ser marcadas. Ou seja, a pessoa seleciona um valor para ser enviado. Caso nenhum valor seja selecionado, não será enviado nenhum dado.

Os atributos são:

- globais
- value
  - valor que aquele campo contém
  - se não estive presente, o padrão é "on"
- checked
  - para deixar o campo marcado por padrão

```html
<label for="subscribe">Receber notificações</label>
<input type="checkbox" name="subscribe" id="subscribe" checked />
```

Para múltiplos valores, utilizamos o atributo name igual:

```html
<fieldset>
  <legend>Choose your interests</legend>
  <div>
    <input type="checkbox" id="music" name="interest" value="music" checked />
    <label for="music">Music</label>
  </div>
  <div>
    <input type="checkbox" id="coding" name="interest" value="coding" />
    <label for="coding">Coding</label>
  </div>
</fieldset>
```

### Hidden

Campo invisível ao usuário, mas será enviado com o formulário.

É um campo que não recebe focus e leitores de tela não percebem esse campo.

Para utilizar, basta criar um campo tipo `hidden`.

Por exemplo, se quero receber o horário que o formulário foi enviado e não deixar o usuário ver isso:

```html
<input type="hidden" id="timestamp" name="timestamp" value="1286705410" />
```

### Radio

Projeto para selecionar uma única opção de um grupo de opções.

Os atributos essenciais são:

- checked (indicando o campo que foi marcado)
- value (valor que aquele campo contém)

```html
<fieldset>
  <legend>Let's have a coffee?</legend>
  <input type="radio" name="coffee" id="yep" value="yes" checked />
  <label for="stay">Yes</label>

  <input type="radio" name="coffee" id="nope" value="no" />
  <label for="go">No</label>
</fieldset>
```

### Textarea

O elemento `<textarea>` é bastante útil para quando precisamos criar campos que necessitem de mais de uma linha, ou seja, é muito utilizado para textos grandes, como caixas para "observações".

Seus atributos são:

- ID (identificar o textarea)
- name (ao enviar o formulário, na recepção o dado chegará com o valor através do name)
- rows e cols
- maxlength / minlength
- wrap (wrap="soft", que é o padrão, ou wrap="off")
- e outros comuns aos inputs:
  - autocomplete, autofocus, disabled, placeholder, readonly, form, required

Lembrando que quando eu tiver um `<label for=""></label>`, o ID vai ser ligado a esse for.

```html
<label for="message">Mensagem</label>

<textarea
  name="message"
  id="message"
  cols="25"
  rows="5"
  maxlength="140"
  minlength="4"
  wrap="on"
  placeholder="Digite sua mensagem aqui..."
></textarea>
```

### Select

O elemento `<select>` é um controle que fornece um menu de opções.

Já o elemento `<option>` faz parte do `<select>` e traz as opções a serem selecionadas. Possui "value" como atribuo necessário.

Ao ser selecionado o valor "não", por exemplo, ele ficará guardado e será enviado pelo formulário ao backend. Algo como `answerselect=nao`.

```html
<label for="answerselect"></label>
<select name="answer" id="answerselect">
  <option value="">Selecione sua resposta</option>
  <option value="sim">Sim</option>
  <option value="nao">Não</option>
  <option value="talvez">Talvez</option>
</select>
```

Para habilitar multiplas opções, basta utilizar o atributo `multiple` no select. Já utilizando `size`, deixo visível quantas opções quero que apareçam:

```html
<label for="carselect">Fábricas de carros</label> <br /><br />
<select name="carmodel" id="carselect" multiple size="2">
  <option value="">Selecione</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
  <option value="toyota">Toyota</option>
  <option value="bmw">BMW</option>
</select>
```

### Optgroup

Sempre vai funcionar dentro do select, pois fará um agrupamento de várias opções dentro dos selects.

É importante sempre colocar o label dentro de optgroup para que a formatação não seja impactada negativamente.

```html
<label>Please choose one or more pets:</label> <br /><br />
<select name="pets" size="6" multiple>
  <optgroup label="4-legged pets">
    <option value="dog">Dog</option>
    <option value="cat">Cat</option>
    <option value="cow">Cow</option>
    <option value="rat" disabled>Rat</option>
  </optgroup>
  <optgroup label="Flying pets">
    <option value="parrot">Parrot</option>
    <option value="macaw">Macaw</option>
    <option value="albatross">Albatross</option>
  </optgroup>
</select>
```

Quando os valores forem passados para o backend, ficarão guardados como `pets=dog,cat,parrot`.

### Search

```html

```

### Number

```html

```

### Range

```html

```

### Data e hora

```html

```
