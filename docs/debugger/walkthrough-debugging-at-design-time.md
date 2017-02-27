---
title: "Tutorial: Depurar en tiempo de dise&#241;o | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "puntos de interrupción, depuración en tiempo de diseño"
  - "depurar [Visual Studio], en tiempo de diseño"
  - "depuración en tiempo de diseño"
  - "Inmediato (ventana), depuración en tiempo de diseño"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Tutorial: Depurar en tiempo de dise&#241;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la ventana **Inmediato** de Visual Studio para ejecutar una función o subrutina mientras su aplicación no se está ejecutando.  Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpirá la ejecución en el punto adecuado.  A continuación puede utilizar las ventanas del depurador para examinar el estado del programa.  Esta característica se denomina depuración en tiempo de diseño.  
  
 El siguiente procedimiento muestra cómo puede utilizar esta característica.  
  
### Para establecer los puntos de interrupción en la ventana Inmediato  
  
1.  Pegue el siguiente código en una aplicación de consola de Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Establezca un punto de interrupción en la línea `s="Add BreakPoint Here"`.  
  
3.  Escriba lo siguiente en la ventana **Inmediato**: `?MyFunction<enter>`  
  
4.  Compruebe que se ha alcanzado el punto de interrupción, y que la pila de llamadas es exacta.  
  
5.  En el menú **Depurar**, haga clic en **Continuar** y compruebe que todavía está en modo de diseño.  
  
6.  Escriba lo siguiente en la ventana **Inmediato**: `?MyFunction<enter>`  
  
7.  Escriba lo siguiente en la ventana **Inmediato**: `?MySub<enter>`  
  
8.  Compruebe que ha alcanzado el punto de interrupción, y examine el valor de la variable estática `i` en la ventana **Variables locales**.  Debería tener el valor de 3.  
  
9. Compruebe que la pila de llamadas es exacta.  
  
10. En el menú **Depurar**, haga clic en **Continuar** y compruebe que todavía está en modo de diseño.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)