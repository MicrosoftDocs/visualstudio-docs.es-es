---
title: 'Tutorial: Depurar un formulario Windows Forms | Documentos de Microsoft'
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
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02db9a01286e65f371ab4d8388102a3db4c5602e
ms.sourcegitcommit: 1e08318a8a684b21609af7a5e48b56abcc3239e6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2017
---
# <a name="walkthrough-debugging-a-windows-form"></a>Tutorial: Depurar Windows Forms
Un Windows Form es una de las aplicaciones administradas más comunes. Con un Windows Form se crean aplicaciones estándar de Windows. Puede completar este tutorial utilizando Visual Basic, C# o C++.  
  
 En primer lugar, debe cerrar las soluciones que estén abiertas.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Pasos preliminares de este tutorial  
  
-   Si tiene una solución abierta, ciérrela. (En el **archivo** menú, seleccione **Cerrar solución**.)  
  
## <a name="create-a-new-windows-form"></a>Crear un nuevo Windows Form  
 A continuación, creará un nuevo Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Para crear el formulario Windows Forms para este tutorial  
  
1.  En el **archivo** menú, elija **New** y haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el panel tipos de proyecto, abra el **Visual Basic**, **Visual C#**, o **Visual C++** nodo, a continuación,  
  
    1.  Para Visual Basic o Visual C#, seleccione la **Windows** nodo, a continuación, seleccione **aplicación de Windows Forms** en el **plantillas** panel.  
  
    2.  Para Visual C++, seleccione el **CLR** nodo, a continuación, seleccione **aplicación de Windows Forms** en el **plantillas** panel...  
  
3.  En el **plantillas** panel, seleccione **aplicación de Windows**.  
  
4.  En el **nombre** cuadro, asigne al proyecto un nombre único (por ejemplo, Walkthrough_SimpleDebug).  
  
5.  Haga clic en **Aceptar**.  
  
     Visual Studio crea un proyecto nuevo y muestra un formulario nuevo en el Diseñador de Windows Forms. Para obtener más información, consulte [Diseñador de Windows Forms](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  En el **vista** menú, seleccione **cuadro de herramientas**.  
  
     Se abrirá el Cuadro de herramientas. Para obtener más información, consulte [cuadro de herramientas](../ide/reference/toolbox.md).  
  
7.  En el cuadro de herramientas, haga clic en el **botón** controlar y arrastre el control a la superficie de diseño del formulario. Coloque el botón en el formulario.  
  
8.  En el cuadro de herramientas, haga clic en el **TextBox** controlar y arrastre el control a la superficie de diseño del formulario. Quitar el **cuadro de texto** en el formulario.  
  
9. En la superficie de diseño del formulario, haga doble clic en el botón.  
  
     Esto le lleva a la página de códigos. El cursor debe estar en `button1_Click`.  
  
10. Agregue el código siguiente a la función `button1_Click`:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. En el **generar** menú, seleccione **generar solución**.  
  
     El proyecto se debe compilar sin errores.  
  
## <a name="debug-your-form"></a>Depurar el formulario  
 Ahora está listo para comenzar la depuración.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Para depurar el Windows Form creado para este tutorial  
  
1.  En la ventana de código fuente, haga clic en el margen izquierdo en la misma línea que el texto que agregó:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Aparecerá un punto rojo y el texto de la línea se resaltará en rojo. El punto rojo representa un punto de interrupción. Para obtener más información, consulte [puntos de interrupción](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Cuando ejecute la aplicación en el depurador, este interrumpirá la ejecución del código en la posición donde encuentre un punto de interrupción. Esto le permite ver el estado de la aplicación y depurarla.  
  
    > [!NOTE]
    >  También puede haga clic en cualquier línea de código, seleccionar **punto de interrupción**y, a continuación, haga clic en **Insertar punto de interrupción** para agregar un punto de interrupción en esa línea.  
  
2.  EN el **depurar** menú, elija **iniciar**.  
  
     El Windows Form comienza su ejecución.  
  
3.  En el Windows Form, haga clic en el botón agregado.  
  
     En Visual Studio, esto le lleva a la línea en la que estableció el punto de interrupción en la página de códigos. Esta línea debe aparecer resaltada en amarillo. Ahora puede ver las variables de la aplicación y controlar su ejecución. La aplicación ha detenido ahora su ejecución y espera a que se le indique una acción.  
  
4.  En el **depurar** menú, elija **Windows**, a continuación, **inspección**y haga clic en **Inspección1**.  
  
5.  En el **Inspección1** ventana, haga clic en una fila en blanco. En el **nombre** columna, escriba `textBox1.Text` (si se utiliza Visual Basic o Visual C#) o `textBox1->Text` (si usas C++), a continuación, presione ENTRAR.  
  
     El **Inspección1** ventana muestra el valor de esta variable entre comillas:  
  
    ```  
    ""  
    ```  
  
6.  En el **depurar** menú, elija **paso a paso**.  
  
     El valor de textBox1.Text cambia en la **Inspección1** ventana para:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  En el **depurar** menú, elija **continuar** para reanudar la depuración del programa.  
  
8.  En el Windows Form, haga clic de nuevo en el botón.  
  
     Visual Studio vuelve a interrumpir la ejecución.  
  
9. Haga clic en el punto rojo que representa al punto de interrupción.  
  
     Esto quita el punto de interrupción del código.  
  
10. En el **depurar** menú, elija **Detener depuración**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Adjuntar la aplicación de Windows Forms para la depuración  
 En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede adjuntar el depurador a un proceso en ejecución. Si utiliza Express Edition, esta característica no es compatible.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Para adjuntar la aplicación de Windows Forms para la depuración  
  
1.  En el proyecto creado anteriormente, haga clic en el margen izquierdo para volver a establecer un punto de interrupción en la línea agregada:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  En el **depurar** menú, seleccione **iniciar sin depurar**.  
  
     El Windows Form comenzará su ejecución en Windows, como si se hubiera hecho doble clic en su archivo ejecutable. El depurador no se ha asociado.  
  
3.  En el **depurar** menú, seleccione **adjuntar al proceso**. (Este comando también está disponible en la **herramientas** menú.)  
  
     Aparecerá el cuadro de diálogo **Asociar al proceso** .  
  
4.  En el **procesos disponibles** panel, busque el nombre del proceso (Walkthrough_SimpleDebug.exe) en la **proceso** columna y haga clic en él.  
  
5.  Haga clic en el **adjuntar** botón.  
  
6.  En el Windows Form, haga clic en el único botón.  
  
     El depurador interrumpe la ejecución del Windows Form en el punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)