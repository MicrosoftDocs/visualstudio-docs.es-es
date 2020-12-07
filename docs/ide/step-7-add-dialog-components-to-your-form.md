---
title: 'Paso 7: Agregar componentes de diálogo al formulario'
description: Aprenda a agregar un componente de diálogo <xref:System.Windows.Forms.OpenFileDialog> y un componente de diálogo <xref:System.Windows.Forms.ColorDialog> al formulario.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37cbd2ca1f0207eaf2a41f6a08248bcedcfbe5bb
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479477"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Paso 7: Agregar componentes de diálogo al formulario

Para permitir que la aplicación abra archivos de imagen y elegir un color de fondo, en este paso agregará un componente <xref:System.Windows.Forms.OpenFileDialog> y un componente <xref:System.Windows.Forms.ColorDialog> al formulario.

En algunos sentidos, un componente es como un control. El **cuadro de herramientas** se usa para agregar un componente al formulario, y las propiedades se establecen mediante la ventana **Propiedades**. Sin embargo, a diferencia de un control, al agregar un componente al formulario no se agrega un elemento visible que el usuario puede ver. En cambio, se proporcionan determinados comportamientos que se pueden desencadenar mediante código. Un componente es lo que abre un cuadro de diálogo **Abrir archivo**.

## <a name="to-add-dialog-components-to-your-form"></a>Para agregar componentes de cuadro de diálogo al formulario

1. Elija el **Diseñador de Windows Forms** (**Form1.cs [Diseño]**) y después abra el grupo **Cuadros de diálogo** del **Cuadro de herramientas**.

    > [!NOTE]
    > El grupo **Cuadros de diálogo** del **cuadro de herramientas** tiene componentes que abren automáticamente muchos cuadros de diálogo de gran utilidad y que se pueden usar para abrir y guardar archivos, examinar carpetas y elegir fuentes o colores. En este proyecto se usan dos componentes de cuadro de diálogo: OpenFileDialog y ColorDialog.

1. Para agregar un componente denominado **openFileDialog1** al formulario, haga doble clic en **OpenFileDialog**. Para agregar un componente denominado **colorDialog1** al formulario, haga doble clic en **ColorDialog** en el **cuadro de herramientas**. (Este se utiliza en el siguiente paso del tutorial.) Debería aparecer un área en la parte inferior del **Diseñador de Windows Forms** (bajo el formulario del **Visor de imágenes**), con un icono para cada uno de los dos componentes de cuadro de diálogo agregados, como se muestra en la imagen siguiente.

     ![Componentes de cuadro de diálogo](../ide/media/express_dialogsadded.png)<br>*Componentes de *_cuadro de diálogo_* __*

1. Elija el icono **openFileDialog1** del área de la parte inferior del **Diseñador de Windows Forms**. Establezca dos propiedades:

    - Establezca la propiedad **Filter** tal y como se indica a continuación (puede copiarlo y pegarlo):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Establezca la propiedad **Title** en lo siguiente: **Select a picture file** (Seleccionar un archivo de imagen).

         Los valores de la propiedad **Filter** especifican las clases de tipos de archivo que se mostrarán en el cuadro de diálogo **Select a picture file** (Seleccionar un archivo de imagen).

    > [!TIP]
    > Para ver un ejemplo del cuadro de diálogo **Abrir archivo** en una aplicación diferente, abra el **Bloc de notas** o **Paint** y, en la barra de menús, elija **Archivo** > **Abrir**. Observe que hay una lista desplegable junto al nombre de archivo que permite elegir el tipo de archivo. <br/><br/>Acaba de usar la propiedad **Filter** del componente **OpenFileDialog** para configurarlo en la aplicación. Observe también que las propiedades **Title** y **Filter** están en negrita en la ventana **Propiedades**. El IDE lo hace para mostrarle todas las propiedades que han cambiado respecto de sus valores predeterminados.

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 8: Escritura de código para el controlador de eventos de botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
