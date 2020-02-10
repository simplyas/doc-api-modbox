# Logs e Métricas

Coleção de métodos para consulta de logs e métricas dos recursos do contrato.

- [Logs de Dados da Wifi](#)
- [Logs de Exibição de Mídias](#)
- [Logs do Histórico de Terminais](#)
- [Métricas do Wifi para Dashboard](#)

----
<br/>

## Logs de Dados da Wifi
Retorna logs dos dados de acesso da wifi.

* **URL**

  {{api-url}}/requestDataWifi

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| list_data_type | Obrigatório | ["devices_online","wifi_totaldevices", 'wifi_hour', 'wifi_differentdays', 'unique_connections', 'reconnections', 'wifi_phonestoday', 'top10_users'] |
	| from_date | Opcional | Data inicial |
	| to_date | Opcional | Data final |
	| groups | Obrigatório | Lista de localidades |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"logs": []}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestClocks' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "list_data_type":"{{list_data_type}}", "from_date":"{{from_date}}", "to_date":"{{to_date}}", "groups":"{{groups}}"}'
  ````

<br/>


## Logs de Exibição de Mídias
----
## Logs do Histórico de Terminais
----
## Métricas do Wifi para Dashboard
Retorna informações agrupadas de 30 dias.

* **URL**

  {{api-url}}/requestMetricsDashboard

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| list_data_type | Obrigatório | ["devices_online","wifi_totaldevices", 'wifi_hour', 'wifi_differentdays', 'unique_connections', 'reconnections', 'wifi_phonestoday', 'top10_users'] |
	| from_date | Opcional | Data inicial |
	| to_date | Opcional | Data final |
	| groups | Obrigatório | Lista de localidades |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"wifi": []}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestClocks' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "list_data_type":"{{list_data_type}}", "from_date":"{{from_date}}", "to_date":"{{to_date}}", "groups":"{{groups}}"}'
  ````

<br/>



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcyODU2Njk5LC0yMzExNTAwNzksLTE5MD
c3NDA0NDQsLTE2NjEzNjU2NzgsLTcxNjQxNTE1OCw2NDc5Mjk3
NDAsLTEwNzI4NDYwMDddfQ==
-->