---
title: "Customize Control Binding (Personalizar enlace a controles) (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Personalizar enlace de control (cuadro de diálogo)"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Customize Control Binding (Personalizar enlace a controles) (Cuadro de di&#225;logo)
Use el cuadro de diálogo **Customize Control Binding** \(Personalizar enlace a controles\) para especificar qué controles están disponibles para los elementos en la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
 Cada elemento de la ventana **Orígenes de datos** tiene asociada una lista de controles que se pueden enlazar al elemento.  Los controles disponibles de cada elemento se determinan por el tipo de datos del elemento.  Cada tipo de datos tiene una lista de controles asociados válidos definida en este cuadro de diálogo, incluido un control predeterminado.  
  
 Antes de arrastrar un elemento a una superficie de diseño para crear un control enlazado a datos, se puede seleccionar qué control se debe crear.  Si se arrastra un elemento desde la ventana **Orígenes de datos** hasta una superficie de diseño sin seleccionar un control, el control predeterminado que corresponde al tipo de datos del elemento seleccionado se agrega a la superficie de diseño.  
  
 Para obtener más información sobre cómo usar este cuadro de diálogo para personalizar la lista de controles de los elementos de la ventana **Orígenes de datos**, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Lista de UIElement  
 **Tipo de datos**  
 Muestra una lista de los tipos que se asocian a los controles:  
  
-   Las tablas, entidades y objetos se representan como tipos **\[Lista\]**.  
  
-   Las columnas o propiedades públicas de entidades y objetos se representan como el tipo de datos real de la columna o propiedad en el almacén de datos subyacente.  
  
-   Los objetos con formas definidas por el usuario se representan como **\[Other\]**.  Por ejemplo, si la aplicación tiene un control personalizado que muestra los datos de más de una propiedad de un objeto, seleccione el tipo de datos **\[Otro\]** para su control.  
  
 **Controles asociados**  
 Muestra una lista de los controles que se pueden asociar a un tipo de datos determinado.  Si desea asociar un control determinado al tipo de datos seleccionado en la lista **Tipo de datos**, active la casilla correspondiente.  Desactive la casilla para quitar una asociación.  Los controles activados aparecen en el menú contextual presentado en la ventana **Orígenes de datos** de un elemento del tipo de datos asociado.  
  
 Para agregar controles a la lista, agregue controles que tengan uno de los posibles atributos de enlace de datos al **Cuadro de herramientas**.  Para obtener más información, vea [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Establecer predeterminado**  
 Asigna el tipo de control seleccionado para que sea el predeterminado para los elementos del tipo de datos seleccionado.  El control predeterminado aparece como la primera opción que se puede seleccionar en el menú contextual presentado por la ventana **Orígenes de datos** de un elemento.  Sólo se puede asignar un tipo de control como valor predeterminado para un tipo de datos.  
  
 **Borrar predeterminado**  
 Quita la designación de un control como valor predeterminado del tipo de datos seleccionado.  Si no hay ningún valor predeterminado para el tipo de datos seleccionado, aparece **\[Ninguno\]** como primera selección en el menú contextual presentado por la ventana **Orígenes de datos** para un elemento del tipo asociado.  
  
## Vea también  
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)