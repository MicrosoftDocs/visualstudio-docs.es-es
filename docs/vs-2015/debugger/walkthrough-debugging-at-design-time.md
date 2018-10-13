---
title: 'Tutorial: Depurar en tiempo de diseño | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4ff1d0e1c155784bd6116be2bc6eb63e6c53d80
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227238"
---
# <a name="walkthrough-debugging-at-design-time"></a>Tutorial: Depurar en tiempo de diseño
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar Visual Studio **inmediato** ventana para ejecutar una función o subrutina mientras la aplicación no se está ejecutando. Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpirá la ejecución en el punto adecuado. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina depuración en tiempo de diseño.  
  
 El siguiente procedimiento muestra cómo puede utilizar esta característica.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Para establecer los puntos de interrupción en la ventana Inmediato  
  
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
  
3.  Escriba lo siguiente en el **inmediato** ventana: `?MyFunction<enter>`  
  
4.  Compruebe que se ha alcanzado el punto de interrupción, y que la pila de llamadas es exacta.  
  
5.  En el **depurar** menú, haga clic en **continuar**y compruebe que está todavía en modo de diseño.  
  
6.  Escriba lo siguiente en el **inmediato** ventana: `?MyFunction<enter>`  
  
7.  Escriba lo siguiente en el **inmediato** ventana: `?MySub<enter>`  
  
8.  Compruebe que el punto de interrupción y examinar el valor de la variable estática `i` en el **variables locales** ventana. Debería tener el valor de 3.  
  
9. Compruebe que la pila de llamadas es exacta.  
  
10. En el **depurar** menú, haga clic en **continuar**y compruebe que está todavía en modo de diseño.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)



