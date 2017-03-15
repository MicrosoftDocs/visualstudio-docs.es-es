---
title: "Paso 7: Agregar componentes de di&#225;logo al formulario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Paso 7: Agregar componentes de di&#225;logo al formulario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para que el programa abra archivos de imagen y para elegir un color de fondo, en este paso agregará un componente **OpenFileDialog** y un componente **ColorDialog** al formulario.  
  
 En algunos sentidos, un componente es como un control.  Se utiliza el Cuadro de herramientas para agregar un componente al formulario y se establecen sus propiedades mediante la ventana **Propiedades**.  Sin embargo, a diferencia de un control, al agregar un componente al formulario no se agrega un elemento visible que el usuario puede ver.  En cambio, se proporcionan determinados comportamientos que se pueden desencadenar mediante código.  Un componente es lo que abre un cuadro de diálogo **Abrir archivo**.  
  
 ![vínculo a vídeo](../data-tools/media/playvideo.png "PlayVideo") Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic \(vídeo 3\)](http://go.microsoft.com/fwlink/?LinkId=205213) o el [Tutorial 1: Crear un visor de imágenes en C\# \(vídeo 3\)](http://go.microsoft.com/fwlink/?LinkId=205202).  En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario.  Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
### Para agregar componentes de cuadro de diálogo al formulario  
  
1.  Elija el Diseñador de Windows Forms \(Form1.cs \[Diseño\] o Form1.vb \[Diseño\]\) y después abra el grupo **Cuadros de diálogo** del cuadro de herramientas.  
  
    > [!NOTE]
    >  El grupo **Cuadros de diálogo** del Cuadro de herramientas tiene componentes que abren automáticamente muchos cuadros de diálogo de gran utilidad y que se pueden utilizar para abrir y guardar archivos, examinar carpetas y elegir fuentes o colores.  En este proyecto se utilizan dos componentes de cuadro de diálogo: **OpenFileDialog** y **ColorDialog**.  
  
2.  Para agregar un componente denominado **a openFileDialog1** al formulario, haga doble clic en **OpenFileDialog**.  Para agregar un componente denominado **colorDialog1** al formulario, haga doble clic en **ColorDialog** en el Cuadro de herramientas. \(Este se utiliza en el siguiente paso del tutorial.\) Debería aparecer un área en la parte inferior del Diseñador de Windows Forms \(bajo el formulario del Visor de imágenes\), con un icono para cada uno de los dos componentes de cuadro de diálogo agregados, tal y como se muestra en la siguiente imagen.  
  
     ![Componentes del cuadro de diálogo](../ide/media/express_dialogsadded.png "Express\_DialogsAdded")  
Componentes de cuadro de diálogo  
  
3.  Elija el icono **openFileDialog1** del área de la parte inferior del Diseñador de Windows Forms.  Establezca dos propiedades:  
  
    -   Establezca la propiedad **Filter** tal y como se indica a continuación \(puede copiarlo y pegarlo\):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Establezca la propiedad **Title** en lo siguiente: Seleccionar un archivo de imagen  
  
         Los valores de la propiedad **Filter** especifican las clases de tipos de archivo que se mostrarán en el cuadro de diálogo **Seleccionar un archivo de imagen**.  
  
    > [!NOTE]
    >  Para ver un ejemplo del cuadro de diálogo **Abrir archivo** en una aplicación diferente, abra el Bloc de notas o Paint y, en la barra de herramientas, elija **Archivo**, **Abrir**.  Observe que hay una lista desplegable de **tipo de archivo** en la parte inferior.  Acabamos de utilizar la propiedad **Filter** del componente **OpenFileDialog** para configurarla.  Observe también que las propiedades **Title** y **Filter** están en negrita en la ventana **Propiedades**.  El IDE lo hace para mostrarle todas las propiedades que han cambiado respecto de sus valores predeterminados.  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md).