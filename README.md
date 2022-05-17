Reconstrução 3D de posicionamento de probe para fNIRS e EEG

Reconstruction of video-based motion resilient three-dimensional position for functional near infra-red spectroscopy and eletroenccephalography head mounted probes
  
Apresentação
  
O presente projeto foi originado no contexto das atividades da disciplina de pós-graduação EA979A - Introdução a Computação Gráfica e Processamento de Imagens, oferecida no primeiro semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

Nome	                  RA	     Curso
  
Manuela Von Ah Davanço	240675	Física Médica
  
Marília Floriam Themer	184687	Física Biomédica
  
Descrição do Projeto
  
Motivado pela Iniciação Cinetífica das duas integrantes, o presente projeto se propõe a recriar o modelo de posicionamento de probe e eletrodo para técnicas de imagens aplicadas à neurofísica, como espectroscopia de infra-vermelho próximo e eletroencefalografia. O projeto consiste na tentativa de recriação do modelo presente no artigo "Video-based motion-resilient reconstruction of three-dimensional position for near infra-red spectroscopy and eletroencephalography head mounted probes" de Jaffe-Dax, Bermano, Erel e Emberson, de setembro de 2020, publicado na revista Neurophotonics.
  
Plano de Trabalho

Etapa 1 (2 semanas): Estudo da lógica de captação e tratamento das imagens contidas no artigo.

  Análise da lógica de programação e teoria das redes neurais de convolução e deconvolução apresentadas na parte de visão computacional. 
  Definição dos parâmetros de captação da imagem (vídeo slow motion).
  Levantamento dos códigos (públicos) utilizados no artigo.

Etapa 2 (1 semana): Captação de imagens.

  Montagem de probe com stickers, gravação de pelo menos 5 takes para teste. 
  Escrever parte do código de limpeza de fundo. 

Etapa 3 (2 semanas): Codificação e Testes da fase de visão computacional.

  Codificar a leitura dos pontos fiduciais e limpeza de fundo e artefatos de movimento.
  Testar em fotos e vídeos.

Etapa 4 (2 semanas): Codificação e Testes da fase de geração de imagens. 

  Codificação da projeção 3D, e extração dos posições dos pontos fiduciais.
  Estimativa das distâncias cabeça-probe.
  
Etapa 5 (2 semanas): Testes e finalização da projeção 3D.

  Execução da projeção, teste de funcionalidade.
  Escrita do relatório de apresentação do projeto.
  

Referências Bibliográficas
  
Sagi Jaffe-Dax, Amit H. Bermano, Yotam Erel, Lauren L. Emberson, "Video-based motion-resilient reconstruction of three-dimensional position for functional near-infrared spectroscopy and electroencephalography head mounted probes," Neurophoton. 7(3) 035001 (20 July 2020) https://doi.org/10.1117/1.NPh.7.3.035001
  
  
Gonzalez & Woods, Digital Image Processing -  2a Edição - 2008


***Atualizações***
A etapa 1 foi concluída, e com ela foram feitas mudanças voltadas para as etapas 2 e 3.
Dentre as mudanças, na etapa 2 não serão mais gravados vídeos, e sim adquiridas fotos por meio do vídeo de referência contido no artigo base (Ref.26 do artigo), através de screenshots da tela.
E na etapa 3, não será mais necessário fazer a limpeza de artefatos de movimento, apenas a filtragem do fundo das imagens.
Para melhor adequação ao escopo da disciplina, o enfoque do projeto passa a ser mais na parte de reconstrução 3D e geração de imagem, que na parte de visão computacional.
