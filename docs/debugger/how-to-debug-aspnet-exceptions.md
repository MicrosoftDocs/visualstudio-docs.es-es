---
title: para depurar excepciones de ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 011094eed88245e3cd83b092a3f1b2e47bc77ae8
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852157"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedimiento Depuración de excepciones de ASP.NET
La depuración de excepciones es una parte importante del desarrollo de una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sólida. Encontrará información general sobre cómo depurar excepciones en [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).

 Para depurar excepciones no controladas de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe asegurarse de que el depurador se detenga en ellas. El runtime de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tiene un controlador de excepciones de nivel superior. Por consiguiente, el depurador nunca se interrumpe en excepciones no controladas de forma predeterminada. Para interrumpir el depurador cuando se produce una excepción, debe seleccionar la opción **Interrumpir cuando una excepción es: Producida** específica para esa excepción en el cuadro de diálogo **Excepciones**.

 Si ha habilitado Solo mi código, **Interrumpir cuando una excepción es: Producida** no hará que el depurador se interrumpa inmediatamente si se produce una excepción en un método de .NET Framework u otro código del sistema. En su lugar, la ejecución continúa hasta que el depurador llega a código que no es del sistema y, a continuación, se interrumpe. Como resultado, no tiene que recorrer el código del sistema cuando se produce una excepción.

 Solo mi código le ofrece otra opción que puede ser aún más útil: **Interrumpir cuando una excepción es: No controlada por el usuario**. Si elige esta configuración para una excepción, el depurador interrumpirá la ejecución en el código de usuario, pero solo si el código de usuario no detecta y controla la excepción. Esta configuración anula el efecto del controlador de excepciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de nivel superior, puesto que se encuentra en código que no es de usuario.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Para habilitar la depuración de las excepciones ASP.NET con Sólo mi código

1. En el menú **Depurar**, haga clic en **Excepciones**.

     Aparecerá el cuadro de diálogo **Excepciones**.

2. Seleccione **Producida** o **No controlada por el usuario**, en la fila **Excepciones de Common Language Runtime**.

     Para utilizar la configuración **No controlada por el usuario**, debe habilitar **Solo mi código**.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Para llevar a cabo los procedimientos recomendados para el control de excepciones ASP.NET

- Sitúe los bloques `try ... catch` alrededor del código susceptible de producir excepciones que pueda prever y sepa cómo controlar. Por ejemplo, si la aplicación realiza llamadas a un servicio Web XML o directamente a un servidor SQL Server, debería incluir ese código en los bloques **try ... catch** ya que ese código puede producir numerosas excepciones.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)