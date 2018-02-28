---
title: "Error: RPC requiere autenticación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 73cd474d415a49b6dd9075559d8618289b1b0d21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Ejecutar `\` *windir*`\system32\regedt32.exe`  
  
2.  Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4.  Si el problema continúa, póngase en contacto con su administrador de dominio sobre la **configuración del equipo > plantillas administrativas > sistema > llamada a procedimiento remoto > restricciones para clientes RPC no autenticados** directiva de grupo configuración de.