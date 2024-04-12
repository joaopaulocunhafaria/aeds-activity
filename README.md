<h1 align="center">ANÁLISE ASSINTÓTICA E CUSTO COMPUTACIONAL</h1>
<div align="center"> <img height="50px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/e23053b2-63e7-486c-aaf0-11bb4a30fd3c">
 </div>
<h3>Sumário</h3>
<ul>
 <li><strong>Introdução</strong></li>
    <li><strong>Descrição da resolução</strong></li>
    <li><strong>Exposição dos algoritmos de teste</strong></li>
    <li><strong>Exposição dos dados de entrada</strong></li>
    <li><strong>Condições de análise</strong></li>
    <li><strong>Resultados e conclusões</strong></li>
    <li><strong>Ferramentas usadas</strong></li>
    <li><strong>Organização do codigo</strong></li>
    <li><strong>Referências</strong></li>
</ul>

 <hr>
<h2 align="center">Introdução</h2>
<p align="center">"A análise de desempenho é uma etapa fundamental na concepção de um algoritmo. Diante de um problema computacional, diversas soluções podem ser propostas. Por exemplo, para ordenar uma sequência de números, o desenvolvedor pode utilizar algoritmos como o BubbleSort, MergeSort, QuickSort, entre outros. Entender como esses algoritmos se comportam à medida que aumentamos o tamanho da entrada a ser ordenada é primordial para decidirmos qual solução adotar em um determinado contexto.</p>

<p align="center">
 
 Analisar um algoritmo significa prever a quantidade de recursos que tal algoritmo consome ao ser executado. Diversas variáveis podem ser objetos de estudo da análise de um algoritmo, por exemplo, consumo de memória, largura de banda de comunicação, entre outros."
(Brunet, 2019)[^1]

</p>



 
<p align="center">Contudo, com frequência, desejamos medir o tempo de execução de um programa em um ambiente controlado e a isso damos o nome de abordagem empírica. Neste contexto, este projeto tem o objetivo de calcular e realizar comparações a respeito de algoritmos que descobrem valores máximos e mínimos em uma base de dados de tamanhos e com ordenações diversas, fazendo uso de três algoritmos formulados de maneiras diferentes, afim de chegar à conclusão de qual deles tem a melhor performance e em quais situações eles se encaixam melhor.</p>
<hr>
<h2 align="center">Descrição da resolucao</h2>
<p align="center">Para tratar adequadamente e chegar às conclusões necessárias quanto à eficiência comparada dos três algoritmos que serão apresentados, a abordagem tomada será a seguinte: serão utilizadas diferentes entradas de dados de tamanhos e ordenações variados. Isso permitirá entender se algum algoritmo tem melhor desempenho em condições específicas, se a eficiência dos algoritmos é independente da ordenação e se existem outras condições que possam interferir no desempenho deles. Para obter uma medida justa do tempo gasto por cada algoritmo em cada situação abordada, será calculado o tempo gasto em cada condição específica de ordenação e tamanho da entrada de dados separadamente.</p>

<p align="center">A forma como será calculado o tempo gasto por cada algoritmo durante sua execução será utilizando a biblioteca padrão da linguagem <strong>C++</strong> <strong>CHRONO</strong>, que é amplamente usada para medição de tempo em programas escritos em C ou C++.</p>

<p align="center">Segue um pseudocódigo de como será feita a medição de tempo. A implementação do mesmo em C++ pode ser encontrado no arquivo <a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/3ae698a2457c64b05d1a82c79345a307ce762a78/AEDS/min_max/src/minMax.cpp#L10">minMax.cpp</a> na linha 10</p>

<div align="center"><img align="center" height="160px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/794be396-1b00-454d-9ce4-cda8efcfbf0d"></div>

</div><p align="center">Dessa forma, obtendo o tempo de execução de cada algoritmo individualmente, poderemos chegar às conclusões necessárias quanto ao custo computacional e análise assintótica dos algoritmos de estudo.</p>

<hr>
<h2 align="center">Exposição dos algoritmos de teste</h2>

<p align="center">
    Como dito anteriormente, os algoritmos a serem analisados executam a tarefa de encontrar um menor e um maior valor dentro de uma base de dados de <strong>n</strong> posições.
    As bases de dados serão vetores preenchidos com números de 1 a 1000.
    Adiante, será esclarecido como serão dispostos tais vetores.
    Faremos uso de três algoritmos que, embora realizem a mesma operação, o fazem de maneiras diferentes.
</p>

<h3 align="center">ALGORITMO 1 - MINMAX 1</h3>

<p align="center">
    O primeiro algoritmo, chamado <strong>minmax1</strong>, realiza sua função de maneira bem simples,
    fazendo com que, dentre os três algoritmos com os quais trabalharemos, ele seja o de menor complexidade
    e também, logicamente, o de implementação mais simples.
    A implementação deste algoritmo em C++ pode ser encontrada na linha 7 do arquivo 
    <a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/7c8fc1f23c02af0dcf4a43c28427759ad79c92e7/AEDS/min_max/src/minMax.cpp#L7">
        <strong>minMax.cpp</strong>
    </a> 
    dentro da pasta <strong>src</strong>.
</p>

<div align="center">
    <img height="150px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/9777f4f1-0753-4a7e-8d3a-00dccceeb351">
    <p>
    
Implementação em COBOL do <strong>minmax1</strong>. (Loureiro A.A.F, 2010)[^2] 
     
</p>
</div>

</div><h3 align="center">ALGORITMO 2 - MINMAX 2</h3>

<p align="center">
    Seguindo um caminho lógico bem semelhante ao primeiro algoritmo, a segunda versão apresenta uma solução um pouco mais elaborada.
    Diferenciando-se apenas na condição de que, ao invés de em cada iteração serem realizadas duas comparações, ele envolve o código com uma condicional <em>if</em> e uma segunda condição <em>else if</em>.
    Dessa forma, em alguns casos, principalmente devido à ordenação dos vetores, será feita durante cada iteração apenas uma única comparação ao invés das duas que sempre são feitas no primeiro caso. Isso consequentemente economiza processamento, visto que o número de instruções realizadas pela máquina é menor. Tal diferença pode causar grandes impactos, principalmente em quantidades massivas de dados.
</p>
<p align="center">A implementacao em C++ da segunda versao do algoritimo pode ser encontrada na linha 34, tambem no arquivo <a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/7c8fc1f23c02af0dcf4a43c28427759ad79c92e7/AEDS/min_max/src/minMax.cpp#L34"><strong>minMax.cpp</strong></a></p>
<div align="center" >
    <img height="150px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/f6590068-4822-4945-901a-58cfd9a33649">
   <p>
    
   Implementação em COBOL do <strong>minmax2</strong>. (Loureiro A.A.F, 2010)[^2] 
    </p>
</div>
</div><h3 align="center">ALGORITMO 3 - MINMAX 3</h3>

<p align="center">
   Seguindo uma abordagem um pouco diferente dos dois primeiros algoritmos, a terceira versão opta por uma abordagem com maior complexidade lógica e de implementação, mas que pode trazer algumas vantagens, novamente em decorrência da organização da massa de dados de entrada. Nesta implementação, o algoritmo utiliza-se de duas comparações consecutivas das posições <em>i</em> e <em>i+1</em> em cada iteração, reduzindo, como que pela metade, a quantidade final de interações realizadas pelo algoritmo.
</p>
<p align="center">A implementação em C++ da terceira versão do algoritmo pode ser encontrada na linha 62, no arquivo <a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/7ba8c27063c41bf034e8e99e1f3fd7f01ef862fd/AEDS/min_max/src/minMax.cpp#L62"><strong>minMax.cpp</strong></a></p>

<div align="center" >
    <img height="300px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/b3e6e628-471a-4d05-a0b3-58de38b7a659">
 <img height="290px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/447a3360-4955-400a-898b-ac76d7bd4db0">
 
 <p>
 
  Implementação em COBOL do <strong>minmax3</strong>. (Loureiro A.A.F, 2010)[^2] 
 </p>
</div>
<hr>
<h2 align="center">Exposição dos dados de entradas</h2>
<p align="center">Com o intuito de melhor testar cada algoritmo de modo a expor cada um deles em uma gama de testes mais diversa, as entradas de dados serão distribuídas da seguinte forma:</p>
 <table border="1" align="center">
      <tr>
        <td>Tamanho da entrada <strong>n</strong></td>
        <td>Ordenações</td>
      </tr>
      <tr>
        <td>1000</td>
        <td>Aleatório, crescente, decrescente</td>
      </tr>
      <tr>
        <td>10000</td>
        <td>Aleatório, crescente, decrescente</td>
      </tr>
      <tr>
        <td>100000</td>
        <td>Aleatório, crescente, decrescente</td>
      </tr>
        <tr>
        <td>500000</td>
        <td>Aleatório, crescente, decrescente</td>
      </tr>
     
 </table>

 <p align="center">Com os números que compõem cada entrada variando de 0 a 1000, as mesmas serão construídas primeiramente inicializando um vetor com números aleatórios de 0 a 1000 e depois ordenando cada um conforme mostrado acima, de modo crescente e decrescente, exceto, é claro, aquela entrada de dados que será aleatória, ou seja, sem ordenação.</p>
<hr> 
<h2 align="center">Condições de análise</h2>
<p align="center">Visando sempre os melhores resultados possíveis e, novamente, com o intuito de testar bem cada algoritmo, as condições de análise serão impostas para que os resultados não sejam afetados por condições que não as presentes nos próprios algoritmos.</p>
<p align="center">Dessa forma, o tempo considerado para análise de cada algoritmo será a média calculada entre dez execuções. Assim, cada algoritmo com cada ordenação e tamanho de dados será testado dez vezes e terá suas médias calculadas para que se obtenha um resultado final.</p>
<p align="center">Somado a isso, as condições da máquina de teste são outra característica que pode interferir de maneira considerável no tempo de execução de cada algoritmo. Embora, de modo geral, as condições e o desempenho de cada um possam ser tomados de maneira comum a todos, fazendo com que mesmo tendo diferenças de tempo devido ao hardware, as devidas proposições sempre são guardadas, fazendo com que nenhum sobreponha outro por estar em um ambiente diferente.</p>
 <p align="center">Este projeto foi testado no seguinte ambiente:</p>

     
     
     
 <table border="1" align="center">
      <tr>
        <td>Sistema Operacional </td>
        <td>Debian 12 - "Bookworm"</td>
      </tr>
      <tr>
        <td>Compilador </td>
        <td>G++ 12.2.0</td>
      </tr>
      <tr>
        <td>Hardware </td>
        <td>11th Gen Intel(R) Core(TM) i5-11400H @ 2.70GHz, 8GB RAM, 512GB SSD</td>
      </tr>   
 </table>
<hr>
<h2 align="center">Resultados e conclusões</h2>

<p align="center">
 
 Tomando a literatura como base para termos noção do que esperar da análise prática, utilizaremos as conclusões teóricas presentes no material de aula do professor Loureiro A.A.F[^2], já citado acima. De acordo com os resultados apresentados pelo professor, o custo assintótico de cada um dos três algoritmos, já apresentados, nos três casos possíveis que são o melhor caso, pior caso e caso médio, são os seguintes:</p>

<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/07a16d2c-eb19-4a19-8d4d-fc9e8550f73f" height="100px">
 
 <p align="center">
  
  Loureiro A.A.F, 2010[^2]
 </p>

</div>

<p align="center">A partir desses resultados, podemos supor que cada algoritmo pode apresentar um desempenho melhor ou pior, dependendo do caso em que está executando. Os "casos" neste trabalho serão as formas como as massas de dados estão organizadas. Analisando os resultados do custo assintótico de cada algoritmo, percebemos que o <strong>minmax1</strong> e o <strong>minmax3</strong> possuem um custo linear, ou seja, não se alteram em relação aos casos, e também que o <strong>minmax3</strong> apresenta um resultado ligeiramente melhor que o <strong>minmax1</strong>. O <strong>minmax2</strong>, por sua vez, possui um custo que pode variar conforme o caso em que está executando. Tal variação pode fazer com que ele tenha uma performance melhor ou pior que os demais, dependendo do caso.</p>

<p align="center">Tendo agora um aparato teórico com o qual podemos nos basear e saber o que esperar, vamos agora para os resultados práticos. Para melhor analisarmos a eficiência e o custo de cada algoritmo, iremos dividir os testes segundo a ordenação de dados. Primeiramente, iremos analisar os resultados para os testes feitos com a massa de dados ordenada crescentemente.</p>

<h4 align="center">Crescente</h4>

<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/be20488a-a255-4712-be30-e2df32fbc0ba" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/561e1556-e954-4208-86a3-eb8b1e72df46" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/e0169ba6-b573-4283-a8db-52e8e93e6011" height="200px">
</div>
<p align="center">Em uma análise puramente empírica, através da interpretação dos gráficos, podemos notar que o desempenho dos algoritmos 1, 2 e 3 em uma massa de dados ordenada de forma crescente não difere de maneira expressiva, principalmente se tratando dos casos onde a quantidade de dados de entrada é inferior a 1000. A partir dessa quantidade de dados de entrada, começa-se a perceber diferenças no desempenho de cada um, embora ainda de forma bem ínfima, onde podemos notar um melhor resultado do algoritmo 3 em comparação com os demais. Contudo, é interessante notar que a diferença de um resultado para o outro está na casa dos microssegundos e tais diferenças tão mínimas podem ocorrer por diversos motivos, como o simples fato de que a temperatura do processador em um ou outro teste pode ser superior, o que por sua vez ocasionaria resultados inferiores, e isso é apenas uma das diversas possíveis causas que podem afetar o desempenho dos algoritmos.</p>

<p align="center">Realizando uma nova bateria de testes e colocando os resultados em um mesmo gráfico pode nos fornecer uma perspectiva diferente da análise dos algoritmos.</p>

<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/03cdc72f-f8a0-4622-aa08-15a661a1eddf" height="250px">
</div>
<p align="center">Interpretando tais resultados, podemos chegar a conclusões parecidas com as expostas logo acima. Todavia, há ainda alguns fatos a serem apontados que são extraídos do seguinte gráfico, como o fato de que nesta sequência de execuções o algoritmo 1 apresentou um resultado inferior aos outros dois. Mesmo se tratando de uma diferença de microssegundos, seria algo inesperado, uma vez que os comportamentos apresentados pelo minmax1 no primeiro teste foram bem semelhantes aos demais. Guardaremos tal questionamento para depois de feitas todas as análises.</p>

 

<h4 align="center">Decrescente</h4>



<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/8d2508e3-e6a0-42ef-8495-aeab0a3eda93" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/47eed561-a5b1-4532-8cf2-4f479fc148aa" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/637444bb-38c7-44d8-aff1-40cb7392155f" height="200px">
</div>
<p align="center">
 
 Tratando agora de uma massa de dados organizada de forma decrescente, nossos algoritmos apresentaram um resultado mais condizente com a tabela de custos assintóticos apresentada pelo professor LOUREIRO, A.F[^2]. Dentre os três algoritmos, o minmax3 apresentou um melhor desempenho em relação aos outros dois, mantendo a condição de que o desempenho de todos os algoritmos é bastante semelhante quando se trata de uma massa de dados menor que 1000 ou 10000 elementos. Nota-se também que o minmax1, assim como tivemos no primeiro caso, apresentou um resultado inferior.
 
</p>
<p align="center">Tomando uma abordagem semelhante ao primeiro caso de ordenação, iremos analisar uma nova sequência de testes realizados e expostos no mesmo gráfico, a fim de termos mais material para realizarmos nossa análise.</p>


<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/d3531e42-7a38-4de1-b0e3-e98c030f803a" height="250px">
</div>
<p align="center">Como bem podemos inferir do gráfico aqui exposto, fica claro que, também nesta ocasião, o algoritmo minmax3 tem um melhor desempenho do que os demais e que o algoritmo minmax1, novamente, é aquele que apresenta o pior resultado. Logicamente, o minmax2 é aquele que apresenta um resultado intermediário, superando o minmax1 e sendo inferior ao minmax3.</p>


<h4 align="center">Aleatório</h4>
<p align="center">Agora, para finalizarmos a exposição de resultados, analisaremos a massa de dados disposta de maneira aleatória.</p>


<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/d71ade5a-481e-49c6-8c43-90f1bbdf00d8" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/11250291-9bfe-4fb4-9d50-a684bd64092e" height="200px">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/de3458ad-9c23-4a2e-903b-5f057c9b1161" height="200px">
</div>
<p align="center">Diferentemente dos primeiros casos, aqui podemos tirar conclusões distintas das duas iniciais. Primeiramente, fica claro que neste caso o algoritmo minmax3 teve o pior desempenho dentre todos, o que vai na contramão do que foi apresentado nos dois primeiros casos. Logo após, percebemos que, também em oposição ao que foi analisado nos dois primeiros casos, o algoritmo minmax1 foi aquele que apresentou o melhor desempenho, superando também o minmax2.</p>

<p align="center">Seguindo o padrão já exposto, vejamos uma nova bateria de testes onde foram plotados todos os algoritmos em um só gráfico.</p>

<div align="center">
    <img src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/f4d245be-bf15-4fae-a490-2df1c71c49cd" height="250px">
</div>

<p align="center">Com esses resultados expostos, fica nítido aquilo que inferimos dos gráficos acima, onde foram plotados os desempenhos de cada algoritmo de maneira separada. Vemos aqui que o minmax1 teve um melhor desempenho e que o minmax3, por sua vez, apresentou o pior desempenho. Tais conclusões diferem de forma enfática daquilo que inferimos dos dois primeiros casos. Nota-se também que para essa organização, diferentemente das demais, os casos onde a massa de dados está entre 1000 e 10000 inidades apresentaram resultados mais dispersos e não todos centrados na mesma quantidade de microssegundos.</p>

<h4 align="center">Conclusoes gerais</h4>

<p align="center">
 
 A partir das análises feitas acima, podemos chegar a algumas conclusões que são de suma importância para a boa compreensão do cálculo de custo computacional e análise assintótica. Primeiramente, é importante notar que, embora em um ambiente controlado onde todos os algoritmos foram executados e tiveram seus tempos de execução calculados da mesma forma, ainda sim as condições físicas da máquina podem interferir no tempo final de execução de cada algoritmo.

Um segundo ponto importante a se perceber é o fato de que todos os algoritmos tiveram tempos diferentes como resultados, porém toda a divergência se encontra na faixa dos microssegundos na maior parte dos casos.

Partindo para uma conclusão prática de cada algoritmo, podemos começar citando novamente o professor LOUREIRO, A. F[^2], mais especificamente a tabela de custos exposta no material de sua aula. Fato é que os algoritmos apresentaram resultados realmente coerentes com o que está explicitado na tabela, embora, logicamente, houvesse casos em que os resultados divergiram.

Feitas as seguintes considerações, um resultado claro que nossos testes não proporcionaram foi o fato de que a ordenação da massa de dados influencia significativamente na eficiência de cada algoritmo. Nos testes realizados nas massas de dados organizadas de forma crescente e decrescente, os resultados para uma maior quantidade de dados, 500.000, ficaram entre 10 e 14 microssegundos. Já para aqueles realizados nas massas de dados dispostas de forma aleatória, os resultados variam de 11 microssegundos até aproximadamente 37 microssegundos, dando ênfase no MinMax 3, que foi o algoritmo que obteve piores resultados nesta condição de ordenação.

 Contudo, o MinMax 3 obteve o melhor desempenho dentre todos, se consideradas apenas as duas primeiras ordenações, crescente e decrescente. Logo, fica claro que, embora a forma como um algoritmo lida com determinado problema seja de grande impacto para o bom desempenho de suas funções, uma vez que se possui diferentes algoritmos que lidam com um mesmo problema de forma semelhante, divergindo-se apenas em alguns pontos, fatores externos aos próprios algoritmos podem surtir um impacto maior do que apenas a lógica por trás da resolução do problema implementada por determinado algoritmo.

Um fator primordial que alterou grandemente a eficácia dos nossos testes foi a maneira como estavam ordenadas as massas de dados, fazendo com que surgissem resultados diferentes para cada caso. No caso em que os dados estavam dispostos de maneira aleatória, o resultado obtido foi divergente em relação aos demais, fazendo com que o MinMax 3 apresentasse pior desempenho, sendo que nas outras condicoes o resultado foi o oposto.

Para finalizarmos e tirarmos uma conclusão final do nosso estudo, não iremos apontar qual dos três algoritmos obteve o melhor desempenho, uma vez que os resultados favoreceram e desfavoreceram a todos em determinadas ocasiões. Afirmaremos então que a análise empírica de algoritmos, que é realizada calculando o tempo de execução dos mesmos, pode nos fornecer bons resultados para tomarmos como base, mas nunca resultados incontestáveis de suas performances. Isso ocorre porque é fisicamente impossível testar algoritmos diferentes nas mesmas condições. Por exemplo, é conhecido que uma mudança efêmera nas condições térmicas de um mesmo processador pode alterar os resultados de uma execução, e isso citando apenas uma única condição física que pode ser alterada durante o processo de testes.

Em casos onde se necessita apenas de uma noção superficial de qual algoritmo teria um melhor desempenho em determinada condição, tal abordagem pode ser proveitosa. Contudo, no estudo aprofundado de análise assintótica e custo computacional, se guiar pela literatura e pelos conceitos já definidos é de maior proveito e maior confiabilidade em comparação com o uso de uma abordagem empírica  que, a depender do hambiente e das condições de teste, pode apresentar resultados não confiaveis e/ou instáveis.    
 
 </p>

<hr>
<h2 align="center">Ferramentas usadas</h2>
<p align="center">Para a plotagem dos gráficos que foram utilizados para melhor analisar os resultados deste estudo, foi utilizada a ferramenta <strong>GNUPLOT</strong>, amplamente utilizada para representar funções matemáticas, dados experimentais e simulações numéricas. O Gnuplot é executado em uma variedade de plataformas, incluindo sistemas operacionais UNIX, Linux, Windows e macOS. Para a plotagem de gráficos personalizados utilizando Gnuplot, uma das maneiras de realizar tal tarefa é criando um <strong>script</strong> com a extensão <em>.gp</em> e fornecendo uma base de dados que será utilizada para plotar os pontos e as linhas no gráfico. Através deste script, o usuário da ferramenta consegue definir diferentes características do gráfico e montá-lo da forma que melhor lhe seja conveniente. Logo após, ainda no mesmo diretório onde está localizado o <strong>script</strong>, deve-se executar o comando <code>gnuplot</code> seguido do nome do seu arquivo com a extensão <em>.gp</em>. Tal comando irá gerar seu gráfico da maneira como você definiu ao criar o <strong>script</strong>.</p>

<h4 align="center">Scripts utilizados</h4>
<p align="center">Neste projeto, foram utilizados dois scripts diferentes para geração dos gráficos, que foram alterados conforme as necessidades aparentes. Ambos podem ser encontrados na pasta raiz deste repositório, nomeados como <em><a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/main/AEDS/min_max/plot.gp">plot.gp</a></em> e <em><a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/main/AEDS/min_max/plot2.gp">plot2.gp</a></em>. O primeiro script foi utilizado para gerar gráficos com apenas uma linha, enquanto o segundo foi utilizado para plotar gráficos com mais de uma linha.</p>

<hr>
<h4 align="center"><strong>Organização do código</strong></h4>
<p align="center">Para testar adequadamente os algoritmos do nosso estudo, cada um dos que foram apresentados na seção <strong>Exposição dos algoritmos de teste</strong> foi implementado em C++, como já mencionado anteriormente. Após realizar o cálculo de tempo, os resultados obtidos são escritos no arquivo <code>data.txt</code>, possibilitando a geração de gráficos para análise utilizando a ferramenta <em>gnuplot</em>. O resultado de cada execução também pode ser conferido através do arquivo <code>results.txt</code>, que guarda uma relação da última execução feita pelo programa e/ou através do arquivo <code>results.csv</code>, que por sua vez guarda os resultados em um arquivo compatível com o formato padrão do Excel.

</p>

<p align="center">A separação de funções no código criado para o estudo se deu da seguinte forma: as classes <code>minMax.hpp</code> e <code>minMax.cpp</code> ficaram responsáveis pela execução e cálculo de tempo dos testes; as classes <code>results.hpp</code> e <code>results.cpp</code> ficaram responsáveis pela escrita dos dados nos arquivos. Para a geração de gráficos com múltiplas linhas, os dados de saída foram armazenados em arquivos diferentes, cada um condizente com a organização da massa de dados de entrada. Esses arquivos são <code>crescente.txt</code>, <code>decrescente.txt</code> e <code>aleatorio.txt</code>.
</p><p align="center">Para os leitores que desejam realizar os testes em suas próprias máquinas, dentro do arquivo <code>minMax.cpp</code>, mais especificamente na função <a href="https://github.com/joaopaulocunhafaria/Faculdade/blob/2bf82a008388f45fffeb015893ca8d68ea56cd54/AEDS/min_max/src/minMax.cpp#L258">manage_executions</a>, podem ser encontradas instruções detalhadas sobre como modificar o código-fonte para executar os testes desejados pelo usuário.</p>
<h3 align="center">COMPILAR E EXECUTAR</h3>
<table border="1" align="center">
      <tr>
        <td>Comando</td>
        <td>Função</td>
      </tr>
      <tr>
        <td>make clean</td>
        <td>Apaga a última compilação realizada contida na pasta build</td>
      </tr>
      <tr>
        <td>make</td>
        <td>Executa a compilação do programa utilizando o gcc, e o resultado vai para a pasta build</td>  
      </tr>
      <tr>
        <td>make run</td>
        <td>Executa o programa da pasta build após a realização da compilação</td>
      </tr>  
    </table>

<hr>


<h2>Contato</h2>
<div><a href="https://www.linkedin.com/public-profile/settings?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_self_edit_contact-info%3BObdM58vxRxmAhVnA76lGBQ%3D%3D"><img  height="25px" src="https://github.com/joaopaulocunhafaria/Faculdade/assets/138056835/03a2e495-7b32-4f8e-93d6-c90963460432"></a></div>
<h2 align="center">Referências</h2>

[^1]: BRUNET, J. A. Introdução à Análise de Algoritmos. Disponivel em: https://joaoarthurbm.github.io/eda/posts/introducao-a-analise/ . Acesso em 10/04/2024
[^2]: LOURERO, A. F.  PROJETO E ANÁLISE DE ALGORITMOS . Disponivel em:  https://homepages.dcc.ufmg.br/~loureiro/alg/091/paa_Analise.pdf. Acesso em 10/04/2024
