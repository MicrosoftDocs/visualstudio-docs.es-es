---
title: "Error: Sitio usa la dirección IP | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e6073fd88221e307b46a90173526876f2e2186d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-site-uses-ip-address"></a>Error: El sitio utiliza una dirección IP
Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP. Esto se produce si cambia **identificación del sitio Web** a **usar dirección IP específica** en IIS.  
  
 Para que funcione la asociación automática, es preciso crear el proyecto con la dirección IP específica en lugar de hacerlo simplemente con el nombre del equipo. De lo contrario, el depurador cambiará el nombre de equipo a localhost, lo que generará un error al enviar el verbo de depuración a IIS.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Utilice la asociación manual (en el menú Depurar, elija **adjuntar al proceso**).  
  
     -O bien-  
  
2.  Cambiar el **identificación del sitio Web de IIS** configuración.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)