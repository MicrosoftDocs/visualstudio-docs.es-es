---
title: "Cómo: rellenar documentos con datos de una base de datos | Documentos de Microsoft"
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
- documents, populating with data
- data, adding to documents
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b5dcbf99dcc6005c89a7bc67030f2e0f2fddfc5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Cómo: Rellenar documentos con datos de una base de datos
  Puede acceder a los datos en proyectos de nivel de documento para Microsoft Office de la misma manera que lo hace en proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para traer los datos de una base de datos hasta su solución y se pueden usar controles de Windows Forms para mostrar los datos.  
  
 Además, puede mostrar datos mediante controles host. Los controles host son objetos nativos de Microsoft Office Word que se han mejorado mediante funcionalidad de enlace de eventos y datos. Para obtener más información, consulta [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En el siguiente ejemplo se muestra cómo agregar controles enlazados a datos en proyectos de nivel de documento usando un diseñador. Para obtener un ejemplo de cómo agregar controles enlazados a datos en los proyectos de complemento de VSTO en tiempo de ejecución, consulte [Tutorial: enlace de datos complejos en VSTO complemento proyecto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [enlazar datos a Word 2007 contenido controles mediante Visual Studio Tools para Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="adding-a-control-to-a-document-at-design-time"></a>Agregar un control a un documento en tiempo de diseño  
  
#### <a name="to-populate-a-document-with-data-from-a-database"></a>Para rellenar un documento con datos de una base de datos  
  
1.  Abra un proyecto de nivel de documento de Word en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con el documento abierto en el diseñador.  
  
2.  Abra la **orígenes de datos** ventana y crear un origen de datos de una base de datos. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
3.  Arrastre el campo que desee desde la **orígenes de datos** ventana para el documento.  
  
 Se agregará un control de contenido al documento. El tipo del control de contenido depende del tipo de datos del campo que haya seleccionado. Para obtener más información, consulta [Content Controls](../vsto/content-controls.md).  
  
 Puede agregar un control diferente seleccionando el campo de datos en el **orígenes de datos** ventana y, a continuación, elige un control diferente de la lista desplegable.  
  
## <a name="objects-in-the-project"></a>Objetos del proyecto  
 Además del control, se agregan automáticamente al proyecto los siguientes objetos relacionados con los datos:  
  
-   Un conjunto de datos con tipo que encapsula las tablas de datos de la base de datos a las que se haya conectado. Para obtener más información, consulte [herramientas de conjunto de datos en Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Un <xref:System.Windows.Forms.BindingSource> que conecta el control al conjunto de datos con tipo. Para obtener más información, consulta [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Un TableAdapter que se conecta el conjunto de datos con tipo a la base de datos. Para obtener más información, consulte [crear y configurar los TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
-   Un TableAdapterManager, que se utiliza para coordinar los adaptadores de tablas en el conjunto de datos para habilitar las actualizaciones jerárquicas. Para obtener más información, consulte [actualización jerárquica](../data-tools/hierarchical-update.md) y [TableAdapterManager referencia](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Al ejecutar el proyecto, el control muestra el primer registro del origen de datos. Puede usar el <xref:System.Windows.Forms.BindingSource> para permitir a los usuarios desplazarse por los registros.  
  
#### <a name="to-scroll-through-the-records"></a>Para desplazarse por los registros  
  
-   Use métodos <xref:System.Windows.Forms.BindingSource>, como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> y <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Para obtener información acerca de cómo enviar actualizaciones a la base de datos y el conjunto de datos con tipo, consulte [Cómo: actualizar un origen de datos con datos de un Control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Agregar nuevos orígenes de datos](/visualstudio/data-tools/add-new-data-sources)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: actualizar un origen de datos con datos de un Control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Uso de archivos de base de datos Local en información general sobre soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectarse a datos en aplicaciones de Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Información general sobre el componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  