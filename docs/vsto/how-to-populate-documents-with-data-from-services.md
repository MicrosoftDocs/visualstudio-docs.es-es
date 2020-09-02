---
title: 'Cómo: rellenar documentos con datos de servicios'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01e2a83f464576d1ca780daa17c0d9478f0caa14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547152"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Cómo: rellenar documentos con datos de servicios

El acceso a los datos funciona de la misma manera en los proyectos de nivel de documento de Microsoft Office Word y en los proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para llevar los datos a la solución; además, también es posible usar controles de Windows Forms para que se muestren los datos. Asimismo, puede aprovechar los controles denominados host, ya que son objetos nativos de Microsoft Office Excel y de Microsoft Office Word mejorados con eventos y capacidad de enlace de datos. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

En el ejemplo siguiente se muestra cómo agregar controles que están enlazados a los datos, a documentos en tiempo de diseño. Para obtener un ejemplo de cómo agregar controles enlazados a datos en complementos de VSTO en tiempo de ejecución, vea [Tutorial: enlazar a datos de un servicio en un proyecto de complemento de VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Para rellenar un proyecto de nivel de documento con datos de un servicio Web

1. Abra la ventana **Orígenes de datos** y cree un origen de datos de servicio para el proyecto. Para obtener más información, vea [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

2. Arrastre el campo o la tabla que desee desde la ventana **Orígenes de datos** al documento.

     Se crea un control en el documento; esto es, un <xref:System.Windows.Forms.BindingSource> se enlaza a la clase del objeto en el proyecto y se generan las clases para el servicio.

3. En el código, cree una instancia de la clase de servicio Web a la que se conectó en el paso 1.

4. Si hay propiedades que son necesarias para la comunicación con el servicio Web, cree instancias de esas propiedades.

5. Cree y envíe una solicitud de datos mediante los métodos expuestos por el servicio web y las instancias de las propiedades que creó en el paso 4.

     Los métodos que utilice dependerán de lo que ofrezca el servicio Web.

6. Asigne la respuesta de datos del servicio Web a la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propiedad de <xref:System.Windows.Forms.BindingSource> .

Cuando ejecute el proyecto, los controles mostrarán el primer registro del origen de datos. Puede habilitar el desplazamiento por los registros si controla los eventos Currency que usan los objetos en <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Vea también

- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)
- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Cómo: rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)