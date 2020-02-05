---
title: Liberados e Bloqueados
author: Simply As

---

<h1 id="mod-wifi---liberados-e-bloqueados">Mod Wifi - Liberados e Bloqueados</h1>
<p>Este recurso permite aos gerenciar a liberação e bloqueios de dispositivos nos serviços de hostspot do contrato.</p>
<ul>
<li><a href="Devices.md#lista-rel%C3%B3gios">Lista Dispositivos</a></li>
<li><a href="Devices.md#novo-rel%C3%B3gio">Novo Dispositivo</a></li>
<li><a href="Devices.md#atualiza-rel%C3%B3gio">Atualiza Dispositivo</a></li>
<li><a href="Devices.md#deleta-rel%C3%B3gio">Deleta Dispositivo</a></li>
</ul>
<hr>
<br>
<h2 id="lista-dispositivos"><strong>Lista Dispositivos</strong></h2>
<p>Retorna uma lista de relógios e suas configurações.</p>
<ul>
<li>
<p><strong>URL</strong></p>
<p>{{api-url}}/requestClocks</p>
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
<td>Obrigatório</td>
<td>Token do usuário</td>
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
<td><code>{"clocks": [{"label": "CLOCK 1000","background_color": "1D1D1D","font_color": "FFFFFF","transparent": "False","screen_area": "0 90 20 100","screen_layer": "3","clock_token": "81c66760-d944-d695-3d1f-4dcab406606e"}]}</code></td>
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
<pre class=" language-curl"><code class="prism  language-curl">curl --request POST \
--url 'http://{{api-url}}/requestClocks' \
--header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
--header 'Content-Type: application/json' \
--data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
</code></pre>
</li>
</ul>
<br>
<h2 id="novo-dispositivo"><strong>Novo Dispositivo</strong></h2>
<p>Recebe requisição contendo a hash do contrato e propriedades para cadastrar novo relógio.</p>
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
<td>Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>Obrigatório</td>
<td>Token do usuário</td>
</tr>
<tr>
<td>label</td>
<td>Obrigatório</td>
<td>Identificação do recurso com no mínimo 1 e máximo 32 caracteres</td>
</tr>
<tr>
<td>background_color</td>
<td>Opcional</td>
<td>Formato de cor hexadecimal. Ex: “1D1D1D”</td>
</tr>
<tr>
<td>font_color</td>
<td>Opcional</td>
<td>Formato de cor hexadecimal. Ex: “FFFFFF”</td>
</tr>
<tr>
<td>transparent</td>
<td>Opcional</td>
<td>“True”/“False”</td>
</tr>
<tr>
<td>screen_area</td>
<td>Opcional</td>
<td>Ex: “0 90 20 100”</td>
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
<pre class=" language-curl"><code class="prism  language-curl">curl --request POST \
--url 'http://{{api-url}}/submitClock' \
--header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
--header 'Content-Type: application/json' \
--data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
</code></pre>
</li>
</ul>
<br>
<h2 id="atualiza-dispositivo"><strong>Atualiza Dispositivo</strong></h2>
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
<td>Obrigatório</td>
<td>Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>Obrigatório</td>
<td>Token do usuário</td>
</tr>
<tr>
<td>clock_token</td>
<td>Obrigatório</td>
<td>Token do relógio</td>
</tr>
<tr>
<td>label</td>
<td>Obrigatório</td>
<td>Identificação do recurso com no mínimo 1 e máximo 32 caracteres</td>
</tr>
<tr>
<td>background_color</td>
<td>Opcional</td>
<td>Formato de cor hexadecimal. Ex: “1D1D1D”</td>
</tr>
<tr>
<td>font_color</td>
<td>Opcional</td>
<td>Formato de cor hexadecimal. Ex: “FFFFFF”</td>
</tr>
<tr>
<td>transparent</td>
<td>Opcional</td>
<td>“True”/“False”</td>
</tr>
<tr>
<td>screen_area</td>
<td>Opcional</td>
<td>Ex: “0 90 20 100”</td>
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
<pre class=" language-curl"><code class="prism  language-curl">curl --request POST \
--url 'http://{{api-url}}/updateClock' \
--header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
--header 'Content-Type: application/json' \
--data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}","label":"{{label}}","background_color":"{{background_color}}","font_color":"{{font_color}}","transparent":"{{transparent}}","screen_area":"{{screen_area}}","screen_layer":"{{screen_layer}}","language":"{{language}}"}'
</code></pre>
</li>
</ul>
<br>
<h2 id="deleta-dispositivo"><strong>Deleta Dispositivo</strong></h2>
<p>Recebe requisição contendo a hash do contrato e o token da relógio para exclusão.</p>
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
<td>contract_hash</td>
<td>Obrigatório</td>
<td>Hash do contrato</td>
</tr>
<tr>
<td>user_token</td>
<td>Obrigatório</td>
<td>Token do usuário</td>
</tr>
<tr>
<td>clock_token</td>
<td>Obrigatório</td>
<td>Token do relógio</td>
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
<pre class=" language-curl"><code class="prism  language-curl">curl --request POST \
--url 'http://{{api-url}}/deleteClock' \
--header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
--header 'Content-Type: application/json' \
--data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","clock_token":"{{clock_token}}"'
</code></pre>
</li>
</ul>

