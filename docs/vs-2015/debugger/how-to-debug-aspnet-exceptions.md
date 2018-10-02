---
title: 'Cómo: depurar excepciones de ASP.NET | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d37a67fd0b25de79ceb764e9e80884b97310a307
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574375"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Cómo: Depurar excepciones de ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar excepciones de ASP.NET](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-aspnet-exceptions).  
  
Depuración de excepciones es una parte importante de desarrollar una sólida [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación. Información general sobre cómo depurar excepciones es en [administrar excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar no controlada [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] excepciones, debe asegurarse de que el depurador se detenga en ellas. El runtime de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tiene un controlador de excepciones de nivel superior. Por consiguiente, el depurador nunca se interrumpe en excepciones no controladas de forma predeterminada. Para interrumpir el depurador cuando se produce una excepción, debe seleccionar **interrumpir cuando una excepción es: producida** para esa excepción específica en el **excepciones** cuadro de diálogo.  
  
 Si ha habilitado sólo mi código, **interrumpir cuando una excepción es: producida** no hace que el depurador se interrumpa inmediatamente si se produce una excepción en un método de .NET Framework u otro código del sistema. En su lugar, la ejecución continúa hasta que el depurador llega a código que no es del sistema y, a continuación, se interrumpe. Como resultado, no tiene que recorrer el código del sistema cuando se produce una excepción.  
  
 Solo mi código le ofrece otra opción que puede ser aun más útil: **interrumpir cuando una excepción es: User-unhandled**. Si elige esta configuración para una excepción, el depurador interrumpirá la ejecución en el código de usuario, pero solo si el código de usuario no detecta y controla la excepción. Esta configuración anula el efecto del controlador de excepciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de nivel superior, puesto que se encuentra en código que no es de usuario.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Para habilitar la depuración de las excepciones ASP.NET con Sólo mi código  
  
1.  En el **depurar** menú, haga clic en **excepciones**.  
  
     El **excepciones** aparece el cuadro de diálogo.  
  
2.  En el **excepciones de Common Language Runtime** fila, seleccione **producida** o **User-unhandled**.  
  
     Para usar el **User-unhandled** establecer, **solo mi código** debe estar habilitada...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Para llevar a cabo los procedimientos recomendados para el control de excepciones ASP.NET  
  
-   Sitúe los bloques `try … catch` alrededor del código susceptible de producir excepciones que pueda prever y sepa cómo controlar. Por ejemplo, si la aplicación realiza llamadas a un servicio Web XML o directamente a un servidor SQL Server, que el código debe estar en **try... catch** bloquea porque hay numerosas excepciones que pueden producirse.



