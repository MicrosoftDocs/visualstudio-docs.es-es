---
title: 'Error: El equipo remoto no pudo iniciar comunicaciones DCOM | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377211f0ca7e4095da58b169f113689db9c7b41e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Error: El equipo remoto no ha podido iniciar comunicaciones DCOM
Se ha producido un error de DCOM cuando el equipo remoto ha intentado comunicarse con el equipo local. El equipo local es el equipo que está  
  
 ejecutando Visual Studio. Este error puede producirse por varias razones:  
  
-   El equipo local tiene habilitado un firewall.  
  
-   No funciona la autenticación de Windows desde el equipo remoto al equipo local.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Si el equipo local tiene habilitado Firewall de Windows, vea [depuración remota](../debugger/remote-debugging.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
2.  Para comprobar la autenticación de Windows, abra un recurso compartido de archivos en el equipo local desde el servidor remoto.  
  
3.  Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)