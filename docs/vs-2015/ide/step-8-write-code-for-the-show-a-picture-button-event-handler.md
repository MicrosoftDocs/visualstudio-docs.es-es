---
title: 'Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f5d58533f6f2207d1b07883ab741eb900cdfbbf
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851111"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este paso, conseguirá que el botón **Mostrar una imagen** funcione así:

- Cuando un usuario pulsa ese botón, el programa abre un cuadro de diálogo **Abrir archivo**.

- Si un usuario abre un archivo de imagen, el programa muestra esa imagen en el control PictureBox.

  El IDE incluye una eficaz herramienta denominada IntelliSense que ayuda a escribir código. Cuando se escribe código, el IDE abre un cuadro con sugerencias para completar las palabras parciales que se escriben. Intenta determinar lo que se desea hacer a continuación y salta automáticamente al último elemento que se elige en la lista. Puede utilizar las flechas arriba o abajo para moverse por la lista o bien continuar escribiendo letras para reducir las opciones propuestas. Cuando vea la opción que busca, elija la tecla TAB para seleccionarla. Otra opción es pasar por alto las sugerencias, si no las necesita.

  ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") Para obtener una versión en vídeo de este tema, vea el [tutorial 1: crear un visor de imágenes en Visual Basic-vídeo 4 o el](https://msdn.microsoft.com/vbasic/gg315355.aspx) [tutorial 1: C# crear un visor de imágenes en-vídeo 4](https://msdn.microsoft.com/vcsharp/gg278412.aspx). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Para escribir código para el controlador de eventos de botón Mostrar una imagen

1. Vaya al Diseñador de Windows Forms y haga doble clic en el botón **Mostrar una imagen**. El IDE va inmediatamente al diseñador de código y mueve su cursor de modo para situarlo dentro del método `showButton_Click()` que agregó previamente.

2. Escriba una `i` en la línea vacía entre las dos llaves { }. (En Visual Basic, escriba en la línea vacía entre sub privado... y End Sub). Se abre una ventana de **IntelliSense** , tal como se muestra en la siguiente imagen.

     ![IntelliSense con código de&#35; visual c++](../ide/media/express-ifintellisense.png "Express_IfIntellisense") IntelliSense con C# código Visual

3. La ventana **IntelliSense** debe mostrar resaltada la palabra **if**. (Si no es así, escriba una `f`en minúsculas y lo hará). Observe cómo un pequeño cuadro de *información sobre herramientas* situado junto a la ventana **IntelliSense** aparece con la descripción, **fragmento de código para la instrucción If**. (En Visual Basic, la información sobre herramientas también indica que se trata de un fragmento de código, pero con un texto ligeramente diferente). Quiere usar ese fragmento de código, así que elija la tecla TAB para **insertarlo** en el código. Pulse de nuevo la tecla TAB para usar el fragmento de código **if**. (Si ha hecho clic en alguna otra parte y ha desaparecido la ventana **IntelliSense**, borre la **i** con la tecla de retroceso y vuelva a escribirla; se volverá a abrir la ventana **IntelliSense**).

     ![Código de Visual C&#35;](../ide/media/express-highlighttrue.png "Express_HighlightTrue") Código de Visual C#

4. A continuación, use IntelliSense para escribir más código y abrir un cuadro de diálogo **Abrir archivo**. Si el usuario selecciona el botón **Aceptar**, el control PictureBox cargará el archivo seleccionado por el usuario. En los siguientes pasos se muestra cómo escribir el código. Aunque los pasos son muchos, solamente habrá que presionar unas cuantas teclas:

    1. Comience con el texto seleccionado **true** del fragmento de código. Escriba `op` para sobrescribirlo. (En Visual Basic, empieza con mayúscula inicial, de modo que deberá escribir `Op`).

    2. Se abre la ventana **IntelliSense** y muestra **openFileDialog1**. Elija la tecla TAB para seleccionarlo. (En Visual Basic, empieza con mayúscula inicial, de modo que aparecerá **OpenFileDialog1**. Asegúrese de que **OpenFileDialog1** está seleccionado).

         Para obtener más información sobre `OpenFileDialog`, vea [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Escriba un punto (`.`) (muchos programadores llaman a este punto). Dado que escribió un punto justo después de **OpenFileDialog1**, se abre una ventana de **IntelliSense** , rellenada con todos los métodos y propiedades del componente **OpenFileDialog** . Se trata de las mismas propiedades que aparecen en la ventana **Propiedades** cuando selecciona este componente en el Diseñador de Windows Forms. También puede elegir métodos que indiquen al componente que realice acciones (como abrir un cuadro de diálogo).

        > [!NOTE]
        > La ventana **IntelliSense** puede mostrar propiedades y métodos. Para determinar qué se está mostrando, fíjese en el icono del lado izquierdo de cada elemento de la ventana **IntelliSense**. Se muestra una imagen de un bloque junto a cada método y una imagen de una llave inglesa (o fija) junto a cada propiedad. Además, aparece un icono de rayo junto a cada evento. Estas imágenes se muestran como sigue.

         ![Icono de método](../ide/media/express-iconmethod.png "Express_IconMethod") Icono de método

         ![Icono de propiedad](../ide/media/express-iconproperty.png "Express_IconProperty") Icono de propiedad

         ![Icono de evento](../ide/media/express-iconevent.png "Express_IconEvent") Icono de evento

    4. Empiece a escribir `ShowDialog` (el uso de mayúsculas o minúsculas no es significativo en IntelliSense). El método `ShowDialog()` mostrará el cuadro de diálogo **Abrir archivo**. Cuando la ventana haya resaltado **ShowDialog**, pulse la tecla TAB. También puede resaltar “ShowDialog” y elegir la tecla F1 para obtener ayuda sobre ella.

         Para obtener más información sobre el método `ShowDialog()`, vea [ShowDialog Method](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. Cuando se usa un método con un control o un componente (lo que se denomina *llamar a un método*), es preciso agregar paréntesis. Así pues, especifique los paréntesis de apertura y cierre inmediatamente después de la "g" en `ShowDialog`: `()` Debe tener la apariencia siguiente: "openFileDialog1.ShowDialog()".

        > [!NOTE]
        > Los métodos constituyen una parte importante de cualquier programa. En este tutorial se han mostrado varias maneras de utilizarlos. Se puede llamar al método de un componente para ordenarle que haga algo, por ejemplo, como cuando llamó al método `ShowDialog()` del componente **OpenFileDialog**. Puede crear sus propios métodos para que los programas realicen acciones, como el que estamos construyendo ahora, que se denomina método `showButton_Click()` y que abre un cuadro de diálogo y una imagen cuando un usuario elige en un botón.

    6. Para Visual C#, agregue un espacio y, después, agregue dos signos igual (`==`). Para Visual Basic, agregue un espacio y, después, use un solo signo igual (`=`). (Visual C# y Visual Basic utilizan distintos operadores de igualdad.)

    7. Agregue otro espacio. En cuanto lo haga, se abrirá otra ventana **IntelliSense**. Empiece a escribir `DialogResult` y pulse la tecla TAB para agregarlo.

        > [!NOTE]
        > Cuando se escribe código para llamar a un método, a veces devuelve un valor. En este caso, el método `ShowDialog()` del componente **OpenFileDialog** devuelve un valor DialogResult. DialogResult es un valor especial que le indica lo que ha sucedido en un cuadro de diálogo. Un componente **OpenFileDialog** puede dar lugar a que el usuario pulse **Aceptar** o **Cancelar**, de modo que el método `ShowDialog()` devuelva DialogResult.OK o DialogResult.Cancel.

    8. Escriba un punto para abrir la ventana **IntelliSense** del valor DialogResult. Escriba la letra `O` y pulse la tecla TAB para insertar **Aceptar**.

         Para obtener más información sobre `DialogResult`, vea [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > Deberá quedar completa la primera línea de código. Para Visual C#, debería ser la siguiente.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  Para Visual Basic, debería ser la siguiente.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Ahora, agregue otra línea de código más. Puede escribirla (o copiar y pegar), pero puede resultar interesante utilizar IntelliSense para agregarla. Cuanto más se familiarice con IntelliSense, más rápidamente podrá escribir su propio código. El método `showButton_Click()` final tendrá el siguiente aspecto. (Pulse la pestaña **VB** para ver la versión de Visual Basic del código).

         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea [Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).

- Para volver al paso anterior del tutorial, vea [Paso 7: Agregar componentes de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md).
