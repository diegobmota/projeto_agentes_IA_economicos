<div align="center">

# 📊 Dashboard Streamlit — UI Modernizada

**Dashboard financeiro com navegação multi-página, histórico inteligente e assistente IA integrado.**

![Status](https://img.shields.io/badge/status-est%C3%A1vel-brightgreen)
![Streamlit](https://img.shields.io/badge/streamlit-compat%C3%ADvel-FF4B4B?logo=streamlit&logoColor=white)
![Compatibilidade](https://img.shields.io/badge/breaking%20changes-zero-blue)

</div>

---

## 📌 Visão Geral

Este dashboard foi reestruturado de uma página única com scroll infinito para uma **arquitetura modular de 6 páginas navegáveis**, com foco em manutenibilidade, reuso de código e experiência do usuário.

| | Antes | Depois |
|---|---|---|
| **Estrutura** | 1 página, scroll longo | 6 páginas via menu lateral |
| **Código** | 431 linhas monolíticas | 654 linhas modulares + 300 linhas de helpers |
| **Carregamento CSV** | 3 funções duplicadas | 1 função reutilizável |
| **Blocos de gráfico** | 2 blocos de 30+ linhas | 2 funções de 15 linhas |

---

## 📁 Estrutura do Projeto

```
streamlit/
├── helpers.py      # Biblioteca de componentes reutilizáveis
└── dashboard.py     # Sistema de páginas com navegação
```

**`helpers.py`** — funções organizadas por categoria:
- **Dados** — carregamento com cache
- **UI** — componentes padronizados
- **Gráficos** — criação automatizada
- **Processamento** — preparação de dados
- **Histórico** — gestão de estado
- **Sidebar** — navegação e status

**`dashboard.py`** — sistema modular de páginas:
- Configuração centralizada
- Estado de sessão
- 6 funções de página independentes
- `main()` com roteamento

---

## 🧭 Navegação

### Menu principal (sidebar)

| Página | Descrição |
|---|---|
| 🏠 **Home** | Métricas gerais e visão consolidada |
| 🤖 **Análise Agentes** | Relatório CrewAI completo |
| 📈 **Ações** | Análise visual de ações da B3 |
| 📊 **Indicadores** | Gráficos de indicadores econômicos |
| 📰 **Notícias** | Feed de notícias com filtros |
| 💬 **Chat** | Assistente IA conversacional |

A sidebar também exibe o **status do sistema** em tempo real: indicadores de arquivos carregados e timestamp da última atualização.

---

## ✨ Funcionalidades

### Home
4 métricas principais (Ações, Indicadores, Notícias, Status IA), preview rápido dos dados e botões de acesso direto às demais páginas.

### Histórico inteligente
- **Ações** — salva consultas com ticker + estatísticas
- **Indicadores** — guarda análises realizadas
- **Chat** — histórico completo de conversas
- Ações disponíveis: `Limpar` | `Download JSON`

### Filtros avançados
- **Notícias** — filtro por quantidade e por fonte, com contador dinâmico de resultados

### Exportação
- Relatório de agentes em `.md`
- Históricos em `.json`
- Download com um clique

### UX
- Padrão consistente **Entrada → Contexto → Saída** em todas as páginas
- Loading spinners
- Estados vazios informativos
- Feedback visual constante

---

## 🚀 Como usar

```bash
streamlit run streamlit/dashboard.py
```

### Fluxo recomendado
1. Comece pela **Home** para uma visão geral
2. Navegue até **Ações** ou **Indicadores** para análises específicas
3. Consulte **Notícias** para contexto de mercado
4. Use o **Chat** para tirar dúvidas
5. Veja o **Relatório dos Agentes** para uma análise mais profunda

### Dicas
- Use "Salvar no Histórico" para guardar análises importantes
- Baixe os históricos em JSON para consultas offline
- Filtre notícias por fonte para focar em veículos específicos
- O chat mantém contexto entre mensagens

---

## ✅ Compatibilidade

- 100% compatível com o código anterior
- Zero breaking changes
- Mesmas variáveis de ambiente (`OPENAI_API_KEY`, etc.)
- Mesmos arquivos de dados (`data/*.csv`)

---

## 🛠️ Troubleshooting

<details>
<summary><strong>ModuleNotFoundError: No module named 'helpers'</strong></summary>

Certifique-se de estar na pasta correta ao executar o comando:

```bash
cd streamlit/
streamlit run dashboard.py
```
</details>

<details>
<summary><strong>Arquivos não encontrados</strong></summary>

- Verifique se a pasta `data/` existe
- Execute `python main/main.py` para gerar os dados
- Confira o status na sidebar do dashboard
</details>

<details>
<summary><strong>Chat não funciona</strong></summary>

- Verifique se `OPENAI_API_KEY` está configurada
- Veja a mensagem de erro exibida na página do Chat
- Configure a chave no `.env` ou nas variáveis de ambiente do sistema
</details>

---

## 🗺️ Roadmap

**Usuários**
- [ ] Explorar todas as páginas do menu
- [ ] Testar os filtros de notícias
- [ ] Salvar consultas no histórico
- [ ] Experimentar o download de dados

**Desenvolvedores**
- [ ] Adicionar testes em `tests/`
- [ ] Criar página de configurações
- [ ] Implementar mais filtros
- [ ] Adicionar novos tipos de gráficos

---

<div align="center">

**Desenvolvido com foco em UX, manutenibilidade e escalabilidade.**

</div>
