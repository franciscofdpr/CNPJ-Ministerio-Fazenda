Script de Processamento de Dados do CNPJ e Geocodificação
Este repositório contém um script Python para processar arquivos de dados do CNPJ, carregá-los no DuckDB e geocodificar endereços para análise posterior. O script está organizado em duas partes principais:

Importação e Transformação de Dados: Utiliza o DuckDB para carregar, transformar e exportar dados de arquivos CSV do CNPJ.
Geocodificação: Geocodifica registros selecionados do CNPJ usando a API iocasta.com.br e exporta os resultados para um arquivo CSV.

Estrutura do Projeto
plaintext
Copiar código
.
├── script.py           # Script principal com funções para DuckDB e geocodificação
├── requirements.txt    # Dependências do Python
└── README.md           # Documentação do projeto

Pré-requisitos
Python 3.x
DuckDB
Pandas
Requests
Logging
ThreadPoolExecutor (do módulo concurrent.futures)
Para instalar as dependências necessárias, execute:

bash
Copiar código
pip install -r requirements.txt
Configuração
O script lê arquivos de uma pasta especificada e requer uma estrutura de pastas específica para os arquivos de dados, especialmente para informações do CNPJ e dos municípios. Defina o caminho data_fribeiro e certifique-se de que os arquivos de dados seguem a convenção de nomenclatura necessária.

Uso
O script está organizado em duas seções:

Importação e Transformação de Dados: Esta seção carrega e processa dados do CNPJ com DuckDB.

Arquivos de dados (cnae.csv, municipios.csv e múltiplos estabelecimentos_x.csv) são lidos de uma pasta.
Cria tabelas no DuckDB para armazenar dados de cnae, municipios e CNPJ.
Realiza join com a tabela municipios para construir endereços completos e armazena os resultados em CNPJ.csv.
Geocodificação: Esta seção realiza a geocodificação de endereços usando uma API.

Filtra registros pelos códigos cnae desejados.
Faz chamadas à API para obter dados de geocodificação dos endereços.
Salva os resultados geocodificados em CNPJ_Resultado.csv.
Para executar o script, use:

bash
Copiar código
python script.py
Logging
O script registra as etapas de processamento, incluindo:

Início e fim do processamento.
Status da importação de cada arquivo de dados.
Resultados da geocodificação ou erros. Os logs são exibidos no terminal para feedback em tempo real.
Tratamento de Erros
Importação de Dados: Ignora linhas com erros durante a importação usando IGNORE_ERRORS no DuckDB.
Requisições de API: Registra quaisquer erros encontrados durante chamadas à API.
Contribuição
Siga estas etapas para contribuir:

Faça um fork do repositório.
Crie uma nova branch.
Realize as alterações desejadas.
Envie um pull request.
Licença
Este projeto é open-source e está licenciado sob a Licença MIT.
