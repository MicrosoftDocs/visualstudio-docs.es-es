---
title: 'Tutorial 1: Crear un visor de imágenes'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46ce6f92acb7ed6e92af07729a14720d3a8421a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821823"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutorial 1: Crear un visor de imágenes

En este tutorial, compilará un programa que carga una imagen de un archivo y la muestra en una ventana. Aprenderá a usar el **Diseñador de Windows Forms** para arrastrar controles como botones y cuadros de imagen en el formulario, establecer sus propiedades y usar los contenedores para cambiar el tamaño del formulario de manera fluida. También empezará a escribir código. Aprenderá a:

- Cree un nuevo proyecto.

- Probar (depurar) una aplicación.

- Agregar controles básicos, como casillas y botones, a un formulario.

- Colocar controles en un formulario mediante los diseños.

- Agregar los cuadros de diálogo **Abrir archivo** y **Color** a un formulario.

- Escribir código mediante IntelliSense y fragmentos de código.

- Escribir métodos de control de eventos.

Cuando termine, el programa se parecerá al de la ilustración siguiente:

![Imagen que creará en este tutorial](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Vínculos del tutorial

Para descargar una versión completa del ejemplo, vea [Complete Picture Viewer tutorial sample](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Ejemplo completo del tutorial de visor de imágenes).

![vínculo al vídeo](../data-tools/media/playvideo.gif) Para obtener una versión en vídeo de este tema, vea [Cómo: Crear un visor de imágenes en Visual Basic](http://go.microsoft.com/fwlink/?LinkId=205207) o [Cómo: Crear un visor de imágenes en C#](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio. En este tutorial, se trata tanto Visual C# como Visual Basic, por lo que deberá centrarse en la información específica del lenguaje de programación que use.
>
> Para ver el código de Visual Basic, pulse la pestaña **VB** que se encuentra en la parte superior de los bloques de código; para ver el código de Visual C#, pulse la pestaña **C#**. Si quiere obtener más información sobre Visual C++, vea [Introducción](../ide/getting-started-with-cpp-in-visual-studio.md) y el [Tutorial del lenguaje C++](http://www.cplusplus.com/doc/tutorial/).
>
> Si le interesa aprender a escribir aplicaciones para UWP de Visual C# o Visual Basic, vea [Crear aplicaciones para UWP](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Paso 1: Crear un proyecto de aplicación de Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Empezar a crear un proyecto de aplicación de Windows Forms.|
|[Paso 2: Ejecutar el programa](../ide/step-2-run-your-program.md)|Ejecutar el programa de aplicación de Windows Forms que se creó en el paso anterior.|
|[Paso 3: Establecer las propiedades del formulario](../ide/step-3-set-your-form-properties.md)|Cambiar el aspecto del formulario mediante la ventana **Propiedades**.|
|[Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Agregue un control `TableLayoutPanel` al formulario.|
|[Paso 5: Agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md)|Agregar controles, como un control `PictureBox` y un control `CheckBox`, al formulario. Agregar botones al formulario.|
|[Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md)|Cambiar el nombre de los botones por otros más significativos.|
|[Paso 7: Agregar componentes de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md)|Agregue un componente `OpenFileDialog` y un componente `ColorDialog` al formulario.|
|[Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Escribir código mediante la herramienta IntelliSense.|
|[Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md)|Revisar y probar el código. Agregar comentarios según sea necesario.|
|[Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Escribir código para hacer que funcionen otros botones y una casilla mediante IntelliSense.|
|[Paso 11: Ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md)|Ejecutar el programa y establecer el color de fondo. Probar con otras características, como cambiar colores, fuentes y bordes.|
