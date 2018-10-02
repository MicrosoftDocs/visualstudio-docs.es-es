---
title: 'Error: No se puede ir automáticamente al servidor | Microsoft Docs'
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
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566358"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Error: No se puede ir al servidor automáticamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: no se puede automáticamente paso en el servidor](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server).  
  
El error reza como sigue:  
  
 No se puede ir al servidor automáticamente. El depurador no recibió una notificación antes de que se ejecutase el procedimiento remoto  
  
 Este error puede aparecer cuando intenta ir a un servicio Web (vea [Ejecutar paso a paso un servicio Web XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Puede producirse cuando [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no se configura correctamente.  
  
 Las posibles causas son:  
  
-   El archivo web.config para su [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación no establecido la depuración en "true" en (consulte [modo de depuración en aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Una versión de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se instaló después de instalar Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] debe instalarse antes que Visual Studio. Use el **Panel de control**de Windows, **Programas y características** para reparar su instalación de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)



