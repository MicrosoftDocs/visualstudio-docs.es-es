---
title: 'Error: RPC requiere autenticación | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e606c0e730b279723248a3fdbdd5b3e2bca1c4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574102"
---
# <a name="error-rpc-requires-authentication"></a>Error: RPC requiere autenticación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: RPC requiere autenticación](https://docs.microsoft.com/visualstudio/debugger/error-rpc-requires-authentication).  
  
El depurador de Visual Studio no se puede conectar al equipo remoto. Hay una directiva de RPC habilitada en el equipo local que evita la depuración remota.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Ejecute `\` *windir*`\system32\regedt32.exe`  
  
2.  Busque y elimine `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie el equipo para que el cambio del Registro surta efecto.  
  
4.  Si el problema persiste, póngase en contacto con su administrador de dominio sobre la **configuración del equipo -> plantillas administrativas - > sistema -> Remote llamada a procedimiento -> restricciones para los clientes RPC no autenticadas** grupo configuración de directiva.



