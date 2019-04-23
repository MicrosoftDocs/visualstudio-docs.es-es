---
title: 'Error: RPC requiere autenticación | Documentos de Microsoft'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092011"
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Ejecute `\` *windir*`\system32\regedt32.exe`

2. Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Reinicie el equipo para que el cambio del Registro surta efecto.

4. Si el problema persiste, póngase en contacto con su administrador de dominio sobre la **configuración del equipo > plantillas administrativas > sistema > llamada a procedimiento remoto > restricciones para los clientes RPC no autenticadas** directiva de grupo configuración de.