# Reproduzindo o SCM no QGis

Primeiramente precisamos fazer o download do arquivo com os polígonos de SCM pelo GeoSampa. Eles estão disponíveis para download em `Articulação de imagens` e `Articulação MDT`
O link direto para o download desse arquivos é [http://geosampa.prefeitura.sp.gov.br/PaginasPublicas/downloadIfr.aspx?orig=DownloadCamadas&arq=20_Articulacao%20de%20Imagens%5C%5CArticula%E7%E3o%20MDT%5C%5CShapefile%5C%5CSIRGAS_SHP_quadriculamdt&arqTipo=Shapefile](este)

## Carregando arquivo de base

Precisamos carregar o arquivo de `Articulação MDT` em um novo projeto no QGis, lembrando sempre de conferir o SRC do arquivo importando. No caso desse arquivo o SRC é SIRGAS2000/23S
Essas quadrículas vão servir de base para conferir o SCM que vamos gerar

[Imagem]

## Preparando a projeção

Agora vamos preparar a projeção. Segundo a denominação da [Carta Internacional ao Milionésimo - CIM](http://coral.ufsm.br/cartografia/index.php?option=com_content&view=article&id=24%3Acartaninternacionalndonmundonaonmilionesimo-cimn&catid=14%3Abasico&Itemid=30) , a folha de menor dimensão e nomeável é a de escala 1:25.000
Nessa escala as arestas das folhas seguem uma sequencia a cada 7'30", ou seja, a cada 0.125 graus. Portanto podemos gerar essa malha, desde que a projeção utilizada no projeto seja em Graus (Latitude e Longitude)
Então vamos ter o SRC da camada em SIRGAS2000 UTM 23S (EPSG:31983) e a projeção em SIRGAS2000 (lat/long) (EPSG:4674)

[Imagem]

## Gerando o Grid do SCM

O Grid inicial do SCM para fins de nomenclatura por digitos deve ser um quadrilátero de 1° por 1°, com uma divisão vertical a cada 0º 15' (minutos de grau) com as sequintes coordenadas:

`-47.250, -46.250, -24.250, -23.250 [EPSG:4674]`

Começando da esquerda para direita, cada uma das feições deve ser nomeada de 1 a 4.


## Gerando o grid 1:25.000

Tudo configurado, podemos gerar a grade para a escala de 1:25.000. Para isso vamos clicar em `Vetor`, `Investigar` e `Criar grade ...`
Vamos gerar um tipo de `linha` e a cada `0.125` graus em cada uma das direções `vertival` e `horizontal` com a seguinte `extensão`

`-46.875, -46.250, -24.125, -23.250 [EPSG:4674]`

[imagem]

## Gerando o grids das outras escalas

Agora precisamos ir gerando grids para cada uma das escalas conforme a tabela seguinte. Para fins didáticos é interessante ir fazendo uma a uma, mas podemos ir direto para a escala de 1:1000 e gerar o mesmo MDC que temos baixado. A questão é somente nomear essas quadrículas. Para isso a ferramenta mais adequada talvez seja a programação. 

## Resumo Tabela de escalas

|Escala     |Div Horizontal	|Div Vertical	|GMS Horizontal	|GMS Vertical	|Decimal Horizontal	|Decimal Vertical |
|-----------|-------|-------|---------------|---------------|-------------------|-------------------|
|1:25000	|-	    |-	    |0° 07' 30''	|0° 07' 30''	|0,125	            |0,125              |
|1:10000	|2	    |3	    |0° 03' 45''	|0° 02' 30''	|0,0625         	|0,041666666666667  |
|1:5000	    |2	    |2	    |0° 01' 53''	|0° 01' 15''	|0,03125        	|0,020833333333333  |
|1:2500	    |3	    |2	    |0° 00' 38''	|0° 00' 38''	|0,010416666666667	|0,010416666666667  |
|1:1000	    |2	    |2	    |0° 00' 19''	|0° 00' 19''	|0,005208333333333	|0,005208333333333  |





