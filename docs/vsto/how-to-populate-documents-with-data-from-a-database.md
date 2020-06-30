---
title: 'Cómo: rellenar documentos con datos de una base de datos'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8470ec4acf686c016088c5f474539a1ab7ed85df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547204"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Cómo: rellenar documentos con datos de una base de datos

Puede acceder a los datos en proyectos de nivel de documento para Microsoft Office de la misma manera que lo hace en proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para traer los datos de una base de datos hasta su solución y se pueden usar controles de Windows Forms para mostrar los datos.

Además, puede mostrar datos mediante controles host. Los controles host son objetos nativos de Microsoft Office Word que se han mejorado mediante funcionalidad de enlace de eventos y datos. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

En el siguiente ejemplo se muestra cómo agregar controles enlazados a datos en proyectos de nivel de documento usando un diseñador. Para obtener un ejemplo de cómo agregar controles enlazados a datos en proyectos de complemento de VSTO en tiempo de ejecución, vea [Tutorial: enlace de datos simple en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [enlazar datos a controles de contenido de Word 2007 mediante Visual Studio Tools para el sistema Office (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Agregar un control a un documento en tiempo de diseño

### <a name="to-populate-a-document-with-data-from-a-database"></a>Para rellenar un documento con datos de una base de datos

1. Abra un proyecto de nivel de documento de Word en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con el documento abierto en el diseñador.

2. Abra la ventana **orígenes de datos** y cree un origen de datos a partir de una base de datos. Para obtener más información, consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. Arrastre el campo que desee desde la ventana **orígenes de datos** hasta el documento.

Se agregará un control de contenido al documento. El tipo del control de contenido depende del tipo de datos del campo que haya seleccionado. Para obtener más información, vea [controles de contenido](../vsto/content-controls.md).

Para agregar un control diferente, seleccione el campo de datos en la ventana **orígenes de datos** y, a continuación, elija un control diferente de la lista desplegable.

## <a name="objects-in-the-project"></a>Objetos del proyecto

Además del control, se agregan automáticamente al proyecto los siguientes objetos relacionados con los datos:

- Un conjunto de datos con tipo que encapsula las tablas de datos de la base de datos a las que se haya conectado. Para obtener más información, vea [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un <xref:System.Windows.Forms.BindingSource> que conecta el control al conjunto de datos con tipo. Para obtener más información, vea [información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter que conecta el conjunto de datos con tipo a la base de datos. Para obtener más información, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Un TableAdapterManager, que se usa para coordinar los adaptadores de tabla en el conjunto de DataSet para habilitar las actualizaciones jerárquicas. Para obtener más información, consulte [actualización jerárquica](../data-tools/hierarchical-update.md) y [referencia de TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Al ejecutar el proyecto, el control muestra el primer registro del origen de datos. Puede usar el <xref:System.Windows.Forms.BindingSource> para permitir a los usuarios desplazarse por los registros.

### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros

- Use métodos <xref:System.Windows.Forms.BindingSource>, como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> y <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Para obtener información acerca de cómo enviar actualizaciones al conjunto de datos con tipo y a la base de datos, consulte [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Consulte también

- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Usar archivos de base de datos local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)