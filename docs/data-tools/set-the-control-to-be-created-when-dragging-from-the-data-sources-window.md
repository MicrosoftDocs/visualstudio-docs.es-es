---
title: "Establecer el control que se crear&#225; al arrastrar desde la ventana Or&#237;genes de datos | Microsoft Docs"
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
  - "Ventana de orígenes de datos, seleccionar controles"
  - "Formularios Windows Forms, mostrar datos"
  - "datos [Visual Studio], mostrar en formularios Windows Forms"
  - "datos [Visual Studio], ventana Orígenes de datos"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Establecer el control que se crear&#225; al arrastrar desde la ventana Or&#237;genes de datos
Puede crear controles enlazados a datos si arrastra los elementos desde la ventana **Orígenes de datos** hasta WPF Designer o el Diseñador de Windows Forms.  Cada elemento de la ventana **Orígenes de datos** tiene un control predeterminado que se crea al arrastrar el elemento hacia el diseñador.  Sin embargo, puede elegir crear un control diferente.  
  
## Establecer los controles que se van a crear para tablas de datos u objetos  
 Antes de arrastrar los elementos que representan objetos o tablas de datos a la ventana **Orígenes de datos**, puede decidir mostrar todos los datos en un control o mostrar cada columna o propiedad en un control independiente.  
  
 En este contexto, el término *objeto* hace referencia a un objeto comercial personalizado, una entidad \(en un Entity Data Model\) o un objeto devuelto por un servicio.  
  
#### Para establecer los controles que se van a crear para tablas de datos u objetos  
  
1.  Asegúrese de que el Diseñador de Windows Forms o de WPF está abierto.  
  
2.  En la ventana **Orígenes de datos**, seleccione el elemento que representa el objeto o la tabla de datos que desea establecer.  
  
3.  Haga clic en el menú desplegable del elemento y, a continuación, en uno de los siguientes elementos en el menú:  
  
    -   Para mostrar cada campo de datos en un control independiente, haga clic en **Detalles**.  Al arrastrar el elemento de datos hacia el diseñador, se creará un control enlazado a datos diferente por cada columna o propiedad del objeto o tabla de datos primaria, junto con las etiquetas de cada control.  
  
    -   Para mostrar todos los datos en un control único, seleccione un control diferente de la lista, como **DataGrid** o **List** en una aplicación WPF o **DataGridView** en una aplicación de Windows Forms.  
  
     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework sea el destino del proyecto y si se han agregado controles personalizados que admiten el enlace de datos al **Cuadro de herramientas**.  Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista.  Para obtener más información, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para obtener información sobre cómo crear un control de Windows Forms personalizado que se pueda agregar a la lista de controles para objetos o tablas de datos en la ventana **Orígenes de datos**, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## Establecer los controles que se van a crear para propiedades o columnas de datos  
 Antes de arrastrar al diseñador un elemento que representa una columna o la propiedad de un objeto en la ventana **Orígenes de datos**, puede establecer el control que se va a crear.  
  
#### Para establecer los controles que se van a crear para columnas o propiedades  
  
1.  Asegúrese de que el Diseñador de Windows Forms o de WPF está abierto.  
  
2.  En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.  
  
3.  Seleccione cada columna o propiedad para la que desea establecer el control que se va a crear.  
  
4.  Haga clic en el menú desplegable de la columna o propiedad y seleccione el control que desea crear cuando el elemento se arrastre al diseñador.  
  
     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework sea el destino del proyecto y qué controles personalizados que admiten el enlace de datos se hayan agregado al **Cuadro de herramientas**.  Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista.  Para obtener más información, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para obtener información sobre cómo crear un control personalizado que se pueda agregar a la lista de controles para columnas de datos o propiedades en la ventana **Orígenes de datos**, vea [Tutorial: Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Seleccione **Ninguno** en el menú desplegable si no desea crear ningún control.  Esto es útil si desea arrastrar la tabla o el objeto principal al diseñador, pero sin incluir la columna o propiedad concreta.  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)