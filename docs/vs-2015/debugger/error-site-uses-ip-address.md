---
title: 'Error: Sitio usa la dirección IP | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e040c45079c9e4b82337cbd1e4b5d7d8306e1a32
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987954"
---
# <a name="error-site-uses-ip-address"></a>Error: Uso de dirección IP por parte del sitio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este error se produce cuando el depurador intenta asociarse automáticamente a una aplicación Web que utilice una dirección IP. Esto ocurre si se cambia **Identificación del sitio Web** a **Usar una dirección IP específica** en IIS.  
  
 Para que funcione la asociación automática, es preciso crear el proyecto con la dirección IP específica en lugar de hacerlo simplemente con el nombre del equipo. De lo contrario, el depurador cambiará el nombre de equipo a localhost, lo que generará un error al enviar el verbo de depuración a IIS.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Utilice la asociación manual (en el menú Depurar, elija **Asociar al proceso**).  
  
     -O bien-  
  
2.  Cambie el valor de configuración de **Identificación del sitio Web de IIS**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
