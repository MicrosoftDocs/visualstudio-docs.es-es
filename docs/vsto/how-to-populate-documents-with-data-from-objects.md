---
title: 'Cómo: rellenar documentos con datos de objetos'
description: Obtenga información sobre cómo puede usar los datos de un objeto en la solución y puede usar controles Windows Forms para mostrar los datos de un documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 73cc795b5476f312f5fc80ba76dc383175596b64
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848058"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Cómo: rellenar documentos con datos de objetos

El acceso a los datos de un objeto de datos funciona de la misma manera en los proyectos de nivel de documento de Microsoft Office Word que en los proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para colocar datos de un objeto en la solución y se pueden usar controles de Windows Forms para mostrar los datos. Además, puede mostrar datos mediante controles host. Los controles host son objetos nativos de Microsoft Office Word que se han mejorado mediante funcionalidad de enlace de eventos y datos. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Para rellenar el documento con datos de un objeto, es necesario completar tres pasos básicos:

- Agregar un control al documento que se puede enlazar a datos.

- Agregar un objeto de datos al documento.

- Conectar el objeto de datos a BindingSource.

## <a name="to-add-a-data-object"></a>Para agregar un objeto de datos

Para agregar un objeto de datos, abra la ventana **orígenes de datos** y cree un origen de datos a partir de un objeto. Para obtener más información, vea [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Conectar el objeto de datos a BindingSource

En los proyectos de nivel de documento, se agregan controles al documento y se enlazan a datos en tiempo de diseño.

En proyectos de complemento de VSTO, se crean controles y se enlazan en tiempo de ejecución.

### <a name="document-level-projects"></a>Proyectos de nivel de documento

Para conectar el objeto de datos a BindingSource:

1. Arrastre el campo de datos que quiera desde la ventana **Orígenes de datos** al documento. Así se crea un control automáticamente.

2. En el código, cree una instancia del tipo del objeto que eligió para el origen de datos.

3. Asigne la instancia a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de la clase <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Proyectos de nivel de aplicación

Para conectar el objeto de datos a BindingSource:

1. En el código, cree una instancia del tipo del objeto que está asociado con el origen de datos.

2. Cree una instancia de <xref:System.Windows.Forms.BindingSource>.

3. Asigne la instancia del origen de datos a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de la clase <xref:System.Windows.Forms.BindingSource>.

4. Agregue el origen de datos como un enlace de datos al control.

## <a name="see-also"></a>Vea también

- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)