# Agendamento de Recursos

Este recurso permite definir agendamento para todos os módulos do Modbox. 

- [Lista Recursos](Resources.md#lista-recursos)
- [Novo Recurso](Resources.md#novo-recurso)
- [Atualiza Recurso](Resources.md#atualiza-recurso)
- [Deleta Recurso](Resources.md#deleta-recurso)
- [Reordena Recursos](Resources.md#reordena-recursos)
----
<br/>


**Lista Recursos**
----
Retorna uma lista de agendamentos do recurso selecionado.

* **URL**

  {{api-url}}/requestResources

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| resource | Obrigatório | Recurso deve ser: "playlist, "network", "clock", "logotype" ou "message" |
	| group_token | Obrigatório | Token do Grupo |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"network": [{"id_resource": "37","name": "WIFI B","token": "fd246d9c-30f0-4a90-928d-fa5d95fbfb77","is_active": "True","order": 1,"schedule": [{"days_week": ["seg","ter","qua","qui","sex","sab"],"day_in": "","day_out": "","time": ["08:00","12:00"]}]}}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` | 
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Nenhum grupo encontrado."}` |
	| 400 | `{"error":"Verifique o recurso informado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestResources' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}, {"resource":"{{resource}}", {"group_token":"{{group_token}}"}'
  ````

<br/>


**Novo Recurso**
----
 Recebe requisição contendo a hash do contrato, recurso, token do grupo e propriedades para cadastrar novo agendamento de recurso.

* **URL**

  {{api-url}}/submitResource

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| resource_token | Obrigatório | Token do recurso |
	| group_token | Obrigatório | Token do grupo |
	| resource | Obrigatório | Recurso deve ser: "playlist, "network", "clock", "logotype" ou "message"  |
	| schedule | Opcional | Json com agendamento ``` "schedule": [{"days_week": ["seg","ter","qui","sex","sab"],"day_in": "","day_out": "","time": ["08:00","12:00"]}] ``` |
	| order | Opcional | Ordem do agendamento no terminal |
	| is_active | Opcional | true / false |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!","resource_token":"3f7f681b-33b8-4595-82cc-41094a9333fc"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 400 | `{"error":"Nenhum grupo encontrado."}` |
	| 400 | `{"error":"Verifique o recurso informado."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitResource' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","contract_hash":"{{group_token}}","resource_token":"{{resource_token}}","resource":"{{resource}}","schedule":"{{schedule}}","order":"{{order}}","is_active":"{{is_active}}"}'
  ````

<br/>

**Atualiza Recurso**
----
 Recebe requisição contendo a hash do contrato, id do agendamento do recurso, recurso, token do grupo e propriedades para atualizar um agendamento de recurso.

* **URL**

  {{api-url}}/updateResource

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| token | Obrigatório | Token do agendamento do recurso |
	| resource | Obrigatório | Recurso deve ser: "playlist, "network", "clock", "logotype" ou "message" |
	| schedule | Opcional | Json com agendamento ``` "schedule": [{"days_week":["seg","ter","qui","sex","sab"],"day_in": "","day_out": "","time": ["08:00","12:00"]}] ``` |
	| order | Opcional | Ordem do agendamento no terminal |
	| is_active | Opcional | true / false |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 400 | `{"error":"Nenhum token encontrado."}` |
	| 400 | `{"error":"Nenhum agendamento encontrado."}` |
	| 400 | `{"error":"Verifique o recurso informado."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateResource' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","token":"{{token}}", "resource":"{{resource}}","schedule":"{{schedule}}","order":"{{order}}","is_active":"{{is_active}}"}'
  ````

<br/>

**Deleta Recurso**
----
  Recebe requisição contendo a hash do contrato, token do agendamento do recurso, recurso e token do grupo para deletar um agendamento de recurso.

* **URL**

  {{api-url}}/deleteResource

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| token | Obrigatório | Token do agendamento do recurso |
	| resource | Obrigatório | Recurso deve ser: "playlist, "network", "clock", "logotype" ou "message"  |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhum token encontrado."}`|
	| 402 | `{"error":"Nenhum agendamento encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteResource' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","token":"{{token}}","resource":"{{resource}}"}'
  ````

<br/>

**Reordena Recursos**
----
  Recebe requisição contendo a hash do contrato, lista de token do agendamento do recurso com a nova ordem, recurso e token do grupo reordenar os agendamentos.

* **URL**

  {{api-url}}/reorderResource

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| resource | Obrigatório | Recurso deve ser: "playlist, "network", "clock", "logotype" ou "message"  |
	| resources_list | Obrigatório | Lista de agendamentos ```` "resources":[{"token": "b2f1f9b7-52cd-5412-9ac0-c34x2aa64bf6","order": 0},{"token": "bec6532f-8e87-8379-bf8b-b869843g8dc6","order": 1},{"token": "19876e3e-faed-a0ab-10c3-fe67afc97a72","order": 2}] ````  |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhum token encontrado."}`|
	| 402 | `{"error":"Nenhum agendamento encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/reorderResource' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","resources":"{{resources}}","resource":"{{resource}}","resource":"{{resource}}","resources_list":"{{resources_list}}"}'
  ````

