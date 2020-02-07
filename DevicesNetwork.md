---
title: Liberados e Bloqueados
author: Simply As

---

<h1 id="mod-wifi---liberados-e-bloqueados">Mod WIFI - Liberados e Bloqueados</h1>
<p>Este recurso permite liberar e bloquear dispositivos no serviço hotspot do contrato.</p>
<ul>
<li><a href="Clocks.md#lista-rel%C>Lista Dis></li>
<li><a href="Clocks.md#novo-rel%C3%B3gio">Novo Dispositivo</a></li>
<li><a href="Clocks.md#atualiza-rel%C3%B3gio">Atualiza Dispositivo</a></li>
<li><a href="Clocks.md#deleta-rel%C3%B3gio">Deleta Dispositivo </a></li>
</ul>
<hr># Mod TV - Relógios

Este recurso permite aos equipamentos Modbox exibir um relógio personalizado na tela.

- [Lista Relógios](Clocks.md#lista-rel%C3%B3gios)
- [Novo Relógio](Clocks.md#novo-rel%C3%B3gio)
- [Atualiza Relógio](Clocks.md#atualiza-rel%C3%B3gio)
- [Deleta Relógio](Clocks.md#deleta-rel%C3%B3gio)
----
<br/>
<h2 id="lista-dispositivos"><strong>Lista Dispositivos</strong></h2>
<p>

**Lista Retorna uma lista de relógios e suas configurações.</p>
<ul>
<li>
<p><strong>URL</strong></p>
<p>{{api-url}}/requestDevicesNetworks</p>
</li>
<li>
<p><strong>Método HTTP:</strong></p>
<p><code>POST</code></p>
</li>
<li>
<p><strong>Parâmetros na URL</strong></p>
<p>Nada</p>
</li>
<li>
<p><strong>Parâmetros</strong></p>

<table>
<thead>
<tr>
<th>Parâmetro</th>
<th>Recurso</th>
<th>Observação</th>
</tr>
</thead>
<tbody>
<tr>
<td>contract_hash</td>
<td>Obrigatório</td>
<td>Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>ObrigatórioToken do usuário</td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Respostas:</strong></p>

<table>
<thead>
<tr>
<th>Código</th>
<th>Resposta</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><code>{"clocks": [{"label": "CLOCK 1000","background_color": 1D1D1D": FFFFFFt": "False 90 20 100","screen_layer": "3","clock_token": "81c66760-d944-d695-3d1f-4dcab406606e"}]}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique o JSON enviado."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Informe um hash correto."}</code></td>
</tr>
<tr>
<td>403</td>
<td><code>{"error":"Sem permissão ao recurso."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique os parâmetros enviados."}</code></td>
</tr>
<tr>
<td>500</td>
<td><code>{"error":"Algo deu errado. Tente novamente."}</code></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Exemplo:</strong></p>
<pre class=" language-curl"><code class="prism  language-curl --request POST \
--url 'http://{{api-url}}/requestClocks' \
--header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
--header 'Content-Type: application/json' \
--data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
</code></pre>
</li>
</ul>  ````

<br/>
<h2 id="novo-relógio"><strong>Novo Relógio</strong></h2>
<p>

**Novo Recebe requisição contendo a hash do contrato e propriedades para cadastrar novo relógio.</p>
<ul>
<li>
<p><strong>URL</strong></p>
<p>{{api-url}}/submitClock</p>
</li>
<li>
<p><strong>Método HTTP:</strong></p>
<p><code>POST</code></p>
</li>
<li>
<p><strong>Parâmetros na URL</strong></p>
<p>Nada</p>
</li>
<li>
<p><strong>Parâmetros</strong></p>

<table>
<thead>
<tr>
<th>Parâmetro</th>
<th>Recurso</th>
<th>Observação</th>
</tr>
</thead>
<tbody>
<tr>
<td>contract_hash</td>
<td>Obrigatório</td>
<td> | Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>Obrigatório</td>
<td>Token do usuário</td>
</tr>
<tr>
<td>label</td>
<td>Obrigatório</td>
<td> | Identificação do recurso com no mínimo 1 e máximo 32 caracteres</td>
</tr>
<tr>
<td>background_color</td>
<td>Opcional</td>
<td>Formato de cor hexadecimal. Ex: “"1D1D1D”</td>
</tr>
<tr>
<td>font_color</td>
<td>Opcional</td>
<td>r |Formato de cor hexadecimal. Ex: “"FFFFFF”</td>
</tr>
<tr>
<td>transparent</td>
<td>Opcional</td>
<td>“" |
	| transparenTrue"/"False”</td>
</tr>
<tr>
<td>screen_area</td>
<td>Opcional</td>
<td>Ex: "0 90 20 100”</td>
</tr>
<tr>
<td>screen_layer</td>
<td>Opcional</td>
<td>Valor numérico. Ex: “3”</td>
</tr>
<tr>
<td>language</td>
<td>Opcional</td>
<td></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Respostas:</strong></p>

<table>
<thead>
<tr>
<th>Código</th>
<th>Resposta</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><code>{"message":"Ajustes aplicados com sucesso!"}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Informe uma hash correta."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique o JSON enviado."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique os parâmetros enviados."}</code></td>
</tr>
<tr>
<td>403</td>
<td><code>{"error":"Sem permissão ao recurso."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Informe o label com 1 a 32 caracteres."}</code></td>
</tr>
<tr>
<td>404</td>
<td><code>{"error":"Nenhum contrato encontrado."}</code></td>
</tr>
<tr>
<td>500</td>
<td><code>{"error":"Algo deu errado. Tente novamente."}</code></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Exemplo:</strong></p>
<pre class=" language-curl"><code class="prism  language-curl --request POST \
  --url 'http://{{api-url}}/submitClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
</code></pre>
</li>
</ul>
<br>
<h2 id="atualiza-relógio"><strong>Atualiza Relógio</strong></h2>
<p>Recebe requisição contendo a hash do contrato, token e propriedades para atualizar um relógio.</p>
<ul>
<li>
<p><strong>URL</strong></p>
<p>{{api-url}}/updateClock</p>
</li>
<li>
<p><strong>Método HTTP:</strong></p>
<p><code>POST</code></p>
</li>
<li>
<p><strong>Parâmetros na URL</strong></p>
<p>Nada</p>
</li>
<li>
<p><strong>Parâmetros</strong></p>

<table>
<thead>
<tr>
<th>Parâmetro</th>
<th>Recurso</th>
<th>Observação</th>
</tr>
</thead>
<tbody>
<tr>
<td>contract_hash</td>
<td> | Obrigatório</td>
<td> | Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>Obrigatório</td>
<td> | Token do usuário</td>
</tr>
<tr>
<td> |
	| clock_token</td>
<td> | Obrigatório</td>
<td> | Token do relógio</td>
</tr>
<tr>
<td>label</td>
<td> |
	| label | Obrigatório</td>
<td> | Identificação do recurso com no mínimo 1 e máximo 32 caracteres</td>
</tr>
<tr>
<td>background_color</td>
<td>Opcional</td>
<td> |
	| background_color | Opcional | Formato de cor hexadecimal. Ex: “"1D1D1D”</td>
</tr>
<tr>
<td>font_color</td>
<td>Opcional</td>
<td>" |
	| font_color | Opcional | Formato de cor hexadecimal. Ex: “"FFFFFF”</td>
</tr>
<tr>
<td>transparent</td>
<td>Opcional</td>
<td>“" |
	| transparent | Opcional | "True”/“"/"False”</td>
</tr>
<tr>
<td>screen_area</td>
<td>Opcional</td>
<td>" |
	| screen_area | Opcional | Ex: “"0 90 20 100”</td>
</tr>
<tr>
<td>screen_layer</td>
<td>Opcional</td>
<td>Valor numérico. Ex: “3”</td>
</tr>
<tr>
<td>language</td>
<td>Opcional</td>
<td></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Respostas:</strong></p>

<table>
<thead>
<tr>
<th>Código</th>
<th>Resposta</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><code>{"message":"Ajustes aplicados com sucesso!"}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Informe uma hash correta."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique o JSON enviado."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique os parâmetros enviados."}</code></td>
</tr>
<tr>
<td>403</td>
<td><code>{"error":"Sem permissão ao recurso."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Informe o label com 1 a 32 caracteres."}</code></td>
</tr>
<tr>
<td>404</td>
<td><code>{"error":"Nenhum contrato encontrado."}</code></td>
</tr>
<tr>
<td>404</td>
<td><code>{"error":"Nenhum token encontrado."}</code></td>
</tr>
<tr>
<td>500</td>
<td><code>{"error":"Algo deu errado. Tente novamente."}</code></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Exemplo:</strong></p>
<pre class=" language-curl"><code class="prism  language-" |
	| screen_layer | Opcional | Valor numérico. Ex: "3" |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` 
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 1 a 32 caracteres."}` |
	| 404 | `{"error":"Nenhum contrato encontrado."}`|
	| 404 | `{"error":"Nenhum token encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl">
	curl --request POST \
  --url 'http://{{api-url}}/updateClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
</code></pre>
</li>
</ul>  ````


<br/>
<h2 id="deleta-relógio"><strong>Deleta Relógio</strong></h2>
<p>
**Deleta Relógio**
----
  Recebe requisição contendo a hash do contrato e o token da relógio para exclusão.</p>
<ul>
<li>
<p><strong>URL</strong></p>
<p>{{api-url}}/deleteClock</p>
</li>
<li>
<p><strong>Método HTTP:</strong></p>
<p><code>POST</code></p>
</li>
<li>
<p><strong>Parâmetros na URL</strong></p>
<p>Nada</p>
</li>
<li>
<p><strong>Parâmetros</strong></p>

<table>
<thead>
<tr>
<th>Parâmetro</th>
<th>Recurso</th>
<th>Observação</th>
</tr>
</thead>
<tbody>
<tr>
<td>

* **URL**

  {{api-url}}/deleteClock

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash</td>
<td> | Obrigatório</td>
<td> | Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td> |
	| user_token | Obrigatório</td>
<td> | Token do usuário</td>
</tr>
<tr>
<td> |
	| clock_token</td>
<td> | Obrigatório</td>
<td> | Token do relógio</td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Respostas:</strong></p>

<table>
<thead>
<tr>
<th>Código</th>
<th>Resposta</th>
</tr>
</thead>
<tbody>
<tr>
<td>200</td>
<td><code>{"message":"Ajustes aplicados com sucesso!"}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique o JSON enviado."}</code></td>
</tr>
<tr>
<td>400</td>
<td><code>{"error":"Verifique os parâmetros enviados."}</code></td>
</tr>
<tr>
<td>403</td>
<td><code>{"error":"Sem permissão ao recurso."}</code></td>
</tr>
<tr>
<td>402</td>
<td><code>{"error":"Nenhum contrato encontrado."}</code></td>
</tr>
<tr>
<td>402</td>
<td><code>{"error":"Nenhum token encontrade."}</code></td>
</tr>
<tr>
<td>500</td>
<td><code>{"error":"Algo deu errado. Tente novamente."}</code></td>
</tr>
</tbody>
</table></li>
<li>
<p><strong>Exemplo:</strong></p>
<pre class=" language-curl"><code class="prism  language-curl"> |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhum token encontrade."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteClock' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}"'
</code></pre>
</li>
</ul>  ````



<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoiZXh0ZW5zaW9uczpcbiAgcHJlc2V0Oi
Bjb21tb25tYXJrXG4iLCJoaXN0b3J5IjpbMTM3NjcyNDQ0Ml19

-->