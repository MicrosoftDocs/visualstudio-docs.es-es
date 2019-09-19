---
title: 'Tutorial 1: Crear un visor de imágenes'
ms.date: 08/30/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c0f867179fd78ecb753a9b66cfbdb8479e16c3b
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913268"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutorial 1: Crear un visor de imágenes

En este tutorial, compilará una aplicación que carga una imagen de un archivo y la muestra en una ventana. Aprenderá a usar el **Diseñador de Windows Forms** para arrastrar controles como botones y cuadros de imagen al formulario, a establecer sus propiedades y a usar los contenedores para cambiar el tamaño del formulario de manera fluida. También empezará a escribir código.

> [!NOTE]
> En este tutorial, se trata tanto Visual C# como Visual Basic, por lo que deberá centrarse en la información específica del lenguaje de programación que use.

Este tutorial le guiará por las tareas siguientes:

* Cree un nuevo proyecto.

* Probar (depurar) una aplicación.

* Agregar controles básicos, como casillas y botones, a un formulario.

* Colocar controles en un formulario mediante diseños.

* Agregar los cuadros de diálogo **Abrir archivo** y **Color** a un formulario.

* Escribir código mediante IntelliSense y fragmentos de código.

* Escribir métodos de control de eventos.

Cuando termine, la aplicación debe ser similar a la de la imagen siguiente:

![Aplicación de visor de imágenes que se crea en este tutorial](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Vínculos del tutorial

|Title|DESCRIPCIÓN|
|-----------|-----------------|
|[Paso 1: Crear un proyecto de aplicación de Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Para empezar, cree un proyecto de aplicación de Windows Forms.|
|[Paso 2: Ejecución de la aplicación de visor de imágenes](../ide/step-2-run-your-program.md)|Ejecute el proyecto de aplicación de Windows Forms que ha creado en el paso anterior.|
|[Paso 3: Establecer las propiedades del formulario](../ide/step-3-set-your-form-properties.md)|Cambiar el aspecto del formulario mediante la ventana **Propiedades**.|
|[Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Agregue un control `TableLayoutPanel` al formulario.|
|[Paso 5: Agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md)|Agregar controles, como un control `PictureBox` y un control `CheckBox`, al formulario. Agregar botones al formulario.|
|[Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md)|Cambiar el nombre de los botones por otros más significativos.|
|[Paso 7: Agregar componentes de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md)|Agregue un componente `OpenFileDialog` y un componente `ColorDialog` al formulario.|
|[Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Escribir código mediante la herramienta IntelliSense.|
|[Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md)|Revisar y probar el código. Agregar comentarios según sea necesario.|
|[Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Escribir código para hacer que funcionen otros botones y una casilla mediante IntelliSense.|
|[Paso 11: Ejecución de la aplicación y prueba de otras características](../ide/step-11-run-your-program-and-try-other-features.md)|Ejecutar la aplicación y establecer el color de fondo. Probar con otras características, como cambiar colores, fuentes y bordes.|

## <a name="next-steps"></a>Pasos siguientes

Para comenzar el tutorial, empiece por el **[Paso 1: Creación de un proyecto de aplicación de Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)** .

## <a name="see-also"></a>Vea también

* [Más tutoriales de C#](/visualstudio/get-started/csharp/)
* [Tutoriales de Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriales de C++](../ide/getting-started-with-cpp-in-visual-studio.md)
