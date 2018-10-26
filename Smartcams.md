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
 | 200 | ```{"clocks": [{"label": "CLOCK 1000","background_color": "1D1D1D","font_color": "FFFFFF","transparent": "False","screen_area": "0 90 20 100","screen_layer": "3","clock_token": "81c66760-d944-d695-3d1f-4dcab406606e"}]}``` |  
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
 | 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |  
 | 404 | `{"error":"Nenhum contrato encontrado."}`|  
 | 500 | `{"error":"Algo deu errado. Tente novamente."}` |  
  
* **Exemplo:**  
    
  ````curl  
	curl --request POST \  
  --url 'http://{{api-url}}/submitSmartcam' \  
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \  
  --header 'Content-Type: application/json' \  
  --data '{"contract_hash":"{{contract_hash}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'  
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
  --data '{"contract_hash":"{{contract_hash}}","clock_token":"{{clock_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'  
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
  

