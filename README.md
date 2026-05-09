# 🤖 RAG com HuggingFace — Atividade Semanal #8

Implementação prática de **RAG (Retrieval Augmented Generation)** usando a plataforma HuggingFace, em Python.

> **Disciplina:** Inteligência Artificial
> **Atividade:** Semana #8 — Sala e Laboratório

---

## 👥 Integrantes do grupo

<!-- Edite a lista abaixo com os nomes do seu grupo -->
- Giovanni Shiroma Amaral
- Vitor Lora
- Guilherme Capel
- Bernardo Almeida

---

## 📌 Sobre o projeto

Este repositório contém a implementação de uma aplicação **RAG** que combina:

1. **Retrieval (Recuperação):** busca de documentos relevantes em uma base de conhecimento
2. **Generation (Geração):** uso de um LLM para gerar respostas baseadas no contexto recuperado

### Por que RAG?

LLMs comuns têm duas limitações:
- **Conhecimento limitado** ao período de treinamento
- **Alucinação** quando não conhecem o fato exato

O RAG resolve isso fornecendo contexto factual no momento da consulta.

---

## 🏗️ Arquitetura

```
Pergunta do usuário
       ↓
[1] Embedding (sentence-transformers/all-MiniLM-L6-v2)
       ↓
[2] Busca por similaridade (FAISS)
       ↓
[3] Prompt + Contexto recuperado
       ↓
[4] LLM gera resposta (google/flan-t5-base)
       ↓
   Resposta final
```

---

## 🛠️ Stack tecnológica

| Componente | Biblioteca | Modelo |
|---|---|---|
| Embeddings | `sentence-transformers` (HuggingFace) | `all-MiniLM-L6-v2` |
| Vector Database | `FAISS` (Facebook AI) | — |
| LLM | `transformers` (HuggingFace) | `google/flan-t5-base` |
| Orquestração | `langchain` | — |

---

## 🚀 Como executar

### Opção 1 — Google Colab (recomendado)

1. Faça upload do arquivo `RAG_HuggingFace.ipynb` no [Google Colab](https://colab.research.google.com/)
2. Execute as células sequencialmente (Runtime → Run all)
3. Não é necessário GPU — todo o pipeline roda em CPU

### Opção 2 — Localmente

```bash
# Clone o repositório
git clone https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
cd SEU_REPOSITORIO

# (Opcional) Crie um ambiente virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate    # Windows

# Instale as dependências
pip install langchain langchain-community langchain-huggingface
pip install faiss-cpu sentence-transformers transformers

# Abra o notebook
jupyter notebook RAG_HuggingFace.ipynb
```

---

## 📁 Arquivos do repositório

```
.
├── README.md                  # Este arquivo
├── RAG_HuggingFace.ipynb      # Notebook com o código completo
└── apresentacao_rag.pdf       # Apresentação de 3 slides
```

---

## 📊 Resultados

O sistema responde corretamente perguntas factuais sobre a base de conhecimento (no notebook usamos uma base sobre exploração de Marte).

**Exemplo de comparação:**

| | Resposta |
|---|---|
| **Sem RAG** | `"24 hours"` (genérica) |
| **Com RAG** | `"cerca de 24 horas e 37 minutos"` (precisa, baseada na base) |

---

## 📖 Referências

### Documentação oficial
- [HuggingFace](https://huggingface.co/)
- [HuggingFace Hub](https://huggingface.co/docs/hub/index)
- [LangChain](https://python.langchain.com/docs/get_started/introduction)
- [Sentence Transformers](https://www.sbert.net/)
- [FAISS — Facebook AI Similarity Search](https://github.com/facebookresearch/faiss)

### Modelos usados
- [`sentence-transformers/all-MiniLM-L6-v2`](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
- [`google/flan-t5-base`](https://huggingface.co/google/flan-t5-base)

### Artigos científicos
- Lewis et al. (2020) — [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401)
- Chung et al. (2022) — [Scaling Instruction-Finetuned Language Models (FLAN-T5)](https://arxiv.org/abs/2210.11416)
- Reimers & Gurevych (2019) — [Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://arxiv.org/abs/1908.10084)

### Tutoriais e materiais auxiliares
- [HuggingFace × LangChain — partner package](https://huggingface.co/blog/langchain)
- [LangChain — RAG Tutorial](https://python.langchain.com/docs/tutorials/rag/)

---

## 📝 Licença

Este projeto foi desenvolvido para fins educacionais como parte da atividade semanal da disciplina de Inteligência Artificial.
