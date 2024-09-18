---


---

<h1 id="apis-smartsuite-for-maos">APIs SmartSuite for maOS</h1>
<blockquote>
<p><em><strong>Informações importantes!</strong></em></p>
</blockquote>
<p><strong>1:</strong> As URLs tem de ser possível a alteração, devido a apontamentos de console de desenvolvimento, produção, e ambientes apartados.<br>
<strong>2:</strong> Assim como as URLs, o tenant tem de ser possível a alteração.<br>
<strong>3:</strong> O campo <strong>_ResourceGuid</strong> é um uuid v4.</p>
<p><strong>Ambiente DEV (BaseUri):</strong> <a href="https://dvp.azurewebsites.net/api/v1/binary/save">https://dvp.azurewebsites.net/api/v1/binary/save</a><br>
<strong>ID Tenant InnovaTech:</strong> 1</p>
<hr>
<blockquote>
<p><strong>1. API para obter o token para autenticação nas APIs</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/authentication</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>origin</strong>”</p>
<pre><code>headers = { 
    "origin": "agent"
}
</code></pre>
<hr>
<blockquote>
<p><strong>2. API para salvar dados de armazenamento/memória:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/insertstorage</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication:</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": true
  },
  "MemorySize": {
    "type": "int",
    "nullable": true
  },
  "TotalSlots": {
    "type": "int",
    "nullable": true
  },
  "SlotsUsed": {
    "type": "int",
    "nullable": true
  },
  "DiskSize": {
    "type": "int",
    "nullable": true
  },
  "DiskFree": {
    "type": "int",
    "nullable": true
  },
  "HdModel": {
    "type": "string",
    "nullable": true
  },
  "HdSerial": {
    "type": "string",
    "nullable": true
  },
  "PowerOnHours": {
    "type": "int",
    "nullable": true
  },
  "EndToEndError": {
    "type": "string",
    "nullable": true
  },
  "UncorrectableError": {
    "type": "string",
    "nullable": true
  },
  "TemperatureDisk": {
    "type": "int",
    "nullable": true
  },
  "DiskType": {
    "type": "string",
    "nullable": true
  },
  "DiskHealth": {
    "type": "string",
    "nullable": true
  },
  "TenantId": {
    "type": "int",
    "nullable": false
  }
}
</code></pre>
<hr>
<blockquote>
<p><strong>3. API para salvar dados históricos de armazenamento/memória:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/insertstoragehistory</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication:</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": true
  },
  "MemorySize": {
    "type": "int",
    "nullable": true
  },
  "PowerOnHours": {
    "type": "int",
    "nullable": true
  },
  "TemperatureDisk": {
    "type": "int",
    "nullable": true
  },
  "DiskSize": {
    "type": "int",
    "nullable": true
  },
  "DiskType": {
    "type": "string",
    "nullable": true
  },
  "TenantId": {
    "type": "int",
    "nullable": false
  }
}
</code></pre>
<hr>
<blockquote>
<p><strong>4. API para salvar dados de erros de sistema:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/insertbluescreen</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication:</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "ErrorName": {
    "type": "string",
    "nullable": false
  },
  "ErrorCode": {
    "type": "string",
    "nullable": false
  },
  "ErrorDate": {
    "type": "string",
    "nullable": false
  },
  "ErrorOrigin": {
    "type": "string",
    "nullable": false
  },
  "CausedBy": {
    "type": "string",
    "nullable": false
  },
  "ErrorDescription": {
    "type": "string",
    "nullable": false
  },
  "Company": {
    "type": "string",
    "nullable": false
  },
  "TenantId": {
    "type": "int",
    "nullable": false
  }
}
</code></pre>
<hr>
<blockquote>
<p><strong>5. API para salvar dados de inventário lógico:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/insertinventory</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication:</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "ComputerName": {
    "type": "string",
    "nullable": false
  },
  "IpAddress": {
    "type": "string",
    "nullable": false
  },
  "MacAddress": {
    "type": "string",
    "nullable": false
  },
  "FQDN": {
    "type": "string",
    "nullable": false
  },
  "Domain": {
    "type": "string",
    "nullable": false
  },
  "CorporateID": {
    "type": "string",
    "nullable": false
  },
  "UserName": {
    "type": "string",
    "nullable": false
  },
  "Manufacturer": {
    "type": "string",
    "nullable": false
  },
  "Model": {
    "type": "string",
    "nullable": false
  },
  "SerialNumber": {
    "type": "string",
    "nullable": false
  },
  "ProductNumber": {
    "type": "string",
    "nullable": false
  },
  "EquipmentType": {
    "type": "string",
    "nullable": false
  },
  "Architecture": {
    "type": "string",
    "nullable": false
  },
  "OperatingSystem": {
    "type": "string",
    "nullable": false
  },
  "ReleaseId": {
    "type": "string",
    "nullable": false
  },
  "Build": {
    "type": "string",
    "nullable": false
  },
  "LastInventoryBasic": {
    "type": "DateTime",
    "nullable": false
  },
  "TenantId": {
    "type": "int",
    "nullable": false
  }
}
</code></pre>
<hr>
<blockquote>
<p><strong>6. API para salvar dados de erros de sistema:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/insertinventory</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication:</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>

