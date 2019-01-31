---
title: 'Error: Sitio usa la dirección IP | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8aa34553f4fb6d4524357f830dbbeabe3296354
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981121"
---
# <a name="error-site-uses-ip-address"></a>Error: Uso de dirección IP por parte del sitio
Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP. Esto ocurre si se cambia **Identificación del sitio Web** a **Usar una dirección IP específica** en IIS.  
  
 Para que funcione la asociación automática, es preciso crear el proyecto con la dirección IP específica en lugar de hacerlo simplemente con el nombre del equipo. De lo contrario, el depurador cambiará el nombre de equipo a localhost, lo que generará un error al enviar el verbo de depuración a IIS.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Utilice la asociación manual (en el menú Depurar, elija **Asociar al proceso**).  
  
     -O bien-  
  
2.  Cambie el valor de configuración de **Identificación del sitio Web de IIS**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)