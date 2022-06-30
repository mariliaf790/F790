# `Reconstrução 3D de posicionamento de probe para fNIRS e EEG`
# `Reconstruction of video-based motion resilient three-dimensional position for functional near infra-red spectroscopy and eletroenccephalography head mounted probes`

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação *EA979A - Introdução a Computação Gráfica e Processamento de Imagens*, 
oferecida no primeiro semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

> |Nome  | RA | Curso|
> |--|--|--|
> | Manuela Von Ah Davanço  | 240675  | Física Médica|
> | Marília Floriam Themer  | 184687  | Física Biomédica|


## Objetivo
> Como objetivo principal desse projeto, buscamos estudar o método de registro de posicionamento de probe, presente no artigo de referência ("Video-based motion-resilient reconstruction of three-dimensional position for near infra-red spectroscopy and eletroencephalography head mounted probes") e propor um código inicial para teste em laboratório.

## Justificativa
> Em métodos de análise em neurofísica, é útil obter o posicionamento correto dos eletrodos/optodos no escalpo do sujeito para determinação da região de ativação cerebral, em especial em estudos longitudinais (onde temos várias seções com o mesmo sujeito), esse procedimento é necessário para garantir que se analisam as mesmas regiões cerebrais nas seções, e não há diferenças no posicionamento dos eletrodos/optodos.

> Um método atual utilizado é em registro com referência magnética, que é sensível a movimentos físicos do sujeito, sendo quase impraticável em crianças, por exemplo, e situações de CTI/UTI. Para tanto, um método baseado em vídeo representa uma solução mais prática, barata, e de alta aplicabilidade.

## Contexto do Projeto
> Motivado pela Iniciação Científica das duas integrantes, o presente projeto se propõe a recriar o modelo de posicionamento de probe e eletrodo para técnicas de imagens aplicadas à neurofísica, como espectroscopia de infra-vermelho próximo e eletroencefalografia.

> O projeto consiste na tentativa de recriação do modelo presente no artigo "Video-based motion-resilient reconstruction of three-dimensional position for near infra-red spectroscopy and eletroencephalography head mounted probes" de Jaffe-Dax, Bermano, Erel e Emberson, de setembro de 2020, publicado na revista Neurophotonics.

## Atividades realizadas
> Como primeiro passo para o trabalho, utilizamos o mesmo vídeo que serviu de referência para o artigo estudado [1][2], o qual decompomos em seus frames a partir das funções '.VideoCapture()' e '.read()' em OpenCV [3][4], como pode-se ver no código do Google Colab fornecido na próxima sessão.

> Obtidos os frames do vídeo, fizemos a conversão de RGB para Grayscale, montamos o histograma e definimos o limiar da máscara de interpolação via função inpaint, para remover os pontos de luz estourada. Em seguida, faz a conversão da grayscale para HSV e definimos as máscaras de cor.

> Feita a filtragem dos pontos brancos, passamos para a filtragem do fundo das imagens, a fim de deixar o destaque apenas na touca de fNIRS. Note que uma fita com padrão de cor em vermelho e azul foi passada pela touca, e os pontos fiduciais nessa estão marcados como pontos verdes. Portanto, para tal, buscamos identificar as cores usadas (vermelho, verde e azul) atribuindo intervalos de valores entre 0 e 255 para cada uma no HSV, e filtramos o que estava fora desses intervalos, zerando-os, a partir de máscaras [5].

> Por fim, foi usado o software SFM [6], onde foi possível carregar os frames do vídeo obtidos anteriormente, a fim de fazer uma reconstrução 3D da touca de fNIRS. O resultado final pode ser visto na sessão seguinte.

## Resultados
> O código completo utilizado em Google Colab pode ser visto em 

> Um exemplo de frame obtido após a aplicação das máscaras de cores pode ser visto na Figura 1, seguido da reconstrução 3D obtida pelo software Visual SFM [6], na Figura 2.

## Mudanças realizadas
> Ao longo do trabalho, foram encontradas algumas dificuldades e formas de simplificar o processo.

> Primeiramente, estava planejado gravarmos nosso próprio vídeo de referência com a touca de fNIRS, o que foi posteriormente considerado tirar prints de tela do vídeo usado no artigo, até que finalmente usamos o vídeo completo do artigo, decompondo em seus frames usando OpenCV.

> Os códigos utilizados pelos autores e indicados no artigo não foram de grande ajuda, pois estavam em uma linguagem muito crua, sem muito desenvolvimento, o que nos levou a buscar nossas próprias referências. O artigo trabalhava com Machine Learning e visão computacional, enquanto que pelo escopo da disciplina, buscávamos focar em processamento de imagens.

> Estava previsto, após a projeção 3D no software de SFM, adquirirmos as distâncias dos probes da touca e as posições dos pontos fiduciais a fim de definir uma posição fixa que a touca fica na cabeça do sujeito. Porém, este processo não estava explicado tão detalhadamente no artigo, e envolvia a utilização de softwares em C++, por exemplo, e vimos muita dificuldade em entender o que devia ser feito. Por conta disso, preferimos dar maior atenção ao processo de filtragem do fundo dos frames e projeção no SFM, já que condiziam mais com o escopo da disciplina.

## Conclusões e sugestões para projetos futuros
> Considerando que o método original do artigo foi desenvolvido da computação para aplicação em neurofísica, e não da neurofísica para uso nela mesma, algumas  dificuldades surgem, por exemplo, os softwares usados (SPM) não são usuais para análise dos dados em fNIRS e EEG. Também, pensando em fazer o processsamento do vídeo por cores e não por redes neurais como no artigo, além de custo computacional menor, existem adaptações na gravação do vídeo que facilitariam o código, como uso de cores sólidas ao invés das funções usadas no artigo (como a chamada "Perlin Noise").
 
## Referências
> * [1] Sagi Jaffe-Dax, Amit H. Bermano, Yotam Erel, Lauren L. Emberson, "Video-based motion-resilient reconstruction of three-dimensional position for functional near-infrared spectroscopy and electroencephalography head mounted probes," Neurophoton. 7(3) 035001 (20 July 2020) https://doi.org/10.1117/1.NPh.7.3.035001
> * [2] https://www.youtube.com/watch?v=sD75ctsGlD4
> * [3] https://github.com/Ai-Genome-Saksham/OpenCV/blob/main/OpenCV/%239%20Extracting%20Images%20from%20Video.py
> * [4] https://www.youtube.com/watch?v=Ay6Nlb3KJog
> * [5] https://acervolima.com/deteccao-de-varias-cores-em-tempo-real-usando-python-opencv/
> * [6] http://ccwu.me/vsfm/








