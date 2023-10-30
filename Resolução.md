#Breve documentação sobre o Case - Engenharia de Dados <br>

Notebook disponível em: https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/7954319091523522/4206084517050175/8320555514782779/latest.html

##Célula 1 - instalação do módulo openpyxl para leitura de arquivos Excel <br>
##Célula 2 - importações das bilbiotecas utilzadas durante o tratamento dos dados <br>
##Célula 3 - declaração de função para retirar acentos e caracteres especiais dos nomes da colunas <br>
##Célula 4 - declaração de função para normalizar o nome das colunas conforme indicado no readme.md <br>
##Célula 5 - leitura das bases <br>
##Célula 6 - utilização da função da [célula 4] <br>
##Célula 7 - transformação do dataframe pandas para spark <br>
##Célula 8 - declaração de função para converter o tipo para "data" <br>
##Célula 9 - declaração de função para arredondar valores para até 4 casas decimais <br>
##Célula 10 - utilizando as funções da [célula 8] e da [célula 9] <br>
##Célula 11 - Organizando as colunas do arquivo de colaboradoes de 2023 para junção <br>
##Célula 12 - trazendo os campos vazios na base de 2022 <br>
##Célula 13 - trazendo os campos vazios na base de 2023 <br>
##Célula 14 - trazendo os campos vazios na base de cargos <br>
##Célula 15 - unindo as bases de 2022 e 2023 <br>
##Célula 16 - esvaziando os dataframes de 2022 e 2023 para liberar memória de processamento do cluster <br>
##Célula 17 - Realizando uma junção dos dados de cargos na base de 2023 <br>
##Célula 18 - Criando um dimensão com o funcionário e sua data de admissão <br>
##Célula 19 - Adicionando à dimensão a idade e o tempo de empresa <br>
##Célula 20 - Adicionando a categoria de idade <br>
##Célula 21 - Adicionando a categoria de tempo de empresa <br>
##Célula 22 - Salvando o resultado em parquet <br>
##Célula 23 - Realizando a junção na base principal do tempo de empresa e idade <br>
##Célula 24 - Agrupando toda a dimensão por categorias e separando conforme solicitação do exercício <br>
##Célula 25 - Salvando o resultado em parquet <br>





