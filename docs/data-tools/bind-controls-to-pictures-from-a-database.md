---
title: "C&#243;mo: Enlazar controles a im&#225;genes desde una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Enlace de datos [formularios Windows Forms], imágenes"
  - "Orígenes de datos (ventana), configurar controles para mostrar imágenes"
  - "imágenes [Visual Basic], enlace de datos"
  - "imágenes [Visual Basic], mostrar en Windows Forms"
  - "imágenes [Visual Basic], arrastrar desde la Ventana de orígenes de datos"
  - "PictureBox (control) [Windows Forms], enlace de datos"
  - "imágenes, enlace de datos"
  - "imágenes, arrastrar desde la Ventana de orígenes de datos"
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enlazar controles a im&#225;genes desde una base de datos
Puede utilizar la ventana **Orígenes de datos** para enlazar una imagen de una base de datos a un control de su aplicación.  Por ejemplo, puede enlazar una imagen a un control <xref:System.Windows.Controls.Image> de una aplicación WPF o a un control <xref:System.Windows.Forms.PictureBox> de aplicaciones de Windows Forms.  
  
 Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes.  Los elementos de la ventana **Orígenes de datos** que están almacenados como matrices de bytes tienen su tipo de control establecido de forma predeterminada en **Ninguno**, porque las matrices de bytes pueden contener cualquier cosa, desde una matriz simple de bytes hasta el archivo ejecutable de una aplicación grande.  Para crear un control enlazado a datos para un elemento de matriz de bytes en la ventana **Orígenes de datos** que represente una imagen, debe seleccionar el control.  
  
 El procedimiento siguiente supone que la ventana **Orígenes de datos** ya incluye un elemento enlazado con la imagen.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### Para enlazar una imagen de una base de datos a un control  
  
1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.  
  
2.  En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.  
  
3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:  
  
    -   Si el diseñador WPF está abierto, seleccione **Imagen**.  
  
    -   Si el diseñador de Windows Forms está abierto, seleccione **PictureBox**.  
  
    -   También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes.  Si el control que desea utilizar no se encuentra en la lista de controles disponibles, puede agregarlo a la lista y, a continuación, seleccionarlo.  Para obtener más información, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Vea también  
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)