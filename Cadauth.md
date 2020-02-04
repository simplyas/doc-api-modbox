# Cadastro e autenticação

Etapa inicial, primeiro crie um usuário em seguida o contrato informando o token do usuário o qual será administrador do contrato.

Guarde em um local seguro os atributos "user_token" e "contract_hash" pois eles serão utilizados em quase todas as operações para validação. O "user_token" é renovado todas as vezes que acontece troca de senha.

- [Autenticação](Cadauth.md#-autentica%C3%A7%C3%A3o-)
- [Cadastra Usuário](Cadauth.md#cadastra-usu%C3%A1rio)
- [Atualiza Usuário](Cadauth.md#atualiza-usu%C3%A1rio)
- [Lista Permissões](Cadauth.md#lista-permiss%C3%B5es)
- [Nova Permissão](Cadauth.md#nova-permiss%C3%A3o)
- [Atualiza Permissão](Cadauth.md#atualiza-permiss%C3%A3o)
- [Deleta Permissão](Cadauth.md#deleta-permiss%C3%A3o)
----
<br/>


**Cadastra Usuário**
----
  Recebe requisição contendo dados para cadastro de novo usuário. Retorna o token do usuário criado.
  

* **URL**

  {{api-url}}/submitUser

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| name | Obrigatório | Nome do usuário  |
	| email | Obrigatório | E-mail do usuário  |
	| password | Obrigatório | Senha |
	| locale_language | Opcional |  |
	| locale_timezone | Obrigatório |  |
	| locale_temperature | Obrigatório |  |
	| locale_metric | Obrigatório |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"user_token":"3e1afbd8-aa5a-4a19-ba4b-0a6939c7074a","language": "en","timezone":"America/New_York","metric": "miles","temperature": "fahrenheit"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um nome completo."}` |
	| 400 | `{"error":"Informe uma senha a partir de 5 caracteres."}` |
	| 400 | `{"error":"Informe uma temperatura correta."}` |
	| 400 | `{"error":"Informe uma metrica correta."}` |
	| 400 | `{"error":"Informe uma linguagem correta."}` |
	| 400 | `{"error":"Informe um fuso horario correto."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 400 | `{"error":"Informe uma linguagem correta."}` |
	| 401 | `{"error":"O e-mail informado esta sendo utilizado, tente outro."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitUser' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"name":"{{name}}","email":"{{email}}","password":"{{password}}","locale_language":"{{language}}"}'
  ````

<br/>

**Atualiza Usuário**
----
  Recebe requisição contendo dados para atualização de um usuário. Retorna novo token quando a senha é alterada.

* **URL**

  {{api-url}}/updateUser

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| name | Obrigatório | Nome do usuário  |
	| email | Obrigatório | E-mail do usuário  |
	| password | Obrigatório | Senha |
	| locale_language | Opcional |  |
	| locale_timezone | Obrigatório |  |
	| locale_temperature | Obrigatório |  |
	| locale_metric | Obrigatório |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Cadastro atualizado com sucesso!"`|
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um nome completo."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 400 | `{"error":"Informe uma senha a partir de 5 caracteres."}` |
	| 400 | `{"error":"Informe uma temperatura correta."}` |
	| 400 | `{"error":"Informe uma metrica correta."}` |
	| 400 | `{"error":"Informe uma linguagem correta."}` |
	| 400 | `{"error":"Informe um fuso horario correto."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 400 | `{"error":"Nenhum cadastro encontrado."}` |
	| 400 | `{"error":"Informe uma linguagem correta."}` |
	| 401 | `{"error":"O e-mail informado esta sendo utilizado, tente outro."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateUser' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"user_token":"{{user_token}}","name":"{{name}}","email":"{{email}}","password":"{{password}}","locale_language":"{{language}}"}'
  ````

<br/>

** Autenticação **
-----
  Recebe as informações de login e retorna o token do usuário. Informe o parâmetro recover para recuperação de senha.

* **URL**

  {{api-url}}/submitLogin

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| email | Obrigatório | E-mail do usuário  |
	| password | Obrigatório | Senha |
	| recover | Opcional |  Recupera senha via email |


* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{ "user_token": "b4d093f0-a940-4c01-8f99-785a7b838125", "created_at": "1312182000" "name": "John Applesee", "language": "en" "timezone": "America/New_York" "metric": "miles" "temperature": "fahrenheit" }`|
	| 200 | `{"message":"Um link foi enviado para o e-mail informado."}`|
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe a sua senha."}` |
	| 400 | `{"error":"Informe um email correto."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 401 | `{"error":"Senha incorreta."}` |
	| 404 | `{"error":"E-mail inexistente."}` |
	| 409 | `{"error":"Um e-mail foi enviado. Procure na caixa de entrada e de spam pelo remetente noreply@simplyas.com"}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitUser' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '"email":"{{email}}","password":"{{password}}","recover":"{{recover}}"}'
  ````
	
<br/>

**Lista Permissões**
----
Retorna uma lista de usuários contendo privilégios e preferências dos usuários.

* **URL**

  {{api-url}}/requestRules

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ``` "users": [{"name": "Nome do Usuário","email": "usuario@email.com","access_devices": "False","access_locations":"access_connectivity": "False","access_administrative": "False","access_api": "False","token": "7fa4ce1b-11f1-41ee-8b3e-df8824d73004a"}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestRules' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}'
  ````

<br/>


**Nova Permissão**
----
 Recebe requisição contendo dados para cadastro de nova permissão para o usuário informado. Retorna uma senha aleatória para o novo usuário criado, caso este não exista.

* **URL**

  {{api-url}}/submitRule

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| name | Obrigatório | Nome completo |
	| email | Obrigatório |  |
	| access_devices | Opcional |True ou False |
	| access_locations | Opcional | True ou False |
	| access_informative | Opcional | True ou False |
	| access_connectivity | Opcional | True ou False |
	| access_administrative | Opcional | True ou False |
	| access_api | Opcional | True ou False |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Usuário criado com sucesso.","password":"ABC123"}` |
	| 200 | `{"message":"Acesso criado com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` 
	| 400 | `{"error":"Informe um nome completo."}` 
	| 400 | `{"error":"Informe um e-email correto."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","name":"J. Random Loser","email":"test@simplyas.com","access_devices":"True","access_locations":"False","access_informative":"False","access_connectivity":"False","access_api":"False"} ````

<br/>

**Atualiza Permissão**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar uma permissão.

* **URL**

  {{api-url}}/updateRule

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| rules_token | Obrigatório | Token da permissão |
	| access_devices | Opcional |True ou False |
	| access_locations | Opcional | True ou False |
	| access_informative | Opcional | True ou False |
	| access_connectivity | Opcional | True ou False |
	| access_administrative | Opcional | True ou False |
	| access_api | Opcional | True ou False |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Cadastro atualizado com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` 
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Usuario nao tem acesso no contrato."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","rules_token":"{{rules_token}}","access_devices":"True","access_locations":"False","access_informative":"False","access_connectivity":"False","access_api":"False"} ````
<br/>

**Deleta Permissão**
----
  Recebe requisição contendo a hash do contrato e o token da permissão para exclusão.

* **URL**

  {{api-url}}/deleteRule

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| rules_token | Obrigatório | Token da permissão |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 404 | `{"error":"Nenhum contrato encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}","rules_token":"{{rules_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgzMjIwMTU5LC01NTIxMjY4MzgsMTgzMj
IwMTU5XX0=
-->