---
title: 'Paso 6: Asignar un nombre a los controles de botón'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 397f65639b6ac277aa6975964ba8317adea58a49
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062854"
---
# <a name="step-6-name-your-button-controls"></a>Paso 6: Asignar un nombre a los controles de botón

Hay solo un <xref:System.Windows.Forms.PictureBox> en el formulario. Al agregarlo, el IDE lo denominó automáticamente **pictureBox1**. Solamente hay un <xref:System.Windows.Forms.CheckBox>, denominado **checkBox1**. Pronto, escribirá código, y ese código hará referencia a CheckBox y PictureBox. Como solo hay un ejemplar de cada control, entenderá lo que significan los términos **pictureBox1** o **checkBox1** cuando los vea en el código.

> [!TIP]
> En Visual Basic, la primera letra del nombre de un control se pone en mayúscula de forma predeterminada, de modo que los nombres son **PictureBox1**, **CheckBox1**, etc.

Hay cuatro botones en el formulario, que el IDE ha denominado **button1**, **button2**, **button3**y **button4**. Solo con mirar los nombres actuales no sabemos cuál es el botón **Cerrar** ni cuál es el botón **Mostrar una imagen** . Por eso resulta útil asignar a los controles de botón nombres más descriptivos.

## <a name="to-name-your-button-controls"></a>Para dar un nombre a los controles de botón

1. En el formulario, elija el botón **Cerrar** . (Si todavía están seleccionados todos los botones, elija la tecla **Esc** para cancelar la selección). Desplácese en la ventana **Propiedades** hasta que vea la propiedad **(Name)** . (La propiedad **(Name)** se encuentra cerca de la parte superior cuando las propiedades están por orden alfabético). Cambie el nombre a **closeButton**, como se muestra en la captura de pantalla siguiente.

    ![Ventana Propiedades mostrando el nombre closeButton](../ide/media/express_setnameproperty.png)<br>***Ventana*** *Propiedades con el*  ***nombre*** *closeButton*

    > [!NOTE]
    > Intente cambiar el nombre del botón por **close Button**, con un espacio entre las palabras "close" (cerrar) y "Button" (botón). Al hacerlo, el IDE muestra un mensaje de error: "El valor de la propiedad no es válido". En los nombres de los controles no se permiten espacios (ni algunos otros caracteres).

1. Cambie el nombre de los otros tres botones a **backgroundButton**, **clearButton**y **showButton**.
Puede comprobar los nombres eligiendo la lista desplegable de selección de controles de la ventana **Propiedades** . Aparecerán los nuevos nombres de los botones.

1. Haga doble clic en el botón **Mostrar una imagen** del formulario. Como alternativa, elija el botón **Mostrar una imagen** del formulario y, después, presione la tecla **Entrar**. Al hacerlo, el IDE abre una pestaña adicional en la ventana principal denominada **Form1.cs**. (Si usa Visual Basic, la pestaña se denomina **Form1.vb**).

   En esta pestaña se muestra el archivo de código subyacente del formulario, como se muestra en la captura de pantalla siguiente.

    ![Pestaña Form1.cs con código de Visual C&#35;](../ide/media/express_showbuttoncode.png)<br>
*Pestaña ***Form1.cs*** con código de C#*

    > [!NOTE]
    > En su lugar, es posible que la pestaña Form1.cs o Form1.vb muestre **showButton** como **ShowButton**.

1. Céntrese en esta parte del código.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   > [!IMPORTANT]
   > Use el control del lenguaje de programación situado en la parte superior derecha de esta página para ver el fragmento de código de C# o el de Visual Basic.<br><br>![Control de lenguaje de programación para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

   Lo que ve es el código llamado `showButton_Click()` (o `ShowButton_Click()`). El IDE lo agregó al código del formulario cuando abrió el archivo de código del botón **showButton** . En tiempo de diseño, cuando abra el archivo de código de un control de un formulario, se generará el código del control si este aún no existe. Este código, conocido como *método*, se ejecuta cuando ejecuta la aplicación y elige el control: en este caso, el botón **Mostrar una imagen**.

1. Vuelva a elegir la pestaña del **Diseñador de Windows Forms** (**Form1.cs [Diseño]** ) y luego abra el archivo de código para que el botón **Borrar la imagen** cree un método para él en el código del formulario. Repita el procedimiento con los dos botones restantes. El IDE agrega cada vez un nuevo método al archivo de código del formulario.

1. Si desea agregar varios métodos, abra el archivo de código del control **CheckBox** en el **Diseñador de Windows Forms** para hacer que el IDE agregue un método `checkBox1_CheckedChanged()`. Cada vez que el usuario activa o desactiva la casilla, se llama a este método.

   > [!TIP]
   > Cuando se trabaja en una aplicación, a menudo se cambia alternativamente entre el editor de código y el **Diseñador de Windows Forms**. El IDE facilita la navegación en el proyecto. Use el **Explorador de soluciones** para abrir el **Diseñador de Windows Forms**: haga doble clic en *Form1.cs* en C# o en *Form1.vb* en Visual Basic o bien, en la barra de menús, elija **Ver** > **Diseñador**.

    A continuación se muestra el nuevo código que aparece en el editor de código.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Es posible que el código no muestre controladores de eventos en letras "camelCase".

    Los cinco métodos que ha agregado se denominan *controladores de eventos*, porque la aplicación los llama cada vez que se produce un evento (por ejemplo, cuando un usuario elige un botón o activa una casilla).

    Cuando ve el código de un control del IDE en tiempo de diseño, Visual Studio agrega un método de control de eventos para el control si aún no está ahí. Por ejemplo, cuando se hace doble clic en un botón, el IDE agrega un controlador para este evento <xref:System.Windows.Forms.Control.Click> (al que se llamará cada vez que el usuario elija el botón). Cuando se hace doble clic en una casilla, el IDE agrega un controlador para el evento <xref:System.Windows.Forms.CheckBox.CheckedChanged> correspondiente (al que se llamará cada vez que el usuario active o desactive la casilla).

    Después de agregar un controlador de eventos para un control, puede volver en cualquier momento a él desde el **Diseñador de Windows Forms** haciendo doble clic en el control o eligiendo **Ver** > **Código** en la barra de menús.

    Los nombres son importantes al compilar programas. Los métodos (incluso los controladores de eventos) pueden tener cualquier nombre que se desee. Cuando agregue un controlador de eventos con el IDE, se creará un nombre basado en el nombre del control y en el evento que se controla.

    Por ejemplo, el evento Click para un botón denominado **showButton** se denomina método de control de eventos `showButton_Click()` (o bien, `ShowButton_Click()`). Además, se suelen agregar paréntesis de apertura y cierre `()` después del nombre de método para indicar que se trata de un método.

    Si decide que desea cambiar un nombre de variable de código, haga clic con el botón secundario en la variable del código y elija **Refactorizar** > **Cambiar nombre**. Todas las instancias de esa variable del código cambiarán de nombre. Para más información, vea [Refactorización de cambio de nombre](../ide/reference/rename.md).

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 7: Adición de componentes de cuadro de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 5: Agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
