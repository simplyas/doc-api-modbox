# Smartcam Presets

Pré-configurações dos módulos Smartcam.

----
**Pré-configurações**
----
Recebe requisição contendo a hash do contrato. Retorna uma lista com pre-configurações para configuração das smartcams.

* **URL**

  {{api-url}}/requestSmartcamPresets

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
	| 200 | ```{"smartcam_presets": [{"category": "Contador de Fluxo","label": "Contador de Pessoas 3 m","token": "322f889e-e4d6-4489-85c1-c421c0683f57"},{"category": "Detecção facial","label": "Contador de sorriso até 2 m","token": "322f889e-e4d6-4489-85c1-c421c0683f58"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhum contrato encontrado."}` | 
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestSmartcamPresets' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}"}'
  ```` 
