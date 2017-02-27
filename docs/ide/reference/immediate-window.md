---
title: "Ventana Inmediato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "evaluación de expresiones en tiempo de diseño"
  - "Inmediato (ventana)"
  - "notificaciones de excepciones de primera oportunidad"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Ventana Inmediato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ventana **Inmediato** se utiliza para depurar y evaluar expresiones, ejecutar instrucciones, imprimir valores de variables, etc.  Permite escribir expresiones que el lenguaje de programación evalúa o ejecuta durante la depuración.  Para mostrar la ventana **Inmediato**, abra un proyecto para su edición, a continuación, elija **Ventanas** en el menú **Depurar** y seleccione **Inmediato** o presione CTRL\+ALT\+I.  
  
 Puede utilizar esta ventana para ejecutar comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individuales.  Entre los comandos disponibles se incluye `EvaluateStatement`, que se puede utilizar para asignar valores a las variables.  La ventana **Inmediato** también admite IntelliSense.  
  
## Mostrar los valores de las variables  
 Esta ventana puede resultar particularmente útil al depurar una aplicación.  Por ejemplo, para comprobar el valor de una variable `varA`, puede utilizar el [Imprimir \(Comando\)](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 El signo de interrogación \(?\) es un alias de `Debug.Print`, por lo que este comando también se puede escribir como:  
  
```  
>? varA  
```  
  
 Ambas versiones de este comando devolverán el valor de la variable `varA`.  
  
> [!NOTE]
>  Para ejecutar un comando de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en la ventana **Inmediato**, se debe incluir un signo mayor que \(\>\) delante del comando.  Para escribir varios comandos, pase a la ventana **Comando**.  
  
## Evaluación de expresiones en tiempo de diseño  
 Puede utilizar la ventana **Inmediato** para ejecutar una función o subrutina en tiempo de diseño.  
  
#### Para ejecutar una función en tiempo de diseño  
  
1.  Copie el código siguiente en una aplicación de consola de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:  
  
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
  
 Si la función o subrutina contiene un punto de interrupción, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interrumpirá la ejecución en el punto adecuado.  A continuación puede utilizar las ventanas del depurador para examinar el estado del programa.  Para obtener más información, vea [Tutorial: Depurar en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 No puede usar la evaluación de expresiones en tiempo de diseño en aquellos tipos de proyectos que requieran el inicio en un entorno de ejecución, incluidos los proyectos de [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], web, Smart Device y SQL.  
  
### Evaluación de expresiones en tiempo de diseño en las soluciones de varios proyectos  
 Al establecer el contexto para la evaluación de expresiones en tiempo de diseño, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hace referencia al proyecto seleccionado en el Explorador de soluciones.  Si no está seleccionado ningún proyecto en el Explorador de soluciones, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] intenta evaluar la función con respecto al proyecto de inicio.  Si la función no se puede evaluar en el contexto actual, recibirá un mensaje de error.  Si está intentando evaluar una función en un proyecto que no es el proyecto de inicio para la solución y recibe un error, seleccione el proyecto en el Explorador de soluciones e intente realizar la evaluación otra vez.  
  
## Escribir comandos  
 Debe escribir el signo mayor que \(\>\) cuando ejecute comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en la ventana **Inmediato**.  Use las teclas de dirección FLECHA ARRIBA y FLECHA ABAJO para desplazarse por los comandos ejecutados previamente.  
  
|Tarea|Soluciones|Ejemplo|  
|-----------|----------------|-------------|  
|Evaluar una expresión.|Escriba una interrogación de cierre \(?\) delante de la expresión.|`? a+b`|  
|Entrar temporalmente en el modo Comando mientras se está en el modo Inmediato \(para ejecutar un único comando\).|Escriba un signo mayor que \(\>\) delante del comando.|`>alias`|  
|Cambiar a la ventana Comando.|Escriba `cmd` en la ventana, precedido por el signo mayor que \(\>\).|`>cmd`|  
|Volver a la ventana Inmediato.|Escriba `immed`  en la ventana sin el signo mayor que \(\>\)|`immed`|  
  
## Modo Marcar  
 Si hace clic en cualquier línea anterior en la ventana **Inmediato**, entrará automáticamente en el modo Marcar.  Esto le permite seleccionar, editar y copiar el texto de comandos anteriores tal como lo haría en cualquier editor de texto, y pegarlo en la línea actual.  
  
## El signo igual \(\=\)  
 La ventana utilizada para escribir el comando `EvaluateStatement` determina si un signo igual \(\=\) se interpreta como un operador de comparación o como un operador de asignación.  
  
 En la ventana **Inmediato**, un signo igual \(\=\) se interpreta como un operador de asignación.  Así, por ejemplo, el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 asignará a la variable `varA` el valor de la variable `varB`.  
  
 Por el contrario, en la ventana **Comando**, un signo igual \(\=\) se interpreta como un operador de comparación.  No es posible utilizar operaciones de asignación en la ventana **Comando**.  Así, por ejemplo, si los valores de las variables `varA` y `varB` son diferentes, el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 devolverá un valor de `False`.  
  
## Notificaciones de excepciones de primera oportunidad  
 En algunas configuraciones, las notificaciones de excepciones de primera oportunidad se muestran en la ventana **Inmediato**.  
  
#### Para cambiar la presentación de notificaciones de excepciones de primera oportunidad en la ventana Inmediato  
  
1.  En el menú **Ver**, haga clic en **Otras ventanas** y, a continuación, en **Resultados**.  
  
2.  Haga clic con el botón secundario del mouse en el área de texto de la **Ventana de salida** y seleccione o anule la selección de **Mensajes de excepción**.  
  
## Vea también  
 [Desplazarse por el código con el depurador](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Depurar en Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Conceptos básicos del depurador](../../debugger/debugger-basics.md)   
 [Tutorial: Depurar en tiempo de diseño](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Usar expresiones regulares en Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)