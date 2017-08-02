---
title: "C&#243;mo: Mostrar datos relacionados en una aplicaci&#243;n de Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "datos [Windows Forms], mostrar"
  - "datos [Windows Forms], relacionados"
  - "mostrar datos en formularios, datos relacionados"
  - "mostrar datos, datos relacionados"
  - "mostrar datos de tablas"
  - "mostrar información de tablas"
  - "mostrar tablas, datos relacionados"
  - "datos relacionados, mostrar"
  - "Windows Forms, mostrar datos"
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Mostrar datos relacionados en una aplicaci&#243;n de Windows Forms
Es posible mostrar los datos relacionados arrastrando elementos que comparten el mismo nodo de tabla principal desde la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) hacia su formulario.  Por ejemplo, si se tiene un origen de datos que tiene una tabla `Customers` y una tabla `Orders` relacionada, puede que vea ambas tablas como nodos de nivel superior \(en la vista de árbol\) en la ventana **Orígenes de datos**.  Expanda el nodo `Customers` para que pueda ver las columnas y observará que la última columna de la lista es un nodo expansible que representa la tabla `Orders`.  Este nodo representa los pedidos relacionados para un cliente.  Esto significa que si desea crear un formulario que permita seleccionar un cliente y a continuación mostrar una lista de pedidos para ese cliente, puede arrastrar los elementos que desea mostrar desde esta jerarquía única.  
  
 ![Ventana Orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif "DataSources2")  
Crear controles enlazados a datos que muestren los registros relacionados  
  
 ![vínculo a vídeo](~/data-tools/media/playvideo.gif "PlayVideo") Para obtener una versión en vídeo de este tema, vea [cómo actualizar tablas relacionadas](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### Para crear controles que muestren los registros relacionados  
  
1.  Abra su formulario en el [Windows Forms Designer](http://msdn.microsoft.com/es-es/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Abra la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Expanda el nodo que representa la tabla primaria en la relación. \(La tabla primaria es la tabla en lado "uno" de una relación uno a varios.\)  
  
4.  Arrastre los elementos que desea mostrar de la tabla primaria de la relación desde la ventana **Orígenes de datos** hasta el formulario.  
  
5.  Las tablas secundarias relacionadas aparecen como nodos expansibles en la parte inferior de la lista de columnas de la tabla primaria.  Arrastre los elementos que desea mostrar de este tipo de nodo relacionado hasta el formulario.  
  
    > [!NOTE]
    >  Si arrastra un elemento desde un nodo de nivel superior, se crean [Componentes BindingSource](../Topic/BindingSource%20Component.md) no relacionados e independientes que no facilitan la navegación de los registros relacionados.  Para enlazar datos relacionados, debe seleccionar las tablas del mismo nodo jerárquico.  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Cómo: Explorar datos con el control BindingNavigator de formularios Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)