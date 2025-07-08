

# **O Poder Discriminatório em Modelos de Risco de Crédito: Uma Análise Comparativa Exaustiva do Coeficiente de Gini e da Estatística de Kolmogorov-Smirnov (KS)**

## **Seção 1: Introdução à Avaliação de Modelos de Risco de Crédito**

### **A Importância da Discriminação de Modelos no Setor Financeiro**

No cerne da indústria de serviços financeiros, a concessão de crédito representa uma atividade fundamental, impulsionando o crescimento econômico e permitindo que indivíduos e empresas alcancem seus objetivos. No entanto, essa atividade é inerentemente arriscada. A capacidade de uma instituição financeira de prosperar depende diretamente de sua habilidade em tomar decisões de crédito lucrativas, o que exige uma avaliação precisa da credibilidade dos solicitantes.1 É nesse contexto que os modelos de  
*score* de crédito, ou *scorecards*, emergem não como exercícios acadêmicos, mas como ferramentas de gestão de risco indispensáveis.  
O objetivo primário de um modelo de *score* de crédito é quantificar a probabilidade de um determinado cliente incorrer em inadimplência (default) no futuro. Para ser eficaz, o modelo deve ser capaz de realizar uma tarefa fundamental: separar, com o máximo de precisão possível, os "bons" clientes (aqueles que cumprirão suas obrigações financeiras) dos "maus" clientes (aqueles que se tornarão inadimplentes).3 Essa capacidade de separação é tecnicamente conhecida como  
**poder discriminatório** do modelo.6 Métricas como o Coeficiente de Gini e a Estatística de Kolmogorov-Smirnov (KS) foram projetadas especificamente para medir essa qualidade essencial, servindo como os principais indicadores da eficácia de um  
*scorecard*.7 Um modelo com alto poder discriminatório permite que as instituições financeiras otimizem suas políticas de concessão de crédito, minimizando perdas com inadimplência e maximizando a aprovação de clientes rentáveis.

### **O Ecossistema de Métricas de Validação: Discriminação, Calibração e Estabilidade**

A validação de um modelo de risco de crédito é um processo multifacetado que vai além da simples medição do poder discriminatório. Embora a discriminação seja crucial, ela é apenas uma das três dimensões que devem ser rigorosamente avaliadas para garantir a robustez e a confiabilidade de um modelo. As outras duas são a calibração e a estabilidade.9

1. **Discriminação:** Como já mencionado, refere-se à capacidade do modelo de ordenar corretamente os clientes por nível de risco. Um modelo com boa discriminação atribuirá consistentemente *scores* mais baixos (maior risco) aos clientes que se tornarão inadimplentes e *scores* mais altos (menor risco) aos que pagarão em dia. O Gini e o KS são as principais métricas para essa dimensão.10  
2. **Calibração:** Refere-se à precisão das probabilidades de *default* (PD) previstas pelo modelo. Um modelo bem calibrado é aquele em que a PD prevista corresponde à taxa de *default* observada na realidade. Por exemplo, se um grupo de clientes recebe uma PD de 5%, espera-se que, de fato, 5% desse grupo se torne inadimplente. Um modelo pode ter excelente discriminação (ordenar o risco perfeitamente) mas péssima calibração (as probabilidades previstas estão sistematicamente erradas), o que o torna perigoso para aplicações como precificação baseada em risco ou cálculo de provisões para perdas.10  
3. **Estabilidade:** Refere-se à consistência do desempenho do modelo ao longo do tempo. Um modelo estável deve manter seu poder discriminatório e sua calibração à medida que novas populações são avaliadas e as condições econômicas mudam. Métricas como o Índice de Estabilidade da População (PSI) são usadas para monitorar essa dimensão.9

Compreender este ecossistema é vital. Gini e KS, embora poderosos, operam quase exclusivamente no domínio da discriminação. Confiar apenas neles para validar um modelo pode criar uma falsa sensação de segurança, ignorando riscos críticos relacionados à calibração e à estabilidade.

### **Posicionando Gini e KS como Pilares na Validação de Scorecards de Crédito**

Apesar da existência de um vasto arsenal de métricas estatísticas, o Coeficiente de Gini e a Estatística KS se consolidaram como os dois pilares para a avaliação do poder discriminatório em modelos de risco de crédito em todo o mundo.4 Sua popularidade é tão grande que são frequentemente utilizados em conjunto durante o desenvolvimento, a validação e o monitoramento contínuo de  
*scorecards*.7 O Gini é particularmente predominante na Europa, enquanto o KS goza de maior popularidade na América do Norte, mas ambos são universalmente reconhecidos pela indústria.14  
A notável resiliência dessas métricas, mesmo com o advento de algoritmos de *machine learning* muito mais complexos, não se deve a uma suposta perfeição estatística. Pelo contrário, como será explorado neste relatório, ambas possuem limitações significativas. Sua longevidade e domínio derivam, em grande parte, de sua **interpretabilidade** e de sua conexão direta com as decisões de negócio. Conceitos como "separação máxima" (KS) ou "medida de desigualdade na predição" (Gini) são muito mais tangíveis para gestores de risco e executivos do que a função de perda de uma rede neural ou a estrutura de um modelo de *gradient boosting*.15 Essa característica destaca uma tensão fundamental na ciência de dados moderna: o equilíbrio necessário entre a complexidade e o poder preditivo de um modelo e a necessidade de resultados que sejam explicáveis, comunicáveis e, acima de tudo, acionáveis para o negócio. Este relatório se propõe a dissecar essas duas métricas, fornecendo uma análise exaustiva de suas fundações, aplicações e nuances estratégicas.

## **Seção 2: A Estatística de Kolmogorov-Smirnov (KS) em Profundidade**

### **Fundamentos Estatísticos: O Teste de KS como uma Medida Não-Paramétrica de Comparação de Distribuições**

Na sua essência, a Estatística de Kolmogorov-Smirnov (KS) origina-se de um teste estatístico fundamental com o mesmo nome. O teste de Kolmogorov-Smirnov é um procedimento **não-paramétrico** projetado para determinar se duas amostras de dados independentes foram extraídas da mesma distribuição de probabilidade subjacente.18 O fato de ser não-paramétrico é uma de suas maiores forças, pois significa que o teste não faz quaisquer suposições sobre a forma da distribuição dos dados (por exemplo, normal, binomial ou outra). Isso o torna uma ferramenta universalmente aplicável a qualquer tipo de dados contínuos ou ordinais, independentemente de sua distribuição.18  
O núcleo do teste é a **estatística KS**, frequentemente denotada como D. Esta estatística é definida como a **diferença absoluta máxima** entre as funções de distribuição acumulada empíricas (eCDFs) das duas amostras, avaliada em todos os pontos de dados.18 Visualmente, se traçarmos os gráficos das duas eCDFs, a estatística KS corresponde à maior distância vertical entre as duas curvas em qualquer ponto do eixo horizontal.18 A fórmula matemática é expressa como:  
D=xsup​∣F1,n​(x)−F2,m​(x)∣  
Onde F1,n​(x) e F2,m​(x) são as funções de distribuição acumulada empíricas para a primeira e a segunda amostra, respectivamente, e supx​ é o supremo da diferença sobre todos os valores de x.  
É crucial distinguir entre o **teste KS de duas amostras** e o **teste KS de uma amostra**. O teste de uma amostra compara a eCDF de uma única amostra com uma distribuição teórica conhecida (por exemplo, para testar se os dados seguem uma distribuição normal). No contexto de risco de crédito, o interesse reside exclusivamente no **teste KS de duas amostras**, onde as duas amostras são as populações de clientes "bons" (adimplentes) e "maus" (inadimplentes).18 O objetivo é medir o quão bem o modelo de  
*score* consegue separar as distribuições de *scores* desses dois grupos.

### **Cálculo e Interpretação no Risco de Crédito**

A aplicação da estatística KS para avaliar um modelo de *score* de crédito segue uma metodologia bem definida e intuitiva, que transforma a teoria estatística em uma métrica de desempenho prática.

#### **Metodologia de Cálculo Passo a Passo**

O cálculo do KS para um modelo de classificação binária, como um *scorecard* de crédito, envolve os seguintes passos 3:

1. **Pontuação e Classificação da Amostra de Validação:** Primeiramente, todos os clientes em uma amostra de validação (dados que não foram usados para treinar o modelo) são pontuados pelo modelo. Cada cliente já possui um resultado de desempenho conhecido (histórico), sendo classificado como "bom" (adimplente) ou "mau" (inadimplente).  
2. **Ordenação por Risco:** A população total da amostra é ordenada com base no *score* ou na probabilidade de *default* (PD) atribuída pelo modelo. A ordenação é tipicamente feita do maior risco para o menor risco (ou seja, do menor *score* para o maior *score*, ou da maior PD para a menor PD).  
3. **Divisão em Decis e Cálculo das Distribuições Acumuladas:** A população ordenada é então dividida em 10 grupos de tamanho igual, conhecidos como decis.12 Para cada decil, calculam-se duas métricas cumulativas:  
   * **% Acumulada de Maus:** A porcentagem de todos os clientes "maus" da amostra que foram capturados até aquele decil.  
   * % Acumulada de Bons: A porcentagem de todos os clientes "bons" da amostra que foram capturados até aquele decil.  
     Por exemplo, no primeiro decil (os 10% de clientes com maior risco), calcula-se a proporção de "maus" e "bons" contidos nesse grupo. No segundo decil, calculam-se as proporções acumuladas dos primeiros 20% de clientes com maior risco, e assim por diante.3  
4. **Cálculo da Diferença e Identificação do KS:** Em cada decil, calcula-se a diferença absoluta entre a "% Acumulada de Maus" e a "% Acumulada de Bons". A **estatística KS é o maior valor encontrado entre essas diferenças** ao longo de todos os decis.3

#### **Visualização e Análise do Gráfico KS**

O gráfico KS é uma ferramenta visual extremamente poderosa e um padrão na indústria de crédito. Ele plota as duas curvas de distribuição acumulada no mesmo eixo: a "% Acumulada de Bons" e a "% Acumulada de Maus", em função dos decis de risco (ou da população acumulada).12

* **Eixo X:** Decis de risco (de 1 a 10\) ou percentil da população (de 0% a 100%), ordenados do maior para o menor risco.  
* **Eixo Y:** Percentual acumulado (de 0% a 100%).  
* **Curvas:** Uma curva para a distribuição acumulada de "maus" e outra para a de "bons".

Em um modelo com bom poder de separação, a curva de "maus" subirá muito mais rapidamente do que a curva de "bons". Isso ocorre porque os decis de maior risco (à esquerda do gráfico) devem conter uma alta concentração de clientes inadimplentes. A distância vertical entre as duas curvas em qualquer ponto do eixo X representa a capacidade de separação do modelo naquele ponto de corte. O valor do KS é a maior distância vertical entre as duas curvas.20 Em um modelo aleatório, as duas curvas se sobreporiam, resultando em um KS de 0, indicando nenhuma capacidade de separação.3

#### **Interpretação do Valor de KS e Benchmarks da Indústria**

A estatística KS varia de 0 a 1 (ou 0% a 100%). Um valor mais alto indica um melhor poder discriminatório do modelo.15

* **KS \= 0:** O modelo não tem capacidade de distinguir entre "bons" e "maus". É equivalente a uma seleção aleatória.  
* **KS \= 1 (ou 100%):** O modelo tem uma separação perfeita. Existe um ponto de corte que separa completamente todos os "bons" de todos os "maus".

Na prática, a indústria financeira adota benchmarks para interpretar o valor do KS, que podem variar ligeiramente entre instituições, mas geralmente seguem estas diretrizes 28:

* **KS \< 20%:** Poder discriminatório fraco. O modelo é geralmente considerado inaceitável.  
* **KS entre 20% e 40%:** Poder discriminatório moderado ou aceitável.  
* **KS entre 40% e 70%:** Bom poder discriminatório. Modelos nesta faixa são considerados fortes.  
* **KS \> 70%:** Poder discriminatório excelente. Valores muito altos podem, no entanto, ser um sinal de *overfitting* (superajuste) do modelo aos dados de treinamento e devem ser investigados com cautela.

Além do valor numérico, a localização do KS é crucial. Uma heurística importante na indústria é que o KS deve ocorrer nos primeiros decis (tipicamente, entre o 1º e o 3º decil).29 Isso garante que o modelo não está apenas separando as populações, mas que está fazendo isso de forma mais eficaz no segmento mais crítico: os clientes de maior risco. Um KS alto que ocorre no 7º decil, por exemplo, seria estatisticamente interessante, mas operacionalmente inútil para um credor que precisa identificar e rejeitar os piores candidatos. Esta regra de negócio sobrepõe-se à medida estatística para garantir sua relevância prática.

### **Vantagens e Limitações Estratégicas da Estatística KS**

Como qualquer métrica, o KS possui um conjunto de forças e fraquezas que determinam sua adequação para diferentes tarefas analíticas.

#### **Vantagens**

* **Intuitividade e Comunicação:** O conceito de "ponto de máxima separação" é extremamente intuitivo e fácil de comunicar a stakeholders não técnicos. A escala de 0 a 1 (ou 0 a 100%) também é mais direta para interpretação de negócios do que a escala de 0.5 a 1 da métrica AUC.16  
* **Identificação do Ponto de Corte Ótimo:** A principal utilidade do KS não é apenas medir a performance, mas também servir como uma ferramenta de decisão. O *score* ou decil onde o KS ocorre representa o ponto onde o modelo melhor distingue entre as duas populações. Isso o torna um candidato natural e empiricamente justificado para ser o ponto de corte (*cutoff*) inicial na política de aprovação/rejeição de crédito.33 Portanto, o KS atua como uma ponte crucial entre a validação estatística e a implementação operacional do modelo.  
* **Robustez:** Sendo uma métrica não-paramétrica baseada em ordenação, o KS é robusto a *outliers* e a transformações monotônicas do *score* (como aplicar logaritmos), desde que a ordem seja preservada.21 Além disso, estudos mostram que o KS é robusto ao desbalanceamento de classes, uma característica comum em dados de crédito, onde os inadimplentes são uma minoria.16

#### **Limitações**

* **Foco Local e Perda de Informação:** A maior fraqueza do KS é sua natureza "local". Ele se concentra exclusivamente no ponto de máxima diferença e ignora completamente o poder de separação do modelo em todas as outras faixas de *score*.25 Dois modelos com curvas de separação muito diferentes, um que separa bem apenas em um ponto e outro que separa razoavelmente bem em toda a distribuição, poderiam ter o mesmo valor de KS. Isso pode ser enganoso se o KS for usado como a única medida de comparação de modelos.  
* **Sensibilidade à Discretização (*Binning*):** O valor calculado do KS pode variar dependendo de como os dados são agrupados. Um cálculo com 10 decis pode produzir um resultado diferente de um com 20 decis ou de um cálculo sobre os dados contínuos. Essa falta de consistência pode levar a conclusões diferentes dependendo da metodologia de cálculo escolhida.12  
* **Insensibilidade à Calibração:** Assim como o Gini, o KS é uma medida de discriminação (ordenação) e é completamente insensível à calibração do modelo. Ele não avalia se as probabilidades de *default* previstas são precisas em termos absolutos, apenas se elas ordenam corretamente o risco.10

## **Seção 3: O Coeficiente de Gini Desmistificado**

### **Fundamentos e Origens: Da Curva de Lorenz na Economia à sua Aplicação em Modelagem**

O Coeficiente de Gini, embora seja um pilar na modelagem de risco de crédito, tem suas raízes em um campo diferente: a economia. Ele foi proposto pelo estatístico italiano Corrado Gini em 1912 como uma medida para quantificar a desigualdade de renda ou riqueza dentro de uma nação ou grupo social.36 Sua genialidade reside na sua capacidade de resumir uma distribuição complexa em um único número.  
A definição matemática do Gini é baseada na **Curva de Lorenz**. Para construir uma Curva de Lorenz no contexto econômico, a população é ordenada da mais pobre para a mais rica. O gráfico então plota a proporção acumulada da população no eixo X contra a proporção acumulada da renda total que essa população detém no eixo Y.36 Uma linha diagonal a 45 graus, conhecida como "linha de igualdade perfeita", representa um cenário onde, por exemplo, os 20% mais pobres da população detêm 20% da renda total. A Curva de Lorenz de uma população real sempre estará abaixo dessa linha. O Coeficiente de Gini é então definido como a razão da área entre a linha de igualdade perfeita e a Curva de Lorenz (Área A) sobre a área total sob a linha de igualdade perfeita (Área A \+ Área B). Matematicamente,  
G=A/(A+B). Como a área total do triângulo (A \+ B) é 0.5, a fórmula simplifica para G=A/0.5=2A.36  
A transição desse conceito para o risco de crédito é um exemplo brilhante de polinização cruzada conceitual. A ideia de "desigualdade de renda" foi engenhosamente adaptada para medir a "desigualdade na distribuição de risco" por um modelo. Em vez de população versus renda, o gráfico compara proporções de diferentes grupos de clientes.41 No contexto de crédito, a  
**Curva de Perfil de Acurácia Cumulativa (CAP)**, que é funcionalmente análoga à Curva de Lorenz, é utilizada. A curva CAP plota a porcentagem acumulada de todos os solicitantes (ordenados por risco, do maior para o menor) no eixo X, contra a porcentagem acumulada de clientes "maus" (inadimplentes) capturados no eixo Y.41 Um modelo perfeito concentraria todos os "maus" nos primeiros percentis da população de maior risco, criando uma curva que sobe verticalmente e depois se torna horizontal. O Gini, neste contexto, mede o quão perto o modelo está dessa concentração perfeita de risco.

### **A Relação Intrínseca com a Curva ROC e AUC**

Embora suas origens visuais estejam na Curva de Lorenz/CAP, a maneira mais comum e poderosa de entender e calcular o Gini no contexto de modelagem moderna é através de sua relação direta com a Curva Característica de Operação do Receptor (ROC) e a Área Sob a Curva (AUC).

#### **Construção da Curva ROC**

A curva ROC é uma ferramenta fundamental para avaliar classificadores binários. Ela é construída plotando-se a **Taxa de Verdadeiros Positivos (TPR)**, também conhecida como Sensibilidade, no eixo Y, contra a **Taxa de Falsos Positivos (FPR)**, ou (1 \- Especificidade), no eixo X, para cada limiar de classificação possível.15 No risco de crédito:

* **TPR (Sensibilidade):** % de clientes "maus" que são corretamente classificados como de alto risco.  
* **FPR:** % de clientes "bons" que são incorretamente classificados como de alto risco.

A curva traça o *trade-off* entre identificar corretamente os inadimplentes e classificar erroneamente os bons pagadores. Um modelo perfeito teria uma curva que passa pelo canto superior esquerdo (TPR=1, FPR=0), enquanto um modelo aleatório seguiria a diagonal (TPR=FPR).

#### **Derivação da Fórmula Gini \= 2 \* AUC \- 1**

A **Área Sob a Curva ROC (AUC)** é uma medida agregada do poder discriminatório do modelo, variando de 0.5 (aleatório) a 1.0 (perfeito).20 O Coeficiente de Gini usado na indústria de crédito é simplesmente uma transformação linear do AUC, dada pela fórmula universalmente aceita 1:  
Gini=2×AUC−1  
Essa fórmula realiza uma reescala, mapeando o intervalo do AUC de \[0.5,1.0\] para o intervalo mais intuitivo do Gini de \[0,1.0\]. A relação é tão fundamental que as duas métricas são funcionalmente equivalentes e medem a mesma propriedade subjacente do modelo: sua capacidade de ordenar o risco.17

#### **O Gini como Medida de Poder de Ordenação (C-statistic) e sua Relação com Somers' D**

A AUC possui uma interpretação probabilística clara: é a probabilidade de que um cliente "mau" selecionado aleatoriamente receba um *score* de maior risco (ou uma PD maior) do que um cliente "bom" selecionado aleatoriamente.42 Esta é precisamente a definição da  
**C-statistic** (Estatística de Concordância).  
Além disso, a terminologia em torno do Gini na indústria de crédito é notoriamente confusa. O termo "Gini" é frequentemente usado como sinônimo de **Somers' D**, uma medida de associação ordinal.6 Somers' D é calculado como a diferença entre o número de pares concordantes (onde o cliente "mau" tem um  
*score* de maior risco que o "bom") e o número de pares discordantes, dividida pelo número total de pares com *scores* diferentes.48 Esta medida é matematicamente equivalente ao Coeficiente de Gini derivado da curva CAP.41  
Essa ambiguidade terminológica entre Gini, Razão de Acurácia (AR), AUC e Somers' D não é apenas uma questão semântica; representa um risco operacional. Se diferentes equipes dentro de uma mesma instituição ou diferentes instituições usam a mesma palavra para se referir a cálculos ligeiramente diferentes (por exemplo, um "Gini Corrigido" que se ajusta à taxa de *default* base, como descrito em 50), isso pode levar a comparações de modelos falhas e decisões de negócio incorretas. A governança de modelos robusta, portanto, exige não apenas processos padronizados, mas também um léxico padronizado.

### **Cálculo e Interpretação no Risco de Crédito**

#### **Interpretação do Valor de Gini**

O Coeficiente de Gini varia de 0 a 1 (ou 0% a 100%).

* **Gini \= 0:** Indica um modelo sem poder discriminatório, não melhor que uma atribuição aleatória de *scores*.  
* **Gini \= 1:** Indica um modelo perfeito, que separa impecavelmente os clientes "bons" dos "maus".1

#### **Benchmarks da Indústria**

O valor de um Gini é altamente dependente do contexto do portfólio (tipo de produto, perfil de risco dos clientes, etc.). No entanto, existem benchmarks gerais para modelos de crédito ao consumidor que servem como referência 31:

* **Gini \< 0.4 (ou 40%):** Modelo com poder discriminatório de fraco a moderado.  
* **Gini entre 0.4 e 0.6 (40% \- 60%):** Modelo forte, geralmente considerado bom.  
* **Gini \> 0.6 (ou 60%):** Modelo excelente.

A Tabela 2 abaixo consolida benchmarks da indústria para diferentes produtos de crédito, fornecendo um contexto prático para a avaliação de modelos.

### **Tabela 2: Benchmarks de Performance por Produto de Crédito**

| Métrica | Produto de Crédito | Faixa Típica da Indústria | Considerado Excelente / Best-in-Class |
| :---- | :---- | :---- | :---- |
| **Gini** | Crédito ao Consumidor (Geral) | 0.60 \- 0.75 | \> 0.75 31 |
| **Gini** | Empréstimos Corporativos | 0.60 \- 0.70 | \> 0.68 51 |
| **KS** | Crédito ao Consumidor (Geral) | 40% \- 70% | \> 50% 29 |
| **KS** | Empréstimos Corporativos | 50% \- 60% | \> 55% 51 |

Esta tabela é de imenso valor prático. Um analista que calcula um Gini de 0.65 para um novo modelo de cartão de crédito precisa de um ponto de referência para saber se esse resultado é bom, medíocre ou excelente. Ao consolidar dados de várias fontes, esta tabela fornece esse contexto essencial, permitindo que os profissionais avaliem seus modelos não apenas em termos absolutos, mas também em relação aos padrões da indústria para produtos específicos. Isso transforma a avaliação de modelos de um exercício puramente interno para um de *benchmarking* competitivo.

### **Vantagens e Limitações Estratégicas do Coeficiente de Gini**

#### **Vantagens**

* **Medida Global e Agregada:** A principal força do Gini é que ele fornece um único número que resume o poder discriminatório de um modelo em *todos* os possíveis pontos de corte. Isso o torna a métrica ideal para comparar o desempenho geral de diferentes modelos, como em um teste *champion-challenger*.14  
* **Intuitividade da Escala:** A escala de 0 a 1 é fácil de entender e comunicar, representando o quão próximo um modelo está da perfeição e o quão distante está da aleatoriedade.17  
* **Robustez à Ordenação:** Sendo uma métrica baseada em ranking, é robusta a *outliers* e não depende dos valores absolutos dos *scores*, apenas de sua ordem.

#### **Limitações**

* **Insensibilidade à Calibração:** Esta é uma das desvantagens mais críticas. O Gini mede apenas a qualidade da ordenação. Um modelo pode ter um Gini muito alto, mas produzir probabilidades de *default* sistematicamente incorretas, tornando-o inadequado para aplicações que dependem da precisão da PD, como cálculo de provisões (ECL), precificação ou alocação de capital.43  
* **Métrica "Ruidosa" para Monitoramento:** O Gini pode ser uma métrica volátil ou "ruidosa" para monitoramento de desempenho ao longo do tempo. Uma queda no Gini não significa necessariamente que o modelo se deteriorou. Pode ser causada por fatores externos, como uma mudança na taxa de *default* da população geral (por exemplo, durante uma recessão), uma alteração no perfil dos novos solicitantes ou mesmo uma mudança na política de ponto de corte da própria instituição.54  
* **Pode Mascarar Problemas Locais:** Por ser uma medida global, um bom valor de Gini pode ocultar um desempenho fraco em faixas de *score* específicas e críticas. Por exemplo, um modelo pode ser excelente na separação de clientes de baixo e médio risco, mas fraco na identificação dos clientes de altíssimo risco. O bom desempenho nas faixas de menor risco pode inflar o Gini geral, mascarando uma falha perigosa na extremidade de maior risco do portfólio.14

## **Seção 4: Análise Comparativa Direta: Gini versus KS**

A escolha entre o Coeficiente de Gini e a Estatística KS não é uma questão de superioridade absoluta, mas de adequação ao propósito. As duas métricas, embora ambas meçam o poder discriminatório, fazem-no a partir de perspectivas fundamentalmente diferentes, o que as torna mais ou menos adequadas para diferentes tarefas analíticas e de negócio.

### **Perspectiva Global vs. Local: O Duelo entre a Performance Agregada e o Ponto Ótimo**

A distinção mais fundamental entre Gini e KS reside na sua abrangência:

* **Gini como Medida Global:** O Coeficiente de Gini é, por natureza, uma **medida global** do desempenho do modelo.14 Derivado da área sob toda a curva ROC (AUC), ele integra a capacidade de separação do modelo em todos os limiares de  
  *score* possíveis. O Gini responde à pergunta: "*No geral, quão bom é este modelo para separar bons e maus pagadores em toda a sua faixa de pontuação?*". Essa característica o torna a ferramenta ideal para comparar o poder de ordenação intrínseco de dois ou mais modelos diferentes, como em uma estrutura de teste *champion-challenger*.45  
* **KS como Medida Local:** Em contraste, a Estatística KS é uma **medida local**.14 Ela foca em um único ponto: o ponto de máxima separação entre as distribuições acumuladas de "bons" e "maus". A métrica ignora deliberadamente o desempenho de separação em qualquer outro ponto da distribuição de  
  *scores*.25 O KS responde a uma pergunta diferente e mais específica: "  
  *Em qual ponto de corte este modelo atinge sua melhor capacidade de separação, e qual é a magnitude dessa separação?*".

Essa dicotomia "global vs. local" é um reflexo de duas filosofias de negócio distintas. Um gestor de risco focado na qualidade holística do portfólio, em comparações de modelos para fins regulatórios ou na seleção do "melhor" algoritmo geral, encontrará mais valor no Gini. Por outro lado, um gestor de operações focado em definir a política de aprovação/rejeição mais eficiente para o dia a dia encontrará no KS uma ferramenta mais direta e acionável. A escolha da métrica, portanto, espelha a função e o objetivo do utilizador.

### **Sensibilidade, Robustez e Impacto da Calibração**

Ambas as métricas compartilham algumas características de robustez e uma fraqueza crítica:

* **Robustez a Desbalanceamento de Classes:** Tanto o Gini (via AUC) quanto o KS são reconhecidos por sua robustez em cenários com classes desbalanceadas, que são a norma em dados de risco de crédito.16 Isso representa uma vantagem significativa sobre métricas como a acurácia, que pode ser enganosamente alta quando a classe majoritária ("bons") domina a amostra.  
* **O Ponto Cego Compartilhado: Insensibilidade à Calibração:** A limitação mais crítica e compartilhada por ambas as métricas é sua total **insensibilidade à calibração**.11 Elas são puramente medidas de  
  **discriminação** (ordenação). Um modelo poderia prever que a PD de um cliente é 0.1% e a de outro é 0.2%, enquanto as PDs reais são 1% e 2%. O Gini e o KS seriam idênticos em ambos os cenários, pois a ordem de risco está correta. No entanto, o segundo cenário representa um risco dez vezes maior. Essa "cegueira" torna ambas as métricas, quando usadas isoladamente, inadequadas e perigosas para qualquer aplicação que dependa do valor absoluto da probabilidade, como cálculo de provisões, precificação ou alocação de capital. Isso implica que um framework de validação que se baseia apenas em Gini e KS é perigosamente incompleto. A verdadeira validação robusta não é uma escolha entre Gini e KS, mas sim a combinação de **(Gini ou KS) \+ Métricas de Calibração** (como o teste de Hosmer-Lemeshow ou gráficos de confiabilidade).  
* **Estabilidade e "Ruído":** O Gini é frequentemente citado como uma métrica "ruidosa" para o monitoramento de desempenho ao longo do tempo. Sua natureza global o torna sensível a mudanças na composição do portfólio ou na taxa de inadimplência geral da economia, o que pode causar flutuações no Gini que não refletem uma deterioração real do poder preditivo do modelo.54 O KS, sendo uma medida de ponto único, também pode ser volátil, mas sua interpretação está mais diretamente ligada a uma estratégia de corte específica.

### **Interpretabilidade e Comunicação para a Tomada de Decisão de Negócio**

A eficácia de uma métrica não reside apenas em sua robustez estatística, mas também em sua capacidade de ser compreendida e utilizada por tomadores de decisão.

* A escala de 0 a 1 do Gini é, sem dúvida, mais intuitiva do que a escala de 0.5 a 1 do AUC, da qual deriva.15  
* No entanto, o conceito subjacente ao KS — "o ponto de máxima separação entre clientes bons e maus" — é frequentemente muito mais tangível e fácil de explicar a uma audiência de negócios do que a definição abstrata do Gini como "duas vezes a área entre a Curva de Lorenz e a linha de igualdade".16  
* O gráfico KS, em si, é uma ferramenta de comunicação superior. Ele demonstra visualmente onde e como o modelo está funcionando, mostrando a divergência entre as curvas de "bons" e "maus" de uma forma que um único número de Gini não consegue capturar.25 Ele responde não apenas "quão bem" o modelo separa, mas também "  
  *onde*" ele o faz melhor.

A tabela a seguir sintetiza esta análise comparativa, servindo como um guia de referência rápida.

### **Tabela 1: Comparativo Resumido \- Gini vs. KS**

| Característica | Coeficiente de Gini | Estatística KS |
| :---- | :---- | :---- |
| **Tipo de Medida** | Global (resumo de toda a distribuição de scores) | Local (ponto único de máxima performance) |
| **Foco Principal** | Poder de ordenação geral do modelo | Ponto de máxima separação entre as populações |
| **Cálculo Base** | Área sob a curva ROC (AUC) | Diferença máxima entre as CDFs de "bons" e "maus" |
| **Gráfico Associado** | Curva de Lorenz / CAP / ROC | Gráfico KS (curvas de distribuição acumulada) |
| **Interpretação** | Mede a que distância o modelo está de uma classificação aleatória e de uma perfeita | Mede a maior "distância" que o modelo consegue criar entre "bons" e "maus" |
| **Ponto Forte Principal** | Excelente para comparar a performance geral de múltiplos modelos (champion-challenger) | Excelente para identificar um ponto de corte (cutoff) ótimo e de fácil comunicação |
| **Ponto Fraco Principal** | Pode mascarar problemas de performance em faixas de score específicas | Ignora a performance de separação em todas as outras faixas de score |
| **Uso Primário** | Seleção e comparação de modelos | Definição de políticas de aprovação/rejeição e otimização de cutoff |

## **Seção 5: Aplicações Práticas no Ciclo de Vida do Crédito**

A teoria por trás do Gini e do KS ganha vida quando aplicada às decisões e processos diários de uma instituição financeira. Desde a seleção de um novo modelo até o seu monitoramento contínuo, essas métricas desempenham papéis distintos e complementares.

### **Validação e Seleção de Modelos (Champion-Challenger)**

No processo de desenvolvimento ou atualização de modelos, é comum usar uma metodologia *champion-challenger*. O modelo atualmente em produção é o "campeão" (*champion*), e um ou mais modelos recém-desenvolvidos são os "desafiantes" (*challengers*). O objetivo é determinar se algum desafiante possui um desempenho superior que justifique a substituição do campeão.56  
Nesse cenário, o **Coeficiente de Gini é a métrica preferencial**.1 Como o Gini fornece uma medida única e global do poder discriminatório, ele permite uma comparação direta e equitativa da capacidade geral de ordenação de risco dos modelos.1 Um aumento estatisticamente significativo no Gini do desafiante em relação ao campeão, quando ambos são testados na mesma amostra de validação, é uma forte evidência para promover o desafiante.  
É de importância crítica que essa comparação seja feita na **mesma amostra de dados e no mesmo período de tempo**. Comparar o Gini de um modelo calculado sobre uma população de 2022 com o Gini de outro modelo calculado sobre uma população de 2024 é uma prática falha e enganosa, pois as diferenças podem ser devidas a mudanças na economia ou no perfil dos clientes, e não na qualidade intrínseca dos modelos.17

### **Definição de Pontos de Corte (Cutoff): Da Discriminação à Maximização do Lucro**

A definição do ponto de corte (*cutoff score*) — o limiar de pontuação que separa os clientes a serem aprovados dos que serão rejeitados — é talvez a decisão de negócio mais direta que um *scorecard* informa.37  
A **Estatística KS oferece um ponto de partida natural e estatisticamente sólido** para essa decisão. O *score* no qual o KS é maximizado representa o ponto de maior separação entre "bons" e "maus", tornando-o um candidato lógico para o *cutoff*.33  
No entanto, é um erro comum presumir que o *cutoff* estatisticamente ótimo é também o *cutoff* financeiramente ótimo. A decisão final de negócio deve incorporar a economia da concessão de crédito: o lucro esperado de um cliente adimplente e o prejuízo esperado de um cliente inadimplente.3 A verdadeira otimização do  
*cutoff* envolve a criação de análises de *trade-off* ou tabelas de lucratividade. Essas análises calculam o lucro marginal e total em diferentes faixas de *score* ou decis, considerando as receitas e os custos associados a cada decisão de aprovação/rejeição.34 O objetivo é encontrar o  
*cutoff* que maximiza o lucro total para o portfólio, um ponto que pode ou não coincidir com o *cutoff* do KS.61  
A seleção final de um *cutoff* representa a cristalização da apetite de risco de uma instituição em um único número. Um *cutoff* baixo (resultando em uma alta taxa de aprovação) reflete uma estratégia de crescimento agressiva, enquanto um *cutoff* alto (baixa taxa de aprovação) indica uma postura conservadora e avessa ao risco.59 A discussão sobre o  
*cutoff* é, portanto, uma reunião estratégica central, onde a modelagem estatística encontra a estratégia financeira.  
Metodologias mais avançadas, como o **Expected Maximum Profit (EMP)**, formalizam essa abordagem. O EMP integra explicitamente informações de custo e benefício na avaliação do modelo, fornecendo um *cutoff* que é, por definição, otimizado para o lucro, em vez de apenas para a separação estatística.63

### **Monitoramento Contínuo e Detecção de Deterioração do Modelo**

Os modelos de crédito não são estáticos; seu desempenho inevitavelmente se degrada ao longo do tempo devido a mudanças nas condições econômicas, no comportamento dos consumidores ou nas próprias ofertas de produtos da instituição.9 O monitoramento contínuo é essencial para garantir que o modelo permaneça relevante e preciso.  
Tanto o Gini quanto o KS são rastreados ao longo do tempo como indicadores-chave de desempenho (KPIs) para detectar essa degradação.18 Uma tendência de queda consistente em qualquer uma dessas métricas é um sinal de alerta que exige investigação.  
No entanto, uma queda no Gini ou no KS é apenas um **sintoma**, não um diagnóstico. Para entender a causa raiz, é crucial usar uma métrica complementar: o **Índice de Estabilidade da População (PSI)**.30 O PSI mede a mudança na distribuição de uma variável (como o  
*score* do modelo ou uma variável de entrada) entre dois períodos de tempo, tipicamente comparando a população atual com a população usada para desenvolver o modelo.65 A interpretação do PSI segue regras de ouro bem estabelecidas:

* **PSI \< 0.1:** Mudança insignificante; o modelo está estável.  
* **PSI entre 0.1 e 0.25:** Mudança moderada; requer investigação.  
* **PSI \> 0.25:** Mudança significativa; a população mudou tanto que o modelo pode não ser mais válido e pode precisar de recalibração ou reconstrução.30

A análise conjunta dessas métricas forma um poderoso framework de diagnóstico. Ao observar uma queda no Gini, o analista deve primeiro verificar o PSI.

* Se o **PSI está alto**, a causa provável da queda no Gini é uma **mudança na população** de entrada (deriva populacional). O perfil dos solicitantes mudou, e o modelo, treinado em uma população diferente, está lutando para performar.  
* Se o **PSI está baixo** (estável), a causa não é a população. O próximo passo é investigar se houve **mudanças na estratégia de negócio** (por exemplo, uma alteração no *cutoff* ou uma nova campanha de marketing).  
* Se tanto o PSI quanto a estratégia de negócio estão estáveis, então pode-se concluir com mais confiança que o problema reside no próprio modelo: suas relações preditivas intrínsecas se **deterioraram**.54

Este processo de investigação, que combina Gini/KS (desempenho), PSI (estabilidade da população) e contexto de negócio, forma um tripé diagnóstico essencial para a governança de modelos eficaz.

## **Seção 6: Contextos Avançados e Recomendações Estratégicas**

Para dominar verdadeiramente a aplicação do Gini e do KS, é necessário ir além de suas definições básicas e compreender como eles se comportam em contextos mais complexos e como interagem com outros conceitos fundamentais da gestão de risco. A escolha da métrica correta não é apenas uma decisão técnica, mas uma decisão estratégica que deve estar alinhada com os objetivos do negócio e a filosofia do modelo.

### **O Impacto da Filosofia do Modelo: Estabilidade de Métricas em Modelos PIT vs. TTC**

A modelagem de risco de crédito não é uma disciplina monolítica. Existem duas filosofias de design de modelo predominantes, cada uma com um propósito diferente: **Point-in-Time (PIT)** e **Through-the-Cycle (TTC)**.69 A compreensão dessa distinção é vital, pois ela dita como as métricas de desempenho, como Gini e KS, devem ser interpretadas.

* **Modelos Point-in-Time (PIT):** Estes modelos são projetados para serem altamente sensíveis ao ciclo econômico atual. Eles incorporam variáveis macroeconômicas (como PIB, taxa de desemprego) e suas estimativas de Probabilidade de *Default* (PD) flutuam com a saúde da economia.70 Durante uma recessão, as PDs previstas por um modelo PIT aumentarão para quase todos os clientes, refletindo o aumento do risco sistêmico. Consequentemente, o poder de separação do modelo (medido por Gini e KS) tende a  
  **diminuir** durante as recessões (quando até mesmo clientes "bons" enfrentam dificuldades, tornando a separação mais difícil) e a **aumentar** durante períodos de expansão econômica. A volatilidade do Gini/KS é, portanto, uma característica esperada e até desejável de um modelo PIT bem construído.69 A regulamentação contábil IFRS 9, por exemplo, exige o uso de PDs com filosofia PIT para o cálculo de provisões.70  
* **Modelos Through-the-Cycle (TTC):** Em contraste, os modelos TTC são projetados para serem **estáveis** ao longo do ciclo econômico. Eles visam estimar a PD média de um cliente ao longo de um ciclo econômico completo, ignorando as flutuações de curto prazo.70 O  
  *rating* de um cliente em um modelo TTC não deve mudar drasticamente apenas porque a economia entrou em recessão. Para um modelo TTC, a **estabilidade do Gini e do KS ao longo do tempo é um critério de qualidade fundamental**. Uma grande flutuação nessas métricas indicaria que o modelo está, na verdade, se comportando como um modelo PIT e falhando em seu propósito de fornecer uma visão de risco de longo prazo. Os modelos TTC são tradicionalmente usados para o cálculo de capital regulatório sob os acordos de Basileia.70

A implicação estratégica é profunda: a avaliação de uma métrica de desempenho não pode ser dissociada da filosofia de design do modelo. Criticar um modelo PIT por ter um Gini volátil é um erro de categoria, pois está se aplicando o critério de sucesso de um modelo TTC a um modelo PIT. A primeira pergunta na validação de um modelo deve ser: "Qual é o propósito e a filosofia deste modelo?". Apenas com essa resposta é possível avaliar corretamente suas métricas de desempenho.

### **Discriminação vs. Calibração: Uma Distinção Crucial para a Gestão de Risco**

Como introduzido anteriormente, a distinção entre discriminação e calibração é um dos conceitos mais importantes e frequentemente mal compreendidos na validação de modelos.

* **Discriminação (Poder de Ordenação):** É a capacidade do modelo de separar corretamente "bons" e "maus". É sobre a **ordem** dos *scores*. Gini e KS são medidas puras de discriminação.10  
* **Calibração (Precisão da Probabilidade):** É a concordância entre a PD prevista pelo modelo e a taxa de *default* observada na realidade. É sobre a **precisão do valor** da probabilidade.10

Um modelo pode ter excelente discriminação, mas péssima calibração, e vice-versa.11 Por exemplo, um modelo atribui PDs de 0.2% para o Grupo A e 0.4% para o Grupo B. Se as taxas de  
*default* reais observadas são 2% e 4%, respectivamente, o modelo tem **discriminação perfeita** (a ordem de risco está correta), mas **calibração terrível** (as previsões estão subestimadas por um fator de 10).  
Como Gini e KS são cegos à calibração 52, usá-los isoladamente para validar um modelo que será usado para fins de calibração é um erro grave. A calibração é absolutamente vital para funções de negócio que dependem do valor da PD, como:

* **Cálculo de Provisões para Perdas de Crédito (ECL):** Sob o IFRS 9, o cálculo do ECL (ECL=PD×LGD×EAD) depende diretamente do valor da PD. Um modelo mal calibrado levará a provisões incorretas.  
* **Precificação Baseada em Risco:** A definição de taxas de juros para diferentes clientes baseia-se na sua PD. Um modelo mal calibrado resultará em preços inadequados, ou cobrando muito de clientes de baixo risco, ou muito pouco de clientes de alto risco.  
* **Alocação de Capital Regulatório:** O cálculo do capital exigido sob a abordagem IRB de Basileia também é uma função da PD.

Essa separação funcional mapeia diretamente para diferentes áreas de uma instituição financeira. A equipe de **originação de crédito**, que toma decisões de aprovar/rejeitar, preocupa-se principalmente com a **discriminação** (Gini/KS) para garantir que estão ranqueando os clientes corretamente. A equipe de **finanças, contabilidade e gestão de capital**, que calcula provisões e capital, preocupa-se principalmente com a **calibração**. Um único modelo serve a múltiplos mestres com diferentes necessidades, tornando a validação holística (discriminação \+ calibração) não apenas uma boa prática, mas uma necessidade organizacional.

### **Recomendações Estratégicas: Um Framework para a Escolha da Métrica Adequada**

Com base na análise detalhada, é possível construir um framework prescritivo para orientar a escolha da métrica mais apropriada para cada tarefa específica no ciclo de vida do crédito. A Tabela 3 abaixo resume essas recomendações.

### **Tabela 3: Framework de Decisão: Quando Priorizar Gini vs. KS**

| Objetivo de Negócio / Tarefa Analítica | Métrica Primária Recomendada | Justificativa Estratégica |
| :---- | :---- | :---- |
| **Comparação Geral de Modelos (Champion-Challenger)** | **Gini** | Como métrica global, resume a performance em todos os pontos de corte, fornecendo a melhor base para uma comparação "maçãs com maçãs" do poder de ordenação geral. |
| **Otimização de Ponto de Corte (Cutoff)** | **KS** | Identifica diretamente o ponto de máxima separação estatística, fornecendo o ponto de partida mais relevante para a definição da política de aprovação/rejeição. |
| **Análise de Rentabilidade e Precificação** | **Nenhuma das duas (foco na Calibração)** | Gini e KS são insensíveis à calibração. Análises de lucro e precificação dependem da precisão das probabilidades de *default* (PDs), exigindo métricas de calibração como o teste de Hosmer-Lemeshow ou gráficos de confiabilidade. |
| **Comunicação para Stakeholders Não-Técnicos** | **Gráfico KS** | O conceito visual de "distância máxima" entre as curvas de bons e maus pagadores é mais intuitivo e impactante para uma audiência de negócios do que o conceito abstrato de Gini. |
| **Monitoramento de Estabilidade do Modelo** | **Painel com Gini, KS e PSI** | Gini oferece uma visão da saúde geral, KS pode indicar problemas em um ponto de corte específico, e PSI diagnostica se as mudanças são devidas a alterações na população, formando um sistema de diagnóstico completo. |

Este framework transforma a análise descritiva em um guia estratégico. Ele responde diretamente à pergunta "onde aplicar os dois, e justifique onde cada métrica é melhor", não com uma resposta única, mas com uma abordagem sofisticada que condiciona a escolha da métrica ao objetivo da tarefa. Isso eleva o relatório de um mero explicador para um guia prático, fornecendo valor imenso para qualquer profissional da área que precise tomar decisões baseadas nessas métricas.

## **Seção 7: Conclusão e Perspectivas Futuras**

### **Síntese das Diferenças, Aplicações e Superioridade Contextual de Gini e KS**

Este relatório realizou uma análise exaustiva do Coeficiente de Gini e da Estatística de Kolmogorov-Smirnov (KS), dois pilares na avaliação de modelos de risco de crédito. A principal conclusão não é que uma métrica seja inerentemente superior à outra, mas que elas são ferramentas distintas, projetadas para trabalhos diferentes, cada uma com um conjunto único de forças e fraquezas.

* O **Coeficiente de Gini** atua como um "termômetro" da saúde geral do modelo. Sendo uma medida global, ele resume o poder discriminatório em toda a distribuição de *scores*, tornando-o a ferramenta ideal para a **comparação de modelos** em um ambiente controlado.  
* A **Estatística KS**, por outro lado, funciona como um "bisturi" cirúrgico. Sendo uma medida local, ela identifica com precisão o ponto de máxima separação, tornando-a a ferramenta mais direta para a **definição de pontos de corte** e para a comunicação visual do poder do modelo.

A sua eficácia, portanto, é contextual. A superioridade de uma sobre a outra depende inteiramente da pergunta que o analista ou o gestor de risco está tentando responder. A validação robusta de modelos reconhece essa complementaridade, utilizando o Gini para seleção de modelos, o KS para implementação de políticas e ambos, em conjunto com o PSI, para um monitoramento contínuo e eficaz. Ambas as métricas, no entanto, compartilham uma limitação crítica: sua insensibilidade à calibração, o que exige que sejam sempre acompanhadas por testes específicos de precisão de probabilidade em qualquer framework de validação completo.

### **O Futuro da Avaliação de Modelos na Era do Machine Learning e de Dados Não Tradicionais**

O cenário de risco de crédito está evoluindo rapidamente, impulsionado por duas forças principais: o avanço de modelos de *Machine Learning* (ML) mais complexos (como *Gradient Boosting*, Redes Neurais) e a crescente utilização de **dados alternativos** para avaliação de crédito.1 Esses dados incluem informações não tradicionais, como histórico de pagamento de contas de serviços públicos e aluguel, dados de telecomunicações, comportamento em redes sociais e a pegada digital geral de um indivíduo.76  
Longe de tornar Gini e KS obsoletos, essa nova era paradoxalmente **aumenta sua importância**. Em um mundo dominado por modelos "caixa-preta" (*black box*), cuja lógica interna é muitas vezes inescrutável, a necessidade de métricas de desempenho que sejam robustas, bem compreendidas e, acima de tudo, **interpretáveis**, torna-se ainda mais crítica. Gini e KS servem como uma primeira linha de defesa compreensível e como uma ponte de comunicação essencial entre cientistas de dados, que constroem os modelos, e gestores de risco e reguladores, que precisam confiar neles.20  
No entanto, o futuro da validação de modelos está se expandindo para incluir uma terceira dimensão crítica, além da discriminação e da calibração: a **justiça (fairness)**. À medida que os modelos utilizam uma gama cada vez maior de dados pessoais, o risco de introduzir vieses discriminatórios contra grupos protegidos (com base em raça, gênero, idade, etc.) aumenta significativamente.80 Um modelo pode ter um Gini alto, ser bem calibrado, mas ser ilegalmente discriminatório, tornando-o não apenas antiético, mas também um passivo legal e de reputação para a instituição.82  
Portanto, a tríade de validação do futuro será **Discriminação (medida por Gini/KS) \+ Calibração \+ Justiça**. Métricas de *fairness*, como a Diferença de Paridade Estatística (SPD) e o Impacto Dispar (DI), estão se tornando componentes não negociáveis do processo de validação.80 Gini e KS continuarão a ser ferramentas essenciais para medir o poder preditivo, mas serão apenas uma parte de uma avaliação muito mais ampla e holística, garantindo que os modelos de crédito do futuro não sejam apenas precisos, mas também justos e responsáveis.

#### **Referências citadas**

1. Definition of Gini Coefficient​ for Lenders \- RiskSeal, acessado em julho 2, 2025, [https://riskseal.io/glossary/gini-coefficient](https://riskseal.io/glossary/gini-coefficient)  
2. Understanding Credit Scoring Models: Types and Examples \- HighRadius, acessado em julho 2, 2025, [https://www.highradius.com/resources/Blog/credit-scoring-models-types-and-examples/](https://www.highradius.com/resources/Blog/credit-scoring-models-types-and-examples/)  
3. Understand and Use a Business Credit Risk Score \- 5-minute FUNdamentals \- Experian, acessado em julho 2, 2025, [https://www.experian.com/blogs/business-information/2020/11/18/understand-and-use-a-business-credit-risk-score-5-minute-fundamentals/](https://www.experian.com/blogs/business-information/2020/11/18/understand-and-use-a-business-credit-risk-score-5-minute-fundamentals/)  
4. modelos de credit e behavior scoring: modelagem e principais indicadores de performance \- eaic@uem.br \- Universidade Estadual de Maringá, acessado em julho 2, 2025, [http://www.eaic.uem.br/eaic2019/anais/artigos/3851.pdf](http://www.eaic.uem.br/eaic2019/anais/artigos/3851.pdf)  
5. Predicting Credit Scores with Boosted Decision Trees \- MDPI, acessado em julho 2, 2025, [https://www.mdpi.com/2571-9394/4/4/50](https://www.mdpi.com/2571-9394/4/4/50)  
6. Gini, Cumulative Accuracy Profile, AUC \- ListenData, acessado em julho 2, 2025, [https://www.listendata.com/2019/09/gini-cumulative-accuracy-profile-auc.html](https://www.listendata.com/2019/09/gini-cumulative-accuracy-profile-auc.html)  
7. Credit Scoring Modeling \- Semantic Scholar, acessado em julho 2, 2025, [https://pdfs.semanticscholar.org/55a2/4bb9578b4fb2228df9cce63a308f8a57333a.pdf](https://pdfs.semanticscholar.org/55a2/4bb9578b4fb2228df9cce63a308f8a57333a.pdf)  
8. Gini & KS Statistics in Credit Scoring \- YouTube, acessado em julho 2, 2025, [https://www.youtube.com/watch?v=MiBUBVUC8kE](https://www.youtube.com/watch?v=MiBUBVUC8kE)  
9. Validate your scoring model with AI-powered credit insights. \- itscredit, acessado em julho 2, 2025, [https://www.itscredit.com/platform/ai-credit-scoring-and-decisions/credit-model-validation](https://www.itscredit.com/platform/ai-credit-scoring-and-decisions/credit-model-validation)  
10. Credit Risk Model Validation. Discriminatory Test, Calibration Test… | by Venkatsai, acessado em julho 2, 2025, [https://venkatsaib.medium.com/credit-risk-model-validation-e5bd7db326a1](https://venkatsaib.medium.com/credit-risk-model-validation-e5bd7db326a1)  
11. Discrimination vs Calibration \- Machine Learning Models \- Data ..., acessado em julho 2, 2025, [https://datascience.stackexchange.com/questions/69622/discrimination-vs-calibration-machine-learning-models](https://datascience.stackexchange.com/questions/69622/discrimination-vs-calibration-machine-learning-models)  
12. SAS : Calculating KS Statistics \- ListenData, acessado em julho 2, 2025, [https://www.listendata.com/2016/01/sas-calculating-ks-test.html](https://www.listendata.com/2016/01/sas-calculating-ks-test.html)  
13. Credit Scoring Modeling \- CORE, acessado em julho 2, 2025, [https://core.ac.uk/download/pdf/32452521.pdf](https://core.ac.uk/download/pdf/32452521.pdf)  
14. How to Measure the Quality of Credit Scoring Models\* \- Czech Journal of Economics and Finance, acessado em julho 2, 2025, [https://journal.fsv.cuni.cz/storage/1228\_rezac.pdf](https://journal.fsv.cuni.cz/storage/1228_rezac.pdf)  
15. ROC Curve, Gini index, and KS statistic | by Fabiana Tortorelli \- Medium, acessado em julho 2, 2025, [https://medium.com/@fabitortorelli/roc-curve-gini-index-and-ks-statistic-6ba1e986742b](https://medium.com/@fabitortorelli/roc-curve-gini-index-and-ks-statistic-6ba1e986742b)  
16. Evaluating classification models with Kolmogorov-Smirnov (KS) test \- Towards Data Science, acessado em julho 2, 2025, [https://towardsdatascience.com/evaluating-classification-models-with-kolmogorov-smirnov-ks-test-e211025f5573/](https://towardsdatascience.com/evaluating-classification-models-with-kolmogorov-smirnov-ks-test-e211025f5573/)  
17. Blog | On the use (and misuse) of Gini Coefficients in Credit Scoring ..., acessado em julho 2, 2025, [https://lenddoefl.com/news/2018/6/26/blog-on-the-use-and-misuse-of-gini-coefficients-in-credit-scoring-comparing-ginis](https://lenddoefl.com/news/2018/6/26/blog-on-the-use-and-misuse-of-gini-coefficients-in-credit-scoring-comparing-ginis)  
18. Kolmogorov Smirnov Test for AI: When and Where To Use It \- Arize AI, acessado em julho 2, 2025, [https://arize.com/blog-course/kolmogorov-smirnov-test/](https://arize.com/blog-course/kolmogorov-smirnov-test/)  
19. Kolmogorov–Smirnov test \- Wikipedia, acessado em julho 2, 2025, [https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov\_test](https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov_test)  
20. ML Model Performance Evaluation: Gini Index, ROC-AUC, Kolmogorov – Smirnov Score, acessado em julho 2, 2025, [https://ginimachine.com/academia-post/ml-model-performance-evaluation/](https://ginimachine.com/academia-post/ml-model-performance-evaluation/)  
21. Interpreting results: Kolmogorov-Smirnov test \- GraphPad Prism 10 Statistics Guide, acessado em julho 2, 2025, [https://www.graphpad.com/guides/prism/latest/statistics/interpreting\_results\_kolmogorov-smirnov\_test.htm](https://www.graphpad.com/guides/prism/latest/statistics/interpreting_results_kolmogorov-smirnov_test.htm)  
22. Kolmogorov-Smirnov Charts Simplified \- Number Analytics, acessado em julho 2, 2025, [https://www.numberanalytics.com/blog/kolmogorov-smirnov-charts-simplified](https://www.numberanalytics.com/blog/kolmogorov-smirnov-charts-simplified)  
23. Evaluating Classifiers: Kolmogorov-Smirnov Chart (K-S Chart) \- YouTube, acessado em julho 2, 2025, [https://www.youtube.com/watch?v=hNs9o5qiY8U](https://www.youtube.com/watch?v=hNs9o5qiY8U)  
24. KS Score for Model Evaluation | Medium, acessado em julho 2, 2025, [https://medium.com/@kstarun/k-s-score-for-model-evaluation-5339f0a5c705](https://medium.com/@kstarun/k-s-score-for-model-evaluation-5339f0a5c705)  
25. Métricas de Avaliação de Modelos de Classificação Binária | by Jéssica Ramos \- Medium, acessado em julho 2, 2025, [https://medium.com/gsgcommunity/m%C3%A9tricas-de-avalia%C3%A7%C3%A3o-de-modelos-de-classifica%C3%A7%C3%A3o-bin%C3%A1ria-5c9b0ce786fa](https://medium.com/gsgcommunity/m%C3%A9tricas-de-avalia%C3%A7%C3%A3o-de-modelos-de-classifica%C3%A7%C3%A3o-bin%C3%A1ria-5c9b0ce786fa)  
26. Validating Credit Scoring Models: A Comparison of Alternative Methods \- Lending Science, acessado em julho 2, 2025, [https://lendingsciencedm.com/wp-content/uploads/2023/03/5-Validating-Credit-Scoring-Models.pdf](https://lendingsciencedm.com/wp-content/uploads/2023/03/5-Validating-Credit-Scoring-Models.pdf)  
27. Model Evaluation Metrics in Machine Learning \- DataSource.ai, acessado em julho 2, 2025, [https://www.datasource.ai/en/data-science-articles/model-evaluation-metrics-in-machine-learning](https://www.datasource.ai/en/data-science-articles/model-evaluation-metrics-in-machine-learning)  
28. Kolmogorov-Smirnov (KS). é uma métrica de perfomance em modelos… | by Gustavo Candido | Data Hackers | Medium, acessado em julho 2, 2025, [https://medium.com/data-hackers/kolmogorov-smirnov-fb90394ca122](https://medium.com/data-hackers/kolmogorov-smirnov-fb90394ca122)  
29. Model Validation Techniques \- ListenData, acessado em julho 2, 2025, [https://www.listendata.com/2015/01/model-validation-in-logistic-regression.html](https://www.listendata.com/2015/01/model-validation-in-logistic-regression.html)  
30. How to evaluate and monitor performance of AI models for Financial Risk Management— a practical guide | by Indraneel Dutta Baruah | ANOLYTICS | Medium, acessado em julho 2, 2025, [https://medium.com/anolytics/how-to-evaluate-and-monitor-performance-of-ai-models-for-financial-risk-management-a-practical-b600d50140cb](https://medium.com/anolytics/how-to-evaluate-and-monitor-performance-of-ai-models-for-financial-risk-management-a-practical-b600d50140cb)  
31. 10 Statistical Insights on Credit Scoring for Banking & Finance \- Number Analytics, acessado em julho 2, 2025, [https://www.numberanalytics.com/blog/10-statistical-insights-credit-scoring-banking-finance](https://www.numberanalytics.com/blog/10-statistical-insights-credit-scoring-banking-finance)  
32. Evaluating classification models with Kolmogorov-Smirnov (KS) test ..., acessado em julho 2, 2025, [https://towardsdatascience.com/evaluating-classification-models-with-kolmogorov-smirnov-ks-test-e211025f5573](https://towardsdatascience.com/evaluating-classification-models-with-kolmogorov-smirnov-ks-test-e211025f5573)  
33. Kolmogorov-Smirnov Graph based Cut-Off Determination Illustrated ..., acessado em julho 2, 2025, [https://www.researchgate.net/figure/Kolmogorov-Smirnov-Graph-based-Cut-Off-Determination-Illustrated-for-Model-1\_fig3\_255560672](https://www.researchgate.net/figure/Kolmogorov-Smirnov-Graph-based-Cut-Off-Determination-Illustrated-for-Model-1_fig3_255560672)  
34. Choosing a proper cut-off for scorecards \- SAS Support Communities, acessado em julho 2, 2025, [https://communities.sas.com/t5/Statistical-Procedures/Choosing-a-proper-cut-off-for-scorecards/td-p/248633](https://communities.sas.com/t5/Statistical-Procedures/Choosing-a-proper-cut-off-for-scorecards/td-p/248633)  
35. Credit Score: Kolmogorov-Smirnov (Python-optbinning) : r/datascience \- Reddit, acessado em julho 2, 2025, [https://www.reddit.com/r/datascience/comments/v467lf/credit\_score\_kolmogorovsmirnov\_pythonoptbinning/](https://www.reddit.com/r/datascience/comments/v467lf/credit_score_kolmogorovsmirnov_pythonoptbinning/)  
36. Gini coefficient \- Wikipedia, acessado em julho 2, 2025, [https://en.wikipedia.org/wiki/Gini\_coefficient](https://en.wikipedia.org/wiki/Gini_coefficient)  
37. Credit Scoring Systems: A Critical Analysis \- Columbia Business School, acessado em julho 2, 2025, [https://business.columbia.edu/sites/default/files-efs/pubfiles/690/24.pdf](https://business.columbia.edu/sites/default/files-efs/pubfiles/690/24.pdf)  
38. Measuring Statistical Dispersion with the Gini Coefficient \- Kimberly Fessel's Blog, acessado em julho 2, 2025, [http://kimberlyfessel.com/mathematics/applications/gini-use-cases/](http://kimberlyfessel.com/mathematics/applications/gini-use-cases/)  
39. Understanding the Gini Coefficient: A Measure of Inequality ..., acessado em julho 2, 2025, [https://www.datacamp.com/blog/gini-coefficient](https://www.datacamp.com/blog/gini-coefficient)  
40. Gould Data Knowledge Base: Gini Index \- Carleton Research Guides, acessado em julho 2, 2025, [https://gouldguides.carleton.edu/c.php?g=146949\&p=965703](https://gouldguides.carleton.edu/c.php?g=146949&p=965703)  
41. Using the Gini coefficient to evaluate the performance of credit score models \- Medium, acessado em julho 2, 2025, [https://medium.com/data-science/using-the-gini-coefficient-to-evaluate-the-performance-of-credit-score-models-59fe13ef420](https://medium.com/data-science/using-the-gini-coefficient-to-evaluate-the-performance-of-credit-score-models-59fe13ef420)  
42. Understanding Gini Coefficient, AUC, and CAP \- SolutionShala, acessado em julho 2, 2025, [https://solutionshala.com/uncategorized/1694/](https://solutionshala.com/uncategorized/1694/)  
43. Model Evaluation Metrics — Gini Coefficient | by Tarun\_KS | Jun, 2023 | Medium, acessado em julho 2, 2025, [https://medium.com/@kstarun/model-evaluation-metrics-gini-coefficient-db919ed09306](https://medium.com/@kstarun/model-evaluation-metrics-gini-coefficient-db919ed09306)  
44. The relationship between Gini terminology and the ROC curve \- Weizmann Institute, acessado em julho 2, 2025, [https://www.weizmann.ac.il/math/gideon/sites/math.gideon/files/uploads/AUC\_Metron%20May%202019%20v4.pdf](https://www.weizmann.ac.il/math/gideon/sites/math.gideon/files/uploads/AUC_Metron%20May%202019%20v4.pdf)  
45. Which one is better to evaluate a logistic regression: Gini, KS or ROC? \- Quora, acessado em julho 2, 2025, [https://www.quora.com/Which-one-is-better-to-evaluate-a-logistic-regression-Gini-KS-or-ROC](https://www.quora.com/Which-one-is-better-to-evaluate-a-logistic-regression-Gini-KS-or-ROC)  
46. Stop Misusing ROC Curve and GINI: Navigate Imbalanced Datasets with Confidence \- Klarna Engineering, acessado em julho 2, 2025, [https://engineering.klarna.com/stop-misusing-roc-curve-and-gini-navigate-imbalanced-datasets-with-confidence-5edec4c187d7](https://engineering.klarna.com/stop-misusing-roc-curve-and-gini-navigate-imbalanced-datasets-with-confidence-5edec4c187d7)  
47. Measuring the Quality of Credit Scoring Models, acessado em julho 2, 2025, [https://crc.business-school.ed.ac.uk/sites/crc/files/2023-10/Measuring-the-quality-of-credit-scoring-models-Presentation.pdf](https://crc.business-school.ed.ac.uk/sites/crc/files/2023-10/Measuring-the-quality-of-credit-scoring-models-Presentation.pdf)  
48. Somers' D \- Wikipedia, acessado em julho 2, 2025, [https://en.wikipedia.org/wiki/Somers%27\_D](https://en.wikipedia.org/wiki/Somers%27_D)  
49. Somer's D Calculation (R and Python code) | Big Data Knowledge Sharing, acessado em julho 2, 2025, [https://qizeresearch.wordpress.com/2013/11/24/somers-d-calculation-r-and-python-code/](https://qizeresearch.wordpress.com/2013/11/24/somers-d-calculation-r-and-python-code/)  
50. Credit Risk Metrics: Misconception with Gini Definitions | by Hugo Lopes \- Medium, acessado em julho 2, 2025, [https://medium.com/@hjdlopes/credit-risk-metrics-misconception-with-gini-definitions-2b6aedd3db4d](https://medium.com/@hjdlopes/credit-risk-metrics-misconception-with-gini-definitions-2b6aedd3db4d)  
51. Approach to the assessment of credit risk for non-financial corporations. Poland Evidence, acessado em julho 2, 2025, [https://www.bis.org/ifc/events/ws\_micro\_macro/nehrebecka\_paper.pdf](https://www.bis.org/ifc/events/ws_micro_macro/nehrebecka_paper.pdf)  
52. Model selection with Gini indices under auto-calibration \- ResearchGate, acessado em julho 2, 2025, [https://www.researchgate.net/publication/367058766\_Model\_selection\_with\_Gini\_indices\_under\_auto-calibration](https://www.researchgate.net/publication/367058766_Model_selection_with_Gini_indices_under_auto-calibration)  
53. The impact of deterioration in rating-model discriminatory power on expected losses, acessado em julho 2, 2025, [https://www.risk.net/journal-of-risk-model-validation/7959891/the-impact-of-deterioration-in-rating-model-discriminatory-power-on-expected-losses](https://www.risk.net/journal-of-risk-model-validation/7959891/the-impact-of-deterioration-in-rating-model-discriminatory-power-on-expected-losses)  
54. (PDF) On factors affecting the change in the Gini coefficient of the ..., acessado em julho 2, 2025, [https://www.researchgate.net/publication/374168999\_On\_factors\_affecting\_the\_change\_in\_the\_Gini\_coefficient\_of\_the\_credit\_scoring\_model](https://www.researchgate.net/publication/374168999_On_factors_affecting_the_change_in_the_Gini_coefficient_of_the_credit_scoring_model)  
55. Measuring the Quality of Credit Scoring Models, acessado em julho 2, 2025, [https://crc.business-school.ed.ac.uk/sites/crc/files/2023-10/Measuring-the-quality-of-credit-scoring-models.pdf](https://crc.business-school.ed.ac.uk/sites/crc/files/2023-10/Measuring-the-quality-of-credit-scoring-models.pdf)  
56. Gini Coefficient — LenddoEFL, acessado em julho 2, 2025, [https://lenddoefl.com/gini-coefficient](https://lenddoefl.com/gini-coefficient)  
57. Credit Scoring Series Part Five: Credit Scorecard Development \- Altair, acessado em julho 2, 2025, [https://altair.com/blog/articles/credit-scoring-series-part-five-credit-scorecard-development](https://altair.com/blog/articles/credit-scoring-series-part-five-credit-scorecard-development)  
58. Cut-Off Score: What It Is, How It Works, Significance \- Investopedia, acessado em julho 2, 2025, [https://www.investopedia.com/terms/c/cut-off-score.asp](https://www.investopedia.com/terms/c/cut-off-score.asp)  
59. VIII. SCORING AND MODELING \- FDIC, acessado em julho 2, 2025, [https://www.fdic.gov/regulations/examinations/credit\_card/pdf\_version/ch8.pdf](https://www.fdic.gov/regulations/examinations/credit_card/pdf_version/ch8.pdf)  
60. Credit Scoring Project — using Logistic Regression | by Skillcate AI | Medium, acessado em julho 2, 2025, [https://medium.com/@skillcate/credit-scoring-project-using-logistic-regression-c1e88bd7cf25](https://medium.com/@skillcate/credit-scoring-project-using-logistic-regression-c1e88bd7cf25)  
61. Credit Scoring, Scorecard, Risk Management \- Spotfire Community, acessado em julho 2, 2025, [https://community.spotfire.com/articles/spotfire-statistica/credit-scoring-scorecard-risk-management/](https://community.spotfire.com/articles/spotfire-statistica/credit-scoring-scorecard-risk-management/)  
62. Credit Risk Scorecards, acessado em julho 2, 2025, [https://students.aiu.edu/submissions/profiles/resources/onlineBook/b9m4e7\_Credit\_Risk%20Scorecards%20Developing%20finance.pdf](https://students.aiu.edu/submissions/profiles/resources/onlineBook/b9m4e7_Credit_Risk%20Scorecards%20Developing%20finance.pdf)  
63. EMP: Expected Maximum Profit Classification Performance Measure, acessado em julho 2, 2025, [https://cran.r-project.org/web/packages/EMP/EMP.pdf](https://cran.r-project.org/web/packages/EMP/EMP.pdf)  
64. Development and application of consumer credit scoring ... \- Lirias, acessado em julho 2, 2025, [https://lirias.kuleuven.be/retrieve/298752](https://lirias.kuleuven.be/retrieve/298752)  
65. Population Stability Index and Characteristic Analysis \- ListenData, acessado em julho 2, 2025, [https://www.listendata.com/2015/05/population-stability-index.html](https://www.listendata.com/2015/05/population-stability-index.html)  
66. Concepts: Performance Monitoring \- SAS Help Center, acessado em julho 2, 2025, [https://documentation.sas.com/doc/da/mdlmgrcdc/v\_051/mdlmgrug/p1c6xm7tthdajkn1t6esm4n3kwnq.htm](https://documentation.sas.com/doc/da/mdlmgrcdc/v_051/mdlmgrug/p1c6xm7tthdajkn1t6esm4n3kwnq.htm)  
67. Population Stability Index (PSI): What You Need To Know \- Arize AI, acessado em julho 2, 2025, [https://arize.com/blog-course/population-stability-index-psi/](https://arize.com/blog-course/population-stability-index-psi/)  
68. A Practical Introduction to Population Stability Index (PSI) \- Coralogix, acessado em julho 2, 2025, [https://coralogix.com/ai-blog/a-practical-introduction-to-population-stability-index-psi/](https://coralogix.com/ai-blog/a-practical-introduction-to-population-stability-index-psi/)  
69. Diff. between PIT and TTC credit scoring models \- Kaggle, acessado em julho 2, 2025, [https://www.kaggle.com/code/uzdavinys/diff-between-pit-and-ttc-credit-scoring-models](https://www.kaggle.com/code/uzdavinys/diff-between-pit-and-ttc-credit-scoring-models)  
70. A Complete Guide to Credit Risk Modelling \- ListenData, acessado em julho 2, 2025, [https://www.listendata.com/2019/08/credit-risk-modelling.html](https://www.listendata.com/2019/08/credit-risk-modelling.html)  
71. Point-in-Time versus Through-the-Cycle Ratings \- Z-Risk Engine, acessado em julho 2, 2025, [https://www.z-riskengine.com/media/ylrpyd2z/point-in-time-versus-through-the-cycle-ratings.pdf](https://www.z-riskengine.com/media/ylrpyd2z/point-in-time-versus-through-the-cycle-ratings.pdf)  
72. Compare Probability of Default Using Through-the-Cycle and Point-in-Time Models, acessado em julho 2, 2025, [https://www.mathworks.com/help/risk/compare-pd-using-ttc-and-pit-models.html](https://www.mathworks.com/help/risk/compare-pd-using-ttc-and-pit-models.html)  
73. Assessing the discriminatory power of loss given default models \- PMC \- PubMed Central, acessado em julho 2, 2025, [https://pmc.ncbi.nlm.nih.gov/articles/PMC9225220/](https://pmc.ncbi.nlm.nih.gov/articles/PMC9225220/)  
74. Compare Model Discrimination and Model Calibration to Validate of Probability of Default, acessado em julho 2, 2025, [https://www.mathworks.com/help/risk/compare-model-discrimination-and-model-calibration-for-validation-pd.html](https://www.mathworks.com/help/risk/compare-model-discrimination-and-model-calibration-for-validation-pd.html)  
75. Traditional Vs. Alternative Credit Scoring Methods \- RiskSeal, acessado em julho 2, 2025, [https://riskseal.io/blog/what-is-alternative-credit-scoring-and-how-does-it-differ-from-the-traditional](https://riskseal.io/blog/what-is-alternative-credit-scoring-and-how-does-it-differ-from-the-traditional)  
76. Alternative Credit Scoring Fintech & Alternative Credit Data \- Django Stars, acessado em julho 2, 2025, [https://djangostars.com/blog/alternative-credit-scoring/](https://djangostars.com/blog/alternative-credit-scoring/)  
77. Types of Alternative Data for Credit Scoring | Brankas, acessado em julho 2, 2025, [https://www.brankas.com/types-of-alternative-data-for-credit-scoring](https://www.brankas.com/types-of-alternative-data-for-credit-scoring)  
78. Enhancing Scorecards With Alternative Data: A Complete Guide \- RiskSeal, acessado em julho 2, 2025, [https://riskseal.io/blog/enhancing-scorecards-with-alternative-data-a-step-by-step-guide](https://riskseal.io/blog/enhancing-scorecards-with-alternative-data-a-step-by-step-guide)  
79. Understanding Alternative Credit Scoring \- Dataforest, acessado em julho 2, 2025, [https://dataforest.ai/blog/understanding-alternative-credit-scoring](https://dataforest.ai/blog/understanding-alternative-credit-scoring)  
80. Explore Fairness Metrics for Credit Scoring Model \- MATLAB & Simulink \- MathWorks, acessado em julho 2, 2025, [https://www.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html](https://www.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html)  
81. (PDF) Application of Decision Tree Model in Personal Credit Scoring and Its Fairness Optimization \- ResearchGate, acessado em julho 2, 2025, [https://www.researchgate.net/publication/390979182\_Application\_of\_Decision\_Tree\_Model\_in\_Personal\_Credit\_Scoring\_and\_Its\_Fairness\_Optimization](https://www.researchgate.net/publication/390979182_Application_of_Decision_Tree_Model_in_Personal_Credit_Scoring_and_Its_Fairness_Optimization)  
82. Alternative credit data 101: What it is and what it's used for \- Stripe, acessado em julho 2, 2025, [https://stripe.com/en-jp/resources/more/alternative-credit-data-101-what-it-is-and-what-its-used-for](https://stripe.com/en-jp/resources/more/alternative-credit-data-101-what-it-is-and-what-its-used-for)  
83. kr.mathworks.com, acessado em julho 2, 2025, [https://kr.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html\#:\~:text=%2C'Defaults'%7D)-,Calculate%20and%20Visualize%20Fairness%20Metrics%20for%20Credit%20Scorecard%20Model,indicates%20the%20presence%20of%20bias.](https://kr.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html#:~:text=%2C'Defaults'%7D\)-,Calculate%20and%20Visualize%20Fairness%20Metrics%20for%20Credit%20Scorecard%20Model,indicates%20the%20presence%20of%20bias.)  
84. Explore Fairness Metrics for Credit Scoring Model \- MathWorks, acessado em julho 2, 2025, [https://kr.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html\#:\~:text=%2C%27Defaults%27%7D)-,Calculate%20and%20Visualize%20Fairness%20Metrics%20for%20Credit%20Scorecard%20Model,indicates%20the%20presence%20of%20bias.](https://kr.mathworks.com/help/risk/explore-fairness-metrics-for-credit-scoring-model.html#:~:text=%2C%27Defaults%27%7D\)-,Calculate%20and%20Visualize%20Fairness%20Metrics%20for%20Credit%20Scorecard%20Model,indicates%20the%20presence%20of%20bias.)