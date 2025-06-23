# Exercício – Análise Técnica de Projetos Reais no GitHub
### Entrega até: 23/06
**Objetivo**: Este exercício tem como objetivo exercitar a análise técnica aplicada, desenvolvendo sua capacidade de reconhecer boas práticas de arquitetura e construção de software em projetos reais de código aberto.


----------------------- 
O que você deve fazer:    
Pesquise no GitHub um ou mais projetos com pelo menos 10 estrelas que implementem cada uma das características técnicas listadas abaixo.        
1.1. Caso você identifique um projeto que atenda mais de uma característica, você pode indicar ele mais de uma vez.       

Para cada o característica técnica, você deve:     

Identificar e apresentar um trecho de código que comprove o uso da característica.     
Escrever uma justificativa técnica, respondendo:     
“Por que você acredita que essa característica foi adotada neste projeto?”     

A entrega pode ser feita em formato Markdown ou PDF, contendo:     

Nome dos projetos e links no GitHub     
Cada característica identificada     
Código (ou trecho relevante)     
Justificativa     
Características Técnicas a serem Identificadas     
Uso de cache (ex: Redis) – melhora desempenho e reduz carga em serviços     
Filas de mensageria (RabbitMQ, Kafka) – desacoplam e distribuem cargas     
Circuit breaker – protege o sistema de cascata de falhas     
CI/CD com pipelines – entrega contínua confiável     
Análise estática de código (linters, SonarQube) – detecta problemas antes de ir para produção     
Autenticação com JWT/OAuth – padrão para APIs modernas e seguras     
Serverless/Lambda – execução sob demanda com economia de recursos     
Autenticação com JWT/OAuth — padrão para APIs modernas e seguras.     
Testes automatizados (unitários e integração) — garantem estabilidade com segurança.     
Exemplo de estrutura da entrega     
### Projeto analisado: [awesome-api-service](https://github.com/usuario/awesome-api-service) ### Característica identificada: Uso de cache (Redis) ### Evidência (trecho de código): import redis cache = redis.Redis(host='localhost', port=6379) value = cache.get('some_key') ## Justificativa: O projeto usa Redis para armazenar temporariamente respostas de API que exigem consultas pesadas ao banco. Isso reduz o tempo de resposta e o número de acessos repetidos à base, especialmente em endpoints públicos com alta demanda.
Dicas     
Prefira projetos com documentação e organização clara.     
Use a busca do GitHub com termos como “redis”, “jwt”, “circuit breaker”, “.github/workflows”, “serverless.yml”.     
Seja objetivo e técnico na justificativa: pense como um engenheiro de software.     
Entrega     
Formato: .md ou .pdf     
Enviar via Moodle ou repositório indicado pelo professor.     
Nome do arquivo: pac7_github_<seunome>.md     
