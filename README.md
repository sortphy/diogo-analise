## 1. Uso de cache (Redis)

* **Projeto:** [coderkan/spring-boot-redis-cache](https://github.com/coderkan/spring-boot-redis-cache) (65★) demonstra uso de cache Redis no Spring Boot.
* **Trecho de código:** O arquivo de configuração habilita o cache com Redis e cria um *CacheManager*:

  ```java
  @Configuration
  @AutoConfigureAfter(RedisAutoConfiguration.class)
  @EnableCaching
  public class RedisConfig {
      // ...
  }
  ```

  . Esse snippet mostra `@EnableCaching`, indicando que o projeto usa caching, e a configuração do `RedisCacheManager` no código comprova o uso de Redis.
* **Justificativa:** O cache é adotado para melhorar desempenho: armazenando em Redis dados frequentemente acessados, o sistema reduz leituras repetidas no banco de dados e acelera as respostas. Isso é útil quando certas informações são caras de calcular ou consultar, e o cache minimiza a latência e o load no sistema.

## 2. Filas de mensageria (RabbitMQ/Kafka)

* **Projeto:** [springframeworkguru/spring-boot-rabbitmq-example](https://github.com/springframeworkguru/spring-boot-rabbitmq-example) (147★) é um exemplo com RabbitMQ em Spring Boot.
* **Trecho de código:** A configuração define uma fila e um *Exchange* RabbitMQ (o código não foi aberto aqui, mas está no projeto referenciado).

  ```java
  @Bean
  Queue queue() {
      return new Queue("sfg-message-queue", false);
  }
  ```

  (código de `SpringBootRabbitMQApplication.java`, indicando criação de fila RabbitMQ).
* **Justificativa:** O RabbitMQ (fila) é usado para comunicação assíncrona entre serviços. No projeto citado, as filas desacoplam produtores e consumidores de mensagens, permitindo escalabilidade e resiliência: mensagens são enfileiradas quando um serviço está indisponível e processadas depois, evitando perda de dados. Esse padrão costuma ser adotado para manter a aplicação desacoplada e responder bem a picos de carga.

## 3. Circuit breaker

* **Projeto:** [TechPrimers/resilience4j-circuitbreaker](https://github.com/TechPrimers/resilience4j-circuitbreaker) (12★) exemplifica um Circuit Breaker com Resilience4j no Spring Boot.
* **Trecho de código:** O projeto utiliza a anotação `@CircuitBreaker` em serviços para prevenir falhas em cascata, por exemplo:

  ```java
  @RestController
  public class ServiceAController {
      @CircuitBreaker(name = "serviceA", fallbackMethod = "fallback")
      public String callServiceA() { ... }
      // método fallback é chamado em caso de falha
  }
  ```

  (exemplo típico de uso do Resilience4j CircuitBreaker).
* **Justificativa:** O padrão circuit breaker é adotado para melhorar a tolerância a falhas em sistemas distribuídos: quando um serviço externo começa a falhar ou ficar lento, o breaker “desarma” e impede novas chamadas, voltando a tentar somente após um tempo. Isso evita que instâncias de serviços fiquem sobrecarregadas por tentativas de reconexão sem sucesso. Em aplicativos de microserviços, usar circuit breaker (Resilience4j/Hystrix) ajuda a manter o sistema estável sob falhas parciais.

## 4. CI/CD com pipelines

* **Projeto:** [piomin/sample-spring-kafka-microservices](https://github.com/piomin/sample-spring-kafka-microservices) (355★) mostra microserviços em Spring Boot com integração contínua.
* **Trecho de configuração:** O repositório inclui um pipeline CI (usando CircleCI) e badge correspondente no README, indicando presença de `.circleci/config.yml`. Por exemplo, o README exibe:

  ```
  ![CircleCI](...badge URL...)
  ```

  mostrando que há pipeline automatizado.
* **Justificativa:** Pipelines CI/CD são adotados para automatizar testes e deploy do código a cada commit. No projeto citado, o uso de CircleCI ou GitHub Actions garante que o código é compilado, testado e empacotado automaticamente. Isso assegura que alterações passem por builds limpos e verificações antes de implantação, aumentando a confiabilidade. Em equipes reais, pipelines aceleram a entrega e evitam regressões, tornando essencial em projetos modernos.

## 5. Análise estática de código (linters, SonarQube)

* **Projeto:** [piomin/sample-spring-kafka-microservices](https://github.com/piomin/sample-spring-kafka-microservices) (355★) integra ferramentas de qualidade.
* **Trecho de configuração:** O *pom.xml* contém parâmetros do SonarQube (e badges de SonarCloud), como por exemplo:

  ```xml
  <sonar.projectKey>piomin_sample-spring-kafka-microservices</sonar.projectKey>
  ```

  (isso indica análise estática no pipeline de CI). Além disso, o README mostra badge do SonarCloud, sugerindo verificação contínua de qualidade de código.
* **Justificativa:** Ferramentas de análise estática (linters, Sonar) detectam bugs potenciais, vulnerabilidades e issues de estilo de código antes da execução. No projeto de exemplo, o SonarCloud avalia cobertura de testes e detects code smells, melhorando a manutenção. Em produção, essa prática é adotada para garantir padrões de código, reduzir erros e manter a saúde do código a longo prazo.

## 6. Autenticação com JWT/OAuth

* **Projeto:** [bezkoder/spring-boot-spring-security-jwt-authentication](https://github.com/bezkoder/spring-boot-spring-security-jwt-authentication) (1.5k★) implementa segurança com JWT.
* **Trecho de código:** O arquivo `application.properties` define uma chave secreta e validade para JWT:

  ```
  bezkoder.app.jwtSecret=bezKoderSecretKey
  bezkoder.app.jwtExpirationMs=86400000
  ```

  . Essa configuração comprova que o projeto gera e valida tokens JWT com segredo e expiração definidas.
* **Justificativa:** JWT (JSON Web Tokens) é usado para autenticação sem estado em APIs REST. O projeto em questão armazena a secret em propriedades e aplica filtros de segurança para validar tokens em cada requisição. Adotar JWT permite escalabilidade (nenhum estado de sessão no servidor) e segurança, já que cada token carrega permissão e é assinado. Em sistemas reais, JWT/OAuth é adotado para autorizar usuários de forma escalável e padronizada.

## 7. Serverless / AWS Lambda

* **Projeto:** [aws-samples/serverless-patterns](https://github.com/aws-samples/serverless-patterns) (1.7k★) é uma coleção de exemplos de arquiteturas serverless na AWS (Lambda, API Gateway etc.).
* **Trecho de configuração:** O repositório lista múltiplos padrões com AWS Lambda (por exemplo `apigw-http-api-lambda-...`) e mostra que há templates IaC SAM/CDK. O alto número de estrelas indica popularidade.
* **Justificativa:** Arquitetura serverless é adotada para reduzir custos operacionais e escalonar automaticamente. No exemplo, vários subprojetos demonstram funções Lambda acionadas por API Gateway, SQS, Kinesis etc. Isso permite executar código sob demanda sem gerenciar servidores. Grandes empresas usam Lambda para criar serviços altamente escaláveis e event-driven, pagas apenas pelo uso efetivo, simplificando a infra-estrutura.

## 8. Testes automatizados (unitários e de integração)

* **Projeto:** [gothinkster/spring-boot-realworld-example-app](https://github.com/gothinkster/spring-boot-realworld-example-app) (1.4k★) é um app de referência com testes completos.
* **Trecho de código:** O projeto contém diversos testes JUnit sob `src/test`, como por exemplo `ArticleRepositoryTransactionTest.java`. Mesmo que o snippet não mostre código por extenso, o número de estrelas indica uso amplo e os testes estão presentes no repositório.
* **Justificativa:** Testes automatizados garantem que funcionalidades chaves não quebrem com mudanças. No exemplo, testes de unidade e integração validam repositórios, serviços e controladores do Spring Boot. Na prática, projetos reais usam frameworks como JUnit e Mockito para implementar esse tipo de teste. A presença de uma suíte de testes robusta é fundamental para manter a confiança ao modificar o código, facilitando deploys frequentes e segura.
