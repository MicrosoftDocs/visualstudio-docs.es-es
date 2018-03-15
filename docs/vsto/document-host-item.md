---
title: Elemento Host de documento | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 85c3520d852575eef6e9dae1fd8c1120b9eccd74
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="document-host-item"></a>Elemento host Document
  El elemento host <xref:Microsoft.Office.Tools.Word.Document> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Word.Document> del ensamblado de interoperabilidad primario de Word. Asimismo, el elemento host <xref:Microsoft.Office.Tools.Word.Document> proporciona las mismas propiedades, métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Word.Document> y, además, también expone eventos adicionales y sirve de contenedor para los controles host y para los controles de Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En los proyectos de nivel de documento, existe un elemento host <xref:Microsoft.Office.Tools.Word.Document> predeterminado que representa al documento del proyecto. En los proyectos de complemento de VSTO, puede generar elementos host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución.  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>Información acerca de los elementos host de documento en los proyectos de nivel de documento  
 Para obtener acceso al documento del proyecto, utilice la clase `ThisDocument` . Cuando se crea un proyecto de nivel de documento, Visual Studio genera la clase `ThisDocument` para que sirva como vínculo de comunicación entre Word y el código de personalización. La clase `ThisDocument` le da acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Word.Document> para que pueda realizar tareas básicas durante la personalización, como por ejemplo, ejecutar el código cuando el documento se abre o se cierra. También puede usar esa clase para agregar controles al documento. Si combina diferentes conjuntos de controles y escribe el código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario. Para obtener más información, consulta [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 La clase `ThisDocument` proporciona una ubicación en la que puede empezar a escribir el código del proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Word.Document> que se encuentra en el ensamblado de interoperabilidad primario de Word, también puede usar `ThisDocument` para obtener acceso al modelo de objetos de Word. Para obtener más información, consulta [Word Object Model Overview](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitaciones del elemento host Document en los proyectos de nivel de documento  
 Un proyecto de nivel de documento puede contener solamente un elemento host <xref:Microsoft.Office.Tools.Word.Document> (es decir, la clase `ThisDocument` ). No puede agregar nuevos elementos host <xref:Microsoft.Office.Tools.Word.Document> al proyecto en tiempo de diseño, ni tampoco crear nuevos elementos host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución desde una personalización de nivel de documento.  
  
 Si crea un nuevo documento de Word en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Word.Document>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información acerca de cómo crear documentos en tiempo de ejecución, consulte [Cómo: crear mediante programación nuevos documentos](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>Información acerca de los elementos Host de documento en los proyectos de nivel de aplicación  
 En los proyectos de complemento VSTO, puede generar en tiempo de ejecución un elemento host <xref:Microsoft.Office.Tools.Word.Document> para cualquier documento que esté abierto en Word. Puede usar el elemento host <xref:Microsoft.Office.Tools.Word.Document> para agregar controles al documento asociado, o para administrar los eventos que no estén disponibles en los objetos <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Para generar un <xref:Microsoft.Office.Tools.Word.Document> elemento host, utilice el método GetVstoObject. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vea también  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  