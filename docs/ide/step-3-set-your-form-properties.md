---
title: 'Paso 3: Establecer las propiedades del formulario'
description: Obtenga información sobre cómo usar la ventana Propiedades para cambiar la apariencia del formulario.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10f021e8f8151216cd2728e1e9723b0edb9b3e1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950736"
---
# <a name="step-3-set-your-form-properties"></a>Paso 3: Establecer las propiedades del formulario

Después, se usa la ventana **Propiedades** para cambiar la apariencia del formulario.

## <a name="how-to-set-your-form-properties"></a>Procedimientos para establecer las propiedades del formulario

1. Asegúrese de que está en el **Diseñador de Windows Forms**. En el entorno de desarrollo integrado (IDE) de Visual Studio, elija la pestaña **Form1.cs [Diseño]** (o la pestaña **Form1.vb [Diseño]** en Visual Basic).

1. Elija cualquier parte del formulario **Form1** para seleccionarlo. Examine la ventana **Propiedades**, que ahora debería mostrar las propiedades del formulario. Los formularios tienen varias propiedades. Por ejemplo, puede establecer el color del primero plano y del fondo, el texto de título que aparece en la parte superior del formulario, el tamaño del formulario y otras propiedades.

   > [!NOTE]
   > Si la ventana **Propiedades** no aparece, elija el botón cuadrado **Detener depuración** de la barra de herramientas para detener la aplicación o simplemente cierre la ventana. Si la aplicación está detenida y todavía no ve la ventana **Propiedades**, elija **Ver** > **Ventana Propiedades** en la barra de menús.

1. Una vez seleccionado el formulario, busque la propiedad **Texto** en la ventana **Propiedades**. En función del orden de la lista, puede que deba desplazarse hacia abajo. Elija **Texto**, escriba **Visor de imágenes** y elija **Entrar**.  Ahora, el formulario debería tener el texto **Visor de imágenes** en la barra de título y la ventana **Propiedades** debería parecerse a la captura de pantalla siguiente.

    ![Ventana Propiedades](../ide/media/express_edittextproperty.png)<br>
   *Ventana **Propiedades** __*

   > [!NOTE]
   > Las propiedades se pueden ordenar en vistas **por categorías** o **alfabéticamente**. Puede alternar entre estas dos vistas con los botones de la ventana **Propiedades**. En este tutorial, resulta más fácil encontrar las propiedades en la vista **alfabética**.

1. Vuelva al **Diseñador de Windows Forms**. Elija el controlador de arrastre inferior derecho del formulario, que es el cuadradito blanco que aparece en el vértice inferior derecho del formulario y tiene el siguiente aspecto.

    ![Controlador de arrastre](../ide/media/express_bottomrt_drag.png)<br>
   *Controlador de arrastre*

    Arrastre el controlador para cambiar el tamaño del formulario de modo que resulte más ancho y un poco más alto.

1. Fíjese en la ventana **Propiedades** y observe que la propiedad **Size** ha cambiado. La propiedad **Size** cambia cada vez que se cambia el tamaño del formulario. Pruebe a arrastrar el controlador del formulario para cambiar su tamaño a unas medidas aproximadas (no es necesario que sean exactas) de **550, 350**, que son las que deberían funcionar bien para este proyecto. Si quiere, también puede escribir los valores directamente en la propiedad **Size** y presionar la tecla **Entrar**.

1. Vuelva a ejecutar la aplicación. Recuerde que puede usar cualquiera de los métodos siguientes para ejecutar la aplicación.

   - Elija la tecla **F5**.

   - En la barra de menús, seleccione **Depurar** > **Iniciar depuración**.

   - En la barra de herramientas, elija el botón **Iniciar depuración**, que es similar al siguiente.

      ![Botón de la barra de herramientas Iniciar depuración](../ide/media/express_icondebug.png)<br>
     *Botón de la barra de herramientas **Iniciar depuración** __*

     Como antes, el IDE compila y ejecuta la aplicación, y aparece una ventana.

1. Antes de ir al paso siguiente, detenga la aplicación, ya que el IDE no le permitirá cambiarla mientras está en ejecución. Recuerde que puede usar cualquiera de los métodos siguientes para detener la aplicación.

   - En la barra de herramientas, elija el botón **Detener depuración**.

   - En la barra de menús, seleccione **Depurar** > **Detener depuración**.

   - Use el teclado y presione **Mayús**+**F5**.

   - Elija el botón **X** de la esquina superior de la ventana **Visor de imágenes**.

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 4: Diseño de un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 2: Ejecutar la aplicación de visor de imágenes](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
