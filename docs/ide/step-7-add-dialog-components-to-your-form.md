---
title: 'Paso 7: Agregar componentes de diálogo al formulario'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff0ed047ed1c77638aed1128d8a73dc3347fd2e6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905577"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Paso 7: Agregar componentes de diálogo al formulario
Para que el programa abra archivos de imagen y para elegir un color de fondo, en este paso agregará un componente <xref:System.Windows.Forms.OpenFileDialog> y un componente <xref:System.Windows.Forms.ColorDialog> al formulario.

 En algunos sentidos, un componente es como un control. El **cuadro de herramientas** se usa para agregar un componente al formulario, y las propiedades se establecen mediante la ventana **Propiedades**. Sin embargo, a diferencia de un control, al agregar un componente al formulario no se agrega un elemento visible que el usuario puede ver. En cambio, se proporcionan determinados comportamientos que se pueden desencadenar mediante código. Un componente es lo que abre un cuadro de diálogo **Abrir archivo**.

 ![vínculo al vídeo](../data-tools/media/playvideo.gif)Para obtener una versión en vídeo de este tema, vea [Tutorial 1: Crear un visor de imágenes en Visual Basic - Vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205213) o [Tutorial 1: Crear un visor de imágenes en C# - Vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205202). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

## <a name="to-add-dialog-components-to-your-form"></a>Para agregar componentes de cuadro de diálogo al formulario

1.  Elija el **Diseñador de Windows Forms** (**Form1.cs [Diseño]** o **Form1.vb [Diseño]**) y después abra el grupo **Cuadros de diálogo** del **cuadro de herramientas**.

    > [!NOTE]
    >  El grupo **Cuadros de diálogo** del **cuadro de herramientas** tiene componentes que abren automáticamente muchos cuadros de diálogo de gran utilidad y que se pueden usar para abrir y guardar archivos, examinar carpetas y elegir fuentes o colores. Use dos componentes de cuadro de diálogo en este proyecto: OpenFileDialog y ColorDialog.

2.  Para agregar un componente denominado **openFileDialog1** al formulario, haga doble clic en **OpenFileDialog**. Para agregar un componente denominado **colorDialog1** al formulario, haga doble clic en **ColorDialog** en el **cuadro de herramientas**. (Este se utiliza en el siguiente paso del tutorial.) Debería aparecer un área en la parte inferior del **Diseñador de Windows Forms** (bajo el formulario del **Visor de imágenes**), con un icono para cada uno de los dos componentes de cuadro de diálogo agregados, tal y como se muestra en la siguiente imagen.

     ![Componentes del cuadro de diálogo](../ide/media/express_dialogsadded.png)
**Dialog** components

3.  Elija el icono **openFileDialog1** del área de la parte inferior del **Diseñador de Windows Forms**. Establezca dos propiedades:

    -   Establezca la propiedad **Filter** tal y como se indica a continuación (puede copiarlo y pegarlo):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    -   Establezca la propiedad **Título** en lo siguiente: **Seleccione un archivo de imagen**

         Los valores de la propiedad **Filter** especifican las clases de tipos de archivo que se mostrarán en el cuadro de diálogo **Select a picture file** (Seleccionar un archivo de imagen).

    > [!NOTE]
    >  Para ver un ejemplo del cuadro de diálogo **Abrir archivo** en una aplicación diferente, abra el **Bloc de notas** o **Paint** y, en la barra de menús, elija **Archivo** > **Abrir**. Observe que hay una lista desplegable de **tipo de archivo** en la parte inferior. Acabamos de usar la propiedad **Filter** del componente **OpenFileDialog** para configurarlo. Observe también que las propiedades **Title** y **Filter** están en negrita en la ventana **Propiedades**. El IDE lo hace para mostrarle todas las propiedades que han cambiado respecto de sus valores predeterminados.

## <a name="to-continue-or-review"></a>Para continuar o revisar

-   Para ir al siguiente paso del tutorial, vea [Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

-   Para volver al paso anterior del tutorial, vea [Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md).
