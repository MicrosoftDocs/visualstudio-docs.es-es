---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
título: "controles de formularios Windows Forms de enlace a datos | Microsoft Docs"ms.custom:" "ms.date: ms.reviewer" 11/04/2016":" "ms.suite:" "ms.tgt_pltfrm:" "ms.topic:"artículo"helpviewer_keywords: 
  - "Mostrar datos, controles de Windows Forms"
  - "Windows Forms, mostrar datos"
  - "orígenes de datos, mostrar"
  - "datos [Windows Forms], mostrar" ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 autor: ms.author "gewarren": "gewarren" administrador: ghogen ms.technology: "vs-data-tools"
---
# <a name="bind-windows-forms-controls-to-data"></a>Enlazar controles de formularios Windows Forms a datos
Puede enlazar orígenes de datos a controles arrastrando los objetos desde la **orígenes de datos** ventana en un formulario Windows Forms o en un control existente en un formulario. Antes de arrastrar elementos, puede establecer el tipo de control que desea enlazar. Aparecen valores diferentes según si eligió la tabla propiamente dicho o una columna individual.  También puede establecer valores personalizados. Para una tabla, "Detalles" significa que cada columna se enlaza a un control independiente.  

![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata el origen de datos de enlace para DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView  
Para DataGridView, toda la tabla está enlazada a ese control único. Cuando se arrastra un control DataGridView al formulario, una herramienta de banda para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>) también aparece. A [conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes. En la siguiente ilustración, también se agrega un TableAdapterManager porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados de la clase de formulario. El código generado automáticamente para rellenar el control DataGridView se encuentra en el controlador de eventos form_load. El código para guardar los datos para actualizar la base de datos se encuentra en el controlador de eventos de guardar para BindingNavigator. Puede mover o modificar este código según sea necesario.  
  
 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
 Puede personalizar el comportamiento de DataGridView y BindingNavigator haciendo clic en la etiqueta inteligente en la esquina superior derecha de cada uno:  
  
 ![Etiquetas inteligentes de DataGridView y enlace navegador](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView y enlace navegador de etiquetas inteligentes")  
  
 Si los controles de la aplicación necesita no está disponible desde dentro de la **orígenes de datos** ventana, puede agregar controles. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 También puede arrastrar elementos desde la **orígenes de datos** ventana a los controles en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus datos enlaces se restablecen en el elemento arrastrado más recientemente. Para ser destinos de colocación válidos, controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado en él desde el **orígenes de datos** ventana. Por ejemplo, no es válido a arrastrar un elemento que tiene un tipo de datos de <xref:System.DateTime> en un <xref:System.Windows.Forms.CheckBox>, porque el <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.  
  
## <a name="bind-to--data-in-individual-controls"></a>Enlazar a datos en controles individuales  
 Al enlazar un origen de datos "Detalles", cada columna del conjunto de datos se enlaza a un control independiente.  
  
 ![Enlazar el origen de datos para obtener más información](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origen de datos de enlace para obtener más información")  
  
> [!IMPORTANT]
>  Tenga en cuenta que en la ilustración anterior, se arrastra desde la propiedad Orders de la tabla Customers, no de la tabla Orders. Mediante un enlace a la propiedad Customer.Orders, los comandos de navegación realizados en el control DataGridView se reflejan inmediatamente en los controles de detalles. Si arrastró desde la tabla Orders, los controles todavía se enlazaría al conjunto de datos, pero no que no se sincronizan con el control DataGridView.  
  
 La ilustración siguiente muestra el valor predeterminado los controles enlazados a datos que se agregan al formulario después de que se enlaza la propiedad de pedidos en la tabla Customers "Detalles" en el **orígenes de datos** ventana.  
  
 ![Tabla de pedidos enlazada a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png "enlazado detalles de la tabla de pedidos raddata")  
  
 Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta permite que las personalizaciones que se aplican a solo ese control.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)