# Canais de Conteúdo

- [Lista Canais de Conteúdo](Contents.md#lista-canais-de-conte%C3%BAdo)

----
<br/>

**Lista Canais de Conteúdo**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista de canais de conteúdo da biblioteca.

* **URL**

  {{api-url}}/getContents

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"channels":[{"name":"Clima","description":"","type":"content","language":"pt","url":"weatherBrazil","token":"7979f5ef-956d-4c96-ae6a-7f7e9a19bae1"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/getContents' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}
  ```` 

