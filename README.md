# Redirect URL Shortner Lambda

## Descrição do Projeto

Este projeto implementa uma função **AWS Lambda** que atua como um resolvedor de URLs encurtadas. Ele recebe uma requisição `GET`, 
extrai o **UUID** passado como parâmetro, acessa o **Amazon S3** para buscar o arquivo correspondente, valida a data de expiração, e, 
se a URL ainda for válida, redireciona o cliente para a URL original.  

## Endpoints

## `GET /{urlCode}`

**Descrição**: Busca no **Amazon S3** o arquivo JSON de acordo com o **UUID** passado como parâmetro da requisição. 
Valida a data de expiração e redireciona para a URL original.

**Parâmetro**:  
- **urlCode**: (String) O UUID que identifica a URL encurtada. 

### Resposta
- **200: OK** caso a operação seja feita com sucesso.
- **404: Not Found** caso o UUID não seja encontrado ou a URL tenha expirado.
- **500: Internal Server Error** em caso de erros inesperados.  

## Funcionamento

- A requisição `GET` é enviada para o endpoint configurado, com o **UUID** como parâmetro.  
- A função Lambda é acionada e processa o UUID.  
- A função consulta o **Amazon S3** para buscar o arquivo JSON correspondente.  
- O conteúdo do arquivo é lido e a data de expiração é validada.  
- Se a URL for válida, o cliente é redirecionado para a URL original.  
- Em caso de falhas, uma mensagem de erro é retornada.  

## Tecnologias Utilizadas

- AWS Lambda: Para processar as requisições.
- Amazon S3: Para armazenar os arquivos JSON.
- Java (versão 17)
- Insomnia: Para testar as requisições
- UUID: Para geração de identificadores únicos.
