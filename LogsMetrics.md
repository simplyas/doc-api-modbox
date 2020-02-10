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
	| date_ini | Opcional | Data inicial |
	| date_end | Opcional | Data final |
	| group_token | Obrigatório | Token da Localidade |
	| connection_type | Obrigatório | 0, 1, 2 ou 3 |
	| network_type | Obrigatório | 0, 1 ou 2 |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"logs": []}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Informe as datas corretamente."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestDataWifi' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "date_ini":"{{date_ini}}", "date_end":"{{date_end}}", "group_token":"{{group_token}}", "connection_type":"{{connection_type}}", "network_type":"{{network_type}}"}'
  ````
<br/>

## Logs de Exibição de Mídias
Retorna logs da exibição das mídias nos terminais.

* **URL**

  {{api-url}}/requestMetricsFromLog

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| date_ini | Opcional | Data inicial |
	| date_end | Opcional | Data final |
	| group_token | Obrigatório | Token da Localidade |
	| connection_type | Obrigatório | 0, 1, 2 ou 3 |
	| network_type | Obrigatório | 0, 1 ou 2 |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"medias":[], ""}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Informe as datas corretamente."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestMetricsFromLog' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "date_ini":"{{date_ini}}", "date_end":"{{date_end}}", "group_token":"{{group_token}}", "connection_type":"{{connection_type}}", "network_type":"{{network_type}}"}'
  ````
<br/>

## Logs do Histórico de Terminais
Retorna histórico de dados dos terminais.

* **URL**

  {{api-url}}/requestMetricsTerminal

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| terminal_token | Obrigatório | Token do Terminal |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```[{}]``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Informe om token correto."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestMetricsTerminal' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "terminal_token":"{{terminal_token}}"}'
  ````
<br/>


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
  --url 'http://{{api-url}}/requestMetricsDashboard' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "list_data_type":"{{list_data_type}}", "from_date":"{{from_date}}", "to_date":"{{to_date}}", "groups":"{{groups}}"}'
  ````

<br/>



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMzAzMDUzMzYsMjEwNjQzMTIyLC00Mz
U5OTEyNDYsLTIwNDcwMjk4MiwyMDY5NDA3NTgxLC0yMzExNTAw
NzksLTE5MDc3NDA0NDQsLTE2NjEzNjU2NzgsLTcxNjQxNTE1OC
w2NDc5Mjk3NDAsLTEwNzI4NDYwMDddfQ==
-->