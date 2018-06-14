# Mod TV - Playlists

Este recurso permite aos equipamentos Modbox exibir programação personalizada em vídeo na TV.

- [Lista Playlist](https://gist.github.com/mmprestes/e339a0cc7de14e6032fc4d0d454f5a08#lista-playlists)
- [Nova Playlist](https://gist.github.com/mmprestes/e339a0cc7de14e6032fc4d0d454f5a08#nova-playlist)
- [Atualiza Playlist](https://gist.github.com/mmprestes/e339a0cc7de14e6032fc4d0d454f5a08#atualiza-playlist)
- [Deleta Playlist](https://gist.github.com/mmprestes/e339a0cc7de14e6032fc4d0d454f5a08#deleta-playlist)
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

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"label": "playlist 1000","playlist_token": "1602f718-910c-4a44-91c4-da60c606ce2c","random": "False","looping": "True","mute": "False","duration_live": "","instagram": "","rss": "","orientation": "0","led": "False","videowall": "False","files": [{"file_name": "Cotações","token": "5bf99754-b591-4ce8-a217-1a2d0040c272","md5": "","description": "","creation_date": "","duration": "","url": "","image": "5bf99754-b591-4ce8-a217-1a2d0040c272","type": "content"}],"terminals": ['06-00-00-00-00-00','06-00-00-00-00-00']}}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestPlaylists' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}'
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
	| files | Opcional | Lista de arquivos ``` [{"file_name": "Cotações","token": "5bf99754-b591-4ce8-a217-1a2d0040c272","md5": "","description": "","creation_date": "","duration": "","url": "","image": "5bf99754-b591-4ce8-a217-1a2d0040c272","type": "content"}] ``` |
	| terminals | Opcional | Lista de mac address de terminais para o videowall  ``` ["06-00-00-00-00-00","06-00-00-00-00-00"] ``` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Playlist criada com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
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
  --data '{"contract_hash":"{{contract_hash}}","label": "{{label}}", "random": "{{random}}","looping": "{{looping}}","mute": "{{mute}}","duration_live": "{{duration_live}}","instagram": "{{instagram}}","rss": "{{rss}}","orientation": "{{orientation}}","led": "{{led}}", "videowall": "{{videowall}}", "files": [{"file_name": "{{file_name}}","token": "{{token}}","md5": "{{md5}}","description": "{{description}}","creation_date": "{{creation_date}}","duration": "{{duration}}","url": "{{url}}","image": "{{image}}","type": "{{type}}"}],"terminals": ["{{mac_address}}"],"language":"{{language}}"}'````

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
	| files | Opcional | Lista de arquivos ``` [{"file_name": "Cotações","token": "5bf99754-b591-4ce8-a217-1a2d0040c272","md5": "","description": "","creation_date": "","duration": "","url": "","image": "5bf99754-b591-4ce8-a217-1a2d0040c272","type": "content"}] ``` |
	| terminals | Opcional | Lista de mac address de terminais para o videowall  ``` ["06-00-00-00-00-00","06-00-00-00-00-00"] ``` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Playlist criada com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
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
  --data '{"contract_hash":"{{contract_hash}}","playlist_token":"{{playlist_token}}","label": "{{label}}", "random": "{{random}}","looping": "{{looping}}","mute": "{{mute}}","duration_live": "{{duration_live}}","instagram": "{{instagram}}","rss": "{{rss}}","orientation": "{{orientation}}","led": "{{led}}", "videowall": "{{videowall}}", "files": [{"file_name": "{{file_name}}","token": "{{token}}","md5": "{{md5}}","description": "{{description}}","creation_date": "{{creation_date}}","duration": "{{duration}}","url": "{{url}}","image": "{{image}}","type": "{{type}}"}],"terminals": ["{{mac_address}}"],"language":"{{language}}"}'````

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



