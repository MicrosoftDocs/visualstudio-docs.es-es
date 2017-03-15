---
title: "Error: RPC requiere autenticaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Error: RPC requiere autenticaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El depurador de Visual Studio no se puede conectar al equipo remoto.  Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### Para corregir este error  
  
1.  Ejecute `\`*windir*`\system32\regedt32.exe`  
  
2.  Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4.  Si el problema continúa, póngase en contacto con su administrador de dominio sobre la configuración de la directiva de grupo Configuración del equipo\-\>Plantillas administrativas\-\>Sistema\-\>Llamada a procedimiento remoto\-\>Restricciones para clientes de RPC no autenticados.