---
title: "Aula 02 - Montagem de genomas e avaliação da qualidade de montagem"
linkTitle: "Aula 02 - Montagem de genomas e avaliação da qualidade de montagem"
weight: 2
description: >
  Softwares utilizados: SPAdes, Canu, QUAST, BUSCO.
---
<div align="justify">
Após o a avaliação dos dados brutos de sequenciamento e devido processamento para remoção de reads ou bases de baixa qualidade, são obtidos arquivos que servem de base para a montagem de genomas e transcriptomas. 
<br><br>
Para este tutorial, acessaremos o <a href="https://www.ncbi.nlm.nih.gov/sra">NCBI Assembly</a> para download de montagens de genomas e utilizaremos os softwares SPAdes, Canu, QUAST e BUSCO (<a href="https://usegalaxy.eu/">na versão online no Galaxy</a> ou instalados em uma distribuição Linux). Se você ainda não tem estes softwares instalados, pode encontrar instruções <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/download/">aqui</a>.
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
Há diversas diferenças em relação à montagem de genomas utilizando reads de Illumina, PacBio, Oxford Nanopore, ou abordagens combinadas. Uma das principais diferenças é o fato de que vários softwares de montagem de genomas e transcriptoma que usam reads de PacBio e Oxford Nanopore são capazes de utilizar diretamente os reads brutos, pois possuem um sistema de correção de erros próprio. Já softwares que utilizam reads de Illumina normalmente necessitam que estes dados tenham sido avaliados e processados previamente. Neste tutorial, abordaremos os processos de montagem de reads de Illumina e de PacBio separadamente.
<br><br>
Clique nos links abaixo para acessar as páginas do NCBI SRA que contém os arquivos que serão utilizados nesta e em atividades práticas futuras:
<br><br>
<ul>
<li><a href="https://www.ncbi.nlm.nih.gov/sra/SRX6433203%5baccn%5d">Sequenciamento de genoma de <i>Phyllosticta citriasiana</i> (linhagem CBS 120486) em Illumina</a></li>
<li><a href="https://www.ncbi.nlm.nih.gov/sra/SRX9601541%5baccn%5d">Sequenciamento de genoma de <i>Phyllosticta citricarpa</i> (linhagem CBS 111.20) em PacBio</a></li>
</ul>
Nesta atividade prática iremos:
<br><br>
<ul>
<li>Realizar a montagem do genoma da linhagem CBS 120486 de Phyllosticta citriasiana utilizando reads de Illumina</li>
<li>Realizar a montagem do genoma da linhagem CBS 128856 de Phyllosticta capitalensis utilizando reads de PacBio</li>
<li>Avaliar as montagens em relação à métricas básicas de contiguidade, tais como N50, L50, quantidade e tamanho dos contigs</li>
<li>Avaliar as montagens em relação à métricas de conteúdo, tais como distribuição de conteúdo GC, completude e presença de contaminantes</li>
</ul>
Após a realização destas etapas, utilizaremos os arquivos obtidos para as <a href="https://gstreinamentoseconsultoria.netlify.app/genomica/2023_01/praticas/aula_03">atividades práticas de predição e anotação de genes</a>
</div>

## Montagem de genomas com reads Illumina no Galaxy

<div align="justify">
Uma das vantagens de trabalhar com as análises diretamente no <a href="https://usegalaxy.org/">Galaxy</a> é a possibilidade utilizar os dados previamente importados do NCBI SRA e processados pelo FastQC e Trimmomatic, sem ter que realizar o download do arquivos no computador. Para realizar a montagem do genoma da linhagem CBS 120486 de Phyllosticta citriasiana com os dados de sequenciamento Illumina, utilizaremos o software SPAdes. Na aba “<i>Tools</i>”, na região esquerda da página, surgirão várias modalidades e submódulos do SPAdes, adaptados à diferentes tipos de dados (como plasmídeos, dados de metagenômica, genomas de SARS-CoV-2, entre outros). Selecione a opção “<i>SPADES - genome assemble for genomes of regular and single-cell projects</i>”:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_01.png" alt="Opção 'SPADES - genome assemble for genomes of regular and single-cell projects' na aba Tools do Galaxy" align="center">
</center>
<br><br>
Na opção “<i>Operation mode</i>” selecione “<i>Only assembler (--only-assembler)</i>”.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_02/aula_02_02.png" alt="Opção 'Operation mode' indicando a modalidade 'Only assembler' para configuração do SPAdes no Galaxy" align="center">
</center>
<br><br>
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
Por fim, podemos manter a opção <i>"Set Phred quality offset"</i> no modo de detecção automática (<i>"Auto"</i>), e selecionar os arquivos de saída desejados na aba <i>"Select optional output files"</i>. Por padrão, o SPAdes oferece a opção de gerar tanto contigs e scaffolds, bem como os respectivos grafos das montagens de contigs (<i>"Assembly graph"</i>) e de scaffolds (<i>"Assembly graph with scaffolds"</i>). Caso deseje remover e não gerar uma das modalidades de arquivo de saída, basta clicar no ícone de "X" e deletar o tipo de arquivo correspondente:
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