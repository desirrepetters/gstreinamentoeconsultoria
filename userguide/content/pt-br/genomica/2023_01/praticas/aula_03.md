---
title: "Aula 03 - Anotação de sequências repetitivas"
linkTitle: "Aula 03 - Anotação de sequências repetitivas"
weight: 2
description: >
  Softwares utilizados: RepeatModeler, RepeatMasker, ISfinder
---
<div align="justify">
Após a avaliação da qualidade das montagens de genomas de interesse, é hora de prospectar e avaliar as sequências em busca de sequências de relevância evolutiva, funcional e estrutural, tais como genes e sequências repetitivas. Neste momento, iremos avaliar a presença de sequências repetitivas e elementos transponíveis em montagens de genomas, para realizar a anotação e marcação destas sequências antes de prosseguir para as etapas de predição gênica. 
<br><br>
Para este tutorial, acessaremos o <a href="https://www.ncbi.nlm.nih.gov/assembly">NCBI Assembly</a> para download de montagens de genomas e utilizaremos os softwares RepeatModeler, RepeatMasker (<a href="https://usegalaxy.eu/">na versão online no Galaxy</a> ou instalados em uma distribuição Linux), bem como a versão online do <a href="https://www-is.biotoul.fr/index.php">ISfinder</a>. Se você ainda não tem estes softwares instalados, pode encontrar instruções <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/download/">aqui</a>.
<br><br>
Ao utilizar estes softwares e servidores, cite as seguintes referências ou agradecimentos em seu trabalho:
<br><br>
<table style="text-align:center; vertical-align:middle;">
  <tr>
    <th><strong>Software</strong></th>
	<th width="650" ><strong>Referência / Agradecimento</strong></th>
  <tr>
    <td>Galaxy Europe</td>
    <td><i>“The authors acknowledge the support of the Freiburg Galaxy Team: Person X and Björn Grüning, Bioinformatics, University of Freiburg (Germany) funded by the <a href="http://www.sfb992.uni-freiburg.de/">Collaborative Research Centre 992 Medical Epigenetics</a> (<a href="http://www.dfg.de/">DFG</a> grant SFB 992/1 2012) and the German Federal Ministry of Education and Research <a href="http://www.bmbf.de/">BMBF</a> grant 031 A538A <a href="https://www.denbi.de/">de.NBI</a>-RBC.”</i><br><br></td>
  </tr>
</table> 
<br><br>
Há diversas diferenças em relação aos processos de detecção de sequências repetitivas em genomas procarióticos e eucarióticos, bem como diferenças nas abordagens para anotação desta sequências nos genomas eucarióticos. Em função da grande diversidade destes tipos de elementos em genomas eucarióticos, existem vários softwares especializados em estratégias <i>de novo</i>, baseadas em homologia ou repetitividade, bem como abordagens híbridas, detectando vários tipos de elementos transponíveis e sequências repetitivas. Já para genomas procarióticos, em geral os softwares focam na detecção de sequências de inserção. Sendo assim, neste tutorial abordaremos a detecção de sequências repetitivas em genomas procarióticos e eucarióticos separadamente.
<br><br>
Clique no link abaixo para acessar as páginas do NCBI Assembly que contém os arquivos que serão utilizados nesta prática:
<br><br>
<ul>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_003018515.1/">Montagem de genoma de <i>Escherichia coli</i> (linhagem 2013C-3996)</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_023614315.1/">Montagem de genoma de <i>Streptomyces sudanensis</i> (linhagem SD 504)</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_009193405.1/">Montagem de genoma da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i></a>
</ul>
Nesta atividade prática iremos:
<br><br>
<ul>
<li>Detectar sequências repetitivas na montagem de genoma linhagem CBS 120486 de <i>Phyllosticta citriasiana</i>, obtida a partir de montagem utilizando reads de Illumina</li>
<li>Detectar sequências repetitivas na montagem de genoma linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>, obtida a partir de montagem utilizando reads de PacBio</li>
<li>Detectar sequências de inserção em montagens de genomas procarióticos (linhagem 2013C-3996 de <i>Escherichia coli</i> e linhagem SD 504 de <i>Streptomyces sudanensis</i></li>
</ul>
Após a realização destas etapas, utilizaremos os arquivos obtidos para as <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/praticas/aula_04">atividades práticas de predição e anotação de genes</a>
</div>

## Preparo de biblioteca de sequências consenso com o RepeatModeler

<div align="justify">
Umas das primeiras e mais importantes etapas para a anotação de sequências repetitivas é o uso de uma biblioteca adequada de sequências de referência, para garantir que o máximo de sequências repetitivas e elementos transponíveis sejam detectadas no genoma de interesse. Nesta etapa, é possível trabalhar tanto com bibliotecas já disponíveis na literatura, bem como construir uma biblioteca inicial a partir do próprio genoma de interesse, e utilizar esta biblioteca numa nova rodada de anotação. 
<br><br>
Para demonstrar o processo de construção de uma biblioteca de sequências para as montagens de genomas das linhagens CBS 120486 e CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>, utilizaremos o RepeatModeler no <a href="https://usegalaxy.org/">Galaxy</a>. Na aba “<i>Tools</i>” do Galaxy, selecione a opção “<i>RepeatModeler - Model repetitive DNA</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_01.png" alt="Opção 'RepeatModeler - Model repetitive DNA' na aba Tools do Galaxy" align="center">
</center>
<br><br>
Na opção “<i>Input genome fasta</i>” selecione o arquivo fasta da montagem de interesse. Neste primeiro momento, utilizaremos a montagem de genoma da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i>, obtida a partir de reads de Illumina:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_02.png" alt="Opção 'Operation mode' indicando a modalidade 'Only assembler' para configuração do RepeatModeler no Galaxy" align="center">
</center>
<br><br>
Por fim, basta clicar em “<i>Run Tool</i>” para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_03.png" alt="Opções para configuração da ferramenta RepeatModeler no Galaxy, indicando Run Tool e Email notification" align="center">
</center>
<br><br>
Repita o mesmo processo para a montagem de genoma da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>. Após a conclusão das duas tarefas, cada análise terá dois arquivos de saída: uma biblioteca de sequências consenso (no formato FASTA) e um arquivo de alinhamentos utilizados como base para a construção da biblioteca (no formato STOCKHOLM, amplamente utilizado pelo Pfam, Rfam e Dfam).
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_04.png" alt="Arquivos de saída 'Consensus sequences' e 'Seed alignments' como resultados do RepeatModeler no Galaxy" align="center">
</center>
<br><br>
</div>

## Obtenção de biblioteca de elementos repetitivos no RepBase

<div align="justify">
Em casos em que a biblioteca de elementos repetitivos construída a partir da montagem de genoma é muito simplificada e há necessidade de incluir sequências de referência adicionais, outra estratégia bastante utilizada é utilizar bibliotecas de sequências já validadas e submetidas a um processo de curadoria, tais como as sequências disponíveis no <a href="https://www.girinst.org/repbase/">Repbase</a>. O Repbase é uma base de dados de sequências representativas da diversidade de elementos repetitivos encontrados nos genomas de diferentes espécies de eucariotos, consistindo em sequências consenso de várias famílias e subfamílias de sequências repetitivas. Entretanto, o acesso e posterior download das bibliotecas do Repbase não é gratuito, sendo necessário possuir uma <a href="https://www.phoenixbioinformatics.org/repbase#product-repbase-subscription">assinatura anual individual ($1.675 dólares) ou institucional ($3.350 dólares) ativa.</a>
<br<br>
Caso você tenha uma assinatura vigente, para realizar o download da biblioteca de sequências, acesse <a href="https://www.girinst.org/server/RepBase/index.php">esta página</a>. Há diversos formatos disponíveis, seja no formato EMBL e também no formato FASTA, bem como formatos específicos para uso junto à pipeline REPET e ao software RepeatMasker. No contexto deste tutorial, ao utilizar o RepeatMasker, o indicado seria realizar o download do arquivo <a href="https://www.girinst.org/server/RepBase/protected/repeatmaskerlibraries/RepBaseRepeatMaskerEdition-20181026.tar.gz">Repbase - derived RepeatMasker libraries / RepBaseRepeatMaskerEdition-20181026.tar.gz</a>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_05.png" alt="Opções de download da biblioteca Repbase" align="center">
</center>
<br><br>
Após o download da biblioteca no formato .tar.gz, bastaria descompactar o arquivo para que ela estivesse pronta para uso no Galaxy ou em outro servidor. 
</div>

## Detecção de sequências repetitivas com o RepeatMasker

<div align="justify">
Possuindo uma biblioteca de sequências repetitivas de referência, seja uma construída com o RepeatModeler, ou uma biblioteca obtida a partir do Repbase, ou ainda a biblioteca predefinida que é fornecida pelo próprio RepeatMasker, podemos prosseguir para a etapa de anotação das sequências repetitivas no genoma de interesse. Na aba “<i>Tools</i>” do Galaxy, selecione a opção “<i>RepeatMasker - screen DNA sequences for interspersed repeats and low complexity regions</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_06.png" alt="Opção 'RepeatMasker - screen DNA sequences for interspersed repeats and low complexity regions' na aba Tools do Galaxy" align="center">
</center>
<br><br>
Na opção <i>"Genomic DNA"</i> selecionaremos a montagem de genoma de interesse. Nesse primeiro momento, utilizaremos a montagem de genoma da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_07.png" alt="Opção 'Genomic DNA' indicando a modalidade 'PCitriasiana_CBS120486.fasta' para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Na aba seguinte, intitulada <i>"Repeat library source"</i>, indicaremos qual a biblioteca de sequências de referência será utilizada para procurar por sequências de elementos repetitivos no genoma. Por predefinição o RepeatMasker utiliza uma versão da database Dfam (que é pública), contendo somente elementos que passaram por curadoria manual (<i>"Dfam (curated only, bundled with RepeatMasker"</i>). 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_08.png" alt="Opção 'Repeat library source' indicando a modalidade 'Dfam (curated only, bundled with RepeatMasker' para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Para utilizar a biblioteca gerada pelo RepeatModeler na etapa anterior, selecione a modalidade <i>"Custom library of repeats"</i> para a opção <i>"Repeat library source"</i>. Na opção seguinte, <i>"Custom library of repeats"</i>, indique o arquivo FASTA correspondente às sequências consenso obtidas a partir do genoma de interesse. Como valor de score para detecção e filtragem de sequências repetitivas (<i>"Cutoff score for masking repeats"</i>), é possível utilizar o valor predefinido de "225":
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_09.png" alt="Opção 'Repeat library source' indicando a modalidade 'Custom library of repeats', opção 'Custom library of repeats' indicando a biblioteca própria e opção 'Cutoff score for masking repeats' com a modalidade '225', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, <i>"Output annotation of repeats in GFF format"</i>, indicaremos a modalidade <i>"Yes"</i> para obtenção de um arquivo de coordenadas das sequências repetitivas em relação ao genoma no formato GFF3, que é bastante útil para elaboração de imagens e representação visual da localização destas sequências no genoma. Para a opção seguinte, <i>"Ignore stretches of Ns when computing statistics"</i>, também selecionaremos a modalidade <i>"Yes"</i> para que o RepeatMasker ignore trechos longos de "N" que existirem nos genomas, os quais usualmente são utilizados para junção artificial de contigs no processo de scaffolding. Em seguida, para a opção <i>"Perform softmasking instead of hardmasking"</i>, é de extrema importância selecionar a modalidade <i>"Yes"</i> para que o RepeatMasker realize apenas o softmasking das sequências repetitivas, deixando as bases correspondentes em letras minúsculas no arquivo. Caso seja selecionada a modalidade <i>"No"</i>, o RepeatMasker realizará o hardmasking, transformando as bases correspondentes às sequências repetitivas em "N", fazendo com que a informação seja perdida.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_10.png" alt="Opção 'Output annotation of repeats in GFF format' indicando a modalidade 'Yes', opção 'Ignore stretches of Ns when computing statistics' indicando a modalidade 'Yes' e opção 'Perform softmasking instead of hardmasking' com a modalidade 'Yes', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Na aba <i>"Advanced options"</i> iremos configurar algumas opções relativas à grupos taxonômicos e condições específicas. As três primeiras opções se referem à análises relevantes apenas para genomas bacterianos ou principalmente para situações em que há suspeitas de contaminação com sequências bacterianas na montagem de genoma analisada. Neste tutorial deixaremos as duas primeiras opções desativadas com a modalidade <i>"No"</i>, visto que estamos trabalhando com sequências fúngicas e não há evidências de contaminação nas montagens de genoma. A primeira opção, <i>"Only clip E coli insertion elements"</i>, realiza a remoção de sequências de inserção com similaridade à sequências de <i>Escherichia coli</i> antes do cálculo da quantidade de sequências repetitivas existentes no genoma, caso estas sequências de inserção sejam detectadas. A segunda opção, <i>"Clip IS elements before analysis"</i> realiza um procedimento similar, mas de forma mais abrangente para qualquer sequência de inserção encontrada, e não somente sequências similares às de <i>E. coli</i>. Para a terceira opção, <i>"Skip bacterial insertion element check"</i>, selecionaremos a modalidade <i>"Yes"</i> para pular a etapa de busca por sequências de inserção bacterianas. Caso deseje realizar essa busca (especialmente para situações em que há suspeita de contaminação, selecione a modalidade <i>"No</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_11.png" alt="Opção 'Only clip E coli insertion elements' indicando a modalidade 'No', opção 'Clip IS elements before analysis' indicando a modalidade 'No' e opção 'Skip bacterial insertion element check' com a modalidade 'Yes', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
As opções seguintes são relevantes para a análise de genomas de roedores (<i>"Only check for rodent specific repeats"</i> ou primatas (<i>"Only check for primate specific repeats"</i>), para que o RepeatMasker não precise fazer uma busca completa, e sim procurar apenas por sequências repetitivas destes grupos taxonômicos. No contexto deste tutorial, selecionaremos a modalidade <i>"No"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_12.png" alt="Opção 'Only check for rodent specific repeats' indicando a modalidade 'No', opção 'Only check for primate specific repeats' indicando a modalidade 'No', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
As opções seguintes se referem a como o RepeatMasker lidará com sequências repetitivas que não necessariamente constituem elementos transponíveis, tais como repetições em tandem, regiões de DNA satélite e repetições intercalares. Neste tutorial, selecionaremos a modalidade <i>"No"</i> para que as buscas por repetições em tandem e de DNA satélite (<i>"No low complexity masking"</i>), repetições intercalares (boa parte dos elementros transponíveis em que estamos interessados!) (<i>"No interspersed repeat masking"</i>) e sequências de RNAs funcionais transcritos pela RNA polimerase III (<i>"No repeat-like-RNA masking"</i> sejam realizadas e estas sequências sejam marcadas. Caso deseje pular estas etapas, basta selecionar a modalidade <i>"Yes"</i> para todas as opções:
 <br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_13.png" alt="Opção 'No low complexity masking' indicando a modalidade 'No', opção 'No interspersed repeat masking' indicando a modalidade 'No' e opção 'No repeat-like-RNA masking' indicando a modalidade 'No', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Na sequência, também selecionaremos a modalidade <i>"No"</i> para as opções <i>"Limit masking to (primate) Alu repeats"</i> e <i>"Limit masking to less diverged (younger repeats)"</i>. No primeiro caso, é importante fazer esta escolha para que o RepeatMasker não se limite somente à busca de sequências Alu, que são relevantes no contexto de genomas de primatas. Já para a segunda situação, é importante fazer esta escolha para que o RepeatMasker não se limite somente à busca de sequências repetitivas que estejam altamente similares às sequências consenso, cuja idade de inserção é mais recente, mas que também busque por sequências de inserção mais antiga, e que provavelmente já divergiram de forma mais significativa em relação às sequências consenso de referência:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_14.png" alt="Opção 'Limit masking to (primate) Alu repeats' indicando a modalidade 'No', opção 'Limit masking to less diverged (younger repeats)' indicando a modalidade 'No', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
 Em seguida, para as opções <i>"Search speed vs sensitivity trade-off"</i>, que estabelece o balanço entre velocidade e sensibilidade da análise, selecionaremos a opção predefinida <i>"Default"</i>. É possível alterar este balanço para que a análise fique mais rápida, porém menos precisa (<i>"Quick (5-10% less sensitive, 3-4 times speedup"</i> ou <i>"Rush (10% less sensitive)"</i>), ou mais lenta e mais precisa (<i>"Slow (0-5% more sensitive, 2.5 times slowdown"</i>):
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_15.png" alt="Opção 'Search speed vs sensitivity trade-off' indicando a modalidade 'Default' para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
 Nas opções seguintes utilizaremos as modalidades já predefinidas. Para a opção <i>"Maximum contiguous sequence searched"</i>, que define o comprimento máximo em pares de bases das sequências a serem analisadas sem que sejam fragmentadas, utilizaremos o valor de 40000 pares de bases. Já para a opção <i>"Select matrices for this GC%"</i>, que restringe as buscas para sequências com uma porcentagem específica de GC, deixaremos o valor em branco:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_16.png" alt="Opção 'Maximum contiguous sequence searched' indicando a modalidade '40000', opção 'Select matrices for this GC%' indicando a modalidade 'em branco', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Para a opção <i>"Calculate GC% for all sequences"</i> selecionaremos a modalidade <i>"No"</i>, para que o RepeatMasker não calcule a porcentagem de GC de sequências repetitivas pequenas. No momento, a modalidade <i>"Yes</i> resulta em erro na análise, não sendo possível utilizá-la no Galaxy. Para as duas opções seguintes, também selecionaremos a modalidade <i>"No"</i>. Dessa forma, o RepeatMasker não pulará etapas de excisão de sequências repetitivas (<i>"Skips cutting of repeats"</i>) e também não irá realizar hardmasking das sequências repetitivas com "X" (<i>"Mask with X instead of N characters"</i>):
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_17.png" alt="Opção 'Calculate GC% for all sequences' indicando a modalidade 'No', opção 'Skips cutting of repeats' indicando a modalidade 'No' e opção 'Mask with X instead of N characters' indicando a modalidade 'No', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Por fim, temos as três últimas opções mais relacionadas ao formato e informações presentes nos arquivos de saída. Para a primeira (<i>"Output alignments file"</i> selecionaremos a modalidade <i>"Yes"</i>, de modo que o RepeatMasker criará um arquivo com os alinhamentos das sequências repetitivas e sequências consenso de referência. Em seguida, para a opção <i>"Invert alignments in alignment file"</i> selecionaremos a modalidade <i>"No"</i>, de modo que o RepeatMasker não inverterá as sequências repetitivas e manterá a orientação original conforme presentes no arquivo de montagem de genoma. Já para a opção <i>"Output list of potentially polymorphic microsatellites"</i> selecionaremos <i>"Yes"</i>, para que o RepeatMasker forneça uma lista dos microsatélites encontrados que sejam potencialmente polimórficos:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_18.png" alt="Opção 'Output alignments file' indicando a modalidade 'Yes', opção 'Invert alignments in alignment file' indicando a modalidade 'No' e opção 'Output list of potentially polymorphic microsatellites' indicando a modalidade 'Yes', para configuração do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
Para a opção <i>"Job Resource Parameters"</i>, manteremos a modalidade predefinida de <i>"Use default job resource parameters"</i>. Por fim, basta clicar em <i>“Run Tool”</i> para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_19.png" alt="Opção 'Job Resource Parameters' indicando a modalidade 'Use default job resource parameters', e opções para configuração da ferramenta RepeatMasker no Galaxy, indicando 'Run Tool' e 'Email notification'" align="center">
</center>
<br><br>
Repita o mesmo processo para a montagem de genoma da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>, utilizando a biblioteca construída pelo RepeatModeler para esta linhagem. Após a conclusão das duas tarefas, cada análise terá sete arquivos de saída: 
<br><br>
<ul>
<li>Arquivo de montagem de genoma com as sequências repetitivas com softmasking (<i>RepeatMasker masked sequence</i>, no formato FASTA)</li>
<li>Arquivo log da análise (<i>RepeatMasker output log</i>, no formato TABULAR)</li>
<li>Arquivo com estatísticas e quantidade de sequências repetitivas encontradas (<i>RepeatMasker repeat statistics</i>, no formato TXT)</li>
<li>Arquivo com catálogo de sequências repetitivas encontradas (<i>RepeatMasker repeat catalogue</i>, no formato TXT)</li>
<li>Arquivo de alinhamento das sequências repetitivas encontradas vs. sequências de referência utilizadas (<i>RepeatMasker alignment</i>, no formato TXT)</li>
<li>Arquivo do conjunto de microssatélites potencialmente polimórficos (<i>RepeatMasker possible polymorphic repeats</i>, no formato TABULAR)</li>
<li>Arquivo de anotação com coordenadas das sequências repetitivas (<i>RepeatMasker repeat annotation</i>, no formato GFF)</li>
</ul>
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_20.png" alt="Arquivos de saída 'RepeatMasker masked sequence', 'RepeatMasker output log', 'RepeatMasker repeat statistics', 'RepeatMasker repeat catalogue', 'RepeatMasker alignment', 'RepeatMasker possible polymorphic repeats' e 'RepeatMasker repeat annotation' como resultados do RepeatMasker no Galaxy" align="center">
</center>
<br><br>
</div>

## Detecção de sequências repetitivas com o EDTA

<div align="justify">
Outra alternativa disponível tanto para construir uma biblioteca de sequências repetitivas de referência ou para realizar todo o processo de anotação é o software EDTA. Na aba “<i>Tools</i>” do <a href="https://usegalaxy.eu">Galaxy Europe</a>, selecione a opção “<i>edta - Whole-genome de-novo TE annotation</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_21.png" alt="Opção 'edta - Whole-genome de-novo TE annotation' na aba Tools do Galaxy Europe" align="center">
</center>
<br><br>
Na primeira opção, <i>"Which Function should be run"</i>, selecionaremos o modo de execução do software. É possível utilizá-lo para anotação de todas as sequências repetitivas presentes em uma montagem de genoma (<i>"Whole Genome"</i>), detecção de todas as cópias de elementos de famílias ou categorias específicas (<i>"Specific TE"</i>) ou anotação de elementos transponíveis seguindo uma abordagem de pangenoma (<i>"Pan-EDTA"</i>). Neste tutorial, utilizaremos o modo <i>"Whole Genome"</i>
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_22.png" alt="Opção 'Which Function should be run' indicando a modalidade 'Whole Genome' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Em seguida, na opção <i>"Genome File"</i>, selecionaremos o arquivo da montagem de genoma de interesse para análise (nesse primeiro momento, a montagem <i>PCitriasiana_CBS120486.fasta</i>). Para o campo seguinte, <i>"Which species should be used for identification of TIR candidates"</i>, em que é possível selecionar a espécie de referência para a busca de sequências de repetições terminais invertidas (TIRs), selecionaremos a modalidade <i>"Others"</i>, visto que as outras opções predefinidas são para genomas de arroz e  milho (<i>"Rice"</i> ou <i>"Maize"</i>, respectivamente):
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_23.png" alt="Opção 'Genome File' indicando o arquivo 'PCitriasiana_CBS120486.fasta' e opção 'Which species should be used for identification of TIR candidates' indicando a modalidade 'Others' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Em seguida, é possível selecionar quais módulos do edta devem ser utilizados. Por padrão, está selecionada a opção <i>"run the entire pipeline (all)"</i>, compreendendo todas as etapas, mas é possível restringir a análise somente à etapa <i>"start from raw TEs to the end (filter)"</i> (para iniciar a partir de um conjunto preliminar de sequências de TEs e seguir até o final da pipeline), ou restringir às etapas <i>"Final"</i> (para iniciar a partir dos TEs já filtrados e seguir até o fim da pipeline) ou <i>"Anno"</i> (realizar a anotação das sequências repetitivas no genoma a partir de uma biblioteca de referência já construída):
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_24.png" alt="Opção 'Genome File' indicando a modalidade 'run the entire pipeline (all)' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Nas opções <i>"Coding Sequence File"</i> é possível fornecer um arquivo FASTA contendo as sequências codificantes encontradas para o genoma analisado ou de espécies filogeneticamente próximas. Neste primeiro momento deixaremos esta opção em branco, mas após a nossa próxima prática de <a href="https://gstreinamentoeconsultoria.netlify.app/genomica/2023_01/praticas/aula_04/">predição de genes</a> você pode retornar ao edta e fornecer estas sequências e posteriormente comparar os resultados. Já para a opção <i>"Curated Library file"</i> é possível fornecer um arquivo no formato FASTA contendo sequências de elementos transponíveis que sejam confiáveis, tendo já passado por um processo de curadoria manual. Nesse momento, deixaremos esta opção em branco também:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_25.png" alt="Opção 'Coding Sequence File' indicando a modalidade 'em branco' e opção 'Curated Library file' indicando a modalidade 'em branco' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Em seguida, é possível habilitar o uso conjunto do RepeatModeler (sobre o qual já discutimos anteriormente) por meio da opção <i>"Use RepeatModeler to identify remaining TEs"</i>, sendo possível identificar sequências que não tenham sido detectadas pelo edta. Para isso, selecionaremos a modalidade <i>"Yes"</i>. No campo <i>"Neutral Mutation Rate"</i> é possível inserir a taxa de mutações neutras para a espécie de interesse, caso esse dado esteja disponível na literatura. Caso esta opção seja deixada em branco, o edta usa por predefinição uma taxa de 1.3e-8, obtida a partir de estudos em arroz:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_26.png" alt="Opção 'Coding Sequence File' indicando a modalidade 'em branco' e opção 'Curated Library file' indicando a modalidade 'em branco' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Para a opção seguinte, <i>"Would you like to perform whole-genome TE annotation after TE library construction?"</i> selecionaremos a modalidade <i>"Yes"</i> para realizar a anotação das sequências repetitivas após obter a biblioteca de sequências de TE. Adicionalmente, também é possível avaliar a consistência da anotação das sequências repetitivas ao selecionar a modalidade <i>"Yes"</i> para a opção <i>"Evaluate"</i>. Caso deseje que o edta ignore algumas regiões genômicas durante o processo de anotação, basta fornecer um arquivo das coordenadas destas regiões no formato BED. Nesse exemplo, não forneceremos coordenadas, deixando esta opção em branco:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_27.png" alt="Opção 'Coding Sequence File' indicando a modalidade 'em branco' e opção 'Curated Library file' indicando a modalidade 'em branco' para configuração do edta no Galaxy Europe" align="center">
</center>
<br><br>
Por fim, basta clicar em <i>“Run Tool”</i> para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_28.png" alt="Opções para configuração da ferramenta edta no Galaxy Europe, indicando 'Run Tool' e 'Email notification'" align="center">
</center>
<br><br>
Repita o mesmo processo para a montagem de genoma da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>. Após a conclusão das duas tarefas, cada análise terá sete arquivos de saída: 
<br><br>
<ul>
<li>Arquivo de biblioteca não-redundante de sequências de elementos transponíveis (<i>Non-redundant TE Library</i>, no formato ...)</li>
<li>Arquivo de anotação com coordenadas das sequências repetitivas na montagem de genoma(<i>Whole Genome TE Annotation</i>, no formato GFF3)</li>
<li>Arquivo com informações gerais sobre anotação de sequências repetitivas no genoma(<i>Summary of Whole Genome TE Annotation</i>, no formato XML)</li>
<li>Arquivo de anotação com coordenadas das sequências repetitivas submetidas ao processo de masking (<i>Low_Threshold_TE_Masking</i>, no formato GFF3)</li>
<li>Arquivo com dados de inconsistência na anotação de TEs (<i>Simple TE Annotation Inconsistency</i>, no formato XML)</li>
<li>Arquivo com dados de inconsistência na anotação de TEs (<i>Nested TE Annotation Inconsistency</i>, no formato XML)</li>
<li>Arquivo com dados de inconsistência na anotação de TEs (<i>Overall TE Annotation Inconsistency</i>, no formato XML)</li>
</ul>
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_29.png" alt="Arquivos de saída 'Non-redundant TE Library', 'Whole Genome TE Annotation', 'Summary of Whole Genome TE Annotation', 'Low_Threshold_TE_Masking', 'Simple TE Annotation Inconsistency', 'Nested TE Annotation Inconsistency' e 'Overall TE Annotation Inconsistency' como resultados do EDTA no Galaxy Europe" align="center">
</center>
<br><br>
</div>

## Detecção de sequências de inserção em genomas procarióticos com o ISfinder

<div align="justify">
Uma alternativa para detecção de elementos genéticos móveis em genomas procarióticos, especialmente para anotação de sequências de inserção, é o <a href="https://www-is.biotoul.fr/index.php">ISfinder</a>. O ISfinder é uma base de dados de sequências de inserção que passaram por um processo de curadoria, sendo um dos recursos mais completos para busca e comparação de sequências de inserção da atualidade. Nesta base de dados é possível, além de encontrar informações sobre sequências de inserção e seus sistemas de classificação e nomenclatura, utilizar sequências de montagens de genoma para realizar buscas via BLAST. Neste tutorial, realizaremos a busca de sequências de inserção no genoma da linhagem 2013C-3996 de <i>Escherichia coli</i> e no genoma da linhagem SD 504 de <i>Streptomyces sudanensis</i>. Para isso, faça o download dos arquivos FASTA das respectivas montagens no NCBI Assembly:
<br><br>
<ul>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_003018515.1/"><i>Escherichia coli</i> 2013C-3996</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_023614315.1/"><i>Streptomyces sudanensis</i> SD 504</a></li>
</ul>
<br><br>
Em seguida, acesse a opção <i>"Blast"</i> na aba <i>"Tools"</i> do <a href="https://www-is.biotoul.fr/blast.php">ISfinder</a>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_30.png" alt="Opção 'Blast' na aba 'Tools' do ISfinder" align="center">
</center>
<br><br>
Na página de BLAST do ISfinder, selecione a modalidade <i>"blastn"</i> (comparação de sequências query de nucleotídeos vs. sequências subject de nucleotídeos). No campo <i>"Job Title"</i> é possível inserir um nome para a análise, caso desejado. No campo <i>"Enter Query Sequence"</i>, utilize a opção <i>"Or, upload file (Fasta format)"</i> para enviar o arquivo de montagem de genoma no formato FASTA:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_31.png" alt="Opção 'Coding Sequence File' indicando a modalidade 'em branco' e opção 'Curated Library file' indicando a modalidade 'em branco' para configuração do ISfinder" align="center">
</center>
<br><br>
Na aba <i>"Choose.."</i> mantenha a seleção do campo <i>"Database"</i> como <i>"ISfinder"</i> e o campo <i>"Programme"</i> como blastn. Iremos configurar alguns parâmetros do BLAST na aba <i>"Algorithm parameters"</i> para refinar a apresentação dos resultados. No campo <i>"Evalue"</i> definiremos o valor de corte como 0.005, para evitar que regiões curtas de similaridade sejam listadas. Para visualização dos resultados no navegador a opção recomendada para <i>"Alignment view options"</i> é <i>"pairwise"</i>, mas para caso deseje trabalhar diretamente com a tabela e filtrá-la no Excel, Notepad++ ou utilizando outros comandos no Linux, utilize a opção <i>"tabular"</i>. Após configurar estes parâmetros, clique em <i>"BLAST"</i> para iniciar a busca: 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_32.png" alt="Opções e parâmetros do BLAST, indicando as modalidade de 'Alignment view options' como 'pairwise' e valor de 'Evalue' como '0.005' para configuração do ISfinder" align="center">
</center>
<br><br>
Aguarde o término da análise e o redirecionamento automático para a página de resultados. Ao selecionar o modo <i>"pairwise"</i>, o ISfinder apresentará uma página contendo uma tabela de resultados contendo 6 colunas:
<br><br>
<ul>
<li><i>Sequences producing significant alignments</i>: nome da sequência de inserção de referência, com o respectivo link do registro da sequência no ISfinder para obtenção de mais informações</li>
<li><i>IS Family</i>: familia da sequência de inserção, segundo o sistema de classificação</li>
<li><i>Group</i>: grupo da sequência de inserção, segundo o sistema de classificação (quando aplicável ou disponível)</li>
<li><i>Origin</i>: espécie do organismo a partir do qual a sequência de referência foi obtida</li>
<li><i>Score (bits)</i>: valor de score do alinhamento entre a sequência de referência e a potencial sequência alvo detectada no genoma analisado</li>
<li><i>Evalue</i>: valor de significância estatística, quanto mais baixo (próximo de zero), menor a chance de que o alinhamento tenha ocorrido ao acaso</li>
</ul>
<br><br>
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_33.png" alt="Tabela de resultados do BLAST na database ISfinder" align="center">
</center>
<br><br>
</div>


