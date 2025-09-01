# 🤖 IA de Atendimento – C++ (Open Source)

Projeto inicial de **chatbot de atendimento** em C++ para rodar no terminal.
Sem dependências externas. A base de conhecimento é um arquivo `TSV` simples.

> Objetivo: ser um **repo-base colaborativo**, fácil de evoluir (adicionar NLP, REST API, WhatsApp, etc.).

---

## 📁 Estrutura
```
ia-atendimento-cpp/
├─ src/
│  └─ main.cpp        # Chatbot em C++
├─ data/
│  └─ faq.tsv         # Base de perguntas|respostas (TSV)
├─ .gitignore
├─ LICENSE
└─ README.md
```

---

## 🛠️ Como compilar
Requer **g++ (C++17)**.

### Linux / WSL / macOS
```bash
g++ -std=gnu++17 -O2 src/main.cpp -o chatbot
```

### Windows (MinGW)
```bash
g++ -std=c++17 -O2 src\main.cpp -o chatbot.exe
```

---

## ▶️ Como rodar
```bash
./chatbot           # usa data/faq.tsv por padrão
# ou
./chatbot data/minha_base.tsv
```

No chat, digite sua pergunta e pressione Enter.
Para sair, digite: `sair`.

---

## 🧠 Como editar a base (TSV)
- Formato: **pergunta \t resposta** (tab entre colunas).
- Tudo em **minúsculas** para melhor correspondência.
- Exemplo:
```
qual o horario de atendimento?	Nossa loja atende de segunda a sexta, das 8h às 18h.
vocês fazem reparo de impressora?	Sim, realizamos manutenção e reparo de impressoras jato de tinta e laser.
```

---

## 🧩 Como funciona a busca
1. Tenta **match exato** (string inteira).
2. Se não achar, usa uma **similaridade simples por tokens (Jaccard)** e retorna a melhor correspondência acima de um limiar.

> É bem básico por design, para ser fácil de evoluir.

---

## 🧭 Roadmap para evoluir (PRs bem-vindos)
- [ ] Normalização com remoção de acentos.
- [ ] Persistência de logs de conversas (CSV/JSON).
- [ ] Modo servidor (REST) com Pistache/crow ou cpp-httplib.
- [ ] Suporte a múltiplas bases (`data/*.tsv`) com auto-load.
- [ ] Integração com modelos de linguagem via API.
- [ ] Exportar/Importar base em JSON/YAML.
- [ ] Interface web em React/Gradio falando com o binário.
- [ ] Testes unitários (Catch2 / GoogleTest).

---

## 🤝 Contribuindo
1. Faça um fork e crie uma branch: `feat/minha-ideia`
2. Rode localmente e adicione exemplos na `data/faq.tsv`
3. Abra PR descrevendo a mudança e motivação

---

## 📜 Licença
[MIT](LICENSE)
