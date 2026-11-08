# Análise de Corridas de Táxi em Chicago

Projeto da Sprint 7 em que analiso dados de corridas de táxi em Chicago para entender as preferências dos passageiros e o impacto do clima na duração das viagens.

## Objetivos

- Identificar as empresas de táxi com mais corridas
- Identificar os bairros mais populares como destino
- Testar se a duração das corridas do Loop até o Aeroporto O'Hare muda aos sábados com clima ruim

## Dados

| Arquivo | Conteúdo |
|---|---|
| `project_sql_result_01.csv` | Nome da empresa e número de corridas (64 empresas) |
| `project_sql_result_04.csv` | Bairro de destino e média de corridas (94 bairros) |
| `project_sql_result_07.csv` | Data/hora de início, condição do clima e duração das corridas Loop → O'Hare aos sábados (1.068 registros) |

## Etapas

1. **Exploração dos dados:** verificação de formato, tipos, valores ausentes e estatísticas descritivas
2. **Preparação:** conversão da coluna de data para `datetime`
3. **Análise exploratória:** gráficos de barras com as 10 maiores empresas e os 10 principais destinos
4. **Teste de hipóteses:** teste t de Welch para comparar a duração média das corridas com clima bom e ruim

## Principais resultados

- **Flash Cab** lidera o mercado com 19.558 corridas, cerca de 8 mil a mais que a segunda colocada (Taxi Affiliation Services).
- **Loop**, **River North** e **Streeterville** são os destinos mais populares, provavelmente por serem áreas comerciais e de negócios. O aeroporto **O'Hare** também aparece entre os principais.
- Aos sábados, as corridas Loop → O'Hare duram em média **~40 minutos com clima ruim**, contra **~33 minutos com clima bom**.

### Teste de hipóteses

- **H0:** a duração média é igual com clima bom e ruim
- **H1:** a duração média é diferente com clima bom e ruim
- **Nível de significância:** α = 0,05
- **Resultado:** valor-p ≈ 6,7 × 10⁻¹², então a hipótese nula foi rejeitada. O clima ruim afeta significativamente a duração das corridas.

## Tecnologias

- Python
- Pandas
- Matplotlib
- Seaborn
- SciPy

## Como executar

1. Clone o repositório
2. Instale as dependências:
   ```bash
   pip install pandas matplotlib seaborn scipy jupyter
   ```
3. Abra o notebook:
   ```bash
   jupyter notebook projetosprint7.ipynb
   ```

> Observação: o notebook lê os arquivos em `/datasets/`. Ajuste os caminhos se os CSVs estiverem em outra pasta.
