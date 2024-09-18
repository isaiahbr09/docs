---


---

<h1 id="apis-smartsuite-for-maos">APIs SmartSuite for maOS</h1>
<p><strong>OBS 1:</strong> As URLs tem de ser possível a alteração, devido a apontamentos de console de desenvolvimento, produção, e ambientes apartados.<br>
<strong>OBS 2:</strong> Assim como as URLs, o tenant tem de ser possível a alteração.</p>
<p><strong>Ambiente DEV (BaseUri):</strong> <a href="https://dvp.azurewebsites.net/api/v1/binary/save">https://dvp.azurewebsites.net/api/v1/binary/save</a><br>
<strong>ID Tenant InnovaTech:</strong> 1</p>
<hr>
<p><strong>1. API para obter o token para autenticação nas APIs</strong><br>
<strong>URL:</strong> ${BaseUri}/authentication</p>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>origin</strong>”</p>
<pre><code>headers = { 
    "origin": "agent"
}
</code></pre>
<hr>
<p><strong>2. API para salvar dados de armazenamento/memória:</strong><br>
<strong>URL:</strong></p>
<p>Em <strong>headers</strong>, adicionar o campo “<strong>authentication</strong>”</p>
<pre><code>headers = { 
    "authentication": "token_aqui"
}
</code></pre>
<p>Campos disponíveis no <strong>Body</strong></p>
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

