# Solicitações HTTP e K6

Este documento irá mostrar um pouco sobre as solicitações HTTP no contexto de testes de carga utilizando a ferramenta k6. A seguir, serão abordados os principais conceitos e funcionalidades destacados no texto do autoestudo, focando nos tipos de solicitações HTTP suportadas pelo k6, a utilização de tags para organização e análise de resultados, e estratégias para agrupar URLs em uma única métrica.

# Conceitos Fundamentais
## Solicitações HTTP
No desenvolvimento de testes de carga, definir as solicitações HTTP que serão feitas ao sistema é geralmente o primeiro passo. O k6, uma ferramenta moderna para testar a performance e a resistência de sistemas sob carga, oferece uma sintaxe simplificada para a criação destas solicitações.

## Tipos de Solicitações

**GET:** Utilizado para recuperar informações do servidor.    
**POST:** Usado, comumente, para enviar dados para serem processados por um recurso no servidor.

## Métodos Disponíveis
O módulo HTTP do k6 suporta diversos métodos para realizar solicitações, incluindo:

- get()
- post()
- put()
- delete()
- options()
- patch()
- head()
- request() para qualquer tipo de solicitação HTTP.
- batch() para emissão de múltiplas solicitações HTTP em paralelo.

## Utilizando Tags em Solicitações
O k6 aplica automaticamente tags às suas solicitações HTTP, permitindo filtrar resultados e organizar a análise de dados. Algumas tags incluem:

- expected_response: Indica se a resposta está dentro de uma faixa esperada (normalmente, 200-399).
- group: Nome do grupo no qual a solicitação foi realizada.
- name: URL da solicitação.
- method: Método da solicitação (GET, POST etc.).
- scenario: Nome do cenário no qual a solicitação foi executada.
- status: Status da resposta.

## Agrupando URLs sob uma Única Tag
Frequentemente, testes com inúmeras URLs dinâmicas podem poluir a métrica com dados únicos dispersos. Uma estratégia para contornar isso é definir explicitamente uma tag name para agrupar estas solicitações sob um único indicador. Isso pode ser feito passando um objeto tags com a chave name definida para o método de solicitação.