---
title: "Cómo: rellenar documentos con datos de servicios | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eb06e77cf45a3c912f569686cdbe246baece8a03
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Cómo: Rellenar documentos con datos de servicios
  El acceso a los datos funciona de la misma manera en los proyectos de nivel de documento de Microsoft Office Word y en los proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para llevar los datos a la solución; además, también es posible usar controles de Windows Forms para que se muestren los datos. Asimismo, puede aprovechar los controles denominados host, ya que son objetos nativos de Microsoft Office Excel y de Microsoft Office Word mejorados con eventos y capacidad de enlace de datos. Para obtener más información, consulta [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 En el ejemplo siguiente se muestra cómo agregar controles que están enlazados a los datos, a documentos en tiempo de diseño. Para obtener un ejemplo de cómo agregar controles enlazados a datos a los complementos de VSTO en tiempo de ejecución, consulte [Tutorial: agregar en el enlace a datos de un servicio en un VSTO proyecto](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [cómo puedo interactuar con los servicios Web de Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Rellenar un proyecto de nivel de documento con los datos de un servicio web  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos de servicio para el proyecto. Para obtener más información, vea [Agregar nuevos orígenes de datos](/visualstudio/data-tools/add-new-data-sources).  
  
2.  Arrastre el campo o la tabla que desee desde la ventana **Orígenes de datos** al documento.  
  
     Se crea un control en el documento; esto es, un <xref:System.Windows.Forms.BindingSource> se enlaza a la clase del objeto en el proyecto y se generan las clases para el servicio.  
  
3.  En el código, cree una instancia de la clase de servicio web con la que se conectó en el paso 1.  
  
4.  Si hay propiedades que son necesarias para la comunicación con el servicio web, cree instancias de esas propiedades.  
  
5.  Cree y envíe una solicitud de datos mediante los métodos expuestos por el servicio web y las instancias de las propiedades que creó en el paso 4.  
  
     Los métodos que utilice dependerán de lo que ofrezca el servicio web.  
  
6.  Asigne los datos de respuesta del servicio web a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
 Cuando ejecute el proyecto, los controles mostrarán el primer registro del origen de datos. Puede habilitar el desplazamiento por los registros si controla los eventos Currency que usan los objetos en <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Agregar nuevos orígenes de datos](/visualstudio/data-tools/add-new-data-sources)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  