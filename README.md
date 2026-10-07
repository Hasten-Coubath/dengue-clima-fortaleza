# Radar Hospitalar CE

Pipeline de dados automatizado que monitora a **pressão sobre a rede hospitalar do SUS no Ceará**, a partir de dados públicos do DATASUS. O pipeline coleta, trata e analisa os dados de internações e de leitos mês a mês, sem intervenção manual, gerando indicadores e relatórios atualizados a cada nova publicação.

## Pergunta central

> Como está evoluindo, mês a mês, a pressão sobre a rede hospitalar do SUS no Ceará, e onde ela está concentrada?

A demanda hospitalar não fica restrita ao município onde o paciente mora: muitos precisam se deslocar para cidades-polo em busca de atendimento, o que sobrecarrega alguns pontos da rede enquanto outros ficam ociosos. Medir essa pressão de forma contínua, e não em análises pontuais, é o centro do projeto. Os fluxos entre município de residência e município de internação também formam uma **rede**, permitindo aplicar métricas de redes complexas para identificar os pontos críticos do sistema.

## Fontes de dados

| Fonte | Conteúdo |
|---|---|
| [DATASUS – SIH/SUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) | Autorizações de Internação Hospitalar (AIH) do Ceará, publicadas mensalmente |
| [DATASUS – CNES](https://datasus.saude.gov.br/transferencia-de-arquivos/) | Cadastro de estabelecimentos e leitos hospitalares |

Os arquivos são baixados diretamente do servidor FTP do DATASUS, no formato `.dbc`, e convertidos para tabelas com a biblioteca `pyreaddbc`.

## Como o pipeline funciona

```
[DATASUS] → Extração → Transformação → Armazenamento → Relatório
               ↑                                           │
               └──────── Orquestração (agendada) ──────────┘
```

| Etapa | Responsabilidade |
|---|---|
| **Extração** | Baixa os arquivos mensais do FTP do DATASUS, com cache e tratamento de falhas |
| **Transformação** | Limpa, padroniza e calcula os indicadores |
| **Armazenamento** | Grava os resultados de forma idempotente, mantendo o histórico |
| **Relatório** | Gera gráficos e resumos atualizados automaticamente |
| **Orquestração** | Executa o pipeline periodicamente via GitHub Actions |

## Indicadores previstos

- Volume de internações por município de residência e de ocorrência
- Tempo médio de permanência hospitalar
- Taxa de evasão: proporção de pacientes internados fora do município onde moram
- Relação entre internações e leitos disponíveis
- Rede de fluxo intermunicipal de pacientes e seus municípios mais centrais

## Estrutura do projeto

```
radar-hospitalar-ce/
├── src/radar/
│   ├── extract.py      # coleta dos dados no DATASUS
│   ├── transform.py    # limpeza e cálculo de indicadores
│   ├── load.py         # armazenamento dos resultados
│   └── report.py       # geração de gráficos e relatórios
├── data/
│   ├── raw/            # arquivos originais baixados, nunca editados manualmente
│   └── processed/      # dados tratados, gerados por código
├── tests/              # testes automatizados
├── requirements.txt
└── README.md
```

## Tecnologias

- Python
- pandas
- pyreaddbc
- SQLite
- GitHub Actions

## Como executar

```bash
git clone https://github.com/Hasten-Coubath/radar-hospitalar-ce.git
cd radar-hospitalar-ce

python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

Os comandos para rodar o pipeline serão adicionados conforme as etapas forem implementadas.

## Roadmap

- [x] Estrutura inicial do projeto
- [ ] Extração de um mês de internações do SIH/SUS
- [ ] Limpeza dos dados e primeiro indicador
- [ ] Armazenamento em banco de dados local
- [ ] Geração automática de relatório
- [ ] Execução agendada com GitHub Actions
- [ ] Série histórica, dados de leitos (CNES) e alertas
- [ ] Rede de fluxo intermunicipal de pacientes
- [ ] Dashboard interativo

## 👤 Autor

**Hasten Coubath** – Ciência da Computação, UNIFOR
[LinkedIn](https://linkedin.com/in/hasten-coubath) · [GitHub](https://github.com/Hasten-Coubath)

---

**Projeto em construção**