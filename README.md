# Projeto de processamento de dados com Spark na AWS, com dados do kaggle. https://www.kaggle.com/nhs/general-practice-prescribing-data

- Criando aplicação de engenharia de dados com Spark para carregamento, processamento e entrega de dados prontos para serem utilizados, utilizando AWS S3 como data lake e AWS EMR para criação de clusters de processamento. 

- 1º passo - criar os buckets no amazon s3, no meu caso criarei 3, a landing zone onde carregarei os dados e meus códigos em Spark, a processing zone onde os dados serão processados e a curated zone onde dados apos serem processados estarão disponíveis para serem utilizados por ciêntistas de dados, engenheiro de machine learning, analistas de dados, ou qualquer outra pessoa que queria utilizar;

- 2º passo - codar a aplicação em spark e subir o arquivo para o s3, mais especificamente no bucket, onde os dados foram carregados;

  -  ps.: no passo dois existe uma conversão de dados do tipo .csv para tipo parquet, isso é algo essecial, uma vez que arquivos do tipo parquet são arquivos super comprimidos, o que na atual era do big data é uma vantagem gigante, pois os torna mais leves para serem trabalhados, no nosso caso os arquivos inicias tinham aproximadamente 4Gb de tamanho e quando convertidos para parquet passam a ter aproximadamente 1,5Gb. Mais infos sobre arquivos parquet: https://learn.microsoft.com/pt-br/azure/databricks/data/data-sources/read-parquet

- 3º passo - criação do cluster: escolhi um cluster barato(não ta facil aprender não! kkkkk) pois na aws os serviços de cluster são cobrados por hora. Nesse momento também se configura o encerramento das atividades do cluster para não gerar mais custos. Neste momento dentro o cluster , no meu caso configurei para logo apos ele rodar o step (ou a aplicação em spark) ele encerra o cluster. No step eu configuro o caminho onde esta o meu código para que quando o cluster rode saiba onde esta o arquivo com os código, no meu caso na landing zone.

- 4º passo - logo após criar o cluster, ele vai iniciar, rodar nossa aplicação spark e assim que terminar de rodar nossa aplicação, ira terminar o cluster como configurado em sua criação e não cobrara mais nada

- 5º passo - Ser feliz que o deploy funcionou o/


## Resumo do Cluster AWS EMR usado
![image](https://user-images.githubusercontent.com/58529172/194558574-7a5f752b-b4e8-489b-a3ee-7e303697d530.png)

## Modelo de DataLake
![image](https://user-images.githubusercontent.com/58529172/194559076-f02e029a-f2d5-40d8-b3b0-b96bc17c813c.png)

### Landing Zone (onde os dados foram carregados)
![image](https://user-images.githubusercontent.com/58529172/194559214-a2979216-73bb-4293-b6c1-3f1d313445ac.png)

### Processing Zone (onde os dados foram processados e transformados para o formato parquet)
![image](https://user-images.githubusercontent.com/58529172/194559718-6ead91e2-84da-4674-9487-374ad70fb1c3.png)
![image](https://user-images.githubusercontent.com/58529172/194560044-71126b81-59e8-48c1-b9c4-ae167d2f5dcd.png)

### Curated Zone (onde os dados estão prontos para serem utilizados)
![image](https://user-images.githubusercontent.com/58529172/194560209-46f17ce0-69d5-4c10-b5cb-7800ddf69eec.png)
![image](https://user-images.githubusercontent.com/58529172/194560326-b84ecdbc-cf14-480c-91eb-64e36272ecfc.png)




