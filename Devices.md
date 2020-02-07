# Mod WIFI - Liberados e Bloqueados

Este recurso permite gerenciar dispositivos no hotspot do contrato.

- [Lista Dispositivos](Clocks.md#lista-rel%C3%B3gios)
- [Novo Dispositivo](Clocks.md#novo-rel%C3%B3gio)
- [Atualiza Dispositivo](Clocks.md#atualiza-rel%C3%B3gio)
- [Deleta Dispositivo](Clocks.md#deleta-rel%C3%B3gio)
----
<br/>


**Lista Dispositivos**
----
Retorna uma lista de dispositivos e suas configurações.

* **URL**

  {{api-url}}/requestDevicesNetworks

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
	| 200 | ```{"clocks": [{"label": "CLOCK 1000","background_color": "1D1D1D","font_color": "FFFFFF","transparent": "False","screen_area": "0 90 20 100","screen_layer": "3","clock_token": "81c66760-d944-d695-3d1f-4dcab406606e"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestDevicesNetworks' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
  ````

<br/>


**Novo Dispositivo**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar novo dispositivo.

* **URL**

  {{api-url}}/submitDevicesNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| is_banned | Opcional | "True"/"False" |
	| phone_number | Opcional | Número do device |
	| mac_address | Opcional | Mac address do device |
	| groups | Obrigatório | Lista de localidades afetadas |
	| expires | Opcional | Tempo de expiração do device |
	| validity_after_activation | Opcional |  Tempo de que o device fica disponível após ativação |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label":"{{label}}","is_banned":"{{is_banned}}","phone_number":"{{phone_number}}","mac_address":"{{mac_address}}","groups":"{{groups}}","expires":"{{expires}}","validity_after_activation":"{{validity_after_activation}}"}'
  ````

<br/>

**Atualiza Dispositivo**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar um dispositivo.

* **URL**

  {{api-url}}/updateDevicesNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário | 
	| devices_network_token | Obrigatório | Token do dispositivo | 
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| groups | Obrigatório | Lista de localidades afetadas |
	| expires | Opcional | Tempo de expiração do device |
	| validity_after_activation | Opcional |  Tempo de que o device fica disponível após ativação |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 400 | `{"error":"A validade apos ativacao deve ser ate 604800 segundos (7 dias)."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label":"{{label}}","is_banned":"{{is_banned}}","phone_number":"{{phone_number}}","mac_address":"{{mac_address}}","groups":"{{groups}}","expires":"{{expires}}","validity_after_activation":"{{validity_after_activation}}"}'
  ````


<br/>

**Deleta Dispositivo**
----
  Recebe requisição contendo a hash do contrato e o token da relógio para exclusão.

* **URL**

  {{api-url}}/deleteDevicesNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| devices_network_token | Obrigatório | Token do device |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhum token encontrade."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteDevicesNetwork' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","devices_network_token":"{{devices_network_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbNzQyMTIyMzA2LC04MDE2ODE3MjldfQ==
-->