# Guia geral de Acessibilidade

### Como usar corretamente o atributo `alt` da imagem

Em algum momento, aprendemos que os atributos `alt` são importantes, então todos começaram a preenchê-los sempre que houvesse uma imagem, mas na verdade eles também precisam seguir algumas regras e dicas úteis:

* Se a imagem tiver um texto próximo a ele que explique a imagem (como uma legenda), o atributo `alt` deverá estar vazio (mas ainda apresentado no elemento `img`);
* As imagens que são links devem ter o `alt` para descrever para onde vão. Por exemplo, um botão que envia o usuário à página Produto deve ter `alt= "Página do produto"`;
* Porém, se a imagem fizer parte de um link âncora que possui um atributo de texto sem formatação, ou texto oculto visualmente, ou se houver rótulo de ária, o atributo `alt` da imagem deve então estar vazio;
* Se a imagem for completamente decorativa, deixe o `alt` vazio;
* Ao usar imagens que contenham texto breve, ou no caso de um logotipo da empresa, o contexto do atributo `alt` deve ser o de explicar a própria imagem ou a ação que a imagem possui, portanto `alt= "Logotipo do Paypal"` está incorreta, deve ser apenas `alt= "Paypal"`;
* Não use as palavras "foto de .." ou "imagem .." na propriedade `alt` da imagem, as tecnologias assistivas já anunciam isso, então você está apenas criando redundância e repetição;
* Nunca tente simular quebras de linha no texto alternativo, pois isso causa problemas nos leitores de tela.

### Formulários

Os formulários são uma parte muito importante dos websites, e existem algumas opções comuns de desenvolvimento que,
infelizmente, cria muitas violações de acessibilidade.

#### 1. Fieldsets

Não use `<fieldset>` em torno de formulários que possuem apenas UM campo de entrada (o `button` não conta).
O `<fieldset>` deve ser usado apenas para agrupar vários campos com um objetivo comum, por exemplo, ao ter 3 elementos selecionados para definir uma data de nascimento, uma lista de botões de opção ou caixas de seleção com várias opções.
Você pode ter vários `<fieldset>` no mesmo formulário, se necessário.

#### 2. Use `labels` apropriadas. O texto do `placeholder` não as substitui

`labels` são elementos muito importantes para a acessibilidade, pois são a principal forma de o usuário com deficiência entender e poder usar os formulários.

Uma opção de design comum é usar apenas o `placeholder` do campo e sem `labels`, mas infelizmente o `placeholder` NÃO é visível para leitores de tela, portanto, isso é uma violação das WCAG.

Para resolver esse problema, siga o uso básico de `labels`:
* Adicione o elemento `<label>` adequado;
* Se, devido a opções de design, o site não puder ter `labels` visíveis, adicione-as usando uma classe que oculte a `label`visualmente;
* Lembre-se de que o rótulo deve ter um atributo `for` vinculado ao `ID` de do atributo `input`.

#### 3. Evite usar bibliotecas e plugins JS para ter elementos `<select>` customizados

Algo que se tornou muito comum nos sites é usar algum plugin para substituir o elemento nativo `<select>` e simulá-lo usando `divs` ou `ul > li`.

Infelizmente, independentemente do que essas páginas de plug-in digam, elas não estão em conformidade com os padrões de acessibilidade, porque mesmo que você possa usá-los com navegação no teclado, eles simulam e implementam esses recursos de maneira incorreta e não-nativa.

Como resolver: A maneira mais simples e de longe a mais recomendada é abandonar completamente os plugins e apenas usar o
elemento HTML nativo padrão `<select>`.

É claro que os clientes/designers não vão gostar, porque existem algumas limitações no que pode ser estilizado por eles, mas se a acessibilidade for um requisito, então é a direção mais simples.

Falando sobre as limitações dos elementos `<select>` nativos, você pode estilizar apenas a seleção em si, definindo o tamanho do texto, a borda, o preenchimento, etc.

É possível trabalhar com estilos e padronizar o elemento *arrow* entre navegadores e dispositivos.

Como sabemos, não há muita personalização para o elemento `option` quando expandido, pois eles são tratados como um elemento do sistema. Os únicos atributos que eles usarão do CSS são:

* As propriedades da fonte como tamanho, família, peso e cor (altura da linha ou qualquer outra propriedade para adicionar espaço entre os itens não funcionarão. solução alternativa é ter opções vazias + desativadas + ocultas por ária entre elas);

* Cor de fundo para toda a lista, com uma cor diferente para a selecionada, se desejado.

Infelizmente, esse é o principal motivo pelo qual alguns designers/clientes exigem o uso de plug-ins, pois não gostam da aparência do elemento `option` padrão.
