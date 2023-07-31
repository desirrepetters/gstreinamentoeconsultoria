---
title: "Aula 06 - Anotação funcional: efetores, localização celular e processos biológicos"
linkTitle: "Aula 06 - Anotação funcional: efetores, localização celular e processos biológicos"
weight: 2
description: >
  Softwares utilizados: SignalP, DeepTMHMM, DeepLoc
---

<div align="justify">
Texto inicial em breve!
</div>

## Detecção de peptídeo sinal com o SignalP

<div align="justify">
Para a detecção de efetores, é importante trabalhar somente com o conjunto de proteínas que são secretadas, pois do contrário, é possível obter falsos positivos e detectar características de proteínas efetoras em proteínas que permanecem no interior da célula. Sendo assim, a primeira etapa é detectar a presença de peptídeo sinal, que será um indicativo de que a proteína de fato é secretada. Para esta análise, utilizaremos a ferramenta SignalP 6.0 em sua versão <a href="https://services.healthtech.dtu.dk/services/SignalP-6.0/">online</a>. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_01.png" alt="Visão geral da página inicial do SignalP 6.0" align="center">
</center>
<br><br>
Antes de efetivamente iniciarmos a análise e escolher o arquivo de interesse, temos uma limitação: o SignalP 6.0 analisa somente 1000 sequências de proteínas por vez. Dessa forma, caso o genoma de interesse apresente mais de 1000 proteínas, como é o caso do genoma da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i> sendo utilizado como exemplo (9282 proteínas), será necessário dividir o arquivo de sequências de proteínas em dois ou mais arquivos distintos. Para dividir o arquivo, utilizaremos uma funcionalidade presente no Galaxy USA, a ferramenta Split Fasta. Na aba <i>"Tools"</i> do Galaxy USA, selecione a opção <i>"Split Fasta into a collection"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_02.png" alt="Opção 'Split Fasta into a collection' na aba Tools do Galaxy USA" align="center">
</center>
<br><br>
Em seguida, faça o upload do arquivo de sequências de aminoácidos das proteínas da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i> utilizando a opção <i>"Upload Data"</i>.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_03.png" alt="Opção 'Upload Data' na aba Tools do Galaxy USA" align="center">
</center>
<br><br>
Ao abrir a aba <i>"Upload from Disk or Web"</i>, selecione a opção <i>"Choose local files"</i> para escolher o arquivo de interesse, e em seguida clique em <i>"Start"</i> para iniciar o upload:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_04.png" alt="Aba 'Upload from Disk or Web' com as opções 'Choose local files' e 'Start' para upload de arquivo no Galaxy USA" align="center">
</center>
<br><br>
Após o término do upload, selecione o arquivo de interesse na opção <i>"Fasta file to split"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_05.png" alt="Opção 'Fasta file to split' indicando o arquivo de interesse para configuração do Split fasta no Galaxy USA" align="center">
</center>
<br><br>
Na opção <i>"Split mode"</i>, selecione a modalidade <i>"Split into a number of chunks"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_06.png" alt="Opção 'Split mode' indicando a modalidade 'Split into a number of chunks' para configuração do Split fasta no Galaxy USA" align="center">
</center>
<br><br>
Já na opção <i>"Number of chunks to split into"</i> indicaremos a quantidade de arquivos para que o arquivo original seja dividido em partes iguais. Como o arquivo original neste caso apresenta 9282 sequências e o SignalP apresenta um limite máximo de 1000 sequências por vez, será necessário dividir o arquivo original em pelo menos 10 arquivos de saída, cada um com 928 sequências: 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_07.png" alt="Opção 'Number of chunks to split into' indicando a modalidade '10' para configuração do Split fasta no Galaxy USA" align="center">
</center>
<br><br>
Por fim, basta clicar em “<i>Run Tool</i>” para iniciar a análise. Caso deseje receber uma notificação por e-mail após a conclusão da tarefa, selecione <i>"Yes"</i> na opção <i>"Email notification"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_08.png" alt="Opções para configuração da ferramenta Split fasta no Galaxy USA, indicando Run Tool e Email notification" align="center">
</center>
<br><br>
Como resultado, o Split Fasta produz um registro de arquivo de saída no formato de lista, a qual contém os arquivos resultantes da divisão. Neste caso, 10 arquivos FASTA, cada um com 982 sequências:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_09.png" alt="Arquivo de saída 'Split Fasta, a list with 10 datasets' como resultados do SplitFasta no Galaxy USA" align="center">
</center>
<br><br>
Clicando na lista, é possível ter acesso aos arquivos individualmente. É possível realizar o download os três arquivos conjuntamente utilizando a opção <i>"Download"</i> ou separadamente pelo ícone de disquete de cada um deles. Após o download, será possível enviá-los ao Galaxy Europe e utilizar o SignalP:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_10.png" alt="Arquivos de saída 'part1', 'part10', 'part2' 'part3' 'part3' e 'part4' como resultados do Split Fasta no Galaxy USA" align="center">
</center>
<br><br>
Voltando ao site do SignalP, faremos o upload do primeiro arquivo FASTA  na aba <i>"Submit data"</i> utilizando a opção <i>"Escolher arquivo"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_11.png" alt="Opção 'Escolher arquivo' na aba 'Submit data' do SignalP" align="center">
</center>
<br><br>
Em seguida, na opção <i>"Organism"</i>, selecione a modalidade <i>"Eukarya"</i>. Para a opção <i>"Output format"</i> selecionaremos a modalidade <i>"Short output (no figures)"</i> para facilitar o posterior processamento da tabela de resultados. Por fim, na opção <i>"Model mode"</i>, selecionaremos a modalidade <i>"Fast"</i>. Após configurar as opções, basta clicar em <i>"Submit"</i> para iniciar a análise:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_12.png" alt="Opção 'Organism' indicando a modalidade 'Eukarya', opção 'Output format' indicando a modalidade 'Short output (no figures)' e opção 'Model mode' indicando a modalidade 'Fast' para configuração do SignalP" align="center">
</center>
<br><br>
Após clicar em <i>"Submit"</i>, somos redirecionados para uma aba de espera, em que a tarefa recebe um identificador único (nesse caso, <i>"64C6E60C000045DC2BDDED64"</i>. Caso deseje, é possível inserir seu endereço de e-mail na opção <i>"Send me email when job finishes"</i>, para receber um aviso quando a análise terminar:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_13.png" alt="Identificador da tarefa e opção 'Send me email when job finishes' do SignalP" align="center">
</center>
<br><br>
Ao terminar a análise, o SignalP fará o redirecionamento automático para a aba de resultados. É possível navegar pelos resultados individualmente para cada sequência analisada ao realizar a rolagem pela página. Para proteínas em que detectou-se a presença de um peptídeo sinal no início da sequência, o campo <i>"Prediction"</i> traz a informação <i>"Signal Peptide (Sec/SPI)"</i>, bem como a posição do sítio de clivagem (<i>"Cleavage site between pos. and pos."</i>) e a probabilidade associada à detecção (<i>"Probability"</i>). Para as outras, a informação apresentada é <i>"Other"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_14.png" alt="Aba de resultados do SignalP, com exemplo de proteínas com e sem peptídeo sinal, apresentando as informações 'Signal Peptide (Sec/SPI)' e 'Other', respectivamente" align="center">
</center>
<br><br>
No ínicio da aba de resultados, é possível realizar o download dos arquivos em vários formatos. O arquivo que utilizaremos para compor nossa lista de proteínas com peptídeo sinal é o arquivo <i>"Prediction summary"</i>:
<br><br>
<ul>
<li><i>"JSON summary"</i>: resumo dos resultados no formato JSON</li>
<li><i>"Prediction summary"</i>: resultados em formato TXT, apresentados como texto separado por tabulações</li>
<li><i>"Processed entries fasta"</i>: arquivo FASTA com as sequências das proteínas para as quais detectou-se a presença de peptídeo sinal, com o peptídeo sinal removido da sequência</li>
<li><i>"Processed entries GFF3"</i>: coordenadas das regiões de peptídeo sinal que foram removidas das sequências de proteínas para as quais detectou-se a presença de peptídeo sinal </li>
<li><i>"Region predictions GFF3"</i>: regiões n-terminal, central (hidrofóbica) e c-terminal presentes nos peptídeos sinal detectados</li>
<li><i>"All results compressed (zip)"</i>: todos os resultados mencionados anteriormente em um único arquivo ZIP</li>
</ul>
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_15.png" alt="Arquivos de saída 'JSON summary', 'Prediction summary', 'Processed entries fasta', 'Processed entries GFF3', 'Region predictions GFF3' e 'All results compressed (zip)' como resultados do SignalP" align="center">
</center>
<br><br>
Basta repetir os mesmos procedimentos com os outros 9 arquivos contendo o restante das sequências, e juntar os arquivos <i>"Prediction summary"</i> de cada análise para obter um resultado único de presença ou não de peptídeo sinal para as sequências de aminoácidos das proteínas do genoma de interesse. Uma estratégia relativamente simples para isso envolve a utilização do Windows Power Shell, mas antes precisaremos preparar os arquivos para a concatenação. Para isso, abra todos os arquivos de resultados no Notepad++. No primeiro arquivo, remova a primeira linha (destacada com a marcação em azul na imagem) e salve o arquivo:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_16.png" alt="Indicação de remoção da primeira linha no primeiro arquivo de resultados do SignalP no Notepad++" align="center">
</center>
<br><br>
Nos arquivos subsequentes, remova sempre as primeiras duas linhas (destacadas com a marcação azul na imagem), e salve os arquivos: 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_17.png" alt="Indicação de remoção das duas primeiras linhas no arquivos subsequentes de resultados do SignalP no Notepad++" align="center">
</center>
<br><br>
Após realizar a remoção das linhas em todos os arquivos, acesse a pasta em que os arquivos estão armazenados, clique com o botão direito do mouse em algum espaço vazio, e após abrir a aba de opções, clique em <i>"Abrir no Terminal"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_18.png" alt="Opção 'Abrir no Terminal' no Windows" align="center">
</center>
<br><br>
Ao abrir a janela do terminal, digite o seguinte comando:
<br><br>
</div>

```
cat *.txt > PCitriasiana_CBS120486_signalp.tab
```

<div align="justify">
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_19.png" alt="Comando de concatenação no Terminal no Windows" align="center">
</center>
<br><br>
Este comando realiza a concatenação de todos os arquivos com extensão txt (indicado pelo asterisco) em um arquivo de saída, aqui indicado como "PCitriasiana_CBS120486_signal.tab".
<br><br>
<b>Atenção:</b> caso existam outros arquivos com extensão "txt" na pasta, este comando também os concatenará no arquivo final, então se esta for sua situação, indique os nomes de cada arquivo individualmente. Neste exemplo, como a pasta utilizada apresenta apenas os arquivos de saída do SignalP, não teremos maiores problemas. Após a concatenação, basta manter este arquivo salvo, para retomar seu uso em etapas futuras.
</div>

## Detecção de domínios e hélices transmembrana com o DeepTMHMM

<div align="justify">
Além, outra etapa prévia antes da anotação de efetores, além da detecção da presença de peptídeo sinal, consiste em avaliar se as proteínas apresentam possíveis domínios e hélices transmembrana, também para evitar resultados falsos positivos ao detectar características de proteínas efetoras em proteínas que permanecem aderidas à membrana da célula. Para esta análise, utilizaremos a ferramenta DeepTMHMM em sua versão <a href="https://dtu.biolib.com/DeepTMHMM">online</a>. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_20.png" alt="Visão geral da página inicial do DeepTMHMM" align="center">
</center>
<br><br>
Na primeira aba, <i>"Input"</i>, utilize a opção <i>"Select File"</i> para inserir o arquivo de interesse. O DeepTMHMM também apresenta uma limitação quanto ao tamanho de arquivo a ser utilizado, então podemos reutilizar os arquivos que preparamos na etapa anterior para <a href="https://gstreinamentoeconsultoria.netlify.app/genomica/2023_01/praticas/aula_06/#detecção-de-peptídeo-sinal-com-o-signalp">detecção de peptídeo sinal</a>. Depois de inserir o arquivo de interesse, clique em <i>"Run"</i> para iniciar a análise.
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_21.png" alt="Aba 'Input' e opção 'Select File' para configuração do DeepTMHMM" align="center">
</center>
<br><br>
A aba <i>"Compute"</i> fornece informações sobre o progresso da análise, que consiste em quatro etapas. 
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_22.png" alt="Aba 'Compute' e etapas da análise do DeepTMHMM" align="center">
</center>
<br><br>
Após o término da análise, o DeepTMHMM redireciona automaticamente a navegação para a aba <i>"Results"</i>. O campo <i>"Job Summary"</i> apresenta um breve resumo dos resultados, indicando a quantidade de proteínas avaliadas e as respectivas categorias de classificação:
<ul>
<li><i>"TM"</i>: quantidade de proteínas com domínio transmembrana dentre as proteínas avaliadas</li>
<li><i>"SP+TM"</i>: quantidade de proteínas com domínio transmembrana e peptídeo sinal dentre as proteínas avaliadas</li>
<li><i>"SP"</i>: quantidade de proteínas com peptídeo sinal dentre as proteínas avaliadas</li>
<li><i>"GLOB"</i>: quantidade de proteínas classificadas como "globulares", ou seja, sem domínio transmembrana e peptídeo sinal</li>
</ul>
Os arquivos de resultados podem ser baixados de forma conjunta por meio da opção <i>"Download"</i>, ou individualmente nos seguintes formatos:
<ul>
<li><i>"GFF3"</i>: coordenadas das hélices e domínios transmembrana para cada proteína avaliada</li>
<li><i>"3line"</i>: arquivo FASTA modificado, apresentando a classificação de cada uma das proteínas em TM, SP+TM, SP ou GLOB, bem como a indicação do posicionamento de cada aminoácido da sequência (por exemplo, se está posicionado em domínio transmembrana ou dentro/fora da célula)</li>
</ul>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_23.png" alt="Aba 'Results' e breve resumo dos resultados no DeepTMHMM" align="center">
</center>
<br><br>
Repita o mesmo processo de configuração do DeepTMHMM para os outros 9 arquivos de sequências de proteínas da linhagem CBS 120486 de <i>Phyllosticta citriasiana</i>. Após o término de todas as análises, iremos juntar os arquivos <i>"predicted_topologies.3line"</i> de cada análise para obter um resultado único de presença ou não de domínio transmembrana para as sequências de aminoácidos das proteínas do genoma de interesse. Utilizaremos a mesma estratégia empregada anteriormente com o Windows Power Shell, mas desta vez não será necessário preparar os arquivos previamente. Acesse a pasta em que os arquivos estão armazenados, clique com o botão direito do mouse em algum espaço vazio, e após abrir a aba de opções, clique em <i>"Abrir no Terminal"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_24.png" alt="Opção 'Abrir no Terminal' no Windows" align="center">
</center>
<br><br>
Ao abrir a janela do terminal, digite o seguinte comando:
<br><br>
</div>

```
cat *.3line > PCitriasiana_CBS120486_deeptmhmm.3line
```

<div align="justify">
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_25.png" alt="Comando de concatenação no Terminal no Windows" align="center">
</center>
<br><br>
Este comando realiza a concatenação de todos os arquivos com extensão 3line (indicado pelo asterisco) em um arquivo de saída, aqui indicado como <i>"PCitriasiana_CBS120486_deeptmhmm.3line".</i> Entretanto, este arquivo, além de conter a lista com as sequências e suas respectivas categorias, apresenta as sequências em formato FASTA, que é uma informação que neste contexto não nos interessa. Existe uma maneira relativamente simples de remover as linhas com estas informações extras utilizando o Notepad++. Para isso, abra o arquivo <i>"PCitriasiana_CBS120486_deeptmhmm.3line"</i> e na aba <i>"Localizar"</i> clique na opção <i>"Marcar"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_26.png" alt="Aba 'Localizar' indicando a opção 'Marcar' no Notepad++" align="center">
</center>
<br><br>
Na aba <i>"Marcar"</i>, ative a opção <i>"Marcar linha"</i> e também a modalidade <i>"Expressão regular"</i> dentre as opções de <i>"Modo de pesquisa"</i>. No campo <i>"Localizar"</i>, utilize o texto "^>", que é uma expressão regular que indica que o Notepad++ deve procurar pelo símbolo ">" em todo início de linha (indicado pelo símbolo "^"). Clique em <i>"Localizar todos"</i> para que a busca seja realizada:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_27.png" alt="Configuração da aba 'Marcar' para uso de expressão regular no Notepad++" align="center">
</center>
<br><br>
Observe que após o uso deste comando, todas as linhas iniciadas pelo símbolo de ">" apresentam um marcador azul, enquanto as demais linhas não possuem marcadores:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_28.png" alt="Linhas com e sem marcadores após uso do comando 'Marcar linha' no Notepad++" align="center">
</center>
<br><br>
Utilizaremos a presença de marcadores para distinguir quais linhas devem permanecer no arquivo e quais linhas devem ser removidas. Na aba <i>"Localizar"</i>, dentro da seção <i>"Marcadores"</i>, clique na opção <i>"Apagar linhas sem marcadores"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_29.png" alt="Aba 'Localizar' indicando a opção 'Apagar linhas sem marcadores' dentro da seção 'Marcadores' no Notepad++" align="center">
</center>
<br><br>
Observe que agora todas as linhas sem marcadores foram removidas do arquivo, restando somente as linhas com marcadores azuis, que são as linhas que nos interessam, visto que apresentam o nome de cada um dos genes, bem como a sua classificação em TM, SP+TM, SP ou GLOB:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_30.png" alt="Linhas com marcadores após uso do comando 'Apagar linhas sem marcadores' no Notepad++" align="center">
</center>
<br><br>
Para remover os marcadores antes de realizarmos outras edições no arquivo, basta acessar novamente a aba <i>"Localizar"</i> e a seção <i>"Marcadores"</i>, e desta vez selecionar a opção <i>"Limpar todos marcadores"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_31.png" alt="Aba 'Localizar' indicando a opção 'Limpar todos marcadores' dentro da seção 'Marcadores' no Notepad++" align="center">
</center>
<br><br>
Observe que agora todos os marcadores foram removidos das linhas:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_32.png" alt="Linhas com marcadores após uso do comando 'Apagar linhas sem marcadores' no Notepad++" align="center">
</center>
<br><br>
Antes de salvarmos o arquivo, iremos realizar algumas outras edições para facilitar a compilação e manipulação do arquivo posteriormente. Para isso, acessaremos novamente a aba <i>"Localizar"</i>, e utilizaremos a seção <i>"Substituir"</i>:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_33.png" alt="Aba 'Localizar' indicando a opção 'Substituir' no Notepad++" align="center">
</center>
<br><br>
Na aba <i>"Substituir"</i>, ative a modalidade <i>"Normal"</i> dentre as opções de <i>"Modo de pesquisa"</i>. No campo <i>"Localizar"</i>, utilize o texto ">", para indicar que o Notepad++ deve procurar pelo símbolo ">". No campo <i>"Substituir"</i>, deixe o texto vazio, para indicar que o Notepad++ deve excluir os símbolos de ">" que encontrar. Clique em <i>"Substituir todos"</i> para que as substituições sejam realizadas:
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_34.png" alt="Configuração da aba 'Substituir' para substituições de texto no Notepad++" align="center">
</center>
<br><br>
</div>

## 