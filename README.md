# `Reconstrução 3D de posicionamento de probe para fNIRS e EEG`
# `Reconstruction of video-based motion resilient three-dimensional position for functional near infra-red spectroscopy and eletroenccephalography head mounted probes`

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação *EA979A - Introdução a Computação Gráfica e Processamento de Imagens*, 
oferecida no primeiro semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

> |Nome  | RA | Curso|
> |--|--|--|
> | Manuela Von Ah Davanço  | 240675  | Física Médica|
> | Marília Floriam Themer  | 184687  | Física Biomédica|


## Descrição do Projeto
> Motivado pela Iniciação Cinetífica das duas integrantes, o presente projeto se propõe a recriar o modelo de posicionamento de probe e eletrodo para técnicas de imagens aplicadas à neurofísica, como espectroscopia de infra-vermelho próximo e eletroencefalografia.
> O projeto consiste na tentativa de recriação do modelo presente no artigo "Video-based motion-resilient reconstruction of three-dimensional position for near infra-red spectroscopy and eletroencephalography head mounted probes" de Jaffe-Dax, Bermano, Erel e Emberson, de setembro de 2020, publicado na revista Neurophotonics.

## Plano de Trabalho
> * Etapa 1 (2 semanas): Estudo da lógica de captação e tratamento das imagens contidas no artigo.
> 
>     Análise da lógica de programação e teoria das redes neurais de convolução e deconvolução apresentadas na parte de visão computacional.
>     Definição dos parâmetros de captação da imagem (vídeo slow motion).
>     Levantamento dos códigos (públicos) utilizados no artigo.
>     
> * Etapa 2 (1 semana): Captação de imagens
> 
>     Montagem de probe com stickers, gravação de pelo menos 5 takes para teste.
>     Escrever parte do código de limpeza de fundo.
>     
> * Etapa 3 (2 semanas): Codificação e Testes da fase de visão computacional.
> 
>     Codificar a leitura dos pontos fiduciais e limpeza de fundo e artefatos de movimento.
>     Testar em fotos e vídeos.
>     
> * Etapa 4 (2 semanas): Codificação e Testes da fase de geração de imagens.
> 
>     Codificação da projeção 3D, e extração dos posições dos pontos fiduciais.
>     Estimativa das distâncias cabeça-probe.
>     
> * Etapa 5 (2 semanas): Testes e finalização da projeção 3D.
>     
>     Execução da projeção, teste de funcionalidade.
>     Escrita do relatório de apresentação do projeto.

## Referências Bibliográficas
> Sagi Jaffe-Dax, Amit H. Bermano, Yotam Erel, Lauren L. Emberson, "Video-based motion-resilient reconstruction of three-dimensional position for functional near-infrared spectroscopy and electroencephalography head mounted probes," Neurophoton. 7(3) 035001 (20 July 2020) https://doi.org/10.1117/1.NPh.7.3.035001
> 
> Gonzalez & Woods, Digital Image Processing -  2a Edição - 2008


## Atualizações
> A etapa 1 foi concluída, e com ela foram feitas mudanças voltadas para as etapas 2 e 3.
> Dentre as mudanças, na etapa 2 não serão mais gravados vídeos, e sim adquiridas fotos por meio do vídeo de referência contido no artigo base (Ref.26 do artigo), através de screenshots da tela.
> E na etapa 3, não será mais necessário fazer a limpeza de artefatos de movimento, apenas a filtragem do fundo das imagens.
> Para melhor adequação ao escopo da disciplina, o enfoque do projeto passa a ser mais na parte de reconstrução 3D e geração de imagem, que na parte de visão computacional.

## Resultados parciais
> Os códigos desenvolvidos até agora foram parciais, e não correspondem à cópia do artigo, mas sim, à estudo do funcionamento de redes neurais e decupagem do vídeo em frames.
> https://colab.research.google.com/drive/1K8-BwV-0-soxphwuxwafbA5YkVMOfI8p?usp=sharing

## Para a entrega final:
## Atividades realizadas
> Como primeiro passo para o trabalho, utilizamos o mesmo vídeo que serviu de referência para o artigo estudado [1][2], o qual decompomos em seus frames a partir das funções '.VideoCapture()' e '.read()' em OpenCV [3][4], como pode-se ver no código do Google Colab fornecido na próxima sessão.

> Obtidos os frames do vídeo, aplicamos primeiro uma máscara para detectar os pontos brancos dos frames (pontos onde a iluminação estava muito intensa) a fim de filtrá-los.

> Feita a filtragem dos pontos brancos, passamos para a filtragem do fundo das imagens, a fim de deixar o destaque apenas na touca de fNIRS. Note que uma fita com padrão de cor em vermelho e azul foi passada pela touca, e os pontos fiduciais nessa estão marcados como pontos verdes. Portanto, para tal, buscamos identificar as cores usadas (vermelho, verde e azul) atribuindo intervalos de valores entre 0 e 255 para cada uma, e filtramos o que estava fora desses intervalos, a partir de máscaras [5].

> Ao final desse processo, obtidos todos os frames do vídeo original com o fundo retirado e com destaque na touca, partimos para salvar os frames em vídeo AVI [6] para fins de visualização.

> Por fim, foi usado o software SFM [7], onde foi possível carregar os frames do vídeo obtidos anteriormente, a fim de fazer uma reconstrução 3D da touca de fNIRS. O resultado final pode ser visto na sessão seguinte.

## Resultados
> O código completo utilizado em Google Colab pode ser visto em 

> Um exemplo de frame obtido após a aplicação das máscaras de cores pode ser visto na Figura 1, seguido da reconstrução 3D obtida pelo software em SFM, na Figura 2.

## Mudanças realizadas
> Ao longo do trabalho, foram encontradas algumas dificuldades e formas de simplificar o processo.

> Primeiramente, estava planejado gravarmos nosso próprio vídeo de referência com a touca de fNIRS, o que foi posteriormente considerado tirar prints de tela do vídeo usado no artigo, até que finalmente usamos o vídeo completo do artigo, decompondo em seus frames usando OpenCV.

> Os códigos utilizados pelos autores e indicados no artigo não foram de grande ajuda, pois estavam em uma linguagem muito crua, sem muito desenvolvimento, o que nos levou a buscar nossas próprias referências.

> Estava previsto, após a projeção 3D no software de SFM, adquirirmos as distâncias dos probes da touca e as posições dos pontos fiduciais a fim de definir uma posição fixa que a touca fica na cabeça do sujeito. Porém, este processo não estava explicado tão detalhadamente no artigo e vimos muita dificuldade em entender o que devia ser feito. Por conta disso, preferimos dar maior atenção ao processo de filtragem do fundo dos frames e projeção no SFM, já que condiziam mais com o escopo da disciplina.
 
## Referências
> * [1] Sagi Jaffe-Dax, Amit H. Bermano, Yotam Erel, Lauren L. Emberson, "Video-based motion-resilient reconstruction of three-dimensional position for functional near-infrared spectroscopy and electroencephalography head mounted probes," Neurophoton. 7(3) 035001 (20 July 2020) https://doi.org/10.1117/1.NPh.7.3.035001
> * [2] https://www.youtube.com/watch?v=sD75ctsGlD4
> * [3] https://github.com/Ai-Genome-Saksham/OpenCV/blob/main/OpenCV/%239%20Extracting%20Images%20from%20Video.py
> * [4] https://www.youtube.com/watch?v=Ay6Nlb3KJog
> * [5] https://acervolima.com/deteccao-de-varias-cores-em-tempo-real-usando-python-opencv/
> * [6] """" referencia pra salvar o video em avi """"
> * [7] http://ccwu.me/vsfm/








