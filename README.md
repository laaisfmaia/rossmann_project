# Previsão de vendas de um conjunto de lojas farmacêuticas 

<div align="center">
 <img height="300em" src="https://github.com/laaisfmaia/rossmann_project/blob/main/foto_capa.png">
</div>

## 1. Problema de negócio

A Rossmann é uma rede farmacêutica que opera mais de 3.000 drogarias em 7 países europeus. Atualmente, os gerentes de loja da Rossmann têm a tarefa de prever suas vendas diárias com até seis semanas de antecedência, a fim de entender quanto pode ser investido em cada loja para reforma da mesma. 

As vendas da loja são influenciadas por muitos fatores, incluindo promoções, competição, feriados escolares e estaduais, sazonalidade e localidade. Com milhares de gerentes individuais prevendo vendas com base em suas circunstâncias únicas, a precisão dos resultados pode ser bastante variada.


## 2. Objetivo do Projeto

Esse projeto tem como objetivo principal prever o faturamento das próximas 6 semanas de algumas lojas para que o CFO consiga usar parte desse faturamento para a reforma dessas lojas. 

A motivação é a dificuldade em determinar o valor que pode ser investido para a reforma de cada loja. 


## 3. Estratégia da solução

No projetado foi usado o método CRISP de desenvolvimento, que é um método cíclico em que se passa várias vezes pela mesma etapa do projeto, sendo que a cada etapa é melhorado alguns aspectos para uma solução mais eficaz. Esse tipo de método permite que o projeto gere valor desde o primeiro ciclo e facilita o mapeamento dos possíveis problemas de cada etapa. 

<div align="center">
 <img height="300em" src="https://github.com/laaisfmaia/rossmann_project/blob/main/crisp.png">
</div>

As etapas do projeto constituem em: 
1. Entender as questões de negócio, o contexto do problema, as principais dores, quem é o mais interessado no problema e qual o formato da solução;
2. Coletar os dados, que foram disponibilizados pelo kaggle; 
3. Entender a quantidade de dados, o tipo de variáveis, a quantidade de dados faltantes e fazer um resumo geral dos dados usando estatística descritiva;
4. Fazer um mapa mental de hipóteses para derivar uma lista de hipóteses que serão validadas com os dados;
5. Fazer a feature engineering;
6. Fazer a análise exploratória de dados para medir o impacto das variáveis em relação a variável resposta;
7. Fazer a preparação dos dados, como a rescaling e a transformação dos dados;
8. Fazer a seleção das variáveis mais importantes para o modelo;
9. Treinar o algoritmo usando cross-validation. Foram usados os algoritmos de Linear Regression, Linear Regression Regularized (Lasso), Random Forest Regressor e XGBoost Regressor a fim de escolher o algoritmo com a melhor performance;
10. Fazer o fine tunning usando a técnica de random search;
11. Por fim, calcular os erros MAE, RMSE, MAPE e MPE e calcular o retorno financeiro do algoritmo.
12. Publicar o modelo em produção;
13. Criar o bot no telegram que consulta a API do algoritmo treinado e retorna a previsão de faturamento das lojas;
14. Fazer um novo ciclo do projeto fazendo as melhorias necessárias. 

## 4. Os 3 principais insights

**Hipótese 1:** Lojas abertas durante o natal vendem mais.
  - **Falso:** Lojas abertas durante o natal vendem menos
  - **Insight de negócio:** No feriado de natal as vendas são bem menores comparadas a outros feriados como os feriados públicos e a páscoa. O aumento das vendas nos feriados públicos pode ser em decorrência da quantidade de feriados, sendo mais dias é natural que o volume de vendas seja maior. Mas comparando diretamente com a páscoa, no natal as vendas são menores, sabendo disso é possível fazer um roteamento dos funcionários nas datas comemorativas. 

<div align="center">
 <img height="300em" src="https://github.com/laaisfmaia/rossmann_project/blob/main/h1.png">
</div>

**Hipótese 2:** Lojas deveriam vender mais depois do dia 10 de cada mês.
  - **Verdadeiro:** Lojas vendem mais depois do dia 10 de cada mês.
  - **Insight de negócio:** É importante notar que a separação after/before_10_days não é homogênea porque tem mais dias depois do dia 10 do que antes. Mas notou-se que as vendas depois do dia 10 são realmente maiores. Sabendo disso, pode preparar o estoque para a segunda metade do mês e se for fazer alguma mudança nas lojas como uma reforma é preferível fazer no início do mês, onde as vendas são menores.


<div align="center">
 <img height="200em" src="https://github.com/laaisfmaia/rossmann_project/blob/main/h2.png">
</div>

**Hipótese 3:** Lojas com competidores mais próximos deveriam vender menos.
  - **Falso:** Lojas com competidores mais próximos vendem mais
  - **Insight de negócio:** Quando há outros concorrentes próximos ao invés de diminuir as vendas, uma vez que o cliente pode comprar com os outros concorrentes, as vendas aumentam. Isso pode acontecer porque um número maior de pessoas vão ao local, já que tem muitas opções, e mesmo que as vendas se distribuam entre as diferentes lojas no final o número de pessoas interessadas no produto acaba sendo maior. 

<div align="center">
 <img height="300em" src="https://github.com/laaisfmaia/rossmann_project/blob/main/h3.png">
</div>

## 5. Formato da solução

Foi desenvolvido um bot no Telegram que ao receber uma mensagem com o código da loja, faz uma consulta ao algoritmo treinado via API e retorna em tempo real a previsão de faturamento das próximas 6 semanas dessa loja. Esse bot fica disponível 24/7 já que foi hospedado na nuvem. 


## 6. Resultados financeiros
- Redução do erro médio da previsão de 21% para 11% em média. 
- Além disso, ter uma previsão assertiva das vendas acarreta em outros benefícios financeiros como melhor gestão de estoque, contratação otimizada de funcionários, melhor margem para negociar com fornecedores, entre outros benefícios.  


## 7. Conclusão

O objetivo do projeto de prever o faturamento das lojas nas próximas 6 semanas foi atingido, resolvendo o problema de determinar o valor que pode ser investido para a reforma de cada loja. 

## 8. Próximos passos
 
- Fazer um outro ciclo CRISP a fim de melhorar o desempenho do modelo, a fim de diminuir o erro da predição. 
- Melhorar o bot do telegram:
   - Deixando o bot mais interativo de modo a ficar mais intuitivo; 
   - Possibilitar a opção de gerar gráficos comparativos com o faturamento de algumas lojas escolhidas. 

## 9. Extra

- Para acessar o código completo [clique aqui](https://github.com/laaisfmaia/rossmann_project/blob/main/projeto_completo.ipynb)
