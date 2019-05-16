---
title: Depuración de aplicaciones de ASP.NET y AJAX | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0645cd28e6124e31e19b03489661c6828799cf4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686743"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Depurar aplicaciones de ASP.NET y AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Depurar las aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] es similar a depurar un Windows Form o cualquier otra aplicación para Windows porque ambos tipos de aplicación implican controles y eventos. No obstante, hay también diferencias básicas entre ambos tipos de aplicación:  
  
- El seguimiento del estado es más complejo en una aplicación Web.  
  
- En una aplicación para Windows, el código que se va a depurar está principalmente en una única ubicación; en una aplicación web, el código puede estar en el cliente y en el servidor. Mientras que el código [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se encuentra por completo en el servidor, también podría haber código de JavaScript o de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] en el cliente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Preparar la depuración en ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Se describen los pasos necesarios para habilitar la depuración de las aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Depurar aplicaciones web](../debugger/debugging-web-applications.md)  
 Se explica cómo depurar una aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], incluidas las aplicaciones de script habilitadas para AJAX.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)  
 Se explica por qué Sólo mi código se debe habilitar para depurar excepciones de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Explica algunas técnicas y herramientas que pueden ayudarle a depurar su código AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Depure el código con más rapidez mediante IntelliTrace para registrar y revisar un historial del estado de la aplicación sin reiniciar la aplicación con tanta frecuencia. Puede ver información sobre los eventos y las llamadas que se producen durante la ejecución de la aplicación e iniciar la depuración desde esos puntos en el tiempo. Requiere Visual Studio Ultimate.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)
