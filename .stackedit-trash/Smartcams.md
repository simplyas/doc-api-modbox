# Smartcams  
  

Este recurso permite aos equipamentos Modbox exibir executar um módulo Smartcam.  
  

- [Lista Smartcams](Smartcams.md#lista-smartcams)  
- [Nova Smartcam](Smartcams.md#nova-smartcam)  
- [Atualiza Smartcam](Smartcams.md#atualiza-smartcam)  
- [Deleta Smartam](Smartcams.md#deleta-smartcam)  

----  

<br/>  
  
  

**Lista Smartcams**  
----  

Retorna uma lista de smartcams e suas configurações.  
  

* **URL**  
  
 {{api-url}}/requestsSmartcams
  
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
 | 200 | ```{"smartcams":[{"label":"Contadordesorrisos","camera_source":"picamera","is_active":"True","debug_web":"True","debug_screen":"True","window_transparent":"True","window_position":"850,400,480,320","smartcam_token":"805470bc-121b-421e-89a9-0652166341c8","smartcam_preset_token":"322f889e-e4d6-4489-85c1-c421c0683f58","comments":"CaixaAbalcao"}``` |
 | 400 | `{"error":"Verifique o JSON enviado."}` |  
 | 400 | `{"error":"Informe um hash correto."}` |  
 | 400 | `{"error":"Verifique os parâmetros enviados."}` |  
 | 500 | `{"error":"Algo deu errado. Tente novamente."}` |  
  
* **Exemplo:**  
    
  ````curl  
	curl --request POST \  
  --url 'http://{{api-url}}/requestSmartcams' \  
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \  
  --header 'Content-Type: application/json' \  
  --data '{"contract_hash":"{{contract_hash}}"}'  
  ````  
  

<br/>  
  
  

**Nova Smartcam**  
----  

 Recebe requisição contendo a hash do contrato e propriedades para cadastrar nova Smartcam.  
  

* **URL**  
  
 {{api-url}}/submitSmartcam
  
* **Método HTTP:**  
  
  `POST`  
    
*  **Parâmetros na URL**  
  
 Nada   
  
* **Parâmetros**  
  
 | Parâmetro | Recurso | Observação |  
 |--|--|--|  
 | contract_hash | Obrigatório | Hash do contrato |  
 | smartcam_preset_token | Obrigatório | Token do preset |  
 | label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |  
 | debug_web | Opcional | Ativa/desativa visualização na web |  
 | debug_screen | Opcional | Ativa/desativa savisualizaçãoída na tela hdmi |  
 | window_transparent | Opcional | "True"/"False" |  
 | window_position | Opcional | Ex: "850,400,480,320" |  
 | is_active | Opcional | "True"/"False" |  
 | language | Opcional | "pt/en" |  
  
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
  --url 'http://{{api-url}}/submitSmartcam' \  
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \  
  --header 'Content-Type: application/json' \  
  --data '{"contract_hash":"{{contract_hash}}","smartcam_preset_token":"{{smartcam_preset_token}}","label":"{{label}}","debug_web":"{{debug_web}}","debug_screen":"{{debug_screen}}","window_transparent":"{{window_transparent}}","window_position":"{{window_position}}","is_active":"{{is_active}}","language":"{{language}}"}'  
  ````  
  

<br/>  
  
**Atualiza Smartcam**  
----  

 Recebe requisição contendo a hash do contrato, token e propriedades para atualizar uma Smartcam.  
  

* **URL**  
  
 {{api-url}}/updateSmartcam
  
* **Método HTTP:**  
  
  `POST`  
    
*  **Parâmetros na URL**  
  
 Nada   
  
* **Parâmetros**  
  
 | Parâmetro | Recurso | Observação |  
 |--|--|--|  
 | contract_hash | Obrigatório | Hash do contrato | 
 | smartcam_token | Obrigatório | Token da smartcam |  
 | smartcam_preset_token | Obrigatório | Token do preset |  
 | label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |  
 | debug_web | Opcional | Ativa/desativa visualização na web |  
 | debug_screen | Opcional | Ativa/desativa savisualizaçãoída na tela hdmi |  
 | window_transparent | Opcional | "True"/"False" |  
 | window_position | Opcional | Ex: "850,400,480,320" |  
 | is_active | Opcional | "True"/"False" |  
 | language | Opcional | "pt/en" |   
  
* **Respostas:**  
    
 |Código| Resposta |  
 |--|--|  
 | 200 | `{"message":"Ajustes aplicados com sucesso!"}` |  
 | 400 | `{"error":"Informe uma hash correta."}`    
 | 400 | `{"error":"Verifique o JSON enviado."}` |  
 | 400 | `{"error":"Verifique os parâmetros enviados."}` |  
 | 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |  
 | 404 | `{"error":"Nenhum contrato encontrado."}`|  
 | 404 | `{"error":"Nenhum token encontrado."}`|  
 | 500 | `{"error":"Algo deu errado. Tente novamente."}` |  
  
* **Exemplo:**  
    
  ````curl  
	curl --request POST \  
  --url 'http://{{api-url}}/updateSmartcam' \  
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \  
  --header 'Content-Type: application/json' \  
  --data '{"contract_hash":"{{contract_hash}}","smartcam_preset_token":"{{smartcam_preset_token}}","token_smartcam":"{{token_smartcam}}","label":"{{label}}","debug_web":"{{debug_web}}","debug_screen":"{{debug_screen}}","window_transparent":"{{window_transparent}}","window_position":"{{window_position}}","is_active":"{{is_active}}","language":"{{language}}"}'  
  ````  
  
  

<br/>  
  

**Deleta Smartcam**  
----  

 Recebe requisição contendo a hash do contrato e o token da Smartcam para exclusão.  
  

* **URL**  
  
 {{api-url}}/deleteSmartcam
  
* **Método HTTP:**  
  
  `POST`  
    
*  **Parâmetros na URL**  
  
 Nada   
  
* **Parâmetros**  
  
 | Parâmetro | Recurso | Observação |  
 |--|--|--|  
 | contract_hash | Obrigatório | Hash do contrato |  
 | smartcam_token | Obrigatório | Token da Smartcam |  
    
* **Respostas:**  
    
 |Código| Resposta |  
 |--|--|  
 | 200 | `{"message":"Ajustes aplicados com sucesso!"}` |  
 | 400 | `{"error":"Verifique o JSON enviado."}` |  
 | 400 | `{"error":"Verifique os parâmetros enviados."}` |  
 | 402 | `{"error":"Nenhum contrato encontrado."}`|  
 | 402 | `{"error":"Nenhum token encontrade."}`|  
 | 500 | `{"error":"Algo deu errado. Tente novamente."}` |  
  
* **Exemplo:**  
    
  ````curl  
	curl --request POST \  
  --url 'http://{{api-url}}/deleteSmartcam' \  
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \  
  --header 'Content-Type: application/json' \  
  --data '{{"contract_hash":"{{contract_hash}}","smartcam_token":"{{smartcam_token}}"'  
  ````  
  

<!--stackedit_data:
eyJoaXN0b3J5IjpbODgxMDAxMjgwXX0=
-->