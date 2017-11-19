---
title: "Error: RPC requiere autenticación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3431ee286787d99e8601fbed7cad3012ffcaf68e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Ejecutar `\` *windir*`\system32\regedt32.exe`  
  
2.  Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4.  Si el problema continúa, póngase en contacto con su administrador de dominio sobre la **configuración del equipo > plantillas administrativas > sistema > llamada a procedimiento remoto > restricciones para clientes RPC no autenticados** directiva de grupo configuración de.