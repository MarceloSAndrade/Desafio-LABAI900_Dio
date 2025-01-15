# Desafio-LABAI900_Dio

Acessar o portal do Azure Página inicial - Microsoft Azure e criar um conta , caso não possua 
 
Selecionar a opção Criar um recurso e pesquise Machine Learning e crie um novo recurso do Azure Machine Learning

 

Assinatura : sua assinatura do Azure .
Grupo de recursos : Crie ou selecione um grupo de recursos .
Nome : Insira um nome exclusivo para seu espaço de trabalho .
Região : Selecione a região geográfica mais próxima,recomendo o EAST 2 para taxas mais baratas.
Conta de armazenamento : observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho .
Cofre de chaves : Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho .
Insights de aplicativo : observe o novo recurso padrão de insights de aplicativo que será criado para seu espaço de trabalho .
Registro de contêiner : Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner ).
3️⃣Selecione Revisar + criar e selecione criar .


 


Aguarde a criação do seu espaço de trabalho (pode demorar alguns minutos) e, em seguida selecione Launch Studio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche todas as mensagens exibidas.
Feito isso, seu espaço de trabalho foi criado✅
Usando aprendizado de máquina automatizado para treinar um modelo:
💬 1️⃣ No Azure Machine Learning Studio procure ML autorizado selecione novo trabalho de ML automatizado e coloque as seguintes configurações : 💻
Configurações básicas :
Nome do trabalho : mslearn-bike-automl
Selecionar : criar novo nome do experimento
Novo nome do experimento:mslearn-bike-rental
Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
Marcas : nenhum
1️⃣☑️
Tipo de tarefa e dados :
Selecione o tipo de tarefa : Regressão
Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:
Tipo de dados : Nome : alugueldebicicletas (Não pode haver espaço no nome escolhido)
Descrição : dados históricos de aluguel de bicicletas
Tipo : Tabular
Fonte de dados :
Selecione De arquivos da web
URL da Web : :https://aka.ms/bike-rentals
Ignorar validação de dados : não selecionar
Configurações :
Formato de arquivo : Delimitado
Delimitador : Vírgula
Codificação : UTF-8
Cabeçalhos de coluna : somente o primeiro arquivo possui cabeçalhos
Pular linhas : Nenhum
O conjunto de dados contém dados multilinhas : não selecione
Examinar :
Revise os tipos detectados automaticamente
Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar o envio do trabalho de ML automatizado. Clique em avançar
Configurações de tarefa :
Tipo de tarefa : Regressão
Conjunto de dados : aluguel de bicicletas
Coluna de destino : Rentals (Interg)
Clique em configurações adicionais :
Métrica primária : Normalized root mean squared error
Desmarque 🔲 explicar o melhor modelo
Desmarque 🔲 Usar todos os modelos suportados, Você restringirá o trabalho para tentar apenas alguns algoritmos específicos para realizar testes.
Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
Limites : expanda esta seção
Máximo de avaliações : 3
Máximo de avaliações simultâneas : 3
Máximo de nós : 3
Limite de pontuação da métrica : 0,085 ( para que, se caso um modelo atingir uma pontuação da métrica Normalized root mean squared error de 0,085 ou menos, o trabalho termina. )
Tempo limite do experimento (minutos) : 15
Tempo limite de iteração : 15
☑️Habilitar encerramento antecipado
Validação e teste :
Tipo de validação : divisão de validação de treinamento
Validação de percentual de dados : 10
Dados de teste : Nenhum
Computação :
Selecione o tipo de computação : sem servidor
Tipo de máquina virtual : CPU
Camada de máquina virtual : Dedicado Tamanho da máquina virtual : Standard_DS3_V2*
Número de instâncias : 1
Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.
Envie o trabalho de treinamento. Ele inicia automaticamente.Espera o trabalho terminar,em alguns casos pode demorar até 15 minutos ou mais 🕑
Avalie o melhor modelo ✅
Na guia Visão geral do trabalho automatizado de aprendizado de máquina,selecione o texto em : Nome do algoritmo,do melhor resumo de modelo para visualizar seus detalhes ao lado direito.
Selecione a guia Métricas e selecione os gráficos residuais e predito_true se eles ainda não estiverem selecionados.
Implantar e testar o modelo 💾
Na guia Modelo selecione Implantar e marque Serviços Web Agora Preencha o campo a seguir com as seguintes configurações :
Nome : prever-alugueis (Sem acentuação)
Descrição : Prever aluguel de bicicletas
Tipo de computação : Instância de Contêiner do Azure
Habilitar autenticação✔️ : selecionado
Aguarde o início da implantação – isso pode levar alguns segundos. O status de implantação de Pontos de Extremidade de previsão de aluguel será indicado na parte principal da página como Running . Aguarde até que o status da implantação mude para Succeeded . Isso pode levar de 5 a 10 minutos.
Testar o serviço implantado :
No estúdio Azure Machine Learning, no menu esquerdo, selecione Pontos de extremidade marque Prever-alugueis clique em testar. No painel Inserir dados para teste de ponto de extremidade copie o código e cole substituindo o modelo JSON pelos seguintes dados de entrada:
{
"Inputs": {
"data": [
{
"day": 1,
"mnth": 1,
"year": 2022,
"season": 2,
"holiday": 0,
"weekday": 1,
"workingday": 1,
"weathersit": 2,
"temp": 0.3,
"atemp": 0.3,
"hum": 0.3,
"windspeed": 0.3
}
]
},
"GlobalParameters": 1.0
}
Clique no botão Testar
Revise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:
{ "Results": [ 444.27799000000000 ] }
Finalizado : O painel de teste pegou os dados de entrada e usou o modelo treinado para retornar o número previsto de aluguéis.
 

 


 

 

 

 

 

 

 

 

 

