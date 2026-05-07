# 🤖 RAG com LLM — Chatbot para Análise de Documentos Financeiros
### Retrieval Augmented Generation com Google Gemini | Relatório de Estabilidade Financeira do Banco Central

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Gemini](https://img.shields.io/badge/Google-Gemini-orange?logo=google)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

---

## 📌 Sobre o Projeto

Sistema de **RAG (Retrieval Augmented Generation)** capaz de responder perguntas em linguagem natural sobre documentos financeiros complexos.

O sistema extrai o texto do PDF, divide em chunks, busca os trechos mais relevantes para cada pergunta e usa o **Google Gemini** para responder com base exclusivamente no conteúdo real do documento — sem alucinar informações.

---

## 🎯 Caso de Uso

> *Fazer perguntas em português sobre o Relatório de Estabilidade Financeira do Banco Central do Brasil e obter respostas fundamentadas no documento.*

**Exemplos de perguntas respondidas:**
- "Qual é a avaliação geral sobre a estabilidade do sistema financeiro brasileiro?"
- "Quais são os principais riscos identificados para o sistema financeiro?"
- "Como está o nível de capitalização dos bancos brasileiros?"
- "Qual é a situação da inadimplência no crédito?"

---

## 🗂️ Estrutura do Projeto

```
📁 rag-llm/
├── rag_llm.ipynb       # Notebook principal com pipeline RAG completo
├── .gitignore          # Ignora .env e PDFs (dados sensíveis)
└── README.md
```

> ⚠️ O arquivo `.env` com a API key e o PDF do documento **não são versionados** por segurança.

---

## 🔧 Tecnologias Utilizadas

| Ferramenta | Uso |
|-----------|-----|
| Python 3.11 | Linguagem principal |
| Google Gemini API | Modelo de linguagem (LLM) |
| google-genai | SDK oficial do Gemini |
| PyPDF2 | Extração de texto do PDF |
| python-dotenv | Gerenciamento seguro de credenciais |

---

## 🏗️ Como Funciona o Pipeline RAG

```
📄 PDF                    🔍 Busca                    🤖 LLM
─────────────────────────────────────────────────────────────
Documento  →  Chunks  →  Chunks         →  Prompt    →  Resposta
           →  (texto      relevantes    →  (contexto    fundamentada
               dividido)  (por keyword)    + pergunta)  no documento
```

**Etapas:**
1. **Extração** — PyPDF2 lê o PDF página por página
2. **Chunking** — Divide o texto em pedaços de ~3.000 caracteres com sobreposição
3. **Busca** — Encontra os chunks mais relevantes para a pergunta (busca por keyword)
4. **Geração** — Gemini responde com base exclusivamente no contexto recuperado

---

## 💬 Exemplos de Respostas

**Pergunta:** Qual é a avaliação geral sobre a estabilidade do sistema financeiro brasileiro?

> *"O Banco Central do Brasil considera que não há risco relevante para a estabilidade financeira. O Sistema Financeiro Nacional (SFN) permanece com capitalização e liquidez confortáveis, provisões adequadas ao nível de perdas esperadas, e os testes de estresse de capital e de liquidez demonstram a robustez do sistema bancário."*

---

**Pergunta:** Quais são os principais riscos identificados?

> *"Os principais riscos são: (1) Inadimplência e Atividade Econômica, (2) Riscos Operacionais — ataques cibernéticos e fraudes, (3) Riscos de IA — transparência e vieses, (4) Riscos Fiscais, (5) Cenário Internacional — tarifas dos EUA, (6) Inflação e taxa de juros doméstica."*

---

## ▶️ Como Executar

**1. Clone o repositório:**
```bash
git clone https://github.com/RoneyGalan/rag-llm.git
```

**2. Instale as dependências:**
```bash
pip install google-genai pypdf2 python-dotenv
```

**3. Configure sua API key:**

Crie um arquivo `.env` na raiz do projeto:
```
GEMINI_API_KEY=sua_key_aqui
```

Obtenha sua key gratuita em: **aistudio.google.com**

**4. Adicione o PDF:**

Coloque seu documento PDF na pasta do projeto e atualize o caminho no notebook.

**5. Execute o notebook:**
```bash
jupyter notebook rag_llm.ipynb
```

---

## 🚀 Próximos Passos

- **Embeddings vetoriais** — Substituir busca por keyword por embeddings semânticos (FAISS + sentence-transformers)
- **Memória de conversa** — Manter histórico para perguntas de follow-up
- **Interface web** — Frontend com Streamlit para uso sem código
- **Múltiplos documentos** — Indexar vários PDFs simultaneamente

---

## 👤 Autor

**Roney Wesley Galan** — Cientista de Dados | Analista de BI

[![LinkedIn](https://img.shields.io/badge/LinkedIn-roney--wesley--galan-blue?logo=linkedin)](https://linkedin.com/in/roney-wesley-galan-ba7aa194)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black?logo=github)](https://github.com/RoneyGalan)

---

> *"RAG é a ponte entre o conhecimento dos documentos e a inteligência dos LLMs."*
