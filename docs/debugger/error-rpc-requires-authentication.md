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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850460"
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Ejecute `\`*windir*`\system32\regedt32.exe`.

2. Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Reinicie el equipo para que el cambio del Registro surta efecto.

4. Si el problema continúa, póngase en contacto con el administrador del dominio con referencia a la configuración de la directiva de grupo **Configuración del equipo > Plantillas administrativas > Sistema > Llamada a procedimiento remoto > Restricciones para clientes de RPC no autenticados**.