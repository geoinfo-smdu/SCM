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

## Gerando o grid 1:25.000

Tudo configurado, podemos gerar a grade para a escala de 1:25.000. Para isso vamos clicar em `Vetor`, `Investigar` e `Criar grade ...`
Vamos gerar um tipo de `linha` e a cada `0.125` graus em cada uma das direções `vertival` e `horizontal` com a seguinte `extensão`

`-46.875, -46.250, -24.125, -23.250 [EPSG:4674]`

[imagem]

## Gerando o grid de 1:10.000

Agora precisamos dividir o grid de 1:25.000 em 6 quadriculas, sendo 3 no sentido horizontal e 2 no sentido vertical, que resultam respectivamente em distancias de 0.041666667 graus e 0.0625 graus

## Gerando o grid de 1:5.000

Agora precisamos dividir o grid de 1:10.000 em 4 quadriculas, que resultam respectivamente em distancias de 0.03125 graus e 0.02083334 graus

## Gerando o grid de 1:2.500

Agora precisamos dividir o grid de 1:5.000 em 4 quadriculas, que resultam respectivamente em distancias de 0.015625 graus e 0.01041667 graus





