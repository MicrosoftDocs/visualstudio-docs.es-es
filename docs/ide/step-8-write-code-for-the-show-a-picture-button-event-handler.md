---
title: 'Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen'
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26bfd4d74580fecd15b1891895e5ae28a18f3296
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887957"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen

En este paso, conseguirá que el botón **Mostrar una imagen** funcione de esta forma:

- Cuando un usuario seleccione ese botón, la aplicación abre un cuadro <xref:System.Windows.Forms.OpenFileDialog>.

- Si un usuario abre un archivo de imagen, la aplicación la muestra en <xref:System.Windows.Forms.PictureBox>.

El IDE incluye una eficaz herramienta denominada IntelliSense que ayuda a escribir código. Cuando se escribe código, el IDE abre un cuadro con sugerencias para completar las palabras parciales que se escriben.

IntelliSense intenta determinar lo que se quiere hacer a continuación y salta de forma automática al último elemento que se elige en la lista. Puede utilizar las flechas arriba o abajo para moverse por la lista o bien continuar escribiendo letras para reducir las opciones propuestas. Cuando vea la opción que busca, elija la tecla **Tab** para seleccionarla. Otra opción es pasar por alto las sugerencias, si no las necesita.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Para escribir código para el controlador de eventos de botón Mostrar una imagen

1. Vaya al **Diseñador de Windows Forms** y haga doble clic en el botón **Mostrar una imagen**. El IDE va inmediatamente al diseñador de código y mueve el cursor para situarlo dentro del método `showButton_Click()` (o `ShowButton_Click()`) que ha agregado previamente.

1. Escriba una `i` en la línea vacía entre las dos llaves `{ }`. (En Visual Basic, escriba en la línea vacía entre `Private Sub...` y `End Sub`). Se abre una ventana **IntelliSense**, como se muestra en la imagen siguiente.

    ![IntelliSense con código de Visual C&#35;](../ide/media/express_ifintellisense.png)

1. En la ventana **IntelliSense** se debe resaltar la palabra `if`. (De lo contrario, escriba una `f` minúscula, y lo hará). Observe cómo aparece un cuadro de *información sobre herramientas* junto a la ventana **IntelliSense** con la descripción, **Fragmento de código para la instrucción if**. (En Visual Basic, la información sobre herramientas dice también que se trata de un fragmento de código, pero con una redacción ligeramente diferente.) Como quiere usar ese fragmento, pulse la tecla **Tab** para insertar `if` en el código. Pulse de nuevo la tecla **Tab** para usar el fragmento de código `if`. (Si ha hecho clic en alguna otra parte y ha desaparecido la ventana **IntelliSense**, borre la `i`con la tecla de retroceso y vuelva a escribirla; se volverá a abrir la ventana **IntelliSense**).

    ![Código de Visual C&#35;](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Uso de IntelliSense para escribir más código

A continuación, use IntelliSense para escribir más código y abrir un cuadro de diálogo **Abrir archivo**. Si el usuario selecciona el botón **Aceptar**, el control PictureBox cargará el archivo seleccionado por el usuario. En los pasos siguientes se muestra cómo escribir el código y, aunque son muchos, solamente habrá que presionar unas cuantas teclas:

 1. Comience con el texto seleccionado **true** del fragmento de código. Escriba `op` para sobrescribirlo. (En Visual Basic, empieza con mayúscula inicial, de modo que deberá escribir `Op`).

 1. Se abre la ventana **IntelliSense** y muestra **openFileDialog1**. Elija la tecla **Tab** para seleccionarlo. (En Visual Basic, empieza con mayúscula inicial, de modo que aparecerá **OpenFileDialog1**. Asegúrese de que **OpenFileDialog1** está seleccionado).

     Para obtener más información sobre `OpenFileDialog`, vea [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Escriba un punto (`.`) (En inglés se denomina period o dot). Dado que ha escrito un punto justo después de **openFileDialog1**, se abre una ventana **IntelliSense**, que contiene todas las propiedades y los métodos de componente de **OpenFileDialog**. Se trata de las mismas propiedades que aparecen en la ventana **Propiedades** cuando selecciona este componente en el **Diseñador de Windows Forms**. También puede elegir métodos que indiquen al componente que realice acciones (como abrir un cuadro de diálogo).

    > [!NOTE]
    > La ventana **IntelliSense** puede mostrar propiedades y métodos. Para determinar qué se está mostrando, fíjese en el icono del lado izquierdo de cada elemento de la ventana **IntelliSense**. Verá una imagen de un bloque junto a cada método y una imagen de una llave inglesa (o fija) junto a cada propiedad. Además, aparece un icono de rayo junto a cada evento. <br><br>Estos son los iconos que aparecen:<br><br>![Icono de método](../ide/media/express_iconmethod.png)<br>![Icono de propiedad](../ide/media/express_iconproperty.png)<br>![Icono de evento](../ide/media/express_iconevent.png)

 1. Empiece a escribir `ShowDialog` (el uso de mayúsculas o minúsculas no es significativo en IntelliSense). El método `ShowDialog()` mostrará el cuadro de diálogo **Abrir archivo**. Cuando la ventana haya resaltado **ShowDialog**, pulse la tecla **Tab**. También puede resaltar "ShowDialog" y pulsar la tecla **F1** para obtener ayuda sobre ella.

    Para obtener más información sobre el método `ShowDialog()`, vea [ShowDialog Method](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Cuando se usa un método con un control o un componente (lo que se denomina *llamar a un método*), es preciso agregar paréntesis. Por tanto, escriba paréntesis de apertura y cierre inmediatamente después de la "g" en `ShowDialog`: `()` Ahora debería tener este aspecto: "openFileDialog1.ShowDialog()".

    > [!NOTE]
    > Los métodos constituyen una parte importante de cualquier aplicación y en este tutorial se han mostrado varias maneras de usarlos. Se puede llamar al método de un componente para ordenarle que haga algo, por ejemplo, como cuando llamó al método `ShowDialog()` del componente **OpenFileDialog**. Puede crear métodos propios para que la aplicación realice acciones, como la que se va a compilar ahora, que se denomina método `showButton_Click()` y que abre un cuadro de diálogo y una imagen cuando un usuario elige en un botón.

 1. Para C#, agregue un espacio y, después, dos signos igual (`==`). Para Visual Basic, agregue un espacio y, después, use un solo signo igual (`=`). (En C# y Visual Basic se usan otros operadores de igualdad).

 1. Agregue otro espacio. En cuanto lo haga, se abrirá otra ventana **IntelliSense**. Empiece a escribir `DialogResult` y pulse la tecla **Tab** para agregarlo.

    > [!NOTE]
    > Cuando se escribe código para llamar a un método, a veces devuelve un valor. En este caso, el método <xref:System.Windows.Forms.CommonDialog.ShowDialog> del componente **OpenFileDialog** devuelve un valor <xref:System.Windows.Forms.DialogResult>. DialogResult es un valor especial que le indica lo que ha sucedido en un cuadro de diálogo. Un componente **OpenFileDialog** puede dar lugar a que el usuario pulse **Aceptar** o **Cancelar**, de modo que el método `ShowDialog()` devuelva `DialogResult.OK` o `DialogResult.Cancel`.

 1. Escriba un punto para abrir la ventana **IntelliSense** del valor DialogResult. Escriba la letra `O` y pulse la tecla **Tab** para insertar **Aceptar**.

    Para obtener más información sobre DialogResult, vea [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > Deberá quedar completa la primera línea de código. Para C#, debe ser similar a lo siguiente.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Para Visual Basic, debería ser la siguiente.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Ahora, agregue otra línea de código más. Puede escribirla (o copiar y pegar), pero puede resultar interesante utilizar IntelliSense para agregarla. Cuanto más se familiarice con IntelliSense, más rápidamente podrá escribir su propio código. El método `showButton_Click()` final será similar al código siguiente.

    > [!IMPORTANT]
    > Use el control del lenguaje de programación situado en la parte superior derecha de esta página para ver el fragmento de código de C# o el de Visual Basic.<br><br>![Control de lenguaje de programación para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 9: Revisión, comentarios y prueba del código](../ide/step-9-review-comment-and-test-your-code.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 7: Agregar componentes de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
