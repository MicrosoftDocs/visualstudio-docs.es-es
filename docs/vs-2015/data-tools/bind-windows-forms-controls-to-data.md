---
title: Enlazar controles de formularios Windows Forms a datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9b81d3d9f7425874c8a3501d8e1d49eb813b97d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996853"
---
# <a name="bind-windows-forms-controls-to-data"></a>Enlazar controles de Windows Forms a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Puede enlazar orígenes de datos a controles, arrastre objetos desde el **orígenes de datos** ventana en un formulario de Windows o en un control existente en un formulario. Antes de arrastrar elementos, puede establecer el tipo de control que desea enlazar. Aparecen valores diferentes dependiendo de si elige la tabla propiamente dicho o una columna individual.  También puede establecer valores personalizados. Para una tabla, "Detalles" significa que cada columna se enlaza a un control independiente.  
  
 ![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata origen de datos de enlace a DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView  
 Para DataGridView, toda la tabla está enlazada a ese control único. Cuando arrastre un control DataGridView hasta el formulario, una herramienta de franja para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>) también aparece. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes. En la ilustración siguiente, también se agrega un TableAdapterManager porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados en la clase de formulario. El código generado automáticamente para rellenar el control DataGridView se encuentra en el controlador de eventos form_load. El código para guardar los datos para actualizar la base de datos se encuentra en el controlador de eventos de guardar para BindingNavigator. Puede mover o modificar este código según sea necesario.  
  
 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
 Puede personalizar el comportamiento de DataGridView y BindingNavigator haciendo clic en la etiqueta inteligente en la esquina superior derecha de cada uno:  
  
 ![Etiquetas inteligentes de DataGridView y enlace Navigator](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView y enlace el navegador de etiquetas inteligentes")  
  
 Si los controles de la aplicación necesita no está disponible desde dentro de la **orígenes de datos** ventana, puede agregar controles. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 También puede arrastrar elementos desde el **orígenes de datos** ventana a los controles ya se encuentren en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus datos de restablecimiento de enlaces para el elemento arrastrado más recientemente. Para ser destinos de colocación válidos, los controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado en él desde el **orígenes de datos** ventana. Por ejemplo, no es válido para arrastrar un elemento que tiene un tipo de datos de <xref:System.DateTime> hasta un <xref:System.Windows.Forms.CheckBox>, porque el <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.  
  
## <a name="bind-to--data-in-individual-controls"></a>Enlazar a datos en controles individuales  
 Al enlazar un origen de datos a "Detalles", cada columna del conjunto de datos se enlaza a un control independiente.  
  
 ![Enlazar el origen de datos a los detalles](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origen de datos de enlace a los detalles")  
  
> [!IMPORTANT]
>  Tenga en cuenta que en la ilustración anterior, arrastra desde la propiedad Orders de la tabla Customers, no de la tabla Orders. Enlazando con la propiedad Customer.Orders, los comandos de navegación realizados en el control DataGridView se reflejan inmediatamente en los controles de detalles. Si arrastró desde la tabla Orders, todavía se enlazaría los controles al conjunto de datos, pero no se podría no pueden sincronizar con el control DataGridView.  
  
 La siguiente ilustración muestra el valor predeterminado los controles enlazados a datos que se agregan al formulario después de que se enlaza la propiedad Orders en la tabla Customers "Detalles" en el **orígenes de datos** ventana.  
  
 ![Enlazado de tabla Orders a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png "enlazado detalles de la tabla de pedidos raddata")  
  
 Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta permite que las personalizaciones que se aplican a sólo ese control.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
