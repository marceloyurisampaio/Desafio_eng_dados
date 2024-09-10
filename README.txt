*Este é o resultado final do desafio de engenharia de dados*

Descrição dos arquivos: 

   - Desafio e-Core Marcelo Yuri Sampaio de Freitas.pdf: 
      ->Arquivo contendo o diagrama lógico da solução, Email
	para o arquiteto de dados e email para o cliente com
	as respostas para os desafios de negócio
   
   -ETL:
      ->Contém o arquivo do notebook do processo de ETL
   
   -SQL_queries:
      ->Contém o arquivo notebook contendo os comandos SQL 
	que respondem as perguntas de negócios.

   -datalake:
      ->Contém todos os arquivos de entrada e saída que são
	pedidos. É dividido em 3 camadas: raw, curated e refined.
	raw contém os arquivo brutos de entrada, curated contém
	arquivos intermediários e a refined contém os arquivos
	finais refinados. 
      ->Na pasta refined, a pasta df_movies contém os arquivos 
	finais de saída em .parquet. A pasta business_challenge
	contém os arquivos que respondem os dois desafios de 
	negócio que dão nome a pasta.

Como rodar o processo de ETL?

    1)O arquivo notebook está escrito de forma a configurar todo o
     ambiente do google colab não necessitando nenhum upload de 
     arquivo de dados, o arquivo baixa automaticamente utilizando 
     a API do kaggle. No entanto é preciso obter uma chave json da
     API no site do kaggle, para facilitar deixo uma chave na raiz 
     dessa pasta(kaggle.json), será preciso dela para que o notebook 
     baixe todos os arquivos diretamente do kaggle. 

    2)Logo no início do notebook, existem os seguintes comandos: 
	.config("spark.driver.memory", "4g") \
        .config("spark.executor.memory", "4g") \
      Aqui está sendo configurada a memória disponível para ser uti- 
      lizada pelo código. NÃO É RECOMENDADO configurar com menos do 
      que 4Gb, pois pode faltar memória durante a execução e não ter 
      o resultado desejado. 
     
     3)Durante o processo, serão baixados os arquivos da base de dados
       e descompactados. Aqui faz-se necessária atenção, pois caso es-
       teja utilizando a versão gratuita do Google Colab, vai faltar
       disco durante a execução, então é necessário que seja acompanhado 
       o consumo de disco durante a descompactação dos arquivos da amazon,
       excluindo arquivos que não serão utilizados na analise. Somente
       devem ser considerados os seguintes arquivos: 
		*Video_v1_00
                *Video_DVD_v1_00
                *Digital_Video_Download_v1_00
       os demais arquivos podem ser excluídos liberando espaço para a 
       execução do código. No total são necessários por volta de 101 Gb.
       Atenção: A descompactação de arquivos pode levar mais de 20 min,
       caso já tenha disponível os arquivos descompactados, fazer o upload
       pode ser uma opção de otimizar esse processo.
     
      4)Durante todo o processo coloquei comando de impressão dos dataframes
	ja pré-disponíveis, para ativa-los basta excluir '#' logo a frente 
	do comando.
      
      5)Ao final existe um comando de compactação do resultado final, ao 
	terminar a execução do processo, basta baixar o arquivo df_movies.zip
	para ter os arquivos de saída reunidos em um só local. 

Espero que tenha uma boa experiência!

Marcelo Yuri Sampaio de Freitas


