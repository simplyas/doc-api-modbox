# Mídias Online

- [Lista Mídias Online](Streamings.md#lista-m%C3%ADdias-online
)

----
<br/>

**Lista Mídias Online**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista de mídias online da biblioteca.

* **URL**

  {{api-url}}/requestStreamings

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"streamings":[{"name":"LIVE","token":"c80f-4748-8558-81bbcdd2c9ca","creation_date":"2018-03-16","url":"https://www.youtube.com/watch?v=q9UAIQjIV2M","md5":"e84a63492ff08470156d82da0f7e0ca5","image":"youtube","description":"live","live":"True","offline":"False"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestStreamings' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}
  ```` 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0MDM5OTM3Ml19
-->