---
title: 'Error: No se puede ir automáticamente al servidor | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9d84f4c7f7f58ae980a266b436207c843926ae1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711740"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Error: No se puede ir al servidor automáticamente
El error reza como sigue:

 No se puede ir al servidor automáticamente. El depurador no recibió una notificación antes de que se ejecutase el procedimiento remoto

 Este error puede aparecer cuando intenta ir a un servicio Web (vea [Ejecutar paso a paso un servicio Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Puede producirse cuando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no se configura correctamente.

 Las posibles causas son:

- No se ha establecido la depuración en "true" en el archivo web.config de la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (vea [Modo de depuración en aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Se instaló una versión de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] después de instalar Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debe instalarse antes que Visual Studio. En Windows, seleccione **Panel de control > Programas y características** para reparar su instalación de Visual Studio.

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)