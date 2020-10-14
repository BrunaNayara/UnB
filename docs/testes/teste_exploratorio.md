# <center>Testes Exploratórios

<div align="justify">

Os testes exploratórios buscam descobrir como o software realmente funciona e fazer perguntas sobre como ele irá lidar com casos difíceis e fáceis. Explorar é vagar de propósito em um espaço, com uma missão geral mas sem ter a rota pré estabelecida.

A qualidade do teste depende da habilidade do testador de inventar casos de teste encontrar defeitos e quanto mais o testador sabe sobre o produto e diferentes métodos de teste, melhor será o teste.

A documentação dos testes exploratórios varia entre documentar todos os testes realizados ou apenas documentar os bugs. Além de bugs funcionais podem ser identificados problemas de layout, UX, regras de negócios que não estão claras e outros pontos relevantes para as próximas fases do teste.

| <center>Vantagens                                       |<center>Desvantagens |
|:--------------------------------------------------------|:--------------------|
| Muito usado quando existe pouca ou nenhuma documentação | A sua eficiência depende da experiência/habilidade|
| Aumentam as variações dos testes                        | Necessitam de certa experiência no domínio |
| Criam novos cenários para testes                        | Não devem ser levados como principal abordagem de teste |
| Incentiva a discussão do time sobre os itens            | |

## Metáfora do turista - Whitaker
Essa metáfora é uma alusão a um viajante visitando uma grande cidade, com pouco tempo, e que sem um guia ele não vai conseguir conhecer a cidade. Então, precisa fazer uma estratégia para o turista conseguir aproveitar o tempo e guiar as decisões. A mesma ideia é associada ao testador de software que deseja explorar um software complexo ou desconhecido, pois ele tem que escolher a **estratégia** e definir as **metas** pra conseguir atingir um objetivo específico.

### 📆 Planejamento do turista
Um bom turista é aquele que, ao planejar sua viagem, divide seu destino em distritos (comercial, entretenimento, teatro, etc). Fazendo a associação, um bom testador pode dividir o sistema em **distritos**, seguindo um critério lógico. Cada distrito é subdividido em **tipos de tour**, conforme apresenta a tabela abaixo.

![Tabela metafora](../_media/testes/metafora_turista.png)

#### Distrito de Negócios
É o local onde os negócio são feitos, com hora do rush e hora de horário comercial. Em software seria sistemas que dependem da inicialização de ...... prontos pra uso. Esse distito tem 7 tours:

* **Tour guiado (tour F1 ou guidebook tour)**: basicamente, significa seguir, à risca, o manual do usuário. O objetivo é executar cada passo do manual de modo mais fiel possível, assim, avalia-se a habilidade do software de fazer o que foi prometido e também a precisão do manual do usuário;

* **Tour com monetário (money tour)**: vai verificar a coerência das funcionalidades de uma versão demonstrativa do produto com as especificações do sistema, com aquilo que foi prometido. O objetivo é detectar inconsistências entre o que foi entregue ao cliente e o que foi prometido. Pra fazer esse tour, é preciso observar as demonstrações de vendas e procurar os erros, procurar as inconssitências com o produto;

* **Tour ao ponto de referência (Lnadmark tour)**: vai procurando por pontos de referência. Define um ponto e vai até ele; de lá, vai até outro, e assim sucessivamente. É como o jogo de ligar pontinhos. O objetivo é avaliar a interação de diferentes características do produto quando executados em diferentes sequências. Pra fazer esse tour, é necessário: escolher uma _lista de pontos de referência_ (selecionando caracterísitcas chave, com base no tour guiado ou no tour monetário) > definir a _ordem_ desses pontos > ir explorando de um ponto ao outro até ter passado por todos os pontos > manter uma lista de quais pontos foram visitados pra ter um rastreamento do progresso (tipo um grafo);

* **Tour intelectual**: O objetivo é fazer perguntas difícies para o software em teste; isso ajuda a detectar falhas na lógica do sistema, tanto de aspecto complexo quanto simples;

* **Tour a correio (FedEx tour)**: brincar de mover dados (informações) pelo software. Um dado entra, você vai mandando ele pra lá, pra cá, e em algum ponto ele vai sair. O objetivo é identificar cada característica que influencia e sofre influência sobre o dado, e possíveis pontos nos quais os dados são corrompidos em função do processamento desse dado (tu moveu tanto que talvez, em algum ponto, ele tenha sido corrompido);

* **Tour fora do horário comercial (After Hour tour)**: é o momento em que a função principal não estpa mais rodando mas muitas aplicações continuam trabalhando (tarefas de manutenção, backup de arquivos, etc). O objetivo é identificar falhas durante a execução dessas tarefas "after hours". Pra fazer isso é necessário identificar as funções que o software faz quando não está mais fazendo o trabalho principal e fazê-las ser executadas;

* **Tour do coletor de lixo (Garbage collector)**: é uma avaliação metódica e em blocos, gastando pouco tempo em cada lugar. Pra fazer esse tour é preciso definir o objetivo (ex.: todos as caixas de diálogo, todas os itens do menu, etc) e visitar cada um deles usando o menor caminho possível. Esse daqui é basicamente você ir fazendo uma varredura sobre as coisas mais óbvias, os "lixinhos pequenos" geralmente ficam pra tras mesmo, esse tour é pra dar uma geralzona no sistema.

#### Distrito histórico
Esse distrito aqui tem como objetivo testar os softwares **legados**, suas inúmeras versões, modificações e defeitos antigos.

* **Tour ao bairro ruim(bad-neighbourhood tour)**: existem áreas de código repletas de defeitos, e são nessas áreas que o testados vai gastar tempo. O objetivo é justamente esse, concentrar o tempo de teste nas áreas mais defeituosas. Pra fazer isso, vai testando as características e anotando o número de defeitos encontrados por características, isso possibilita rastrear quais áreas são mais problemáticas. Quando identificado um defeito, é interessante fazer o "tour coletor de lixo", porque aí ele vai verificar se a correção de um defeito não ocasionou novos defeitos;

* **Tour pelo museu (museum tour)**: esse aqui é a consulta ao código legado pela data da última modificação no repositório ou registros de alterações. Partindo do pressuposto que o código legado tem pouca documentação, esse tour serve pra garantir que as modificações recentes tenham sido testadas. Pra fazer esse tour é necessário identificar um código legado e testar seus artefatos que sofreram alterações recentes;

* **Tour da versão anterior (the prior version)**: reexecutar os cenários e testes das versões anteriores pra garantir que as funcionalidades que o usuário está acostumado continuam funcionando. O objetivo é validar que na nova versão de um software tudo continua funcionando como antes, se as que seriam removidas foram mesmo removidas e garantir que nenhuma funcionalidade tenha se perdido durante essa atualização. 

#### Distrito de entretenimento
Esses são os testes mais tranquilos, que envolvem características que não são as principais do sistema mas que auxiliam as principais, pra garantir que elas estejam integradas de forma consistente.

* **Tour do ator coadjuvante (supporting actor tour)**: o testador se concentra nas características que não são as principais. O objetivo desse tour é garantir que as funções secundárias funcionem corretamente e interajam certinho com as demais. Pra fazer isso é necessário focar a atenção aos elementos que ficam "mais à direta" ou "mais à esquerda" da tela pois ali estarão os elementos secundários;

* **Tour pelo beco (the back alley tour**: testar as caracterísitcas menos prováveis de serem utilizadas, dos bastidores, e as menos atrativas ao usuário. O objetivo disso é exercitar as características pouco exploradas por testes, pois ali pode-se encontrar comportamentos improváveis já que, provavelmente, as pessoas não testaram muito bem. É um ótimo tour para as áreas que não foram testadas;

* **Tour noturno (all-nighter tour)**: o teste não pode parar... é o teste do truvs eterno! "Quanto tempo a aplicação pode durar em execução?", "por quanto tempo a aplicação consegue executar e processar dados antes de entrar em colapso?". O objetivo é desafiar o software inserindo dados e forçando leituras, e a tendência é que ele falhe em algum momento. Pra fazer isso, é necessário aplicar os testes por um longo período de tempo até que se obtenham os resultados.
⚠️ Dúvida: isso não é um teste de stress? Qual a diferença?

#### Distrito turístico
Esses testes são breves e com um propósito especial, bem específico. Ele não é para fazer o software funcionar, é pra marcar as funcionalidades ainda não visitadas.

* **Tour do colecionador (collector's tour)**: o testador vai experimentar as coisas, colecionar saídas de software. O objetivo é visitar todos os locais possíveis e documentar toda saída obtida, fazer o software produzir todas as saídas possíveis. É um tour grande, então pra fazer isso é necessário dividir as características pelo grupo e atibuir determinadas saídas pra cada pessoa realizar a coleta dessas saídas.

* **Tour do empresário solitário (lonely bussinessman tour)**: o objetivo desse tour é testar as características mais distantes do ponto incial da aplicação. A ideia é sair do ponto mais distante e ir "viajando" até o objetivo ser atingido. Pra fazer isso é preciso saber "qual característica precisa da maior quantidade de cliques pra ser atingida?" e "qual característica precisa-se navegar pela maior quantidade de telas até o objetivo ser atingido?". A resposta dessas perguntas indicam as características a serem testadas;

* **Tour do supermodelo (supermodel tour)**: esse tour tem o foco na interface, naquilo que é visto, não nas funcionalidades em si. O objetivo desse tour é encontrar defeitos superficiais relacionados à interface e os elementos apresentados. É importante saber que os produtos que passam por esse teste (são "aprovados") ainda podem ter graves defeitos mas não foram detectados aqui porque apresentam aparência impecável (como um top model mesmo). É bem teste de IHC mesmo;

* **Tour TOGOF**: esse nome é uma adaptação para o acrônimo BOGOF (buy one, get one free), no caso aqui, seria "test one, get one free", e tem esse nome porque indica que se um defeito for encontrado em uma cópia, será encontrado em todas as cópias dessa aplicação. É um tour simples pra testar várias cópias de uma mesma aplicação de forma simultânea. O objetivo é identificar possíveis problemas de concorrência e compartilhamento indevido de recursos. Pra fazer isso é necessário começar executando uma aplicação e depois vai executando as outras cópias, de forma que cada cópia seja forçada a executar algo em memória ou disco. Tente fazer todas as cópias abrirem os mesmos arquivos ou transmitir dados pela rede de forma simultânea.

* **Tour pelo bar escocês (scottish pub tour)**: 
 




</div>

### 📌 Links topzeiras
[Explicação no Linkedin](https://www.linkedin.com/pulse/para-que-servem-os-testes-explorat%C3%B3rios-diego-conrado/?originalSubdomain=pt)
<br>
[Aula da Iolane](https://www.youtube.com/watch?v=9h65WEjmqTg&feature=youtu.be)