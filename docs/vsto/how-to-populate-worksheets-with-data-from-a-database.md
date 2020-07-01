---
title: 'Cómo: rellenar hojas de cálculo con datos de una base de datos'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1b594014b2564b5730c1895a007294ee66e07637
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520125"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Cómo: rellenar hojas de cálculo con datos de una base de datos

Puede tener acceso a los datos de los proyectos de Office de nivel de documento de la misma manera que tiene acceso a los datos en proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para llevar los datos a la solución; además, también es posible usar controles de Windows Forms para que se muestren los datos. Además, puede aprovechar los controles denominados controles host, que son objetos nativos de Microsoft Office Excel que se han mejorado con eventos y funciones de enlace de datos. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

En el siguiente ejemplo se muestra cómo agregar controles enlazados a datos en proyectos de nivel de documento usando un diseñador. Para obtener un ejemplo de cómo agregar controles enlazados a datos en proyectos de nivel de aplicación en tiempo de ejecución, vea [Tutorial: enlace de datos complejo en un proyecto de complemento de VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Agregar un control enlazado a datos a una hoja de cálculo en tiempo de diseño

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Para rellenar una hoja de cálculo con datos de una base de datos

1. Abra un proyecto de nivel de documento de Excel en Visual Studio, con la hoja de cálculo abierta en el diseñador.

2. Abra la ventana **Orígenes de datos** y cree un origen de datos para su proyecto. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. Arrastre el campo o la tabla que desee desde la ventana **orígenes de datos** hasta la hoja de cálculo.

Uno de los siguientes controles se crea en la hoja de cálculo:

- Si arrastra un campo, <xref:Microsoft.Office.Tools.Excel.NamedRange> se crea un control en la hoja de cálculo. Para obtener más información, vea [NamedRange (control](../vsto/namedrange-control.md)).

- Si arrastra una tabla, <xref:Microsoft.Office.Tools.Excel.ListObject> se crea un control en la hoja de cálculo. Para obtener más información, vea [ListObject (control](../vsto/listobject-control.md)).

Puede Agregar un control diferente si selecciona la tabla o el campo en la ventana **orígenes de datos** y, a continuación, elige un control diferente de la lista desplegable.

## <a name="objects-in-the-project"></a>Objetos del proyecto

Además del control, se agregan automáticamente al proyecto los siguientes objetos relacionados con los datos:

- Un conjunto de datos con tipo que encapsula las tablas de datos de la base de datos a las que se haya conectado. Para obtener más información, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un <xref:System.Windows.Forms.BindingSource> que conecta el control al conjunto de datos con tipo. Para obtener más información, vea [información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter que conecta el conjunto de datos con tipo a la base de datos. Para obtener más información, vea [información general de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- Un TableAdapterManager, que se usa para coordinar los adaptadores de tabla en el conjunto de DataSet para habilitar las actualizaciones jerárquicas. Para obtener más información, consulte [actualización jerárquica](../data-tools/hierarchical-update.md) y [referencia de TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Al ejecutar el proyecto, el control muestra el primer registro del origen de datos. Puede usar el <xref:System.Windows.Forms.BindingSource> para permitir a los usuarios desplazarse por los registros.

### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros

- Use métodos <xref:System.Windows.Forms.BindingSource>, como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> y <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Para obtener información acerca de cómo enviar actualizaciones al conjunto de datos con tipo y a la base de datos, consulte [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Vea también

- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)