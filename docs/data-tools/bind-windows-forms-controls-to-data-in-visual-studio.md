---
title: Enlazar controles de Windows Forms a datos
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 24c3549cf98e49f3419ef0e7387a6c236c15e9e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648841"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Enlazar controles de Windows Forms a datos en Visual Studio

Para mostrar datos a los usuarios de la aplicación, puede enlazarlos a Windows Forms. Para crear estos controles enlazados a datos, arrastre los elementos desde la ventana **orígenes de datos** hasta el diseñador de Windows Forms en Visual Studio.

![Operación de arrastre de origen de datos](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Si la ventana **orígenes de datos** no está visible, puede abrirla eligiendo **Ver**  > **otras ventanas**  > **orígenes de datos**o presionando **MAYÚS** +**Alt** +**D**. Debe tener un proyecto abierto en Visual Studio para ver la ventana **orígenes de datos** .

Antes de arrastrar elementos, puede establecer el tipo de control al que desea enlazar. Aparecen valores diferentes en función de si se elige la propia tabla o una columna individual.  También puede establecer valores personalizados. En el caso de una tabla, **detalles** significa que cada columna está enlazada a un control independiente.

![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Controles BindingSource y BindingNavigator

El componente <xref:System.Windows.Forms.BindingSource> sirve para dos propósitos. En primer lugar, proporciona una capa de abstracción al enlazar los controles a los datos. Los controles del formulario se enlazan al componente <xref:System.Windows.Forms.BindingSource> en lugar de directamente a un origen de datos. Segundo, puede administrar una colección de objetos. Al agregar un tipo a <xref:System.Windows.Forms.BindingSource>, se crea una lista de ese tipo.

Para obtener más información acerca del componente <xref:System.Windows.Forms.BindingSource>, vea:

- [BindingSource component](/dotnet/framework/winforms/controls/bindingsource-component) (Componente BindingSource)

- [BindingSource component overview](/dotnet/framework/winforms/controls/bindingsource-component-overview) (Información general sobre el componente BindingSource)

- [BindingSource component architecture](/dotnet/framework/winforms/controls/bindingsource-component-architecture) (Arquitectura del componente BindingSource)

El [control BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) proporciona una interfaz de usuario para navegar por los datos mostrados por una aplicación de Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView

Para un [control DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), toda la tabla se enlaza a ese control único. Al arrastrar una **DataGridView** al formulario, también aparece una franja de herramientas para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>). Aparece un componente [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator> en la bandeja de componentes. En la ilustración siguiente, también se agrega [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados en la clase de formulario. El código generado automáticamente para rellenar **DataGridView** se encuentra en el controlador de eventos `Form_Load`. El código para guardar los datos para actualizar la base de datos se encuentra en el controlador de eventos `Save` para **BindingNavigator**. Puede trasladar o modificar este código según sea necesario.

![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Para personalizar el comportamiento de **DataGridView** y **BindingNavigator** , haga clic en la etiqueta inteligente en la esquina superior derecha de cada una de ellas:

![Etiquetas inteligentes de DataGridView y navegador de enlace](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Si los controles que necesita su aplicación no están disponibles en la ventana **orígenes de datos** , puede Agregar controles. Para obtener más información, vea [Agregar controles personalizados a la ventana orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

También puede arrastrar elementos desde la ventana **orígenes de datos** hasta controles que ya están en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus enlaces de datos restablecidos en el elemento que se arrastró más recientemente a él. Para ser destinos de colocación válidos, los controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado a él desde la ventana **orígenes de datos** . Por ejemplo, no es válido arrastrar un elemento que tenga un tipo de datos de <xref:System.DateTime> a un <xref:System.Windows.Forms.CheckBox>, porque la <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.

## <a name="bind-to-data-in-individual-controls"></a>Enlazar a datos en controles individuales

Al enlazar un origen de datos a los **detalles**, cada columna del conjunto de datos se enlaza a un control independiente.

![Enlazar el origen de datos a los detalles](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Tenga en cuenta que en la ilustración anterior, arrastre de la propiedad Orders de la tabla Customers, no de la tabla Orders. Al enlazar a la propiedad `Customer.Orders`, los comandos de navegación realizados en **DataGridView** se reflejan inmediatamente en los controles de detalles. Si arrastra desde la tabla Orders, los controles seguirán estando enlazados al DataSet, pero no se sincronizarán con **DataGridView**.

En la ilustración siguiente se muestran los controles enlazados a datos predeterminados que se agregan al formulario después de que la propiedad Orders de la tabla Customers esté enlazada a los **detalles** de la ventana **orígenes de datos** .

![Tabla de pedidos enlazada a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png)

Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta habilita las personalizaciones que solo se aplican a ese control.

## <a name="see-also"></a>Vea también

- [Binding controls to data in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) (Enlazar controles a los datos en Visual Studio)
- [Enlace de datos en Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)