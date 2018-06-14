

# Contratos

Lista os contratos do parceiro. Recebe requisição contendo dados para cadastro (incluindo o usuário administrador) ou atualiza as informações do contrato. Retorna a licença e a hash do contrato criado.

- [Lista Contratos](https://gist.github.com/mmprestes/359963067ff4875465f4ffee6fed00ec#lista-contratos)
- [Novo Contrato](https://gist.github.com/mmprestes/359963067ff4875465f4ffee6fed00ec#novo-contrato)
- [Atualiza Contrato](https://gist.github.com/mmprestes/359963067ff4875465f4ffee6fed00ec#atualiza-contrato)

----
<br/>


**Lista Contratos**
----
Retorna lista de todos os contratos administrados pelo usuários informado.

* **URL**

  {{api-url}}/requestContracts

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| user_token | Obrigatório | Token do usuário administrador |
	| status | Opcional | false: contratos desabilitados,  true: contratos habilitados  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"contracts": [{"company_name": "ACME S/A","company_token": "0e43067c-aa3e-479f-a0de-b5ac2fd3ba19","company_partner": "True","contract_name": "ACME MATRIZ","master": "False","activation_date": "2018-05-15","status": "False","contract_hash": "d6a11f9d-aa85-4f6b-be7c-233c3f5d8a1b","sms_gateway": "","sms_shorturl": "", "api_key": "MjMzYzNmNWM8YTFiOjJDNzT0MEVD", "storage": "0","licences": "0","licence_number": "7ebe2a44", "path": "526e88b2db624ed2324193ac3792f9fd","file_server": "xyz.fileserve.com","msg_server": "msg_server.com","level": "Administrator","map_latitude": "","map_longitude": "","map_type": "mapbox.streets","map_zoom": "12","map_refresh": "10","map_debug": "True","video_image": "10","video_live": "120","video_instagram": "nasa", "video_rss": "https://www.nasa.gov/rss/dyn/lg_image_of_the_day.rss", "wifi_time": "60","wifi_redirect": "http://google.com","menu_informative": "True", "menu_connectivity": "True"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um token de usuário correto."}` |
	| 400 | `{"error":"Não informe um hash para novo contrato."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 404 | `{"error":"Nenhum usuário foi encontrado."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestContracts' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"user_token":"{{user_token}}","status":"{{status}}"}'
  ````

<br/>


**Novo Contrato**
----
  Recebe requisição contendo dados para cadastro de um novo contrato. Retorna a hash e licença do contrato criado.

* **URL**

  {{api-url}}/submitContract

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| user_token | Obrigatório | Token do usuário administrador |
	| parent_token | Obrigatório | Token da empresa parceira |
	| name | Obrigatório | Nome da empresa do contrato |
	| language | Opcional | formato: "pt" |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"licence_number": "7ebe2j44","contract_hash": "d6a11f9d-aa45-4f6b-be7c-233c3f5d8a1b"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um token de parceiro correto."}` |
	| 400 | `{"error":"Informe um token de usuário correto."}` |
	| 400 | `{"error":"Informe um nome de empresa com mais de 3 caracteres."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 401 | `{"error":"O e-mail informado esta sendo utilizado, tente outro."}` |
	| 404 | `{"error":"Nenhum parceiro foi encontrado."}` |
	| 404 | `{"error":"Nenhum usuário foi encontrado."}` |
	| 409 | `{"error":"O contrato principal possui o mesmo nome. Escolha um nome diferente."}`
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitContract' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"user_token":"{{user_token}}","partner_token":"{{partner_token}}","name":"{{name}}","language":"{{language}}"}'
  ````

<br/>

**Atualiza Contrato**
----
  Recebe requisição contendo dados para atualização de um contrato. Ativa e desativa contrato.

* **URL**

  {{api-url}}/updateContract

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| user_token | Obrigatório | Token do usuário administrador |
	| parent_token | Obrigatório | Token da empresa parceira |
	| contract_hash | Obrigatório | Hash do contrato |
	| name | Opcional | Nome da empresa do contrato |
	| status | Opcional | true: habilitado, false: desabilitado |
	| language | Opcional | formato: "pt" |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"messagem": "Contrato atualizado com sucesso."}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um token de parceiro correto."}` |
	| 400 | `{"error":"Informe um token de usuário correto."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Informe um nome de empresa com mais de 3 caracteres."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateContract' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"user_token":"{{user_token}}","partner_token":"{{partner_token}}","contract_hash":"{{contract_hash}}","name":"{{name}}","status":"{{status}}","language":"{{language}}"}'
  ````



