---
title: Enlazar controles de formularios Windows Forms a datos en Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7ade7aa6e103a8637d26b10029faabc434ce3a83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Enlazar controles de formularios Windows Forms a datos en Visual Studio
Para mostrar datos a los usuarios de la aplicación, puede enlazarlos a Windows Forms. Para crear estos controles enlazados a datos, puede arrastrar elementos desde la **orígenes de datos** ventana en el Diseñador de Windows Forms en Visual Studio.
  
![La operación de arrastrar del origen de datos](../data-tools/media/raddata-data-source-drag-operation.png "raddata origen de datos de la operación de arrastrar")

Antes de arrastrar elementos, puede establecer el tipo de control que desea enlazar. Aparecen valores diferentes según si eligió la tabla propiamente dicho o una columna individual.  También puede establecer valores personalizados. Para una tabla, "Detalles" significa que cada columna se enlaza a un control independiente.  

![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata el origen de datos de enlace para DataGridView")  
  
## <a name="bindingsource-and-bindingnavigator-controls"></a>Componente BindingSource y controles de BindingNavigator
El componente <xref:System.Windows.Forms.BindingSource> sirve para dos propósitos. En primer lugar, proporciona una capa de abstracción cuando se enlazan los controles a datos. Controles del formulario se enlazan a la <xref:System.Windows.Forms.BindingSource> componente en lugar de directamente a un origen de datos. Segundo, puede administrar una colección de objetos. Al agregar un tipo a <xref:System.Windows.Forms.BindingSource>, se crea una lista de ese tipo.  
  
Para obtener más información acerca del componente <xref:System.Windows.Forms.BindingSource>, vea:  
  
-   [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)  
  
-   [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
-   [Arquitectura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)  
  
El [control BindingNavigator de formularios](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) proporciona una interfaz de usuario para navegar por los datos mostrados por una aplicación de Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView  
Para una [DataGridView (control)](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), toda la tabla está enlazada a ese control único. Cuando se arrastra un control DataGridView al formulario, una herramienta de banda para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>) también aparece. A [conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes. En la siguiente ilustración, también se agrega un TableAdapterManager porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados de la clase de formulario. El código generado automáticamente para rellenar el control DataGridView se encuentra en el controlador de eventos form_load. El código para guardar los datos para actualizar la base de datos se encuentra en el controlador de eventos de guardar para BindingNavigator. Puede mover o modificar este código según sea necesario.  
  
![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
Puede personalizar el comportamiento de DataGridView y BindingNavigator haciendo clic en la etiqueta inteligente en la esquina superior derecha de cada uno:  
  
![Etiquetas inteligentes de DataGridView y enlace navegador](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView y enlace navegador de etiquetas inteligentes")  
  
Si los controles de la aplicación necesita no está disponible desde dentro de la **orígenes de datos** ventana, puede agregar controles. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
También puede arrastrar elementos desde la **orígenes de datos** ventana a los controles en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus datos enlaces se restablecen en el elemento arrastrado más recientemente. Para ser destinos de colocación válidos, controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado en él desde el **orígenes de datos** ventana. Por ejemplo, no es válido a arrastrar un elemento que tiene un tipo de datos de <xref:System.DateTime> en un <xref:System.Windows.Forms.CheckBox>, porque el <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.  
  
## <a name="bind-to-data-in-individual-controls"></a>Enlazar a datos en controles individuales  
Al enlazar un origen de datos "Detalles", cada columna del conjunto de datos se enlaza a un control independiente.  
  
![Enlazar el origen de datos para obtener más información](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origen de datos de enlace para obtener más información")  
  
> [!IMPORTANT]
> Tenga en cuenta que en la ilustración anterior, se arrastra desde la propiedad Orders de la tabla Customers, no de la tabla Orders. Mediante un enlace a la propiedad Customer.Orders, los comandos de navegación realizados en el control DataGridView se reflejan inmediatamente en los controles de detalles. Si arrastró desde la tabla Orders, los controles todavía se enlazaría al conjunto de datos, pero no que no se sincronizan con el control DataGridView.  
  
La ilustración siguiente muestra el valor predeterminado los controles enlazados a datos que se agregan al formulario después de que se enlaza la propiedad de pedidos en la tabla Customers "Detalles" en el **orígenes de datos** ventana.  
  
![Tabla de pedidos enlazada a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png "enlazado detalles de la tabla de pedidos raddata")  
  
Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta permite que las personalizaciones que se aplican a solo ese control.
  
## <a name="see-also"></a>Vea también
[Enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Enlace de datos en formularios Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)