---
title: 'Error: No se puede ir automáticamente al servidor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37298dcbb2443755136c4c57eb4633fcb3197a87
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849520"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Error: No se puede ir al servidor automáticamente
El error reza como sigue:  
  
 No se puede ir al servidor automáticamente. El depurador no recibió una notificación antes de que se ejecutase el procedimiento remoto  
  
 Este error puede aparecer cuando intenta ir a un servicio Web (vea [Ejecutar paso a paso un servicio Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Puede producirse cuando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no se configura correctamente.  
  
 Las posibles causas son:  
  
- No se ha establecido la depuración en "true" en el archivo web.config de la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (vea [Modo de depuración en aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- Se instaló una versión de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] después de instalar Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debe instalarse antes que Visual Studio. Para corregir este problema, use el Windows **Panel de Control > programas y características** para reparar la instalación de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)