---
title: "C&#243;mo: Depurar excepciones de ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, excepciones"
  - "depurar [Visual Studio], excepciones de ASP.NET"
  - "excepciones, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar excepciones de ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La depuración de excepciones es una parte importante del desarrollo de una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sólida.  Puede obtener información general sobre cómo depurar excepciones en [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Para depurar excepciones no controladas de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe asegurarse de que el depurador se detenga en ellas.  El runtime de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tiene un controlador de excepciones de nivel superior.  Por consiguiente, el depurador nunca se interrumpe en excepciones no controladas de forma predeterminada.  Para interrumpir el depurador cuando se produce una excepción, debe seleccionar la configuración **Interrumpir cuando una excepción es: Producida** para esa excepción específica en el cuadro de diálogo **Excepciones** y .  
  
 Si ha habilitado Sólo mi código, **Interrumpir cuando una excepción es: Producida** no hará que el depurador se interrumpa inmediatamente si se produce una excepción en un método de .NET Framework u otro código del sistema.  En su lugar, la ejecución continúa hasta que el depurador llega a código que no es del sistema y, a continuación, se interrumpe.  Como resultado, no tiene que recorrer el código del sistema cuando se produce una excepción.  
  
 Sólo mi código le ofrece otra opción que puede ser aun más útil: **Interrumpir cuando una excepción es: No controlada por el usuario**.  Si elige esta configuración para una excepción, el depurador interrumpirá la ejecución en el código de usuario, pero solo si el código de usuario no detecta y controla la excepción.  Esta configuración anula el efecto del controlador de excepciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de nivel superior, puesto que se encuentra en código que no es de usuario.  
  
### Para habilitar la depuración de las excepciones ASP.NET con Sólo mi código  
  
1.  En el menú **Depurar**, haga clic en **Excepciones**.  
  
     Aparecerá el cuadro de diálogo **Excepciones**.  
  
2.  Seleccione **Producida** o **No controlada por el usuario**, en la fila **Excepciones de Common Language Runtime**.  
  
     Para utilizar la configuración **No controlada por el usuario**, debe habilitar **Solo mi código**.  
  
### Para llevar a cabo los procedimientos recomendados para el control de excepciones ASP.NET  
  
-   Sitúe los bloques `try … catch` alrededor del código susceptible de producir excepciones que pueda prever y sepa cómo controlar.  Por ejemplo, si la aplicación realiza llamadas a un servicio Web XML o directamente a un servidor SQL Server, debería incluir ese código en los bloques **try ... catch** ya que ese código puede producir numerosas excepciones.