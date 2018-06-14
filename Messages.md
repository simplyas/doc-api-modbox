# Mod TV - Mensagens

Este recurso permite aos equipamentos Modbox exibir mensagens personalizadas (avisos curtos) na tela.

- [Lista Mensagens](Messages.md#lista-mensagens)
- [Nova Mensagem](Messages.md#nova-mensagem)
- [Atualiza Mensagem](Messages.md#atualiza-mensagem)
- [Deleta Mensagem](Messages.md#deleta-mensagem)
----
<br/>


**Lista Mensagens**
----
Retorna uma lista de mensagens (avisos curtos) e suas configurações.

* **URL**

  {{api-url}}/requestMessages

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash da mensagem |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{ "logos": [{"label": "MENSAGENS 01","image": "b79f9179287401b5cd123deced189887", "background_color": "1D1D1D","transparent": "True","extended": "False","screen_area": "80 90 100 100","screen_layer": "2","message_token": "47d6bdc1-b3d3-d3e8-a24d-7d88cfa612a1",""informations": ["Mensagem 01","Mensagem 02","Mensagem 03","Mensagem 04","Mensagem 05"]}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestMessage' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}'
  ````

<br/>


**Nova Mensagem**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar nova mensagem.

* **URL**

  {{api-url}}/submitMessage

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
	| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
	| transparent | Opcional | "True"/"False" |
	| screen_area | Opcional | Ex: "0 90 20 100" |
	| screen_layer | Opcional | Valor numérico. Ex: "3" |
	| informations | Obrigatório | Até 5 mensagens ```"informations": ["Mensagem 01","Mensagem 02","Mensagem 03","Mensagem 04","Mensagem 05"]```   |
	| language | Opcional |  |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitMessage' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","informations": ["Mensagem 01","Mensagem 02","Mensagem 03","Mensagem 04","Mensagem 05"],"language":"{{language}}"}'
  ````

<br/>

**Atualiza Mensagem**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar uma mensagem.

* **URL**

  {{api-url}}/updateMessage

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| message_token | Obrigatório | Token da mensagem |
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
	| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
	| transparent | Opcional | "True"/"False" |
	| screen_area | Opcional | Ex: "0 90 20 100" |
	| screen_layer | Opcional | Valor numérico. Ex: "3" |
	| informations | Obrigatório | De 1 até 5 mensagens  ```"informations": ["Mensagem 01","Mensagem 02","Mensagem 03","Mensagem 04","Mensagem 05"]```   |
	| language | Opcional |  |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Nenhuma mensagem encontradoa."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateMessage' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","message_token":"{{message_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","informations": ["Mensagem 01","Mensagem 02","Mensagem 03","Mensagem 04","Mensagem 05"],"language":"{{language}}"}'
  ````

<br/>

**Deleta Mensagem**
----
  Recebe requisição contendo a hash do contrato e o token da mensagem para exclusão.

* **URL**

  {{api-url}}/deleteMessage

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| message_token | Obrigatório | Token da mensagem |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhuma mensagem encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteMessage' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}","message_token":"{{message_token}}"'
  ````



