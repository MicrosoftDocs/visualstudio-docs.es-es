---
title: Enlazar controles de formularios Windows Forms a datos en Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4652d8dd3e9be582bc15c4644711accc06fd283f
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845527"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Enlazar controles de formularios Windows Forms a datos en Visual Studio
Para mostrar datos a los usuarios de la aplicación, puede enlazarlos a Windows Forms. Para crear estos controles enlazados a datos, arrastre elementos desde el **orígenes de datos** ventana hasta el Diseñador de Windows Forms en Visual Studio.

![Operación de arrastre del origen de datos](../data-tools/media/raddata-data-source-drag-operation.png)

Antes de arrastrar elementos, puede establecer el tipo de control que desea enlazar. Aparecen valores diferentes dependiendo de si elige la tabla propiamente dicho o una columna individual.  También puede establecer valores personalizados. Para una tabla, **detalles** significa que cada columna se enlaza a un control independiente.

![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controles BindingSource y BindingNavigator
El componente <xref:System.Windows.Forms.BindingSource> sirve para dos propósitos. En primer lugar, proporciona una capa de abstracción cuando se enlazan los controles a datos. Los controles del formulario se enlazan a la <xref:System.Windows.Forms.BindingSource> componente en lugar de directamente a un origen de datos. Segundo, puede administrar una colección de objetos. Al agregar un tipo a <xref:System.Windows.Forms.BindingSource>, se crea una lista de ese tipo.

Para obtener más información acerca del componente <xref:System.Windows.Forms.BindingSource>, vea:

-   [Componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

-   [Información general del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [Arquitectura del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

El [control BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) proporciona una interfaz de usuario para navegar por los datos que se muestren en una aplicación de Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView
Para un [control DataGridView de formularios](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), toda la tabla está enlazada a ese control único. Cuando se arrastra un **DataGridView** al formulario, una herramienta de franja para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>) también aparece. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes. En la siguiente ilustración, un [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) también se agrega porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados en la clase de formulario. El código generado automáticamente para rellenar el **DataGridView** se encuentra en la `Form_Load` controlador de eventos. El código para guardar los datos para actualizar la base de datos se encuentra en la `Save` controlador de eventos para el **BindingNavigator**. Puede mover o modificar este código según sea necesario.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Puede personalizar el comportamiento de la **DataGridView** y **BindingNavigator** haciendo clic en la etiqueta inteligente en la esquina superior derecha de cada uno:

![Etiquetas inteligentes de DataGridView y navegador de enlace](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Si los controles de la aplicación necesita no está disponible desde dentro de la **orígenes de datos** ventana, puede agregar controles. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

También puede arrastrar elementos desde el **orígenes de datos** ventana a los controles ya se encuentren en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus datos de restablecimiento de enlaces para el elemento arrastrado más recientemente. Para ser destinos de colocación válidos, los controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado en él desde el **orígenes de datos** ventana. Por ejemplo, no es válido para arrastrar un elemento que tiene un tipo de datos de <xref:System.DateTime> hasta un <xref:System.Windows.Forms.CheckBox>, porque el <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.

## <a name="bind-to-data-in-individual-controls"></a>Enlazar a datos en controles individuales
Al enlazar un origen de datos a **detalles**, cada columna del conjunto de datos se enlaza a un control independiente.

![Enlazar el origen de datos a los detalles](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Tenga en cuenta que en la ilustración anterior, arrastra desde la propiedad Orders de la tabla Customers, no de la tabla Orders. Enlazando con la `Customer.Orders` comandos de navegación de propiedad realizan en el **DataGridView** se reflejan inmediatamente en los controles de detalles. Si arrastró desde la tabla Orders, todavía se enlazaría los controles al conjunto de datos, pero no se podría no pueden sincronizar con el **DataGridView**.

La siguiente ilustración muestra el valor predeterminado de los controles enlazados a datos que se agregan al formulario después de la propiedad Orders en la tabla Customers se enlaza a **detalles** en el **orígenes de datos** ventana.

![Tabla de pedidos que se enlaza a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png)

Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta permite que las personalizaciones que se aplican a sólo ese control.

## <a name="see-also"></a>Vea también

- [Enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Enlace de datos en Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)