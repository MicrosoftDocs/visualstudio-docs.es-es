---
title: "Error: No se puede iniciar la comunicación DCOM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4aead8cd4396df540779fdeebec953859122fd47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Error: No se puede iniciar la comunicación con DCOM
Se ha producido un error de DCOM cuando el equipo local ha intentado comunicarse con el equipo remoto. Esto se debe a la presencia de un firewall en el servidor remoto o a un incumplimiento de la autenticación de Windows en el equipo remoto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Si el equipo remoto tiene habilitado Firewall de Windows, vea [depuración remota](../debugger/remote-debugging.md) para obtener instrucciones sobre cómo configurar el firewall para la depuración local.  
  
-   Para restaurar la autenticación de Windows, reinicie ambos equipos. Examine los registros de eventos en los equipos local y remoto para buscar errores Kerberos y póngase en contacto con los administradores de dominio para averiguar si existen problemas conocidos.  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)