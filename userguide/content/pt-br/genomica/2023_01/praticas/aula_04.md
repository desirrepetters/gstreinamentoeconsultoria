---
title: "Aula 04 - Predição de genes"
linkTitle: "Aula 04 - Predição de genes"
weight: 2
description: >
  Softwares utilizados: Prokka, HISAT2 e Funannotate
---
<div align="justify">
Após a avaliação detecção e anotação das sequências repetitivas e de elementos transponíveis em montagens de genomas, é hora de prospectar e avaliar as sequências em busca das coordenadas de genes que codificam proteínas e RNAs funcionais, para que estas coordenadas possam ser posteriormente utilizadas para caracterização dos genes na etapa de anotação funcional.
<br><br>
Para este tutorial, acessaremos o <a href="https://www.ncbi.nlm.nih.gov/sra">NCBI Assembly</a> para download de montagens de genomas e utilizaremos os softwares Prokka, HISAT2 e Funannotate (<a href="https://usegalaxy.eu/">na versão online no Galaxy</a> ou instalados em uma distribuição Linux). Se você ainda não tem estes softwares instalados, pode encontrar instruções <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/download/">aqui</a>.
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
Há diversas diferenças ao processos utilizados para predição de genes em genomas procarióticos e eucarióticos. Uma das principais diferenças  está relacionada à tipica estrutura gênica em cada um dos grupos. Visto que os genes procarióticos não apresentam íntrons, a busca por sequências codificantes em genomas procarióticos normalmente consiste na busca por ORFs e posterior validação das ORFs potencialmente codificantes a partir da comparação com sequências de referência de proteínas e RNAs funcionais já caracterizados, bem como busca por domínios conservados. Já nos eucariotos, a presença de íntrons nos genes não permite com que esta abordagem seja viável, de modo que as abordagens mais precisas normalmente envolvem a comparação com sequências de transcritos e alinhamentos de dados de RNA-Seq, para delimitação precisa das junções éxon/íntron e posterior determinação das sequências codificantes. Por conta disso, existem diferentes softwares de predição disponíveis na literatura, geralmente especializados na predição de genes em procariotos ou eucariotos, mas dificilmente em ambos. Dessa forma, neste tutorial, abordaremos os processos de predição de genes em genomas procarióticos e eucarióticos separadamente.
<br><br>
Clique no link abaixo para acessar as páginas do NCBI SRA e NCBI Assembly que contém os arquivos que serão utilizados nesta prática:
<br><br>
<ul>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_003018515.1/">Montagem de genoma de <i>Escherichia coli</i> (linhagem 2013C-3996)</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_023614315.1/">Montagem de genoma de <i>Streptomyces sudanensis</i> (linhagem SD 504)</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_009193405.1/">Montagem de genoma da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i></a>
<li><a href="https://www.ncbi.nlm.nih.gov/sra/SRX1670869">Sequenciamento de transcriptoma de <i>Phyllosticta citriasiana</i> (linhagem CBS 120486) com reads Illumina</a></li>
</ul>
Nesta atividade prática iremos:
<br><br>
<ul>
<li>Realizar a predição gênica em montagens de genomas procarióticos (linhagem 2013C-3996 de <i>Escherichia coli</i> e linhagem SD 504 de <i>Streptomyces sudanensis</i>)</li>
<li>Alinhar reads de RNA-Seq obtidos a partir de sequenciamento Illumina contra a montagem de genoma da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i>, para uso do alinhamento durante o processo de predição gênica</i>
<li>Realizar a predição gênica a partir das montagens de genomas da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i> e da linhagem CGMCC 3.14344 de <i>Phyllosticta citriasiana</i>, combinando estratégias ab initio e baseadas em homologia com sequências de RNA e proteínas</li>
<li>Avaliar a completude das anotações obtidas por meio de comparação com o conjunto de ortólogos conservados do BUSCO</li>
</ul>
Após a realização destas etapas, utilizaremos os arquivos obtidos para as <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/praticas/aula_05">atividades práticas anotação funcional de genes</a>
</div>

## Predição de genes em genomas procarióticos com o Prokka

<div align="justify">
Em breve!
</div>

## Preparo de alinhamentos de reads de transcriptomas vs. montagens de genoma com o HISAT2

<div align="justify">
Em breve!
</div>

## Predição de genes em genomas eucarióticos com o Funannotate

<div align="justify">
Em breve!
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
Possuindo uma biblioteca de sequências repetitivas de referência, seja uma construída com o RepeatModeler, obtida a partir do Repbase, ou a que é fornecida pelo próprio RepeatMasker, podemos prosseguir para a etapa de anotação das sequências repetitivas no genoma de interesse. Na aba “<i>Tools</i>” do Galaxy, selecione a opção “<i>RepeatMasker - screen DNA sequences for interspersed repeats and low complexity regions</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_03/aula_03_06.png" alt="Opção 'RepeatMasker - screen DNA sequences for interspersed repeats and low complexity regions' na aba Tools do Galaxy" align="center">
</center>
<br><br>
Na opção <i>"Genomic DNA"</i> selecionaremos a montagem de genoma de interesse. Nesse primeiro momento, utilizaremos a montagem de genoma da linhagem CBS 120486 de Phyllosticta citriasiana:
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
As opções seguintes se referem a como o RepeatMasker lidará com sequências repetitivas que não necessariamente constituem elementos transponíveis, tais como repetições em tandem, regiões de DNA satélite e repetições intercalares. Neste tutorial, selecionaremos a modalidade <i>"No"</i> para que as buscas por repetições em tandem e de DNA satélite (<i>"No low complexity masking"</i>), repetições intercalares (<i>"No interspersed repeat masking"</i>) e sequências de RNAs funcionais transcritos pela RNA polimerase III (<i>"No repeat-like-RNA masking"</i> sejam realizadas e estas sequências sejam marcadas. Caso deseje pular estas etapas, basta selecionar a modalidade <i>"Yes"</i> para todas as opções:
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
Para a opção <i>"Job Resource Parameters"</i>, manteremos a modalidade predefinida de <i>"Use default job resource parameters"<i/>. Por fim, basta clicar em <i>“Run Tool”</i> para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
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
Nas opções <i>"Coding Sequence File"</i> é possível fornecer um arquivo FASTA contendo as sequências codificantes encontradas para o genoma analisado ou de espécies filogeneticamente próximas. Neste primeiro momento deixaremos esta opção em branco, mas após a nossa próxima prática de <a href="">predição de genes</a> você pode retornar ao edta e fornecer estas sequências e posteriormente comparar os resultados. Já para a opção <i>"Curated Library file"</i> é possível fornecer um arquivo no formato FASTA contendo sequências de elementos transponíveis que sejam confiáveis, tendo já passado por um processo de curadoria manual. Nesse momento, deixaremos esta opção em branco também:
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



 com a possibilidade de clicar no nome da sequência de inserção para obter mais informações sobre a sequência de referência.

Na aba “<i>Single-end or paired-end short-reads</i>”, na primeira opção podemos selecionar a modalidade de biblioteca com a qual estamos trabalhando: se são reads não pareados, ou se forem pareados, especificar se são arquivos individiduais ou um conjunto de arquivos. Nesse caso, como temos um arquivo para os reads forward ainda pareados após processamento pelo Trimmomatic, e outro arquivo com os reads reverse, podemos selecionar a opção “<i>Paired-end: individual datasets</i>”. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_03.png" alt="Opção 'Single-end or paired-end short-reads' indicando a modalidade 'Paired-end: individual datasets' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Em seguida, na aba "FASTA/FASTQ file(s): forward reads" devemos especificar qual arquivo corresponde ao conjunto de reads forward, selecionando o arquivo <i>"Trimmomatic on SRR9672751:forward (R1 paired)"</i>. Consequentemente, na aba <i>"FASTA/FASTQ file(s): reverse reads"</i>, selecionaremos o arquivo <i>"Trimmomatic on SRR9672751:reverse (R2 paired)</i> como o arquivo com o o conjunto de reads reverse:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_04.png" alt="Opções 'FASTA/FASTQ file(s): forward reads' e 'FASTA/FASTQ file(s): reverse reads' indicando os arquivos correspondentes para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Dado que trabalharemos com uma biblioteca de reads pareados, nas opções seguintes é necessário fornecer algumas informações em relação ao tipo de reads pareados e orientação dos reads nos pares. Na opção <i>"Type of paired-reads"</i> selecionaremos a modalidade <i>"Default (--pe)"</i>, visto que estamos utilizando paired-end reads e não mate-pair reads. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_05.png" alt="Opção 'Type of paired-reads' indicando a modalidade 'Default (--pe)' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Já para a opção <i>"Select orientation of reads"</i>, selecionaremos a modalidade <i>"FR (-> <-)"</i> visto que, em cada par, os reads forward estão na orientação oposta em relação ao reads reverse. Neste ponto, é importante se atentar ao tipo de biblioteca ou plataforma de sequenciamento utilizada, pois algumas outras estratégias de biblioteca podem apresentar outro tipo de orientação (como bibliotecas mate-pair, que apresentam fragmentos na orientação RF (-> <-)).
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_06.png" alt="Opção 'Select orientation of reads' indicando a modalidade 'FR (-> <-)' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Em seguida, caso você deseje combinar dados da biblioteca principal e utilizar conjuntos adicionais de reads curtos de Illumina obtidos a partir de outras corridas, basta modificar a seleção da opção <i>"Use an additional set of short-reads"</i> de <i>"Disabled"</i> para <i>"Enabled"</i>, e indicar os reads forward e reverse da mesma forma que fizemos na etapa anterior:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_07.png" alt="Opção 'Use an additional set of short-reads' indicando a modalidade 'Enabled' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Além disso, caso você tenha dados de sequenciamento de reads longos (como PacBio ou Oxford Nanopore) e deseja utilizá-los na montagem para melhor resolução de regiões repetitivas e fechamento de gaps, é possível clicar na aba <i>"Additional reads files"</i> e especificar estes arquivos.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_08.png" alt="Opção 'Additional reads files' indicando as modalidades 'Nanopore reads' e 'PacBio CLR reads' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Adicionalmente, também é possível utilizar reads de sequenciamento Sanger ou também contigs confiáveis/não-confiáveis para nortear o processo de montagem.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_09.png" alt="Opção 'Additional reads files' indicando as modalidades 'Sanger reads', 'Trusted contigs' e 'Untrusted contigs' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Na aba <i>"Pipeline options"</i>, é importante selecionar as opções <i>"Isolate: highly recommended for high-coverage isolate and multi-cell data (--isolate)"</i> (para selecionar a modalidade de montagem a ser utilizada) e a opção <i>"Careful: ties to reduce the number of mismatches and short indels. Only recommended for small genomes (--careful)"</i>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_10.png" alt="Opção 'Pipeline options' indicando as modalidades 'Isolate' e 'Careful' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Na opção <i>"Set coverage cutoff option"</i> podemos utilizar a opção predefinida pelo Galaxy de <i>"Off"</i>, e na aba de escolha do tamanho dos k-mers a serem utilizados, podemos utilizar a opção de escolha automática de tamanho (<i>"Auto"</i>).
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_11.png" alt="Opção 'Set coverage cutoff option' indicando a modalidade 'Off' e opção 'Select k-mer detection option' indicando a modalidade 'Auto' e para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Caso deseje especificar manualmente os tamanhos de k-mers, basta modificar a opção para <i>"User specific"</i> e informar os tamanhos desejados na opção <i>"K-mer size values"</i>, seguindo dois critérios: (1) os valores precisam ser números ímpares, e (2) precisam ser menores do que o tamanho dos reads utilizados (limite máximo de 128).
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_12.png" alt="Opção 'Select k-mer detection option' indicando a modalidade 'User-specific', com valores de k-mer de 21, 33, 55 e 77 indicados na opção 'K-mer size values', para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Em seguida, podemos manter a opção <i>"Set Phred quality offset"</i> no modo de detecção automática (<i>"Auto"</i>), e selecionar os arquivos de saída desejados na aba <i>"Select optional output files"</i>. Por padrão, o SPAdes oferece a opção de gerar tanto contigs e scaffolds, bem como os respectivos grafos das montagens de contigs (<i>"Assembly graph"</i>) e de scaffolds (<i>"Assembly graph with scaffolds"</i>). Caso deseje remover e não gerar uma das modalidades de arquivo de saída, basta clicar no ícone de "X" e deletar o tipo de arquivo correspondente:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_13.png" alt="Opção 'Set Phred quality offset' indicando a modalidade 'Auto', e opção 'Select optional output files' com as modalidades de arquivo de saída, para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
Por fim, basta clicar em “<i>Run Tool</i>” para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_14.png" alt="Opções para configuração da ferramenta SPAdes no Galaxy, indicando Run Tool e Email notification" align="center">
</center>
<br><br>
</div>

## Avaliação de qualidade de montagem de genoma - Métricas de Contiguidade (QUAST)

<div align="justify">
Conforme discutimos em nossa aula teórica, existem várias abordagens para avaliação de qualidade de uma montagem de genoma, seja pensando em termos de contiguidade, como na questão de distribuição de bases e avaliação de conteúdo. Primeiramente, começaremos a avaliar a montagem obtida em termos de contiguidade, e para isso utilizaremos o software QUAST. Na aba “<i>Tools</i>”, na região esquerda da página, selecione a opção “<i>Quast - Genome assembly Quality</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_15.png" alt="Opção 'Quast - Genome assembly Quality' na aba Tools do Galaxy" align="center">
</center>
<br><br>
Na aba “<i>Assembly mode?</i>” selecione a opção “<i>Individual assembly (1 contig file per sample)</i>”.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_16.png" alt="Opção 'Assembly mode' indicando a modalidade 'Individual assembly (1 contig file per sample)' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Em seguida, na aba <i>"Use customized names for the input files?"</i>, caso deseje especificar identificadores para as montagens e facilitar a avaliação dos arquivos posteriormente, selecione a opção <i>"Yes, specify custom names"</i>. Na opção <i>"Contigs/scaffolds file"</i> selecione o arquivo FASTA a ser avaliado. Nesse exemplo faremos a avaliação do arquivo de Contigs gerado pelo SPAdes na etapa anterior. Como o QUAST gera um arquivo de saída no formato PDF contendo as informações da avaliação, é recomendável fazer a avaliação de uma montagem por vez e não utilizar a modalidade <i>"Multiple datasets"</i>. Se esta modalidade for utilizada, todas as avaliações de montagens serão salvas em um mesmo PDF, o que pode dificultar a organização de resultados posteriormente. Por fim, na aba <i>"Name"</i>, indique o identificador personalizado que será utilizado para os arquivos de saída. Nesse exemplo, utilizaremos o nome da espécie e linhagem (Phyllosticta citriasiana CBS 120486):
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_17.png" alt="Opção 'Use customized names for the input files' indicando a modalidade 'Yes, specify custom names', opção 'Contigs/scaffolds file' indicando o arquivo a ser utilizado, e opção 'Name' indicando o identificador personalizado para os arquivos de saída, para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Muitas métricas do QUAST são baseadas na comparação com genomas de referência, especialmente no que se refere à potenciais erros de montagem ou presença/ausência de rearranjos. Para auxiliar na diferenciação de rearranjos oriundos de problemas de montagem (que seriam artefatos) de rearranjos que efetivamente tem comprovação biológica, é possível empregar os reads utilizados para montagem do genoma durante este processo de comparação. Caso deseje utilizar os reads, na aba <i>"Reads options"</i> selecione a opção correspondente ao tipo de reads de interesse (Illumina, PacBio SMRT ou Oxford Nanopore). Nesse exemplo, utilizaríamos a opção <i>"Illumina paired-end reads"</i>, indicando os reads forward na aba <i>"FASTQ/FASTA file #1" </i> e os reads reverse na aba <i>"FASTQ/FASTA file #2"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_18.png" alt="Opção 'Reads options' indicando a modalidade 'Illumina paired-end reads', com os respectivos reads selecionados nas opções 'FASTQ/FASTA file #1' e 'FASTQ/FASTA file #2', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção "<i>Type of assembly</i>" selecionaremos a opção <i>"Genome"</i>. Na opção seguinte, <i>"Use a reference genome?"</i>, caso deseje comparar a montagem à uma montagem de referência já existente, selecione a modalidade <i>"Yes"</i>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_19.png" alt="Opção 'Type of assembly' indicando a modalidade 'Genome', e opção 'Use a reference genome?' indicando a modalidade 'Yes', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Nesse exemplo utilizaremos como comparação uma montagem já publicada da linhagem CBS 120486 de Phyllosticta citriasiana. Para incluir esta montagem na comparação, usaremos a opção <i>"Upload Data"</i> na aba <i>"Tools"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_20.png" alt="Opção 'Upload Data' na aba 'Tools' do Galaxy" align="center">
</center>
<br><br>
Na janela <i>"Upload from Disk or Web"</i>, utilizaremos a opção <i>"Choose local files"</i> para selecionar o arquivo de montagem de genoma em formato FASTA salvo no computador. Após selecionar o arquivo, clique na opção <i>"Start"</i> e acompanhe o progresso do envio na barra de status. Após conclusão do envio, clique na opção <i>"Close"</i>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_21.png" alt="Aba 'Upload from Disk or Web', indicando as opções 'Choose local files', 'Start' e 'Close', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Após o término do upoload, selecione o arquivo correspondente na aba <i>"Reference genome"</i>. Caso ele não apareça automaticamente, é possível procurá-lo utilizando o ícone da opção "Browse Datasets": 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_22.png" alt="Opção 'Reference genome' indicando o arquivo FASTA a ser utilizado para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Caso possua arquivos de coordenadas de genes ou regiões de interesse, ou coordenadas de operons (no caso de genomas bacterianos), é possível selecionar estes arquivos nas opções <i>"Genomic feature positions in the reference genome"</i> e/ou <i>"Operon positions in the reference genome"</i>. Para fazer o envio destes arquivos para o Galaxy, basta seguir os mesmos passos utilizados anteriormente para envio da montagem de genoma de referência. No nosso exemplo, deixaremos estas opções em branco:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_23.png" alt="Opção 'Genomic feature positions in the reference genome' e opção 'Operon positions in the reference genome' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Nas opções "Compute k-mer-based quality metrics" e "Generate Circos plot" podemos manter as modalidades já predefinidas como "No":
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_24.png" alt="Opção 'Compute k-mer-based quality metrics' indicando a modalidade 'No', e opção 'Generate Circos plot' indicando a modalidade 'No', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na aba <i>"Type of organism"</i> é possível selecionar o grupo taxonômico correspondente à montagem (<i>"Prokaryotes"</i>, <i>"Eukaryote"</i> ou <i>"Fungus"</i>), e direcionar os softwares a serem utilizados para detecção preliminar de genes e completude utilizando o BUSCO. No nosso exemplo, selecionaremos a opção <i>"Fungus: use of GeneMark-ES for gene finding, Barrnap for ribosomal RNA genes prediction, BUSCO for conserved orthologs finding (--fungus)"</i>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_25.png" alt="Opção 'Type of organism' indicando a modalidade 'Fungus: use of GeneMark-ES for gene finding, Barrnap for ribosomal RNA genes prediction, BUSCO for conserved orthologs finding (--fungus)' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção <i>"Minimum IDY% considered as proper alignment"</i>, utilizada para definir a porcentagem de identidade a ser usada como critério na comparação entre a montagem e o genoma de referência, podemos deixar a opção já predefinida de 95%. Em casos de comparação com genomas de referência que sejam evolutivamente mais distantes (por exemplo, diferentes espécies de um mesmo gênero), essa porcentagem pode ser diminuída até o limite de 80%:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_26.png" alt="Opção 'Minimum IDY% considered as proper alignment' indicando a modalidade '95,0%' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, intitulada <i>"Lower threshold for a contig length (in bp)"</i>, podemos definir o comprimento mínimo (em pares de bases) que um contig deve apresentar para que seja considerado no cálculo das métricas de contiguidade. Especialmente para montagens obtidas a partir do SPAdes, em que muitos contigs de tamanho extremamente reduzido estão incluídos no arquivo final, esta opção se faz bastante importante. Por predefinição o QUAST sugere um valor de 500 pares de bases, mas é possível customizar este valor em casos de genomas maiores, levando em consideração o tamanho médio de genes, éxons, íntrons, entre outros fatores.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_27.png" alt="Opção 'Lower threshold for a contig length (in bp)' indicando a modalidade '500' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Caso você deseje avaliar uma montagem em que os contigs tenham sido organizados em scaffolds (com gaps fechados por meio da adição de N's) ou avaliar um genoma de tamanho maior que 100 milhões de pares de bases, selecione <i>"Yes"</i> para as opções <i>"Are assemblies scaffolds rather than contigs?"</i> e <i>"Is genome large (>100Mbp)?"</i>. No nosso exemplo, como nenhuma das situações se aplica, iremos manter a seleção predefinida como "No":
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_28.png" alt="Opção 'Are assemblies scaffolds rather than contigs?' indicando a modalidade 'No', e opção 'Is genome large (>100Mbp)?' indicando a modalidade 'No', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na aba <i>"Genes"</i>, caso deseje realizar uma predição de genes preliminar para as buscas de genes de RNA ribossomal e uma análise básica de completude com o BUSCO, basta selecionar a modalidade desejada na opção <i>"Tool for gene prediction"</i>. Nesse caso, selecionaremos a modalidade <i>"GeneMarkS if prokaryotes or GeneMark-ES if eukaryotes or fungi"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_29.png" alt="Opção 'Tool for gene prediction' indicando a modalidade 'GeneMarkS if prokaryotes or GeneMark-ES if eukaryotes or fungi' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, <i>"Comma-separated list of thresholds (in bp) for gene lengths to find with a finding tool"</i>, indique os tamanhos de interesse para busca de genes. Por predefinição, o QUAST sugere os valores de 0, 300, 1500 e 3000 pares de bases, mas estes valores podem ser ajustados para genomas maiores ou casos em que há evidências de que os genes correspondam à sequências mais longas:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_30.png" alt="Opção 'Comma-separated list of thresholds (in bp) for gene lengths to find with a finding tool' indicando a modalidade '0, 300, 1500 e 3000 pares de bases' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Em relação às opções seguintes, <i>"Enables ribosomal RNA gene finding?"</i> e <i>"Enables search for Universal Single-Copy Orthologs using BUSCO?"</i>, podemos selecionar a modalidade <i>"Yes"</i>, para que o QUAST forneça a quantidade de genes de RNA ribossomal e porcentagem de completude segundo a quantidade de BUSCOs no corpo do arquivo de resultados em PDF. O uso destas opções não descarta a necessidade de realizar estas análises posteriormente de forma separada para obter um resultado mais completo, mas já fornece uma primeira indicação do grau de completude da montagem.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_31.png" alt="Opção 'Enables ribosomal RNA gene finding?' indicando a modalidade 'Yes', e opção 'Enables search for Universal Single-Copy Orthologs using BUSCO?' indicando a modalidade 'Yes', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Seguindo para a aba <i>"Alignments"</i>, configuraremos parâmetros que são utilizados nos alinhamentos para a comparação com o genoma de referência. Na primeira opção, <i>"Use all alignments as in QUAST v.1.. to compute genome fraction, # genomic features, # operon metrics"</i>, utilizaremos a modalidade <i>"No"</i> conforme a configuração já predefinida. Dessa forma, o QUAST filtrará alinhamentos ambíguos e redundantes, e manterá somente o melhor alinhamento:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_32.png" alt="Opção 'Use all alignments as in QUAST v.1.. to compute genome fraction, # genomic features, # operon metrics' indicando a modalidade 'No' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Nas opções seguintes configuraremos alguns parâmetros relativos ao tamanho e score dos alinhamentos. Primeiramente, para a opção <i>"Minimum length of alignment"</i> podemos especificar o comprimento mínimo, em pares de bases, dos alinhamentos a serem considerados pelo QUAST durante a análise. Por predefinição, alinhamentos de comprimento menor que 65 pares de bases são sempre filtrados e desconsiderados, mas é possível aumentar este valor:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_33.png" alt="Opção 'Minimum length of alignment' indicando a modalidade '65' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Em seguida, configuraremos uma opção relevante especialmente no contexto de montagens de genomas com grande quantidade de sequências repetitivas. A opção <i>"How processing equally good alignments of a contig (probably repeats)?"</i> se refere aos procedimentos realizados pelo QUAST quando há vários alinhamentos de boa qualidade de um contig. Por predefinição, a modalidade <i>"Take only one (the very best one)"</i> está configurada, mas é possível modificá-la para utilizar todos os alinhamentos (<i>"Use all alignments"</i>). Esta mudança não é recomendada, exceto em casos de montagem de metagenomas. A outra modalidade, <i>"Skip such alignments"</i> também é não recomendada, dada a possibilidade de perda de informações no caso de montagens altamente repetitivas.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_34.png" alt="Opção 'How processing equally good alignments of a contig (probably repeats)?' indicando a modalidade 'Take only one (the very best one)' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, <i>"Score S for defining equally good alignments of a single contig"</i>, atribui-se o score S utilizado para filtrar os alinhamentos. Todos os alinhamentos são ranqueados de acordo com o comprimento do alinhamento multiplicado pela porcentagem de identidade das sequências (LEN x IDY%). De acordo com o score S, todos os alinhamentos com pontuação menor do que S multiplicado pelo valor máximo de ranqueamento dos alinhamentos (S x best(LEN x IDY%) são descartados. Por predefinição, o valor de 0,99 para o score S é utilizado, mas este valor pode ser modificado para qualquer valor entre 0,8 e 1.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_35.png" alt="Opção 'Score S for defining equally good alignments of a single contig' indicando a modalidade '0,99' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, <i>"Fragmented reference genome"</i>, podemos manter a modalidade predefinida como <i>"No"</i>, para não realizar a fragmentação do genoma de referência antes de detectar potenciais erros de montagem. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_36.png" alt="Opção 'Fragmented reference genome' indicando a modalidade 'No' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
As duas próximas opções são relevantes somente para montagens que além dos reads curtos, utilizem blibiotecas mate-pair ou também combinem reads longos como reads de PacBio SMRT ou Oxford Nanopore, para ajudar a delimitar um possível tamanho máximo para a montagem. No nosso exemplo, como utilizaremos somente reads curtos de uma biblioteca paired-end, deixaremos a opção <i>"Simulate upper bound assembly"</i> com a modalidade <i>"No"</i>, e a opção <i>"Minimal number of 'connecting reads' needed for joining upper bound contigs into a scaffold"</i> em branco:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_37.png" alt="Opção 'Simulate upper bound assembly' indicando a modalidade 'No', e opção 'Minimal number of 'connecting reads' needed for joining upper bound contigs into a scaffold' indicando a modalidade 'em branco', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Por fim, para a última opção da aba "Alignments", intitulada <i>"Minimal local missassembly size"</i>, podemos definir o valor de corte de comprimento em pares de bases para detecção local de regiões de erros de montagem. O valor predefinido é de 200 pares de bases, mas pode ser aumentado até o limite de 1000 pares de bases.,<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_38.png" alt="Opção 'Minimal local missassembly size' indicando a modalidade '200' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na aba <i>"Advanced options"</i> configuraremos algumas opções relativas aos tamanhos de contigs utilizados para filtrar e avaliar os resultados. Na primeira opção, <i>"Comma-separated list of contig length thresholds (in bp)"</i>, podemos definir vários valores mínimos de comprimento de contigs para filtrar e reavaliar as métricas de contiguidade. Em montagens de baixa contiguidade e muito fragmentadas, espera-se grande variação nos resultados ao utilizar diferentes comprimentos de contig para filtragem, de modo que os resultados gerados por esta opção são muito úteis para avaliação de métricas de contiguidade. Por padrão, são utilizados os comprimentos mínimos de 0 e 1000 pares de bases, mas podemos adicionar alguns outros valores úteis como 5000, 10000, 25000, 50000 e 100000 pares de bases:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_39.png" alt="Opção 'Comma-separated list of contig length thresholds (in bp)' indicando a modalidade '0, 1000, 5000, 10000, 25000, 50000, 100000' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Na opção seguinte, <i>"Break contigs at every misassembly event (including local ones) to compute NAx and NGAx statistics?"</i>, é recomendável manter a predefinição como <i>"No"</i>, pois em alguns casos as quebras excessivas em qualquer evento de diferença entre montagens numa escala local podem impactar drasticamente as estatísticas de NAx e NGAx. Por padrão, o QUAST só realiza estas quebras e inclui no cálculo de NAx e NGAx em casos de diferenças extensas e de larga escala entre as montagens. Para a opção seguinte, <i>"Lower threshold for the relocation size (gap or overlap size between left and right flanking sequence)"</i>, que estabelece o tamanho mínimo para considerar uma região como sendo um evento de relocação, podemos manter o valor predefinido de 1000 pares de bases. Este valor pode ser alterado, desde que seja maior que 85 pares de bases:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_40.png" alt="Opção 'Break contigs at every misassembly event (including local ones) to compute NAx and NGAx statistics?' indicando a modalidade 'No', e opção 'Lower threshold for the relocation size (gap or overlap size between left and right flanking sequence)' indicando a modalidade '1000', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Para as próximas opções, <i>"Max allowed scaffold gap length difference for detecting corresponding type of misassemblies"</i> e <i>"Lower threshold for detecting partially unaligned contigs"</i>, podemos utilizar os valores pré-definidos de 10000 e 500 pares de bases, respectivamente. A primeira opção se refere ao comprimento mínimo em pares de bases para que uma região seja considerada como um evento de relocação de maior escala. Já a segunda se refere ao tamanho mínimo que contigs parcialmente não alinhados precisam ter para serem levados em consideração nos cálculos das métricas de contiguidade, para não incluir contigs muito pequenos e gerar distorções nos cálculos. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_41.png" alt="Opção 'Max allowed scaffold gap length difference for detecting corresponding type of misassemblies' indicando a modalidade '10000', e opção 'Lower threshold for detecting partially unaligned contigs' indicando a modalidade '500', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Para as opções seguintes, também podemos utilizar as modalidades pré-definidas. Para a opção <i>"Distinguish contigs with more than 50% unaligned bases as a separate group of contigs?"<i/> podemos manter a modalidade <i>"Yes"<i/>, para que contigs que apresentem extensas regiões não alinhadas ao genoma de referência sejam distinguidos como um grupo separado de contigs. Para a opção seguinte, <i>"Fragment max indent"</i>, deixaremos o valor em branco, visto que não selecionamos a opção de fragmentação do genoma de referência em uma etapa anterior:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_42.png" alt="Opção 'Distinguish contigs with more than 50% unaligned bases as a separate group of contigs?' indicando a modalidade 'Yes', e opção 'Fragment max indent' indicando a modalidade 'em branco', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Por fim, nas duas últimas opções da aba <i>"Alignments"</i>, podemos direcionar a organização do arquivo de saída dos resultados. Na opção <i>"Report all metrics"</i>, deixaremos a modalidade <i>"No"</i>, para apresentar no arquivo de saída somente as métricas relevantes à análise em questão. Por exemplo, em casos em que não é realizada uma comparação com genoma de referência, o QUAST omitirá essa seção dos arquivos de resultados, deixando o arquivo mais enxuto. Para a opção <i>"Report Nx, Lx, etc metrics for the specific value of 'x'"</i>, podemos selecionar qual valor queremos que o arquivo saída apresente  além das típicas métricas de N50, L50, NG50 e NGA50. Por padrão, a modalidade pré-definida para o valor de 'x' é 90, mas este valor pode ser modificado:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_43.png" alt="Opção 'Report all metrics' indicando a modalidade 'No', e opção 'Report Nx, Lx, etc metrics for the specific value of 'x'' indicando a modalidade '90', para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Para a opção <i>"Output files"</i> podemos selecionar os formatos de arquivos de saída a serem gerados pela análise. Além da modalidade <i>"HTML reports"</i>, para análises de montagens de genoma é importante também selecionar as modalidades <i>"PDF reports"</i>, <i>"Tabular reports"</i>, <i>"Log file"</i>. Para a opção <i>"Job Resource Parameters"</i>, manteremos a modalidade predefinida de <i>"Use default job resource parameters"<i/>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_44.png" alt="Opção 'Output files' indicando as modalidades 'HTML reports', 'PDF reports', 'Tabular reports' e 'Log file', e opção 'Job Resource Parameters' indicando a modalidade 'Use default job resource parameters' para configuração do QUAST no Galaxy" align="center">
</center>
<br><br>
Por fim, basta clicar em <i>“Run Tool”</i> para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_45.png" alt="Opções para configuração da ferramenta SPAdes no Galaxy, indicando Run Tool e Email notification" align="center">
</center>
<br><br>
</div>

## Avaliação de qualidade de montagem de genoma - Métricas de Conteúdo (BUSCO)

<div align="justify">
Em breve!
<br><br>
</div>

## Montagem de reads de PacBio no Canu

<div align="justify">
Em breve!
<br><br>
</div>