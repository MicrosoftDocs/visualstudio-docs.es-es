---
title: Depuración de Windows Forms | Microsoft Docs
description: Siga un tutorial para ver cómo crear y depurar una instancia de Windows Form, una aplicación administrada común. Puede usar C#, Visual Basic, C++ o F#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73b58326bb594f275a508e5ba7fb17071f283ac2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385180"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Tutorial: Depurar un formulario Windows Form
Un Windows Form es una de las aplicaciones administradas más comunes. Con un Windows Form se crean aplicaciones estándar de Windows. Puede completar este tutorial utilizando Visual Basic, C# o C++.

 En primer lugar, debe cerrar las soluciones que estén abiertas.

### <a name="to-prepare-for-this-walkthrough"></a>Pasos preliminares de este tutorial

- Si tiene una solución abierta, ciérrela. (En el menú **Archivo**, seleccione **Cerrar solución**).

## <a name="create-a-new-windows-form"></a>Crear un nuevo Windows Form
 A continuación, creará un nuevo Windows Form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Para crear el formulario Windows Forms para este tutorial

1. En el menú **Archivo**, elija **Nuevo** y, a continuación, haga clic en **Proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. En el panel Tipos de proyecto, abra el nodo **Visual Basic**, **Visual C#** o **Visual C++** y, a continuación,

    1. Para Visual Basic o Visual C#, seleccione **Escritorio de Windows** > **Aplicación de Windows Forms**.

    2. Para Visual C++, seleccione **Aplicación de escritorio de Windows**.

3. En el cuadro **Nombre**, asigne un nombre único al proyecto (por ejemplo, Walkthrough_SimpleDebug).

4. Haga clic en **Aceptar**.

     Visual Studio crea un proyecto nuevo y muestra un formulario nuevo en el Diseñador de Windows Forms. Para obtener más información, vea [Diseñador de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. En el menú **Ver**, seleccione **Cuadro de herramientas**.

     Se abrirá el Cuadro de herramientas. Para obtener más información, vea [Cuadro de herramientas](../ide/reference/toolbox.md).

6. En el Cuadro de herramientas, haga clic en el control **Button** y arrástrelo a la superficie de diseño del formulario. Coloque el botón en el formulario.

7. En el Cuadro de herramientas, haga clic en el control **TextBox** y arrástrelo a la superficie de diseño del formulario. Coloque el control **TextBox** en el formulario.

8. En la superficie de diseño del formulario, haga doble clic en el botón.

     Esto le lleva a la página de códigos. El cursor debe estar en `button1_Click`.

10. Agregue el código siguiente a la función `button1_Click`:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. En el menú **Compilar**, seleccione **Compilar solución**.

     El proyecto se debe compilar sin errores.

## <a name="debug-your-form"></a>Depurar el formulario
 Ahora está listo para comenzar la depuración.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Para depurar el Windows Form creado para este tutorial

1. En la ventana de código fuente, haga clic en el margen izquierdo en la misma línea que el texto que agregó:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Aparecerá un punto rojo y el texto de la línea se resaltará en rojo. El punto rojo representa un punto de interrupción. Para obtener más información, vea [Puntos de interrupción](/previous-versions/ktf38f66(v=vs.100)). Cuando ejecute la aplicación en el depurador, este interrumpirá la ejecución del código en la posición donde encuentre un punto de interrupción. Esto le permite ver el estado de la aplicación y depurarla.

    > [!NOTE]
    > También puede hacer clic con el botón derecho en cualquier línea de código, seleccionar **Punto de interrupción** y, a continuación, hacer clic en **Insertar punto de interrupción** para agregar un punto de interrupción en esa línea.

2. En el menú **Depurar**, elija **Iniciar**.

     El Windows Form comienza su ejecución.

3. En el Windows Form, haga clic en el botón agregado.

     En Visual Studio, esto le lleva a la línea en la que estableció el punto de interrupción en la página de códigos. Esta línea debe aparecer resaltada en amarillo. Ahora puede ver las variables de la aplicación y controlar su ejecución. La aplicación ha detenido ahora su ejecución y espera a que se le indique una acción.

4. En el menú **Depurar**, elija **Ventanas**, después **Inspección** y, a continuación, haga clic en **Inspección1**.

5. En la ventana **Inspección1**, haga clic en una fila en blanco. En la columna **Nombre**, escriba `textBox1.Text` (si usa Visual Basic o Visual C#) o `textBox1->Text` (si usa C++), luego presione ENTRAR.

     En la ventana **Inspección1** se muestra el valor de esta variable entre comillas:

    `""`

6. En el menú **Depurar**, elija **Depurar paso a paso por instrucciones**.

     El valor de textBox1.Text cambia en la ventana **Inspección1** a:

    `Button was clicked!`

7. En el menú **Depurar**, elija **Continuar** para reanudar la depuración del programa.

8. En el Windows Form, haga clic de nuevo en el botón.

     Visual Studio vuelve a interrumpir la ejecución.

9. Haga clic en el punto rojo que representa al punto de interrupción.

     Esto quita el punto de interrupción del código.

10. En el menú **Depurar**, elija **Detener depuración**.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Adjuntar la aplicación de Windows Forms para la depuración
 En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], puede adjuntar el depurador a un proceso en ejecución. Si utiliza Express Edition, esta característica no es compatible.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Para adjuntar la aplicación de Windows Forms para la depuración

1. En el proyecto creado anteriormente, haga clic en el margen izquierdo para volver a establecer un punto de interrupción en la línea agregada:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. En el menú **Depurar**, seleccione **Iniciar sin depurar**.

     El Windows Form comenzará su ejecución en Windows, como si se hubiera hecho doble clic en su archivo ejecutable. El depurador no se ha asociado.

3. En el menú **Depurar**, seleccione **Asociar al proceso**. (Este comando también está disponible en el menú **Herramientas**).

     Aparecerá el cuadro de diálogo **Asociar al proceso** .

4. En el panel **Procesos disponibles**, busque el nombre del proceso (Walkthrough_SimpleDebug.exe) en la columna **Proceso** y haga clic en él.

5. Haga clic en el botón **Adjuntar**.

6. En el Windows Form, haga clic en el único botón.

     El depurador interrumpe la ejecución del Windows Form en el punto de interrupción.

## <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Seguridad del depurador](../debugger/debugger-security.md)