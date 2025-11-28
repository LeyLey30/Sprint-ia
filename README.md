TELEHEALTH
Análise de Adoção da Telemedicina por Perfil Regional e Demográfico
Gustavo Felex RM554242
Vinicius Santos RM552904
Vinicius Issa Gois Rm553814
Gustavo Bonani RM553493
Wesley Leopoldino RM553496

1. INTRODUÇÃO
A telemedicina tem se tornado uma ferramenta importante no sistema de saúde moderno, especialmente após o contexto da pandemia de COVID-19. Entender quais regiões e perfis demográficos utilizam mais esse tipo de serviço é essencial para identificar desigualdades, direcionar investimentos e tomar melhores decisões na saúde pública.
Neste trabalho, o objetivo foi investigar se características regionais e demográficas são capazes de prever quais regiões apresentam alta adoção de telemedicina. Para isso, utilizamos o conjunto de dados TMEDTREND_PUBLIC_250827.csv, que contém informações sobre beneficiários do sistema de saúde dos Estados Unidos.
A pergunta principal de pesquisa foi:
"É possível prever se uma combinação de características regionais e demográficas leva uma região (estado/trimestre) a estar entre os grupos de alta adoção de telemedicina?"
2. FORMULAÇÃO DO PROBLEMA
A variável pct_telehealth representa o percentual de uso de telemedicina em cada combinação de região, trimestre e perfil demográfico. A partir dela, criamos uma nova variável chamada high_adoption para transformar o problema em uma tarefa de classificação:
Classe 1: alta adoção = valores acima do percentil 75% em cada trimestre
Classe 0: baixa adoção = demais 75%
Assim, o modelo tenta prever se uma região (estado + trimestre + grupo demográfico) faz parte do grupo de maior uso de telemedicina.
3. DESCRIÇÃO DOS DADOS
O dataset contém informações sobre ano, trimestre, estado, sexo, idade, raça, nível de ruralidade e percentual de uso de telemedicina. As principais variáveis utilizadas foram:
year e quarter (ano e trimestre)
bene_geo_desc (estado)
bene_race_desc (raça)
bene_sex_desc (sexo)
bene_age_desc (faixa etária)
bene_ruca_desc (nível urbano ou rural)
pct_telehealth (percentual de telemedicina)
Essa estrutura permite uma análise cruzada entre região, demografia e comportamento de uso.
4. ANÁLISE EXPLORATÓRIA (EDA)
Foi realizada a análise exploratória dos dados através de:
Histogramas para visualizar a distribuição do pct_telehealth
Heatmap de correlação para identificar relação entre variáveis numéricas
Verificação de valores extremos e padrões por trimestre
Com isso, foi possível observar que o uso de telemedicina varia bastante entre faixas etárias, regiões e grupos demográficos, indicando que há perfis mais propensos à adoção.

5. PREPARAÇÃO PARA O MODELO
Selecionamos como variáveis de entrada (features) somente as características regionais e demográficas. Como essas variáveis são categóricas, utilizamos o método OneHotEncoder para convertê-las em números.
O conjunto de dados foi dividido em 80% para treino e 20% para teste, mantendo o equilíbrio entre as classes através de estratificação.

6. MODELAGEM DE MACHINE LEARNING
O modelo utilizado foi o Random Forest Classifier, pois ele lida bem com variáveis categóricas e consegue capturar interações complexas entre fatores demográficos e regionais.
Foi criado um Pipeline para unir o pré-processamento dos dados com o modelo, garantindo a execução correta de todas as etapas.

7. AVALIAÇÃO DO MODELO
As principais métricas usadas foram:
Acurácia
Precision
Recall
F1-score
Matriz de confusão
Também analisamos a importância das variáveis, e foi possível identificar quais grupos populacionais e quais regiões têm maior influência nos níveis de adoção da telemedicina.
8. RESULTADOS PRINCIPAIS
O modelo conseguiu classificar com boa precisão os casos de alta e baixa adoção de telemedicina. As variáveis que mais influenciaram o modelo foram:
Estado (bene_geo_desc)
Faixa etária (bene_age_desc)
Nível urbano ou rural (bene_ruca_desc)
Isso indica que fatores sociais e geográficos afetam diretamente a probabilidade de uso da telemedicina.
9. CONCLUSÃO
Os resultados mostram que é possível prever a adoção de telemedicina com base em fatores regionais e demográficos. Portanto, o uso de técnicas de Machine Learning pode ajudar a identificar regiões vulneráveis e direcionar políticas públicas mais eficientes.
Como próximos passos, sugerem-se:
Testar outros modelos, como Regressão Logística e XGBoost
Aplicar validação cruzada
Adicionar dados socioeconômicos externos
Fazer análise temporal mais profunda
Este estudo demonstra que a telemedicina não depende apenas da tecnologia, mas também de fatores demográficos, geográficos e sociais. Assim, modelos como este podem ser utilizados para planejamento estratégico e tomada de decisão em saúde pública.
