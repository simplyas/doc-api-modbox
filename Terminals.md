# Terminais

- [Lista Terminais](https://gist.github.com/mmprestes/97568ad3a621d5a4d4c98b9eafe7933a#lista-terminais)

----
<br/>


**Lista Terminais**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista de terminais e suas informações.

* **URL**

  {{api-url}}/requestTerminals

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| terminal_token | Opcional |   Retorna apenas o dispositivo |
	| locale_timezone | Opcional | Retorna o campo formatado (Fusos horários) |
	| locale_metric | Opcional | Versão da aplicação cliente |
	| locale_temperature | Opcional | Retorna o campo formatado (celcius ou fahrenheit) |
	| only_gps | Opcional | Retorna apenas dispositivos com GPS |
	| only_available | Opcional | Retorna apenas dispositivos sem grupo associado |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{ "terminals": [ { "name": "mbox-938", "status": "offline", "last_status": "1491686569", "color": "#AD4A4A","client": "software", "screen_size": "", "uptime": "", "version": "", "preference_icon": "", "internet_interface": "eth0","internet_macaddress": "36:4b:50:b7:ef:49", "internet_address": "191.191.142.3", "internet_download": "10 Mbit/s", "internet_uplad": "5 Mbit/s","local_address": "192.168.0.10" "dhcp": "True" "wifi_ssid": "" "wifi_signal": "" "wifi_quality": "" "wifi_clients": """temperature": "" "throttled": """latitude": "37.804005", "longitude": "-122.436809", "velocity": "", "altitude": "", "camera": "", "token": "490fb6dc-950c-4304-b02a-cecf0ce7a4c2", "group_token": "", "group_name": "", "timezone": "America/Sao_Paulo", "language": "en" } ] }``` |
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
  --data '{"contract_hash":"{{contract_hash}}","terminal_token":"{{terminal_token}}"}
  ```` 

