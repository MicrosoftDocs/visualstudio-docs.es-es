---
title: Personalizar el Control de cuadro de diálogo de enlace | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4d47fe3962651db91dcfdf6e59653db539a9f44b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576738"
---
# <a name="customize-control-binding-dialog-box"></a>Customize Control Binding (Personalizar enlace a controles) (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **Personalizar enlace de Control** cuadro de diálogo para especificar qué controles están disponibles para los elementos de la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Cada elemento de la **orígenes de datos** ventana tiene asociada una lista de controles que pueden estar limitados por el elemento. Los controles disponibles para cada elemento se determinan por el tipo de datos del elemento. Cada tipo de datos tiene una lista de controles asociados válidos definida en este cuadro de diálogo, incluido un control predeterminado.  
  
 Antes de arrastrar un elemento a una superficie de diseño para crear un control enlazado a datos, puede seleccionar qué control va a crear. Si se arrastra un elemento desde el **orígenes de datos** ventana hasta una superficie de diseño sin seleccionar un control, el control predeterminado para el tipo de datos del elemento seleccionado se agrega a la superficie de diseño.  
  
 Para obtener más información acerca de cómo usar este cuadro de diálogo para personalizar la lista de controles para los elementos de la **orígenes de datos** ventana, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Tipo de datos**  
 Muestra una lista de tipos que se asociación a los controles:  
  
-   Las tablas, entidades y objetos se representan como **[lista]** tipos.  
  
-   Las columnas o propiedades públicas de entidades y objetos se representan como el tipo de datos real de la columna o propiedad en el almacén de datos subyacente.  
  
-   Objetos con formas definidas por el usuario se representan como **[otros]**. Por ejemplo, si la aplicación tiene un control personalizado que muestra los datos de más de una propiedad de un objeto, seleccione el **[otros]** tipo de datos para el control.  
  
 **Controles asociados**  
 Muestra una lista de controles que se pueden asociar con un tipo de datos determinado. Si desea asociar un control determinado con el tipo de datos seleccionado en el **tipo de datos** lista, seleccione la casilla correspondiente. Desactive la casilla de verificación para quitar una asociación. Comprueba los controles aparecen en el menú contextual presentado por el **orígenes de datos** ventana para un elemento del tipo de datos asociado.  
  
 Puede agregar controles a la lista mediante la adición de controles que tienen uno de varios atributos de enlace de datos a la **cuadro de herramientas**. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Establezca el valor predeterminado**  
 Asigna el tipo de control seleccionado en el valor predeterminado para los elementos del tipo de datos seleccionado. El control predeterminado aparece como la primera selección en el menú contextual presentado por el **orígenes de datos** ventana para un elemento. Tipo de solo control puede asignarse como el valor predeterminado para un tipo de datos.  
  
 **Borrar el valor predeterminado**  
 Quita la designación de un control como el valor predeterminado para el tipo de datos seleccionado. Si no hay ningún valor predeterminado para el tipo de datos seleccionado, **[Ninguno]** aparece como la primera selección en el menú contextual presentado por el **orígenes de datos** ventana para un elemento del tipo asociado.  
  
## <a name="see-also"></a>Vea también  
 [Ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)