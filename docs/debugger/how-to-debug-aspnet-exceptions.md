---
title: "Cómo: depurar excepciones de ASP.NET | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba38521b8d3d224d6544d95b947d5f0e29727c0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-aspnet-exceptions"></a>Cómo: Depurar excepciones de ASP.NET
Depuración de excepciones es una parte importante del desarrollo de una sólida [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación. Información general sobre cómo depurar excepciones está en [administrar excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar no controlada [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] excepciones, debe asegurarse de que el depurador se detenga en ellas. El runtime de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tiene un controlador de excepciones de nivel superior. Por consiguiente, el depurador nunca se interrumpe en excepciones no controladas de forma predeterminada. Para interrumpir el depurador cuando se produce una excepción, debe seleccionar **interrumpir cuando una excepción es: producida** para esa excepción específica en el **excepciones** cuadro de diálogo.  
  
 Si ha habilitado sólo mi código, **interrumpir cuando una excepción es: producida** no hará que el depurador se interrumpa inmediatamente si se produce una excepción en un método de .NET Framework u otro código del sistema. En su lugar, la ejecución continúa hasta que el depurador llega a código que no es del sistema y, a continuación, se interrumpe. Como resultado, no tiene que recorrer el código del sistema cuando se produce una excepción.  
  
 Sólo mi código le ofrece otra opción que puede ser aun más útil: **interrumpir cuando una excepción es: no controlada por el usuario**. Si elige esta configuración para una excepción, el depurador interrumpirá la ejecución en el código de usuario, pero solo si el código de usuario no detecta y controla la excepción. Esta configuración anula el efecto del controlador de excepciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de nivel superior, puesto que se encuentra en código que no es de usuario.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Para habilitar la depuración de las excepciones ASP.NET con Sólo mi código  
  
1.  En el **depurar** menú, haga clic en **excepciones**.  
  
     El **excepciones** aparece el cuadro de diálogo.  
  
2.  En el **excepciones de Common Language Runtime** fila, seleccione **producida** o **no controlada por el usuario**.  
  
     Para usar el **no controlada por el usuario** establecer, **solo mi código** debe estar habilitada...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Para llevar a cabo los procedimientos recomendados para el control de excepciones ASP.NET  
  
-   Sitúe los bloques `try ... catch` alrededor del código susceptible de producir excepciones que pueda prever y sepa cómo controlar. Por ejemplo, si la aplicación realiza llamadas a un servicio Web XML o directamente a un servidor SQL Server, que el código debe estar en **try... catch** se bloquea porque hay numerosas excepciones que se pueden producir.

## <a name="see-also"></a>Vea también
[Depurar aplicaciones ASP.](../debugger/how-to-enable-debugging-for-aspnet-applications.md)