---


---

<h1 id="apis-smartsuite-for-maos">APIs SmartSuite for maOS</h1>
<blockquote>
<p><em><strong>Informações importantes!</strong></em></p>
</blockquote>
<p><strong>1:</strong> As URLs tem de ser possível a alteração, devido a apontamentos de console de desenvolvimento, produção, e ambientes apartados.<br>
<strong>2:</strong> Assim como as URLs, o tenant tem de ser possível a alteração.<br>
<strong>3:</strong> O campo <strong>_ResourceGuid</strong> é um uuid v4.</p>
<p><strong>Ambiente DEV (BaseUri):</strong> <a href="https://dvp.azurewebsites.net/">https://dvp.azurewebsites.net/</a><br>
<strong>ID Tenant InnovaTech:</strong> 1</p>
<hr>
<blockquote>
<p><strong>1. API para obter as features ativas:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/features/get/{tenant_id_aqui}</p>
<blockquote>
<p><strong>StatusCodes</strong><br>
200: OK<br>
401: Unauthorized<br>
422: Unprocessable Entity</p>
</blockquote>
<p>Resultado:</p>
<pre><code>{
    "script_powershell": true,
    "script_wmi": false,
    "script_native": false,
    "checkpoint_client": true,
    "checkpoint_ssl": false,
    "fortclient_vpn": false,
    "cisco_client": false,
    "cisco_portal": false,
    "open_vpn": false,
    "speedtest": true,
    "altiris": false,
    "crowdstrike": false,
    "ivanti": false,
    "sccm": true,
    "sep": false,
    "bit_defender": true,
    "sentinel_one": false,
    "trend_apex": false,
    "windows_defender": false,
    "google_wifi": true,
    "server_a": "google.com.br.innova",
    "server_b": "google.com.br.innova",
    "server_c": "google.com.br.innova",
    "monday": true,
    "tuesday": true,
    "wednesday": true,
    "thursday": true,
    "friday": true,
    "saturday": false,
    "sunday": false,
    "days_collect": 100,
    "proofpoint": true
}
</code></pre>
<blockquote>
<p><strong>2. API para obter o token para autenticação nas APIs</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/authentication</p>
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
<p><strong>3. API para salvar dados de armazenamento/memória:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertstorage</p>
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
<p><strong>4. API para salvar dados históricos de armazenamento/memória:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertstoragehistory</p>
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
<p><strong>5. API para salvar dados de erros de sistema:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertbluescreen</p>
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
<p><strong>6. API para salvar dados de inventário lógico:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertinventory</p>
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
<p><strong>7. API para salvar dados de status dos serviços:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertservices</p>
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
<p>Baseado nos campos obtidos na API de features ativas, o agente deve verificar os status dos serviços (se for possível), e enviar se está:</p>
<p>Running<br>
Stopped<br>
N/A</p>
<p>E se possível, caminho de instalação, e se a instalação foi encontrada.</p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
   "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "ServiceEndpointState": {
    "type": "string",
    "nullable": true
  },
  "ServiceAvState": {
    "type": "string",
    "nullable": true
  },
  "ServiceDlpState": {
    "type": "string",
    "nullable": true
  },
  "ServiceVpnState": {
    "type": "string",
    "nullable": true
  },
  "InstallEndpointPath": {
    "type": "string",
    "nullable": true
  },
  "InstallAvPath": {
    "type": "string",
    "nullable": true
  },
  "InstallDlpPath": {
    "type": "string",
    "nullable": true
  },
  "InstallVpnPath": {
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
<p><strong>8. API para salvar dados de conectividade:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertconnectivity</p>
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
<p>Baseado nos campos obtidos na API de features ativas, o agente deve verificar os status da VPN, se está conectada ou não, e enviar:</p>
<p>true/false</p>
<p><em><strong>Se, os IPs obtidos na API de features para qualquer um do (server_a, server_b ou server_c), responder a ping, o teste de conectividade não deve ser realizado.</strong></em></p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "Download": {
    "type": "string",
    "nullable": false
  },
  "Upload": {
    "type": "string",
    "nullable": false
  },
  "PacketLoss": {
    "type": "string",
    "nullable": false
  },
  "Jitter": {
    "type": "string",
    "nullable": false
  },
  "Provider": {
    "type": "string",
    "nullable": false
  },
  "ConnectedVpn": {
    "type": "bool",
    "nullable": false
  },
  "LastDateRun": {
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
<p><strong>9. API para salvar dados históricos de conectividade:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/inserthistoryconnectivity</p>
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
<p>Baseado nos campos obtidos na API de features ativas, o agente deve verificar os status da VPN, se está conectada ou não, e enviar:</p>
<p>true/false</p>
<p><em><strong>Se, os IPs obtidos na API de features para qualquer um do (server_a, server_b ou server_c), responder a ping, o teste de conectividade não deve ser realizado.</strong></em></p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "Download": {
    "type": "string",
    "nullable": false
  },
  "Upload": {
    "type": "string",
    "nullable": false
  },
  "PacketLoss": {
    "type": "string",
    "nullable": false
  },
  "Jitter": {
    "type": "string",
    "nullable": false
  },
  "Provider": {
    "type": "string",
    "nullable": false
  },
  "ConnectedVpn": {
    "type": "bool",
    "nullable": false
  },
  "LastDateRun": {
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
<p><strong>10. API para salvar dados versão do agente:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertagentversion</p>
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
<p>Atualmente estamos na versão <strong>1.0.9.10.2024</strong></p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "AgentVersion": {
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
<p><strong>11. API para salvar dados de criptografia:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertcryptography</p>
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
<p>Baseado nos campos obtidos na API de features ativas, o agente deve verificar os status da criptografia (bitlocker), se for possível/compátivel.</p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "EncryptionMethod": {
    "type": "string",
    "nullable": false
  },
  "ProtectionStatus": {
    "type": "string",
    "nullable": false
  },
  "VolumeStatus": {
    "type": "string",
    "nullable": false
  },
  "DriveID": {
    "type": "string",
    "nullable": false
  },
  "RecoveryKey": {
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
<p><strong>12. API para salvar dados de performance do equipamento:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/insertperformance</p>
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
<p>O campo BootPerformane, se for possível no macOS, deve ser calculado do tempo de pré-boot e pós-boot (depois de logar).</p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>
<pre><code>{
  "_ResourceGuid": {
    "type": "string",
    "nullable": false
  },
  "ProcessorName": {
    "type": "string",
    "nullable": true
  },
  "NumberOfCores": {
    "type": "string",
    "nullable": true
  },
  "MaxClockSpeed": {
    "type": "string",
    "nullable": true
  },
  "CpuUsage": {
    "type": "string",
    "nullable": false
  },
  "RamUsage": {
    "type": "string",
    "nullable": false
  },
  "BootPerformance": {
    "type": "string",
    "nullable": false
  },
  "LastUpBootTime": {
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
<p><strong>12. API para salvar dados de performance do equipamento:</strong></p>
</blockquote>
<p><strong>URL:</strong> ${BaseUri}/api/v1/binary/save/inserthistoryperformance</p>
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
<p>O campo BootPerformane, se for possível no macOS, deve ser calculado do tempo de pré-boot e pós-boot (depois de logar).</p>
<p>Campos disponíveis no <strong>Body (JSON):</strong></p>

