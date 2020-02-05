# Mod WIFI - Compartilhamento Internet

Este recurso permite aos equipamentos modbox habilitar o compartilhamento de Internet (cabo ou modem USB) via hotspot Wi-Fi de forma autenticada e gerenciada.

Todos os equipamentos participantes do mesmo grupo que tenha este recurso habilitado, irão criar uma única rede Wi-Fi expandindo a área de cobertura do sinal.

- [Lista Redes](ModWIFI.md#lista-redes)
- [Nova Rede](ModWIFI.md#nova-rede)
- [Atualiza Rede](ModWIFI.md#atualiza-rede)
- [Deleta Rede](ModWIFI.md#delete-rede)
----
<br/>


**Lista Redes**
----
Retorna uma lista de redes e suas configurações.

* **URL**

  {{api-url}}/requestNetworks

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
	| 200 | ``` {"networks":[{"label":"WIFI","password","name":"WIFI","password":"","auth":"False","auth_url":"","wifi_banner":"fa5d95fbfb77fd246d9c928d","max_time":"60","filter":"low","deny_reauth":"False","redirect":"http://google.com.br","deny_networks":"True","deny_captive":"False","dhcp_beginning":"5","dhcp_ending":"254","dhcp_lease":"1h","bandwidth":"60","allow_devices":[],"deny_devices":[],"network_token":"fd246d9c-30f0-4a90-928d-fa5d95fbfb77"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestNetworks' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
  ````

<br/>


**Nova Rede**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar nova rede wifi.

* **URL**

  {{api-url}}/submitNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| label | Obrigatório | Identificação do recurso com no mínimo 5 e máximo 32 caracteres |
	| name | Obrigatório | Nome da Wi-Fi com no mínimo 5 e máximo 32 caracteres |
	| password | Opcional | Se informada, deve conter no mínimo 8 e máximo 64 caracteres |	
	| auth | Opcional | Autenticação Inteligente, desabilita a senha da Wi-Fi |	
	| auth_url | Opcional | URL personalizada para autenticação externa (solicite documentação) |	
	| deny_captive | Opcional | Customiza fluxo de autenticação (True ou False) |	
	| redirect | Opcional | Redireciona para um site após autenticação |	
	| max_time | Opcional | Limite de tempo de conexão, após desconecta o usuário (máximo 1440 minutos) |
	| bandwidth | Opcional | Percentual de internet disponibilizado na rede |		
	| deny_reauth | Opcional | Bloqueio de re-autenticação em intervalo de 24 horas (True or False) |	
	| filter | Opcional | Filtro de Internet (low, medium, high) |	
	| deny_networks | Opcional | Isola a rede Wi-Fi (True ou False) |	
	| dhcp_beginning | Opcional | Início da faixa de IP da rede Wi-Fi (de 2 até 254) |	
	| dhcp_ending | Opcional | Final da faixa de IP da rede Wi-Fi (de 2 até 254) |	
	| dhcp_lease | Opcional | Tempo para liberação dos IP's no DHCP (ex: 15m, 1h) |
	| wifi_banner | Opcional | Imagem de boas vindas do captive portal |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe uma URL correta."}` |
	| 400 | `{"error":"Informe o nome com 5 a 32 caracteres."}` |
	| 400 | `{"error":"Informe o label com 5 a 32 caracteres."}` |
	| 400 | `{"error":"Informe a senha com 8 a 64 caracteres."}` |
	| 400 | `{"error":"Informar um valor menor que 1440 minutos (24 horas)."}`|
	| 400 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitNetwork' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}", "label":"{{label}}", "name":"{{name}}","password":"{{password}}","auth":"{{auth}}","auth_url":"{{auth_url}}","deny_captive":"{{deny_captive}}","redirect":"{{redirect}}","max_time":"{{max_time}}","bandwidth":"{{bandwidth}}","deny_reauth":"{{deny_reauth}}","filter":"{{filter}}","deny_networks":"{{deny_networks}}","dhcp_beginning":"{{dhcp_beginning}}","dhcp_ending":"{{dhcp_ending}}","dhcp_lease":"{{dhcp_lease}}","wifi_banner":"{{wifi_banner}}","language":"{{language}}"}'
  ````

<br/>

**Atualiza Rede**
----
  Recebe requisição contendo dados para atualização de uma rede.

* **URL**

  {{api-url}}/updateNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| network_token | Obrigatório | Token da rede |
	| label | Obrigatório | Identificação do recurso com no mínimo 5 e máximo 32 caracteres |
	| name | Obrigatório | Nome da Wi-Fi com no mínimo 5 e máximo 32 caracteres |
	| password | Opcional | Se informada, deve conter no mínimo 8 e máximo 64 caracteres |	
	| auth | Opcional | Autenticação Inteligente, desabilita a senha da Wi-Fi |	
	| auth_url | Opcional | URL personalizada para autenticação externa (solicite documentação) |	
	| deny_captive | Opcional | Customiza fluxo de autenticação (True ou False) |	
	| redirect | Opcional | Redireciona para um site após autenticação |	
	| max_time | Opcional | Limite de tempo de conexão, após desconecta o usuário (máximo 1440 minutos) |	
	| bandwidth | Opcional | Percentual de internet disponibilizado na rede |	
	| deny_reauth | Opcional | Bloqueio de re-autenticação em intervalo de 24 horas (True or False) |	
	| filter | Opcional | Filtro de Internet (low, medium, high) |	
	| deny_networks | Opcional | Isola a rede Wi-Fi (True ou False) |	
	| dhcp_beginning | Opcional | Início da faixa de IP da rede Wi-Fi (de 2 até 254) |	
	| dhcp_ending | Opcional | Final da faixa de IP da rede Wi-Fi (de 2 até 254) |	
	| dhcp_lease | Opcional | Tempo para liberação dos IP's no DHCP (ex: 15m, 1h) |
	| wifi_banner | Opcional | Imagem de boas vindas do captive portal |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe uma URL correta."}` |
	| 400 | `{"error":"Informe o nome com 5 a 32 caracteres."}` |
	| 400 | `{"error":"Informe o label com 5 a 32 caracteres."}` |
	| 400 | `{"error":"Informe a senha com 8 a 64 caracteres."}` |
	| 400 | `{"error":"Informar um valor menor que 1440 minutos (24 horas)."}`|
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhuma rede encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateNetwork' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","network_token":"{{network_token}}", "label":"{{label}}", "name":"{{name}}","password":"{{password}}","auth":"{{auth}}","auth_url":"{{auth_url}}","deny_captive":"{{deny_captive}}","redirect":"{{redirect}}","max_time":"{{max_time}}","bandwidth":"{{bandwidth}}","deny_reauth":"{{deny_reauth}}","filter":"{{filter}}","deny_networks":"{{deny_networks}}","dhcp_beginning":"{{dhcp_beginning}}","dhcp_ending":"{{dhcp_ending}}","dhcp_lease":"{{dhcp_lease}}"},"wifi_banner":"{{wifi_banner}}"},"language":"{{language}}"}'
  ````

<br/>

**Delete Rede**
----
  Recebe requisição contendo a hash do contrato e o token da rede para exclusão.

* **URL**

  {{api-url}}/deleteNetwork

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| network_token | Obrigatório | Token da rede |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhuma rede encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteNetwork' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","network_token":"{{network_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbNDIwNTc0ODgwXX0=
-->