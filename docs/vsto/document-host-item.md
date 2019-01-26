---
title: Elemento host Document
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4da1dce5eb668c3f43f886da4044c28c880b1246
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866784"
---
# <a name="document-host-item"></a>Elemento host Document
  El elemento host <xref:Microsoft.Office.Tools.Word.Document> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Word.Document> del ensamblado de interoperabilidad primario de Word. Asimismo, el elemento host <xref:Microsoft.Office.Tools.Word.Document> proporciona las mismas propiedades, métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Word.Document> y, además, también expone eventos adicionales y sirve de contenedor para los controles host y para los controles de Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En los proyectos de nivel de documento, existe un elemento host <xref:Microsoft.Office.Tools.Word.Document> predeterminado que representa al documento del proyecto. En los proyectos de complemento de VSTO, puede generar elementos host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución.  
  
## <a name="understand-the-document-host-item-in-document-level-projects"></a>Comprender el elemento host document en los proyectos de nivel de documento  
 Para obtener acceso al documento del proyecto, utilice la clase `ThisDocument` . Cuando se crea un proyecto de nivel de documento, Visual Studio genera la clase `ThisDocument` para que sirva como vínculo de comunicación entre Word y el código de personalización. La clase `ThisDocument` le da acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Word.Document> para que pueda realizar tareas básicas durante la personalización, como por ejemplo, ejecutar el código cuando el documento se abre o se cierra. También puede usar esa clase para agregar controles al documento. Si combina diferentes conjuntos de controles y escribe el código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario. Para obtener más información, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 La clase `ThisDocument` proporciona una ubicación en la que puede empezar a escribir el código del proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Word.Document> que se encuentra en el ensamblado de interoperabilidad primario de Word, también puede usar `ThisDocument` para obtener acceso al modelo de objetos de Word. Para obtener más información, consulte [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitaciones del elemento host document en los proyectos de nivel de documento  
 Un proyecto de nivel de documento puede contener solamente un elemento host <xref:Microsoft.Office.Tools.Word.Document> (es decir, la clase `ThisDocument` ). No puede agregar nuevos <xref:Microsoft.Office.Tools.Word.Document> elementos host para el proyecto en tiempo de diseño, y que no se puede crear nuevos <xref:Microsoft.Office.Tools.Word.Document> elementos en tiempo de ejecución desde una personalización de nivel de documento host.  
  
 Si crea un nuevo documento de Word en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Word.Document>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información sobre la creación de documentos en tiempo de ejecución, vea [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understand-document-host-items-in-application-level-projects"></a>Comprender los elementos host de documento en los proyectos de nivel de aplicación  
 En los proyectos de complemento VSTO, puede generar en tiempo de ejecución un elemento host <xref:Microsoft.Office.Tools.Word.Document> para cualquier documento que esté abierto en Word. Puede usar el elemento host <xref:Microsoft.Office.Tools.Word.Document> para agregar controles al documento asociado, o para administrar los eventos que no estén disponibles en los objetos <xref:Microsoft.Office.Interop.Word.Document> .  
  
 Para generar un elemento host <xref:Microsoft.Office.Tools.Word.Document>, use el método `GetVstoObject`. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vea también  
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
