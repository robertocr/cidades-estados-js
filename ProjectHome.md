## Update ##

27/05/2015
A última versão é a **1.4**, que contempla os exatos 5.570 municípios brasileiros (Muito obrigado, Ian Pacheco!)
Observe o exemplo funcionando com o implementacao-utf8.html e o cidades-estados-1.4-utf8.js

-

Saiu do forno a nova versão **1.2** estável na qual não é mais preciso criar selects obstrusivos. Agora você pode implementar o cidades-estados-js em inputs (type text) ou qualquer outra tag. [Veja a implementação do script funcionando (v1).](http://cidades-estados-js.googlecode.com/files/implementacao-utf8.html)

## Geral ##

A intenção deste projeto é colocar sempre em um único lugar um arquivo javascript que pode ser utilizado em qualquer site para criar duas combo-box (em html, select) com escolha de estados e cidades.

Decidi hospedá-lo no servidor do google porque assim é mais improvável que hajam problemas de servidor em qualquer servidor que eu hospede. Para instalá-lo em seu site, coloque a seguinte instrução entre suas tags head.

```
<script type="text/javascript" src="http://cidades-estados-js.googlecode.com/files/cidades-estados-1.4-utf8.js"></script>
```

Feito isso, a biblioteca está instalada em seu site. O legal é que todos os sites que usarem esta biblioteca usarão o mesmo provedor/servidor. Gravando no cache do usuário o mesmo arquivo, sendo assim, carregado mais rapidamente na próxima vez que o usuário acessar qualquer outro site que tenha referencia para o mesmo arquivo.

Para ativar a biblioteca você pode utilizar os próprios métodos do javascript ou o **dgDomReady** da biblioteca ou mesmo qualquer biblioteca como prototype, mootools ou jQuery.

A forma mais simples de ativar a biblioteca é esta, usando o objeto **dgCidadesEstados** passando os objetos que serão serão usados como select de estados e cidades. Veja um exemplo:

```
<script type="text/javascript">
window.onload = function() {
  new dgCidadesEstados({
    estado: document.getElementById('estado'),
    cidade: document.getElementById('cidade')
  });
}
</script>
```

## dgDomReady ##

**dgDomReady** é um evento auxiliar que executa uma determinada função quando o objeto DOM é carregado. A diferença básica entre window.onload e dgDomReady é que o window.load é executado quando a página é carregada por completo, com as imagens em anexo e os arquivos flash. Já o dgDomReady é executado quando apenas o arquivo html é carregado, sendo assim, mais rápida a execução do que no outro caso. O exemploanterior ficaria assim:

```
<script type="text/javascript">
window.onDomReady(function() {
  new dgCidadesEstados({
    estado: document.getElementById('estado'),
    cidade: document.getElementById('cidade')
  });
});
</script>
```

## Aplicações usando sua biblioteca preferida ##

Em jQuery, o mesmo exemplo poderia ser explicado por:

```
<script type="text/javascript">
$(function() {
  new dgCidadesEstados({
    estado: $('#estado').get(0),
    cidade: $('#cidade').get(0)
  });
});
</script>
```


Prototype:
```
<script type="text/javascript">
Event.observe(window, 'load', function() {
  new dgCidadesEstados({
    estado: $('estado'),
    cidade: $('cidade')
  });
});
<script>
```

## Recuperando os dados ##

Para fazer o sistema recuperar uma informação dada anteriormente, basta passar os parâmetros **estadoValue** e **cidadeValue** dentro do construtor.

```
new dgCidadesEstados({
  cidade: document.getElementById('cidade2'),
  estado: document.getElementById('estado2'),
  estadoVal: 'SP',
  cidadeVal: 'São Paulo'
});
```

Ou então passando como atributo **value** em sua tag select (ou input como descrito mais abaixo).

```
<select id="estado1" value="TO"></select>
<select id="cidade1" value="Araguaína"></select>
```

```
new dgCidadesEstados({
  cidade: document.getElementById('cidade1'),
  estado: document.getElementById('estado1')
});
```

## Obstrusividade?! Não! ##

Não é preciso que você escreva uma tag select, você pode executar usando um input que será substituido pelo select necessário. Para ativar esta opção, basta passar o parâmetro **change**.

```
<input type="text" name="estado3" id="estado3" value="MG" />
<input type="text" name="cidade3" id="cidade3" value="Viçosa" />
```

```
new dgCidadesEstados({
  cidade: document.getElementById('cidade3'),
  estado: document.getElementById('estado3'),
  change: true
});
```

## Charset?! ##

Você não precisa se preocupar em codificação de caracteres, o cidades-estados-js é disponibilizado nas versões Latin (ANSII) e UTF-8. Para isso, basta alterar a forma como você chama a biblioteca.

```
<script type="text/javascript" src="http://cidades-estados-js.googlecode.com/files/cidades-estados-1.0-utf8.js"></script>
```

```
<script type="text/javascript" src="http://cidades-estados-js.googlecode.com/files/cidades-estados-1.0.js"></script>
```

Dê preferencia a usar o charset utf-8, mas se seu sistema não aceitar essa codificação ou você usa DreamWeaver e nem sabe o que é isso, provavelmente você vai precisar da versão em ASCII. ;D

**Nota:** Vale a pena ler o [artigo sobre intercacionalização de caracteres](http://www.w3.org/International/O-charset.pt-br.php) da w3c que explica mais sobre codificação, inclusive o utf-8.


---


## update ##

Na versão 0.2 podemos pedir para o plugin inseir os valores de estados quando carregar o plugin. Para isto, basta inserir um terceiro parâmetro (true) na criação do objeto.

Usando como base a função cifrão ($) como:

```
function $(elm){
  return document.getElementById(elm);
}
```

Chamamos a função de inicialização assim. Onde o _true_ indica que queremos que sejam preenchidos os estados automaticamente.

```
new dgCidadesEstados($('estado'), $('cidade'), true);
```


---


## todo ##

~~Automatizar o estado e cidade. Assim a cidade e o estado aparecerão já marcados com um único comando.~~

~~Criar os devidos elementos, assim pode-se criar a partir de inputs text para gerar os selects dinamicamente, acabando com o problema de javascript desabilitado.~~

Implementar plugin para Dreamweaver.