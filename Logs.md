# Logs de aplicativos

Os logs dos aplicativos são armazenados conforme tabela abaixo. Caso necessite de um período de armazenamento maior, crie uma rotina diaria de importação para a sua base de dados.

-   Informativo (video) 45 dias
-   Compartilhamento (wifi) 365 dias
-   Monitoramento (mgps) 45 dias

----
<br/>

**Logs**
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
  --url 'http://{{api-url}}/requestTerminals' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","module":"{{module}}","date_ini":"{{date_ini}}","date_end":"{{date_end}}","terminal_token":"{{terminal_token}}"}'
  ```` 
