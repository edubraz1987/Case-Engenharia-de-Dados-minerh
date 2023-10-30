# Case-Engenharia-de-Dados-minerh
Repositório para armazenar os códigos do case / exame para a engenharia de dados.

# Case - Engenharia de Dados

# Introdução

A MINEHR é uma startup desenvolvedora de uma plataforma que permite a visualização, diagnóstico e predição dos dados de gestão de pessoas para empresas. Por meio da adoção do analytics aos modelos preditivos mais avançados, transforma dados em informações relevantes para orientar as decisões estratégicas e empoderar times de RH e lideranças.

# Desafio de Engenharia de Dados

O time de Engenharia de Dados tem como uma de suas tarefas, receber bases de dados brutas diversas do time de Gestão de Pessoas das empresas, e refiná-las para que possam ser usadas pelo time de Ciência de Dados e pela plataforma.

O cliente inseriu a base de dados na nuvem, e seu objetivo é aplicar os tratamentos necessários, que incluem:

<aside>
⚠️ **Toda a sua solução deve estar versionada e disponível em um repositório público no GitHub.**

</aside>

- Realizar a leitura e união dos arquivos de 2022 e 2023  em uma única base;
    - Você terá que carregar arquivos de dados de diferentes extensões disponibilizados no nosso Data Lake.
        - Base colaboradores 2022: https://storage.googleapis.com/desafio-ed/ingestion/base_colaboradores_2022.csv
            - Obs: use encoding “latin-1” e o separador “;”
        - Base colaboradores 2023: https://storage.googleapis.com/desafio-ed/ingestion/base_colaboradores_2023.xlsx
        - Base de-para: https://storage.googleapis.com/desafio-ed/ingestion/de-para.xlsx

<aside>
⚠️ No caso de leitura direta das URLs via Python, leia todos os arquivos usando o Pandas e depois converta-os para um DataFrame do Spark.

</aside>

```python
from pyspark.sql import SparkSession
import pandas as pd

## Aqui partimos do pressuposto que você já carregou os arquivos em um pandas df

# Converta o DataFrame do Pandas para um DataFrame do Spark
spark_df = spark.createDataFrame(pandas_df)
```

- Defina o esquema de dados corretamente, padronizando a nomenclatura das colunas existentes e atribuindo os tipos corretos para cada uma delas.
- Faça o pré-processamento dos dados de acordo com seus tipos:
    - Para as colunas textuais, retire os leading and trailing whitespace e coloque as iniciais maiúsculas.
    - Para as colunas numéricas, certifique-se que tenha no máximo 4 casa decimais.
    - Para presença de valores nulos, decida qual abordagem você acha mais apropriados. São algumas: descarte completo da coluna, imputação de dados, remoção da linha ou não fazer nada.
- Criação de coluna via de-para (grupo cargo): olhar planilha extra fornecida;
- Criação das duas colunas inteiras:
    - idade: idade da pessoa naquele mês referência;
    - tempo_empresa: o tempo, em meses, em que a pessoa pessoa está ativa na empresa até aquele mês;
- Criação das duas colunas categóricas, obedecendo os critérios abaixo. Certifique sempre de que os testes lógicos estão de acordo com a unidade de medida que queremos utilizar.

| ds_idade_cat | ds_tempo_empresa_cat |
| --- | --- |
| < 21 Anos | Até 3 Meses |
| Entre 21 E 25 Anos | Entre 3 E 6 Meses |
| Entre 26 E 30 Anos | Entre 6 Meses E 1 Ano |
| Entre 31 E 40 Anos | Entre 1 E 2 Anos |
| Entre 41 E 50 Anos | Entre 2 E 5 Anos |
| Acima De 50 Anos | Entre 5 E 10 Anos |
|  | Acima De 10 Anos |
- Nesse momento, é necessário que você salve o atual estado do seu spark dataframe no formato parquet com o nome **“mensalizada”**.
- Em seguida, você deve agrupar seus dados por **mês referência** e **cargo** e fazer as seguintes contas:
    - Contar o número de mulheres e homens;
    - Contar o número de estado civil;
    - Média de idades;
    - Idade máximo;
    - Idade mínima;
    - Data de admissão mais antiga por cargo.
- Salve o spark dataframe agrupado no formato parquet com o nome **“fato”**

# **Sugestão de ferramentas:**

Aqui estão as ferramentas que usamos e sugerimos que você use neste processo:

- Notebooks Jupyter  / Databricks ⇒ para criar os códigos;
- GitHub ⇒ como um repositório para armazenar os códigos e alguma, simples, documentação.

# Materiais

O time de RH forneceu duas bases de colaboradores - em CSV e Excel -, com os dados mais úteis. 

Considere a seguinte definição de dados abaixo:

| mês referência | Indica o mês ao qual os dados de referem |
| --- | --- |
| matricula | Número único atribuído a cada funcionário da empresa para identificação interna. |
| data admissao | A data em que o funcionário foi contratado pela empresa. |
| funcionario | Nome do funcionário. |
| nacionalidade | A nacionalidade do funcionário, indicando o país de origem. |
| estado civil | O estado civil do funcionário |
| sexo | O sexo do funcionário. |
| cargo | O cargo do funcionário. |
| empresa | O empresa do funcionário. |
| data de nascimento | O data de nascimento do funcionário. |
| data demissao | A data de demissão do funcionário. |

Além disso, o time forneceu uma planilha de-para para a criação da coluna de grupo cargo.

# Entrega final

O que se espera que você entregue dentro do período:

<aside>
⚠️ **Toda a sua solução deve estar versionada e disponível em um repositório público no GitHub.**

</aside>

**Códigos:** Notebook com códigos em pySpark;

**Documentação técnica:** de preferência um README simples em markdown, para
explicar a lógica do código em mais detalhes.

Você deve enviar um email com o link do seu repositório do github para os seguintes destinatários:

<aside>
⚠️ **As bases 'mensalizada' e 'fato' devem estar disponíveis no repositório do GitHub. Na presença de qualquer dificuldade em fazer o upload dessas tabelas, elas podem ser anexadas ao corpo do email.**

</aside>

# Critérios de avaliação

**Qualidade do seu código**: avaliação do desempenho e facilidade de leitura /
compreensão do código.

**Explicação/Retórica:** avaliação da sua capacidade de entendimento do desafio e capacidade explicar as estratégias adotadas. Somos um time diverso e muitas vezes você terá que explicar conceitos técnicos para pessoas não técnicas.

**Documentação:** o material possui documentação clara da lógica dos tratamentos? Outro/a Engenheiro de Dados é capaz de reutilizar seu código para casos similares?
