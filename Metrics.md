# Métricas Distribuidor

Retorna métricas do contrato do distribuidor.

----
<br/>

**Métricas**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista com métricas do contrato do distribuidor.

* **URL**

  {{api-url}}/requestMetrics

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
	| 200 | ```{"metrics":[{"terminals_by_companies":[{"company_name":"SIMPLY AS","count":[{"date":"01/05","number":9265}]}]},{"terminals_total":[{"date":"01/05","number":47974}]},{"users_by_companies":[{"company_name":"SIMPLY AS","count":[{"users":4239,"date":"01/05"}]}]},{"users_total":[{"users":23386,"date":"01/05"}]},{"users_sum":[{"users":19709,"date":"01/05"}]},{"terminals_sum":[{"company_name":"SIMPLY AS","count":[{"terminals":28745,"date":"01/05"}]}]},{"people":[{"count":124,"date":"01/05"}]},{"people_sum":[{"count":558,"date":"01/05"}]}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestMetrics' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}'
  ```` 
