---
title: 'Error: RPC requiere autenticación | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f319ba24a52a99994e693774aa9e7c0db7757e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874412"
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Ejecute `\` *windir*`\system32\regedt32.exe`  
  
2.  Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4.  Si el problema persiste, póngase en contacto con su administrador de dominio sobre la **configuración del equipo > plantillas administrativas > sistema > llamada a procedimiento remoto > restricciones para los clientes RPC no autenticadas** directiva de grupo configuración de.