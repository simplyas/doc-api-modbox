# Mod Wifi - Liberados e Bloqueados

Este recurso permite aos equipamentos Modbox exibir um relógio personalizado na tela.

- [Lista Relógios](Clocks.md#lista-rel%C3%B3gios)
- [Novo Relógio](Clocks.md#novo-rel%C3%B3gio)
- [Atualiza Relógio](Clocks.md#atualiza-rel%C3%B3gio)
- [Deleta Relógio](Clocks.md#deleta-rel%C3%B3gio)
----
<br/>


**Lista Relógios**
----
Retorna uma lista de relógios e suas configurações.

* **URL**

  {{api-url}}/requestClocks

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
  --url 'http://{{api-url}}/requestClocks' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
  ````

<br/>


**Novo Relógio**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar novo relógio.

* **URL**

  {{api-url}}/submitClock

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
	| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
	| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
	| transparent | Opcional | "True"/"False" |
	| screen_area | Opcional | Ex: "0 90 20 100" |
	| screen_layer | Opcional | Valor numérico. Ex: "3" |
	| language | Opcional |  |

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
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
  ````

<br/>

**Atualiza Relógio**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar um relógio.

* **URL**

  {{api-url}}/updateClock

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| clock_token | Obrigatório | Token do relógio |
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
	| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
	| transparent | Opcional | "True"/"False" |
	| screen_area | Opcional | Ex: "0 90 20 100" |
	| screen_layer | Opcional | Valor numérico. Ex: "3" |
	| language | Opcional |  |

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
	| 404 | `{"error":"Nenhum token encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
  ````


<br/>

**Deleta Relógio**
----
  Recebe requisição contendo a hash do contrato e o token da relógio para exclusão.

* **URL**

  {{api-url}}/deleteClock

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| clock_token | Obrigatório | Token do relógio |
	
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
  --url 'http://{{api-url}}/deleteClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTYwNTE5Nl19
-->