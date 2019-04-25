---
title: 'Error: RPC requiere autenticación | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102736"
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1. Ejecute `\` *windir*`\system32\regedt32.exe`  
  
2. Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3. Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4. Si el problema persiste, póngase en contacto con su administrador de dominio sobre la **configuración del equipo -> plantillas administrativas - > sistema -> Remote llamada a procedimiento -> restricciones para los clientes RPC no autenticadas** grupo configuración de directiva.
