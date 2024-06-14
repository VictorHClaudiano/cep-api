<h1 align="center">
   <a href="#"> Pesquisa de endereço usando várias APIs </a>
</h1>

<h3 align="center">
   Este programa Go permite aos usuários consultar informações de endereço com base em CEPs usando duas APIs diferentes: BrasilAPI e ViaCEP. Ele consulta ambas as APIs simultaneamente e retorna as informações de endereço da API que responde primeiro. Também inclui um mecanismo de tempo limite para evitar a espera indefinida por uma resposta.
</h3>

<h4 align="center"> 
	 Status: Concluído
</h4>

## Uso
1. Clone o repositório.
2. Navegue até o diretório que contém o arquivo main.go.
3. Execute go run main.go.
4. Digite o código postal quando solicitado.

## Dependências
Este programa usa as seguintes dependências:
1. contexto: para gerenciar cancelamentos e tempos limite.
2. net/http: para fazer solicitações HTTP.
3. io: para ler o corpo da resposta das solicitações HTTP.

## Como funciona
O programa solicita que o usuário insira um código postal para pesquisa de endereço. Ele consulta simultaneamente a BrasilAPI e o ViaCEP usando goroutines. Cada goroutine faz uma solicitação HTTP para a respectiva API com o CEP fornecido. O programa espera pela primeira resposta usando uma instrução select com tempo limite. Se uma resposta for recebida dentro do período de tempo limite, ele imprimirá as informações de endereço. Se nenhuma resposta for recebida dentro do período de tempo limite, ele imprimirá uma mensagem de tempo limite.

## Funções
main: O ponto de entrada do programa. Ele solicita a entrada do usuário, cria um contexto com um tempo limite e inicia goroutines para consultar ambas as APIs. RequestBrasilApi e RequestViaCep: Funções para consultar a BrasilAPI e ViaCEP respectivamente. Eles tratam de erros e enviam as informações de endereço ou mensagem de erro para o canal fornecido. fetchAddress: Função para fazer solicitações HTTP para a URL especificada com o contexto fornecido. Ele retorna o corpo da resposta ou uma mensagem de erro.

## Manipulação de erros
O programa lida com erros como falha na criação de uma solicitação HTTP, falha na busca do endereço e falha na leitura do corpo da resposta. Se ocorrer um erro durante a pesquisa de endereço de qualquer uma das APIs, o programa imprimirá uma mensagem de erro.
## Notas
Ambas as APIs fornecem funcionalidades semelhantes, mas podem ter diferenças no formato ou na disponibilidade dos dados. O programa seleciona a resposta da primeira API para responder dentro do período de tempo limite, fornecendo um mecanismo de fallback caso uma API esteja lenta ou indisponível. Sinta-se à vontade para usar, modificar ou estender este programa conforme necessário!


