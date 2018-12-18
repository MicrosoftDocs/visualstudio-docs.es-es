---
title: 'Tutorial 1: Crear un visor de imagen | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cdc926121212a8082fac126e4ab91b753df7dee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884971"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutorial 1: Crear un visor de imagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, compilará un programa que carga una imagen de un archivo y la muestra en una ventana. Aprenderá a arrastrar controles como botones y cuadros de imagen en el formulario, establecer sus propiedades y utilizar los contenedores para cambiar el tamaño del formulario de manera fluida. También empezará a escribir código. Aprenderá a:  
  
- Cree un nuevo proyecto.  
  
- Probar (depurar) una aplicación.  
  
- Agregar controles básicos, como casillas y botones, a un formulario.  
  
- Colocar controles en un formulario mediante los diseños.  
  
- Agregar los cuadros de diálogo **Abrir archivo** y **Color** a un formulario.  
  
- Escribir código mediante IntelliSense y fragmentos de código.  
  
- Escribir métodos de control de eventos.  
  
  Cuando termine, el programa se parecerá al de la ilustración siguiente.  
  
  ![Imagen que creará en este tutorial](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone")  
  Imagen que creará en este tutorial  
  
  Para descargar una versión completa del ejemplo, vea [Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Ejemplo completo del tutorial de visor de imágenes).  
  
  ![vínculo al vídeo](../data-tools/media/playvideo.gif "ReproducirVídeo")Para obtener una versión en vídeo de este tema, vea el [Tutorial: Crear un visor de imágenes en Visual Basic](http://go.microsoft.com/fwlink/?LinkId=205207) o el [Tutorial: Crear un visor de imágenes en C#](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio. En este tutorial, se trata tanto Visual C# como Visual Basic, por lo que deberá centrarse en la información específica del lenguaje de programación que use.  
>   
>  Para ver el código de Visual Basic, pulse la pestaña **VB** que se encuentra en la parte superior de los bloques de código; para ver el código de Visual C#, pulse la pestaña **C#**. Si quiere obtener más información sobre Visual C++, vea [Introducción](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) y el [Tutorial del lenguaje C++](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Si quiere obtener más información sobre cómo escribir aplicaciones en Visual C# o Visual Basic para la Tienda Windows, vea [Crear la primera aplicación de la Tienda Windows con C# o Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Para obtener información sobre cómo crear aplicaciones JavaScript para la Tienda Windows, vea [Crear la primera aplicación de la Tienda Windows con JavaScript](http://msdn.microsoft.com/library/windows/apps/br211385.aspx).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Paso 1: Crear un proyecto de aplicación de Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Empezar a crear un proyecto de aplicación de Windows Forms.|  
|[Paso 2: Ejecutar el programa](../ide/step-2-run-your-program.md)|Ejecutar el programa de aplicación de Windows Forms que se creó en el paso anterior.|  
|[Paso 3: Establecer las propiedades del formulario](../ide/step-3-set-your-form-properties.md)|Cambiar el aspecto del formulario mediante la ventana **Propiedades**.|  
|[Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Agregue un control `TableLayoutPanel` al formulario.|  
|[Paso 5: Agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md)|Agregar controles, como un control `PictureBox` y un control `CheckBox`, al formulario. Agregar botones al formulario.|  
|[Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md)|Cambiar el nombre de los botones por otros más significativos.|  
|[Paso 7: Agregar componentes de diálogo al formulario](../ide/step-7-add-dialog-components-to-your-form.md)|Agregar un componente **OpenFileDialog** y un componente **ColorDialog** al formulario.|  
|[Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Escribir código mediante la herramienta IntelliSense.|  
|[Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md)|Revisar y probar el código. Agregar comentarios según sea necesario.|  
|[Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Escribir código para hacer que funcionen otros botones y una casilla mediante IntelliSense.|  
|[Paso 11: Ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md)|Ejecutar el programa y establecer el color de fondo. Probar con otras características, como cambiar colores, fuentes y bordes.|



