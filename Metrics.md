# Métricas

Retorna dados das métricas do contrato.

----
<br/>

**Métricas**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista de terminais e suas informações.

* **URL**

  {{api-url}}/requestData

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| module | obrigatório |  Aplicativos diponíveis: video, wifi e mgps |
	| date_ini | Opcional | Filtro de data inicial (formato Unix epoch) |
	| date_end | Opcional | Filtro de data final (formato Unix epoch) |
	| terminal_token | Opcional | Retorna apenas o dispositivo |
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{ "logs": [ { "terminal_name":"modbox-01", "group_name":"teste", "module":"video", "log": [ { "date":"1491686569", "duration":"10.0", "file":"IMG_2750" } ] } ] }``` |
	| 200 | ```{ "logs": [ { "module":"mgps", "log": [ { "terminal_name":"modbox-01", "group_name":"teste", "date":"1491686569", "latitude":"-16.691355", "longitude":"-49.295645", "velocity":"80", "altitude":"150" } ] } ] }``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestData' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","module":"{{module}}","date_ini":"{{date_ini}}","date_end":"{{date_end}}","terminal_token":"{{terminal_token}}"}'
  ```` 
