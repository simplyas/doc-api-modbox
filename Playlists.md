# Mod TV - Playlists

Este recurso permite aos equipamentos Modbox exibir programação personalizada em vídeo na TV.

- [Lista Playlist](Playlists.md#lista-playlists)
- [Nova Playlist](Playlists.md#nova-playlist)
- [Atualiza Playlist](Playlists.md#atualiza-playlist)
- [Deleta Playlist](Playlists.md#deleta-playlist)
----
<br/>


**Lista Playlists**
----
Retorna uma lista de playlists e suas configurações.

* **URL**

  {{api-url}}/requestPlaylists

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
	| 200 | ```{"label": "playlist 1000","playlist_token": "1602f718-910c-4a44-91c4-da60c606ce2c","random": "False","looping": "True","mute": "False","duration_live": "","instagram": "","rss": "","orientation": "0","led": "False","videowall": "False","files": ["5bf99754-b591-4ce8-a217-1a2d0040c272","5bf99754-b591-4ce8-a217-1a2d0040c272"],"terminals": ['06-00-00-00-00-00','06-00-00-00-00-00']}}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestPlaylists' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
  ````

<br/>


**Nova Playlist**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar nova playlist.

* **URL**

  {{api-url}}/submitPlaylist

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
	| random | Opcional | "True"/"False" |
	| looping | Opcional | "True"/"False" |
	| mute | Opcional | "True"/"False" |
	| orientation | Opcional | "0", "90", "180" ou "270" |
	| led | Opcional | "True"/"False" |
	| videowall | Opcional | "True"/"False" |
	| duration_live | Opcional |  |
	| instagram | Opcional |  |
	| rss | Opcional |  |
	| files | Opcional | Lista de arquivos ``` [["5bf99754-b591-4ce8-a217-1a2d0040c272","5bf99754-b591-4ce8-a217-1a2d0040c272"]] ``` |
	| terminals | Opcional | Lista de mac address de terminais para o videowall  ``` ["06-00-00-00-00-00","06-00-00-00-00-00"] ``` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Playlist criada com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 400 | `{"error":"O campo orientation aceita apenas: 0, 90, 180 ou 270."}` | 
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitPlaylist' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label": "{{label}}", "random": "{{random}}","looping": "{{looping}}","mute": "{{mute}}","duration_live": "{{duration_live}}","instagram": "{{instagram}}","rss": "{{rss}}","orientation": "{{orientation}}","led": "{{led}}", "videowall": "{{videowall}}", "files": [{{file_name}}],"terminals": ["{{mac_address}}"],"language":"{{language}}"}'````

<br/>

**Atualiza Playlist**
----
 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar uma playlist.

* **URL**

  {{api-url}}/updatePlaylist

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| playlist_token | Obrigatório | Token da playlist |
	| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
	| random | Opcional | "True"/"False" |
	| looping | Opcional | "True"/"False" |
	| mute | Opcional | "True"/"False" |
	| orientation | Opcional | "0", "90", "180" ou "270" |
	| led | Opcional | "True"/"False" |
	| videowall | Opcional | "True"/"False" |
	| duration_live | Opcional |  |
	| instagram | Opcional |  |
	| rss | Opcional |  |
	| files | Opcional | Lista de arquivos ``` [["5bf99754-b591-4ce8-a217-1a2d0040c272","5bf99754-b591-4ce8-a217-1a2d0040c272"]] ``` |
	| terminals | Opcional | Lista de mac address de terminais para o videowall  ``` ["06-00-00-00-00-00","06-00-00-00-00-00"] ``` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Playlist criada com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 400 | `{"error":"O campo orientation aceita apenas: 0, 90, 180 ou 270."}` | 
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Nenhuma playlist encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updatePlaylist' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","playlist_token":"{{playlist_token}}","label": "{{label}}", "random": "{{random}}","looping": "{{looping}}","mute": "{{mute}}","duration_live": "{{duration_live}}","instagram": "{{instagram}}","rss": "{{rss}}","orientation": "{{orientation}}","led": "{{led}}", "videowall": "{{videowall}}", "files": [{{file_name}}],"terminals": ["{{mac_address}}"],"language":"{{language}}"}'````

<br/>

**Deleta Playlist**
----
  Recebe requisição contendo a hash do contrato e o token da playlist para exclusão.

* **URL**

  {{api-url}}/deletePlaylist

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	
	| playlist_token | Obrigatório | Token da playlist |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhuma playlist encontrada."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deletePlaylist' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}","playlist_token":"{{playlist_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ5NjIzNjM1Ml19
-->