# Arquivos de mídia

- [Lista Arquivos](Files.md#lista-arquivos)

----
<br/>

**Lista Arquivos**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista de arquivos da biblioteca.

* **URL**

  {{api-url}}/requestFiles

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
	| 200 | ```{"custom":"0","files":[{"name":"OFP6620","md5":"7de83bdd072116e25bd30998413d2708","creation_date":"2018-03-28","duration":"10"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestFiles' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}
  ```` 

