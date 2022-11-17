# airnbn_predict_first-booking
==============================

# Project in progress...

Projeto de Previsão do primeiro destino que um novo usuario irá escolher.


## Contextualização:

Os dados do projeto foram obtidos do kaggle, do desafio "airnbn_predict_first-booking".

O contexto do negócio é fictício, porem todo o planejamento e desenvolvimento da solução esta sendo realizado seguindo todos os passos de um projeto real para o mercado de trabalho.

Todo o projeto é desenvolvido utilizando a metodologia CRISP-DS

# Entendendo o problema

- Objetivo do problema: Precisamos prever qual será o primeiro destino que um novo usuario irá escolher.
- Tipo de Negocio Airbnb: Marketplace (Conecta pessoas que oferecem acomodações, com pessoas que estão procurando acomodações)
- Oferta: Pessoas oferencendo acomodações (Tamanho do portfolio, Diversidade/densidade de portfolio, preço medio)
- Demanda: Pessoas procurando acomodações (Numero de Usuarios, LTV(Lifitime value), CAC(Client Acquisition cost))
- Gross Revenue ( FEE * Numero de clientes) - CAC

# Informações das Features Tabela train_user

|Feature Name| Information|
|----------------|:---------------:|
|id:                         |user id
|date_account_created:       |the date of account creation
|timestamp_first_active:     |timestamp of the first activity, note that it can be earlier than date_account_created or date_first_booking because a user can search before signing up
|date_first_booking:         |date of first booking
|gender                      |
|age                         |     
|signup_method               |
|signup_flow:                |the page a user came to signup up from
|language:                   |international language preference
|affiliate_channel:          |what kind of paid marketing
|affiliate_provider:         |where the marketing is e.g. google, craigslist, other
|first_affiliate_tracked:    |whats the first marketing the user interacted with before the signing up
|signup_app                  |
|first_device_type           |
|first_browser               |
|country_destination:        |this is the target variable you are to predict

|Feature Name| Information|
|----------------|:---------------:|
|id:                         |ID do Usuario
|date_account_created:       |Data da Criação da Conta
|timestamp_first_active:     |Data do cadastro, note que pode ser anterior à data de criação da conta ou à data da primeira reserva porque um utilizador pode pesquisar antes de se inscrever
|date_first_booking:         |data da primeira reserva
|gender                      |Sexo
|age                         |Idade 
|signup_method               |Metodo de inscrição
|signup_flow:                |fluxo de inscrição: a página de onde um utilizador veio para se inscrever
|language:                   |Preferencia linguistica internacional
|affiliate_channel:          |canal afiliado: que tipo de marketing pago
|affiliate_provider:         |fornecedor afiliado: onde o marketing é, por exemplo, google, craigslist, outro
|first_affiliate_tracked:    |primeira afiliação rastreada: qual foi o primeiro marketing com que o utilizador interagiu antes da inscrição
|signup_app                  |Aplicativo de inscrição
|first_device_type           |Primeiro tipo de dispositivo
|first_browser               |Primeiro nagevagor
|country_destination:        |Destino do pai:Variavel alvo que deve prever

# Informações das Features Tabela session
|Feature Name| Information|
|----------------|:---------------:|
|user_id:           | to be joined with the column 'id' in users table
|Id in users Table  | Tabela de utilizadores
|action             | Açao
|action_type        | Tipo de ação
|action_detail      | Detalhe da ação
|device_type        | Tipo de dispositivo
|secs_elapsed       | segundos

# Criação das Hipóteses

- H1 - Escolha do destino pela estação do ano
- H2 - Escolha do destino em relação aos Feriados 
- H3 - Escolha do Destino em relação a promoção
- H4 - Escolha do Destino em relação ao Sexo
- H5 - Escolha do destino em relação a idade
- H6 - A maioria dos clientes escolhem UK, tentar identificar por qual motivo.
- H7 - Data da primeira Reserva, qual periodo do ano, qual estção e lugar escolhido.
- H8 - Proporção do sexo e idade que acessa o site.
- H9 - Qual o metodo de incrição mais utilizado com os destino escolhido, será que o metodo pode inflienciar na escolha do local
- H10- Fluxo de inscrição, A pagina acessada antes de vim para a pagina do airbnb conseguimos identificar se influencia na escolha do destino
- H11- Tipo de preferencia linguistica influencia na escolha do destino
- H12- Fornecedor afiliado, não pode ser de algum destino e de alguma forma pode influenciar a decisão do cliente
- H13- 

# Ciclo001 - End to End

No primeiro Ciclo do crisp (End to End) foi criado todo o pipeline do projeto, e consegui identificar que existe um grande desbalanceamento na nossa variavel respota, e nosso modelos inicial teve uma performance de 0.09 (Balanced Accuracy: 0.09)

Porque utilizei Balanced Accuracy: Uma metrica para classes desbalanceada, pois como ela vai da uma media muito alto para a classe majoritaria e uma media muito baixa para as demais classe, chegando em um resultado final baixo, como deve ser nesses casos de classe desbalanceada.

### Conclusão do primeiro ciclo:

Não posso avaliar a matriz de confusão, onde ficou bem claro o desbalanceamento onde o modelo fez previsão na classe majoritária e arrumar o desbalanceamento atraves de tecnicas estatisticas, precisamos antes 

seguir alguns passos:
- Criar Feature
- Limpar o ruido
- e depois sim realizar o balanceamento

Fazendo o balanceamento com os dados sujos ou sem nenhuma features criada para representar o modelo o Balanceamento vai piorar ainda mais o problema.

# Ciclo002 - Imbalanced Metrics


Neste ciclo estarei focando: 

- Realizando a analise descritiva das features, procurando inconsistencia nos dados
- Criando as Hipóteses e validando, tentando encontra padrões nos dados que possa nos ajuda a entender melhor cada features.
- criação de Features Relevantes 
- Filtrando e removendo ruidos caso necessário
- Balanceamento das Classes 
- Escolha de outros Algoritmos de Ml

## Registro de algumas manipulações

- Tratamento das colunas com dados faltante
    - Feature idade, tem 87.990 dados faltantes, para este ciclo a decisão foi colocar a mediana no lugar. (34 anos)



### Conclusão do Segundo ciclo: