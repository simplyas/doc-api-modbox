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
	| 200 | ``` "users": [{"name": "Marcelo Prestes","email": "marcelo.prestes@simplyas.com","level": "Administrator","menu_informative": "True","menu_connectivity": "True","id_rules": "10608"}``` |
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
 Recebe requisição contendo dados para cadastro (cria um novo usuário caso não exista) ou se informado o token do usuário atualiza as informações de preferências. Retorna uma senha aleatória para o novo usuário criado.

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
	| level | Obrigatório | Administrator ou Operator |
	| menu_informative | Opcional |True ou False |
	| menu_connectivity | Opcional | True ou False |
	| menu_monitoring | Opcional | True ou False |
	| menu_advertising | Opcional | True ou False |
	| menu_smartcamera | Opcional | True ou False |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"password":"ABC123"}` |
	| 200 | `{"message":"Acesso criado com sucesso!"}` |
	| 200 | `{"message":"Cadastro atualizado com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` 
	| 400 | `{"error":"Informe um nome completo."}` 
	| 400 | `{"error":"Informe um e-email correto."}` 
	| 400 | `{"error":"Informe o level do contrato (Administrator ou Operator)"}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Nenhum usuario encontrado."}`|
	| 404 | `{"error":"Usuario nao tem acesso no contrato."}`|
	| 409 | `{"error":"O usuario informado consta com acesso ativo neste contrato."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","name":"J. Random Loser","email":"test@simplyas.com","level":"Operator","menu_informative":"True","menu_connectivity":"False","menu_monitoring":"False","menu_advertising":"False","menu_smartcamera":"False"} ````

<br/>

**Atualiza Permissão**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar um relógio.

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
	| name | Obrigatório | Nome completo |
	| email | Obrigatório |  |
	| level | Obrigatório | Administrator ou Operator |
	| user_token | Opcional | Atualiza informações |
	| menu_informative | Opcional |True ou False |
	| menu_connectivity | Opcional | True ou False |
	| menu_monitoring | Opcional | True ou False |
	| menu_advertising | Opcional | True ou False |
	| menu_smartcamera | Opcional | True ou False |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"password":"ABC123"}` |
	| 200 | `{"message":"Acesso criado com sucesso!"}` |
	| 200 | `{"message":"Cadastro atualizado com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` 
	| 400 | `{"error":"Informe um nome completo."}` 
	| 400 | `{"error":"Informe um e-email correto."}` 
	| 400 | `{"error":"Informe o level do contrato (Administrator ou Operator)"}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 400 | `{"error":"Verifique os parametros enviados."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Nenhum usuario encontrado."}`|
	| 404 | `{"error":"Usuario nao tem acesso no contrato."}`|
	| 409 | `{"error":"O usuario informado consta com acesso ativo neste contrato."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}","user_token":"{{user_token}}","name":"{{name}}","email":"{{email}}","level":"{{level}}","menu_informative":"{{menu_informative}}","menu_connectivity":"{{menu_connectivity}}","menu_monitoring":"menu_monitoring","menu_advertising":"{{menu_advertising}}","menu_smartcamera":"{{menu_smartcamera}}"} ````
<br/>

**Deleta Permissão**
----
  Recebe requisição contendo a hash do contrato e o token da relógio para exclusão.

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
	| id_rules | Obrigatório | ID da permissão |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 402 | `{"error":"Nenhuma permissão encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteRule' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}","id_rules":"{{id_rules}}"'
  ````



