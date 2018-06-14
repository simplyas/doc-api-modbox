# Configurações

- [Lista Configurações](https://gist.github.com/mmprestes/651414f9abaae61dd479a8c74357d0c0#lista-configura%C3%A7%C3%B5es)

----
<br/>


**Lista Configurações**
----
Recebe requisição contendo o token do terminal e informações adicionais. Retorna uma lista com todas as configurações definidas para o dispositivo.

* **URL**

  {{api-url}}/requestSettings

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| token | Obrigatório | token do terminal |
	| screen | Opcional |   Resolução da tela |
	| uptime | Opcional | Tempo ligado em segundos |
	| version | Opcional | Versão da aplicação cliente |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{ "settings": { "name": "mbox-938", "group": "14251171-7c35-4bca-9f73-1e80f99cc54b" } }``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um token correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestGroups' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"token":"{{terminal_token}}"}````

