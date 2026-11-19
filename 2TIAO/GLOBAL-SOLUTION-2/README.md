# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href="https://www.fiap.com.br/">
  <img src="../../assets/logo-fiap.png" 
       alt="FIAP - Faculdade de Informática e Administração Paulista" 
       width="40%">
</a>
</p>

<br>

# Nome do projeto/atividade

## Nome do grupo

## 👨‍🎓 Integrantes: 
- Carlos Daniel Silveira do Nascimento - RM88439
- Mauricio Jose Ferlin Tonnera - RM565469 
- Rodrigo Portugal Santos - RM564773


## 👩‍🏫 Professores:

### Tutor(a)
- <a href="Link do perfil no LinkedIn">Nome do Tutor</a>
  
### Coordenador(a)
- <a href="https://www.linkedin.com/in/andregodoichiovato/">André Godoi Chiovato</a>

## 📜 Descrição

O VozCidadã AI é uma Prova de Conceito (POC) desenvolvida para a Global Solution 2026.2 (CitizenTech – Tecnologia centrada no cidadão), alinhada diretamente ao ODS 11 (Cidades e Comunidades Sustentáveis) e ao ODS 9 (Indústria, Inovação e Infraestrutura) da ONU.
Nos centros urbanos, o cidadão enfrenta burocracia, falta de transparência e lentidão para reportar problemas cotidianos de zeladoria e infraestrutura (como descarte irregular de lixo, buracos nas vias e falhas de iluminação pública), enquanto gestores municipais lidam com triagem manual e chamados mal classificados.
Para solucionar esse desafio, o VozCidadã AI integra múltiplas frentes da Inteligência Artificial e Engenharia de Software em um fluxo automatizado, seguro e acessível:
- Governança e Privacidade desde a Concepção (LGPD): Antes de qualquer dado ser processado externamente, um módulo de sanitização local detecta e anonimiza CPFs, telefones e e-mails via expressões regulares (Regex), gerando um protocolo auditável com hash criptográfico (SHA-256) e timestamp UTC.
- Visão Computacional Híbrida: A imagem enviada pelo cidadão é processada por um pipeline que combina detecção de objetos com YOLOv8 e análise de densidade de bordas via OpenCV (Canny) para identificar elementos urbanos e irregularidades visuais.
- Agente Inteligente de Triagem (IA Generativa): Um agente baseado na API do Google Gemini (gemini-3.8-flash) com saída estruturada (Pydantic) cruza o relato anonimizado e as evidências visuais para classificar a categoria da demanda, definir o nível de urgência, rotear para a secretaria competente e gerar uma resposta clara e inclusiva ao cidadão.
- Painel de Monitoramento e Auditoria: Exibe indicadores de impacto (ODS 11), métricas de conformidade LGPD e uma tabela rastreável que distingue claramente registros de Base Simulada dos Testes Reais da POC.

## 📁 Estrutura de pastas 

Abaixo encontra-se a descrição da organização da raiz do projeto e a finalidade de cada diretório e arquivo:

* **`docs/`** Centraliza a documentação técnica e de negócio do projeto.

* **`src/`** Contém todo o código-fonte desenvolvido para o projeto. Dependendo do âmbito da atividade, pode incluir arquivos como: scripts (Python, R, JS), ficheiros web (HTML), firmware para hardware (ESP32/Arduino), além de APIs, microsserviços e ficheiros de modelos e inferências.
   * **`app.py`** Interface web interativa e dashboard de indicadores desenvolvido em Streamlit.
   * **`governanca.py`** Módulo de anonimização de dados sensíveis (LGPD) e geração de rastreabilidade (SHA-256).
   * **`visao_computacional.py`** Pipeline híbrido de análise de imagens com YOLOv8 e OpenCV.
   * **`agente_ia.py`** Agente de IA Generativa (Google Gemini + Pydantic) com mecanismo de contingência (fallback).
   * **`requirements.txt`** Lista de dependências e bibliotecas Python do projeto.

* **`README.md`** Este ficheiro. Funciona como o guia principal de introdução, configuração e contextualização do projeto.

## 📎 Links e Observações

### 🔗 Links do Projeto


* **[Vídeo de Entrega no YouTube](https://youtu.be/7uSkTmNIm6E?is=FQ4ViAOyJRm4uTjF)** - Sistema sendo executado na prática.

### 🧠 Decisões Técnicas

> - Interface Web em Streamlit (Python): Escolhida para permitir prototipagem ágil e integração nativa com bibliotecas de Ciência de Dados, Visão Computacional e IA Generativa em um único ecossistema.
> - Governança e Anonimização Local (Regex + SHA-256): Implementada localmente antes das chamadas externas à LLM para garantir conformidade com a LGPD (Privacy by Design) e rastreabilidade sem exposição de dados pessoais em texto claro.
> - Visão Computacional Híbrida (YOLOv8n + OpenCV): O modelo pré-treinado yolov8n.pt (dataset COCO) foi otimizado com cache de memória (@st.cache_resource) e redimensionamento (640px) para inferência rápida em CPU. Como o dataset COCO não possui classes específicas para entulho ou buracos no asfalto (limitação documentada da POC), combinamos a detecção de objetos com a análise de densidade de bordas via cv2.Canny e com a interpretação multimodal do agente LLM. Em etapas futuras, recomenda-se aplicar Transfer Learning com datasets específicos de resíduos urbanos (ex.: TACO).
> - Agente de IA Generativa Estruturado (Google Gemini + Pydantic) e Resiliência: Utilizou-se saída estruturada via JSON Schema (Pydantic) para garantir integração determinística com o roteamento de secretarias, além de controle de timeout (5s) e plano de contingência local (fallback por regras de NLP) para evitar falhas de disponibilidade (erro HTTP 503).
> - Segurança de Credenciais: A chave da API (GEMINI_API_KEY) não é versionada no repositório, sendo informada de forma mascarada em tempo de execução pela interface.

### 📢 Observações Gerais

* **Participação na Competição:** [ ] Sim, aceitamos participar / [X] Não vamos participar.

## 🔧 Como executar o código

*Acrescentar as informações necessárias sobre pré-requisitos (IDEs, serviços, bibliotecas etc.) e instalação básica do projeto, descrevendo eventuais versões utilizadas. Colocar um passo a passo de como o leitor pode baixar o seu código e executá-lo a partir de sua máquina ou seu repositório.*

---

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/fiap-tutoria/FIAP-PORTFOLIO-AI">TEMPLATE - FIAP PORTFÓLIO AI</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">FIAP</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>
