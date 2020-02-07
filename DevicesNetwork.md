---
extensions:
  preset: commonmark

---

<h1 id="mod-tv---relógios">Mod TV - Relógios</h1>
<p>Este recurso permite aos equipamentos Modbox exibir um relógio personalizado na tela.</p>
<ul>
<li><a href="Clocks.md#lista-rel%C3%B3gios">Lista Relógios</a></li>
<li><a href="Clocks.md#novo-rel%C3%B3gio">Novo Relógio</a></li>
<li><a href="Clocks.md#atualiza-rel%C3%B3gio">Atualiza Relógio</a></li>
<li><a href="Clocks.md#deleta-rel%C3%B3gio">Deleta Relógio</a></li>
</ul>
<hr>
<br>
<h2 id="lista-relógios"><strong>Lista Relógios</strong></h2>
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
<p>| Parâmetro | Recurso | Observação |
|--|--|--|
| contract_hash | Obrigatório | Hash do contrato |
| user_token | Obrigatório | Token do usuário |</p>
</li>
<li>
<p><strong>Respostas:</strong></p>
<p>|Código| Resposta |
|--|--|
| 200 | <code>{"clocks": [{"label": "CLOCK 1000","background_color": "1D1D1D","font_color": "FFFFFF","transparent": "False","screen_area": "0 90 20 100","screen_layer": "3","clock_token": "81c66760-d944-d695-3d1f-4dcab406606e"}]}</code> |
| 400 | <code>{"error":"Verifique o JSON enviado."}</code> |
| 400 | <code>{"error":"Informe um hash correto."}</code> |
| 403 | <code>{"error":"Sem permissão ao recurso."}</code> |
| 400 | <code>{"error":"Verifique os parâmetros enviados."}</code> |
| 500 | <code>{"error":"Algo deu errado. Tente novamente."}</code> |</p>
</li>
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
<h2 id="novo-relógio"><strong>Novo Relógio</strong></h2>
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
<p>| Parâmetro | Recurso | Observação |
|--|--|--|
| contract_hash | Obrigatório | Hash do contrato |
| user_token | Obrigatório | Token do usuário |
| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
| transparent | Opcional | "True"/"False" |
| screen_area | Opcional | Ex: "0 90 20 100" |
| screen_layer | Opcional | Valor numérico. Ex: "3" |
| language | Opcional |  |</p>
</li>
<li>
<p><strong>Respostas:</strong></p>
<p>|Código| Resposta |
|--|--|
| 200 | <code>{"message":"Ajustes aplicados com sucesso!"}</code> |
| 400 | <code>{"error":"Informe uma hash correta."}</code>
| 400 | <code>{"error":"Verifique o JSON enviado."}</code> |
| 400 | <code>{"error":"Verifique os parâmetros enviados."}</code> |
| 403 | <code>{"error":"Sem permissão ao recurso."}</code> |
| 400 | <code>{"error":"Informe o label com 1 a 32 caracteres."}</code> |
| 404 | <code>{"error":"Nenhum contrato encontrado."}</code>|
| 500 | <code>{"error":"Algo deu errado. Tente novamente."}</code> |</p>
</li>
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
<p>| Parâmetro | Recurso | Observação |
|--|--|--|
| contract_hash | Obrigatório | Hash do contrato |
| user_token | Obrigatório | Token do usuário |
| clock_token | Obrigatório | Token do relógio |
| label | Obrigatório | Identificação do recurso com no mínimo 1 e máximo 32 caracteres |
| background_color | Opcional | Formato de cor hexadecimal. Ex: "1D1D1D" |
| font_color | Opcional | Formato de cor hexadecimal. Ex: "FFFFFF" |
| transparent | Opcional | "True"/"False" |
| screen_area | Opcional | Ex: "0 90 20 100" |
| screen_layer | Opcional | Valor numérico. Ex: "3" |
| language | Opcional |  |</p>
</li>
<li>
<p><strong>Respostas:</strong></p>
<p>|Código| Resposta |
|--|--|
| 200 | <code>{"message":"Ajustes aplicados com sucesso!"}</code> |
| 400 | <code>{"error":"Informe uma hash correta."}</code>
| 400 | <code>{"error":"Verifique o JSON enviado."}</code> |
| 400 | <code>{"error":"Verifique os parâmetros enviados."}</code> |
| 403 | <code>{"error":"Sem permissão ao recurso."}</code> |
| 400 | <code>{"error":"Informe o label com 1 a 32 caracteres."}</code> |
| 404 | <code>{"error":"Nenhum contrato encontrado."}</code>|
| 404 | <code>{"error":"Nenhum token encontrado."}</code>|
| 500 | <code>{"error":"Algo deu errado. Tente novamente."}</code> |</p>
</li>
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
<h2 id="deleta-relógio"><strong>Deleta Relógio</strong></h2>
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
<p>| Parâmetro | Recurso | Observação |
|--|--|--|
| contract_hash | Obrigatório | Hash do contrato |
| user_token | Obrigatório | Token do usuário |
| clock_token | Obrigatório | Token do relógio |</p>
</li>
<li>
<p><strong>Respostas:</strong></p>
<p>|Código| Resposta |
|--|--|
| 200 | <code>{"message":"Ajustes aplicados com sucesso!"}</code> |
| 400 | <code>{"error":"Verifique o JSON enviado."}</code> |
| 400 | <code>{"error":"Verifique os parâmetros enviados."}</code> |
| 403 | <code>{"error":"Sem permissão ao recurso."}</code> |
| 402 | <code>{"error":"Nenhum contrato encontrado."}</code>|
| 402 | <code>{"error":"Nenhum token encontrade."}</code>|
| 500 | <code>{"error":"Algo deu errado. Tente novamente."}</code> |</p>
</li>
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

