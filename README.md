# 🎮 Desafio Técnico 2: Know Your Fan

Este repositório contém a solução desenvolvida para o Desafio Técnico "Know Your Fan". O projeto simula as etapas iniciais de um sistema de CRM (Customer Relationship Management) voltado para fãs de e-sports, demonstrando a coleta de dados, validação de informações via OCR e uma simulação de análise de relevância utilizando Python em um ambiente como o Google Colab.

## Objetivo do Desafio

O objetivo principal foi criar um protótipo interativo que pudesse:
1.  Coletar informações básicas e interesses de um fã de e-sports.
2.  Simular a validação da identidade do fã através do processamento de imagem de um documento com OCR.
3.  Simular uma análise de relevância do fã com base em sua descrição online, utilizando lógica baseada em palavras-chave.
4.  Demonstrar a aplicação de diferentes tecnologias e bibliotecas Python para resolver um problema de negócio no contexto de e-sports.

## Tecnologias Utilizadas

* **Python:** Linguagem de programação principal.
* **Google Colab:** Ambiente para execução e prototipagem interativa.
* **PIL (Pillow):** Biblioteca para manipulação e processamento de imagens.
* **Pytesseract:** Biblioteca Python para interfacear com o Tesseract OCR Engine, permitindo a extração de texto de imagens.
* **`re` (Módulo de Expressões Regulares):** Utilizado para buscar e manipular padrões de texto, como o formato de CPF.
* **`google.colab.files`:** Módulo específico do Google Colab para facilitar o upload de arquivos.
* **`libfluidsynth1`:** Dependência de sistema operacional para o Tesseract OCR Engine (instalada via `apt-get`).

## Pré-requisitos

* Uma conta Google para acessar o Google Colab.
* Um navegador web compatível.
* Um arquivo de imagem (JPG, PNG, etc.) contendo o nome e CPF para a etapa de validação OCR.

## Configuração e Execução (via Google Colab)

O projeto foi desenvolvido para ser executado diretamente no Google Colab, o que simplifica a configuração.

1.  Faça o upload do notebook `Know_Your_Fan_Solution.ipynb` (ou copie o código) para o seu ambiente Google Colab.
2.  Execute as células do notebook sequencialmente.
3.  As primeiras células instalam as bibliotecas Python necessárias (`pytesseract`) e as dependências de sistema operacional para o motor Tesseract (`libfluidsynth1`). Certifique-se de executá-las primeiro.
    ```python
    !pip install matplotlib-venn # Nota: Esta biblioteca não é usada no código final, pode ser removida
    !pip install pytesseract
    !apt-get -qq install -y libfluidsynth1
    ```
4.  Prossiga executando as células seguintes, que solicitarão entrada de dados e o upload do documento.

## Como Utilizar

Ao executar as células, o script irá interagir com você solicitando as seguintes informações via input:

1.  Dados Básicos do Fã (Nome, CPF, Endereço, Email, Telefone)
2.  Interesses em E-sports (Jogos, Eventos, Compras)
3.  Upload do Documento para OCR: Uma caixa de diálogo aparecerá solicitando que você faça o upload do arquivo de imagem contendo o nome e CPF.
4.  Links de Redes Sociais (Twitter, Twitch, Outros)
5.  Descrição do Conteúdo Online (para a simulação de relevância)

Siga as instruções na tela para fornecer as informações solicitadas.

## Estrutura do Código

O notebook está organizado nas seguintes seções principais (comentários e células de texto no código):

* **Coleta de Dados Básicos:** Recebe informações do usuário via `input()`.
* **Upload e Validação de Documento com OCR:** Lida com o upload de arquivo, processa a imagem com OCR e tenta validar o nome e CPF.
* **Redes Sociais e Atividades Online:** Coleta links para perfis online.
* **Validação de Relevância com IA (Simulada):** Realiza uma verificação simples baseada em palavras-chave.
* **Storytelling Profissional / Conclusão:** Textos explicativos sobre o projeto, processo e futuro.

## Detalhes da Implementação

* **Coleta:** Utiliza a função `input()` padrão do Python para interagir com o usuário no ambiente de console/notebook.
* **OCR e Validação:**
    * O upload é feito via `google.colab.files.upload()`.
    * A imagem é aberta com `PIL.Image.open()`.
    * A extração de texto é feita com `pytesseract.image_to_string()`.
    * A busca pelo CPF no texto extraído usa `re.search()` com uma expressão regular para o formato padrão `###.###.###-##`.
    * O CPF extraído é limpo de pontos e traço usando `re.sub()` para conter apenas dígitos.
    * A validação compara se o nome digitado está presente no texto extraído (verificação básica) E se o CPF digitado corresponde ao CPF extraído (limpo). *Nota: Para uma validação mais robusta, seria ideal limpar também o CPF digitado antes de compará-lo com o CPF extraído limpo.*
* **Simulação de IA:**
    * Define uma lista de `palavras_chave` relevantes para e-sports.
    * Pede uma descrição do conteúdo online do fã.
    * Utiliza `any(palavra in conteudo_simulado for palavra in palavras_chave)` para verificar se pelo menos uma palavra-chave está presente na descrição (não importa a posição ou contexto, é uma simulação simples).

## Limitações e Melhorias Futuras

Este projeto é um protótipo para demonstração e possui algumas limitações inerentes à simulação:

* **Validação Limitada:** A validação de nome e CPF via OCR é básica e depende muito da qualidade da imagem e do layout do documento. Um sistema real exigiria algoritmos de OCR mais avançados e lógicas de validação mais robustas.
* **Simulação de IA Simples:** A análise de relevância é apenas uma busca por palavras-chave. Uma IA real utilizaria NLP para entender o contexto, sentimento, engajamento e interesses de forma muito mais sofisticada.
* **Sem Persistência de Dados:** Os dados coletados não são armazenados em um banco de dados. Em um sistema de CRM real, a persistência dos dados é fundamental.
* **Sem Integração Real:** Não há integração com APIs reais de redes sociais ou serviços de validação.
* **Ambiente:** Executa em um notebook interativo, não como uma aplicação web ou backend robusto.

Possíveis melhorias futuras incluem:

* Integrar um banco de dados (SQL, NoSQL) para armazenar os dados dos fãs.
* Implementar autenticação de usuários e gerenciamento de permissões.
* Utilizar APIs (com as devidas autorizações) para coleta de dados sociais e validação mais precisa.
* Desenvolver ou integrar modelos de Machine Learning para análise de sentimento, classificação de interesses, segmentação de público, etc.
* Construir uma interface de usuário (web ou mobile) para melhorar a experiência de coleta e visualização dos dados.
* Adicionar dashboards (ex: Power BI, Tableau) para visualização e análise dos dados coletados.

## Autor

* **Fabio Souza de Morais Filho** - *Desenvolvimento* - [[Linkedin]](https://www.linkedin.com/in/fabio-souza-12f/)

---
