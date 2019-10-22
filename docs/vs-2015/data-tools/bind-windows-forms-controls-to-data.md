---
title: Enlazar controles de Windows Forms a datos | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672974"
---
# <a name="bind-windows-forms-controls-to-data"></a>Enlazar controles de Windows Forms a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede enlazar orígenes de datos a controles arrastrando objetos desde la ventana **orígenes de datos** hasta un formulario Windows Forms o hasta un control existente en un formulario. Antes de arrastrar elementos, puede establecer el tipo de control al que desea enlazar. Aparecen valores diferentes en función de si se elige la propia tabla o una columna individual.  También puede establecer valores personalizados. En el caso de una tabla, "detalles" significa que cada columna está enlazada a un control independiente.

 ![Enlazar el origen de datos a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata enlazar el origen de datos a DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Enlazar a datos en un control DataGridView
 En el caso de DataGridView, toda la tabla se enlaza a ese control único. Al arrastrar una DataGridView al formulario, también aparece una franja de herramientas para navegar por los registros (<xref:System.Windows.Forms.BindingNavigator>). En la bandeja de componentes aparecen un [conjunto](../data-tools/dataset-tools-in-visual-studio.md)de objetos, TableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>. En la ilustración siguiente, también se agrega TableAdapterManager porque la tabla Customers tiene una relación con la tabla Orders. Estas variables se declaran en el código generado automáticamente como miembros privados en la clase de formulario. El código generado automáticamente para rellenar DataGridView se encuentra en el controlador de eventos Form_Load. El código para guardar los datos para actualizar la base de datos se encuentra en el controlador de eventos Save para BindingNavigator. Puede trasladar o modificar este código según sea necesario.

 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")

 Para personalizar el comportamiento de DataGridView y BindingNavigator, haga clic en la etiqueta inteligente en la esquina superior derecha de cada una de ellas:

 ![Etiquetas inteligentes de DataGridView y navegador de enlace](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "etiquetas inteligentes raddata DataGridView y navegador de enlace")

 Si los controles que necesita su aplicación no están disponibles en la ventana **orígenes de datos** , puede Agregar controles. Para obtener más información, vea [Agregar controles personalizados a la ventana orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 También puede arrastrar elementos desde la ventana **orígenes de datos** hasta controles que ya están en un formulario para enlazar el control a los datos. Un control que ya está enlazado a datos tiene sus enlaces de datos restablecidos en el elemento que se arrastró más recientemente a él. Para ser destinos de colocación válidos, los controles deben ser capaces de mostrar el tipo de datos subyacente del elemento arrastrado a él desde la ventana **orígenes de datos** . Por ejemplo, no es válido arrastrar un elemento que tenga un tipo de datos de <xref:System.DateTime> a un <xref:System.Windows.Forms.CheckBox>, porque la <xref:System.Windows.Forms.CheckBox> no es capaz de mostrar una fecha.

## <a name="bind-to--data-in-individual-controls"></a>Enlazar a datos en controles individuales
 Al enlazar un origen de datos a "detalles", cada columna del conjunto de datos se enlaza a un control independiente.

 ![Enlazar el origen de datos a los detalles](../data-tools/media/raddata-bind-data-source-to-details.png "raddata enlazar el origen de datos a los detalles")

> [!IMPORTANT]
> Tenga en cuenta que en la ilustración anterior, arrastre de la propiedad Orders de la tabla Customers, no de la tabla Orders. Al enlazar con la propiedad Customer. Orders, los comandos de navegación realizados en DataGridView se reflejan inmediatamente en los controles de detalles. Si arrastra desde la tabla Orders, los controles seguirán estando enlazados al DataSet, pero no se sincronizarán con DataGridView.

 En la ilustración siguiente se muestran los controles enlazados a datos predeterminados que se agregan al formulario después de que la propiedad Orders de la tabla Customers esté enlazada a "details" en la ventana **orígenes de datos** .

 ![Tabla de pedidos enlazada a detalles](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata tabla de pedidos enlazada a detalles")

 Tenga en cuenta también que cada control tiene una etiqueta inteligente. Esta etiqueta habilita las personalizaciones que solo se aplican a ese control.

## <a name="see-also"></a>Vea también
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
