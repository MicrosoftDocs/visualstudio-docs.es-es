---
title: Ventana Inmediato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87f8cd822dcd67ff7837dcaa31e47c23e0a0550b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203676"
---
# <a name="immediate-window"></a>Inmediato (ventana)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
La ventana **Inmediato** sirve para depurar y evaluar expresiones, ejecutar instrucciones, imprimir valores de variables, etc. Permite escribir expresiones para evaluarlas o ejecutarlas mediante el lenguaje de desarrollo durante la depuración. Para mostrar la ventana **Inmediato**, abra un proyecto para editarlo, elija **Ventanas** en el menú **Depurar** y seleccione **Inmediato**, o bien presione CTRL+ALT+I.  
  
 Puede usar esta ventana para emitir comandos [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] individuales. Entre los comandos disponibles se incluye `EvaluateStatement`, que puede usarse para asignar valores a variables. La ventana **Inmediato** también admite IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Mostrar los valores de las variables  
 Esta ventana puede resultar particularmente útil al depurar una aplicación. Por ejemplo, para comprobar el valor de una variable `varA`, usar el [comando Imprimir](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 El signo de interrogación (?) es un alias de `Debug.Print`, por lo que este comando también puede escribirse:  
  
```  
>? varA  
```  
  
 Ambas versiones de este comando devolverán el valor de la variable `varA`.  
  
> [!NOTE]
>  Para emitir un comando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en la ventana **Inmediato**, el comando debe ir precedido de un signo mayor que (>). Para escribir varios comandos, cambie a la ventana **Comando**.  
  
## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño  
 Puede usar la ventana **Inmediato** para ejecutar una función o subrutina en tiempo de diseño.  
  
#### <a name="to-execute-a-function-at-design-time"></a>Para ejecutar una función en tiempo de diseño  
  
1.  Copie el código siguiente en una aplicación de consola [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  En el menú **Depurar**, haga clic en **Ventanas** y en **Inmediato**.  
  
3.  Escriba `?MyFunction(2)` en la ventana **Inmediato** y presione Entrar.  
  
     La ventana **Inmediato** ejecutará `MyFunction` y mostrará `4`.  
  
 Si la función o la subrutina contienen un punto de interrupción, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interrumpirá la ejecución en el punto adecuado. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Para más información, vea [Tutorial: Depurar en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 No puede usar la evaluación de expresiones en tiempo de diseño en los tipos de proyectos que requieren que se inicie un entorno de ejecución, incluidos los proyectos de [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)], proyectos web, proyectos de Smart Device y proyectos de SQL.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Evaluación de expresiones en tiempo de diseño en soluciones de varios proyectos  
 Al establecer el contexto de evaluación de expresiones en tiempo de diseño, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hace referencia al proyecto seleccionado actualmente en el Explorador de soluciones. Si no se selecciona ningún proyecto en el Explorador de soluciones, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] intenta evaluar la función en el proyecto de inicio. Si no se puede evaluar la función en el contexto actual, recibirá un mensaje de error. Si está intentando evaluar una función en un proyecto que no es el proyecto de inicio para la solución y recibe un error, pruebe a seleccionar el proyecto en el Explorador de soluciones e intente realizar la evaluación otra vez.  
  
## <a name="entering-commands"></a>Escribir comandos  
 Debe escribir el signo mayor que (>) al emitir comandos de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en la ventana **Inmediato**. Use las teclas FLECHA ARRIBA y FLECHA ABAJO para desplazarse por los comandos ejecutados anteriormente.  
  
|Tarea|Soluciones|Ejemplo|  
|----------|--------------|-------------|  
|Evaluar una expresión.|Empezar la expresión con un signo de interrogación (?).|`? a+b`|  
|Entrar temporalmente en el modo Comando mientras está en el modo Inmediato (para ejecutar un único comando).|Escribir el comando, precedido de un signo mayor que (>).|`>alias`|  
|Cambiar a la ventana Comandos.|Escribir `cmd` en la ventana, precedido de un signo mayor que (>).|`>cmd`|  
|Volver a la ventana Inmediato.|Escribir `immed` en la ventana sin el signo mayor que (>).|`immed`|  
  
## <a name="mark-mode"></a>Modo Marcar  
 Cuando hace clic en cualquier línea anterior de la ventana **Inmediato**, cambia automáticamente al modo Marcar. Esto le permite seleccionar, editar y copiar el texto de los comandos anteriores como lo haría en cualquier editor de texto, y pegarlo en la línea actual.  
  
## <a name="the-equals--sign"></a>El signo igual (=)  
 La ventana que se usa para escribir el comando `EvaluateStatement` determina si el signo igual (=) se interpreta como un operador de comparación o como un operador de asignación.  
  
 En la ventana **Inmediato**, un signo igual (=) se interpreta como un operador de asignación. Por lo tanto, por ejemplo, el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 asignará a la variable `varA` el valor de la variable `varB`.  
  
 Por el contrario, en la ventana **Comando**, un signo igual (=) se interpreta como un operador de comparación. No puede usar operaciones de asignación en la ventana **Comando**. Por lo tanto, por ejemplo, si los valores de las variables `varA` y `varB` son diferentes, entonces el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 devolverá un valor de `False`.  
  
## <a name="first-chance-exception-notifications"></a>notificaciones de excepciones de primera oportunidad  
 En algunas configuraciones, se muestran notificaciones de excepciones de primera oportunidad en la ventana **Inmediato**.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Para activar o desactivar las notificaciones de excepciones de primera oportunidad en la ventana Inmediato  
  
1.  En el menú **Vista**, haga clic en **Otras ventanas** y en **Salida**.  
  
2.  Haga doble clic en el área de texto de la ventana **Salida** y seleccione o anule la selección de **Mensajes de excepción**.  
  
## <a name="see-also"></a>Vea también  
 [Desplazarse por el código con el depurador](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Depurar en Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Conceptos básicos del depurador](../../debugger/debugger-basics.md)   
 [Tutorial: Depuración en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Usar expresiones regulares en Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)



