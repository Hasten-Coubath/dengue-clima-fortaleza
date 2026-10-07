# Dengue x Clima em Fortaleza

Projeto de Machine Learning que investiga a relação entre variáveis climáticas (chuva, temperatura e umidade) e o número de casos de dengue em Fortaleza – CE, com o objetivo de **prever a quantidade de casos semanais** a partir das condições climáticas das semanas anteriores.

## Pergunta central

> É possível antecipar surtos de dengue em Fortaleza usando dados climáticos das semanas anteriores?

A dengue tem forte componente sazonal: chuva e calor favorecem a reprodução do *Aedes aegypti*, mas o efeito no número de casos aparece com **atraso** de algumas semanas. Entender e modelar esse atraso é o centro do projeto.

## Fontes de dados (previstas)

| Fonte | Conteúdo |
|---|---|
| [InfoDengue](https://info.dengue.mat.br/) / [DATASUS – SINAN](https://datasus.saude.gov.br/) | Casos notificados de dengue por semana epidemiológica |
| [INMET](https://portal.inmet.gov.br/) | Dados meteorológicos da estação de Fortaleza |

## Estrutura do projeto

```
dengue-clima-fortaleza/
├── data/
│   ├── raw/          # dados originais, nunca editados manualmente
│   └── processed/    # dados limpos e integrados, gerados por código
├── notebooks/        # análises exploratórias e experimentos
├── src/              # código reutilizável (coleta, limpeza, features, modelos)
├── models/           # modelos treinados
├── reports/
│   └── figures/      # gráficos e visualizações
├── requirements.txt
└── README.md
```

## Tecnologias

- Python
- pandas e NumPy
- scikit-learn
- Matplotlib e Seaborn
- Jupyter

##  Como executar

```bash
git clone https://github.com/Hasten-Coubath/dengue-clima-fortaleza.git
cd dengue-clima-fortaleza

python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

## 👤 Autor

**Hasten Coubath** – Ciência da Computação, UNIFOR
[LinkedIn](https://linkedin.com/in/hasten-coubath) · [GitHub](https://github.com/Hasten-Coubath)

---

**Projeto em construção**
