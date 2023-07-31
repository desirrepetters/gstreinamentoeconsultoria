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
</div>

```
cat *.txt > PCitriasiana_CBS120486.tab
```

<div align="justify">
<br><br>
<center>
<img src="https://raw.githubusercontent.com/desirrepetters/gstreinamentoeconsultoria/master/userguide/content/pt-br/genomica/2023_01/praticas/img/aula_06/aula_06_19.png" alt="Comando de concatenação no Terminal no Windows" align="center">
</center>
<br><br>
Este comando realiza a concatenação de todos os arquivos com extensão txt (indicado pelo asterisco) em um arquivo de saída, aqui indicado como "PCitriasiana_CBS120486.tab". <b>Atenção:</b> caso existam outros arquivos com extensão "txt" na pasta, este comando também os concatenará no arquivo final, então cuidado ao utilizar este comando! Neste exemplo, como a pasta utilizada apresenta apenas os arquivos de saída do SignalP, não teremos maiores problemas.
</div>


## Detecção de domínios e hélices transmembrana com o DeepTMHHM

<div align="justify">
Em breve!
</div>

