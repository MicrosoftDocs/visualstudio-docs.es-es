---
title: "Elemento host Document"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documentos [desarrollo de Office en Visual Studio]"
  - "documentos [desarrollo de Office en Visual Studio], elementos host de documentos"
  - "elementos host de documentos"
  - "Word [desarrollo de Office en Visual Studio], documentos de Word"
  - "Word [desarrollo de Office en Visual Studio]"
  - "documentos de Word"
  - "elementos host [desarrollo de Office en Visual Studio], Document"
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Elemento host Document
  El elemento host <xref:Microsoft.Office.Tools.Word.Document> es un tipo que extiende el tipo <xref:Microsoft.Office.Interop.Word.Document> del ensamblado de interoperabilidad primario de Word. Asimismo, el elemento host <xref:Microsoft.Office.Tools.Word.Document> proporciona las mismas propiedades, métodos y eventos que un objeto <xref:Microsoft.Office.Interop.Word.Document> y, además, también expone eventos adicionales y sirve de contenedor para los controles host y para los controles de Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En los proyectos de nivel de documento, existe un elemento host <xref:Microsoft.Office.Tools.Word.Document> predeterminado que representa al documento del proyecto. En los proyectos de complemento de VSTO, puede generar elementos host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución.  
  
## Información acerca de los elementos host de documento en los proyectos de nivel de documento  
 Para obtener acceso al documento del proyecto, utilice la clase `ThisDocument`. Cuando se crea un proyecto de nivel de documento, Visual Studio genera la clase `ThisDocument` para que sirva como vínculo de comunicación entre Word y el código de personalización. La clase `ThisDocument` le da acceso a los miembros del elemento host <xref:Microsoft.Office.Tools.Word.Document> para que pueda realizar tareas básicas durante la personalización, como por ejemplo, ejecutar el código cuando el documento se abre o se cierra. También puede usar esa clase para agregar controles al documento. Si combina diferentes conjuntos de controles y escribe el código, puede enlazar los controles a los datos, recopilar información del usuario y responder a las acciones del usuario. Para obtener más información, consulta [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 La clase `ThisDocument` proporciona una ubicación en la que puede empezar a escribir el código del proyecto. Como esta clase proporciona las mismas propiedades, métodos y eventos que el objeto <xref:Microsoft.Office.Interop.Word.Document> que se encuentra en el ensamblado de interoperabilidad primario de Word, también puede usar `ThisDocument` para obtener acceso al modelo de objetos de Word.  Para obtener más información, consulta [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
### Limitaciones del elemento host Document en los proyectos de nivel de documento  
 Un proyecto de nivel de documento puede contener solamente un elemento host <xref:Microsoft.Office.Tools.Word.Document> \(es decir, la clase `ThisDocument`\). No puede agregar nuevos elementos host <xref:Microsoft.Office.Tools.Word.Document> al proyecto en tiempo de diseño, ni tampoco crear nuevos elementos host <xref:Microsoft.Office.Tools.Word.Document> en tiempo de ejecución desde una personalización de nivel de documento.  
  
 Si crea un nuevo documento de Word en tiempo de ejecución, será del tipo <xref:Microsoft.Office.Interop.Word.Document>. Como no se trata de un elemento host, este no puede contener controles host ni controles de Windows Forms. Para obtener más información sobre cómo crear documentos en tiempo de ejecución, consulte [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md).  
  
## Información acerca de los elementos Host de documento en los proyectos de nivel de aplicación  
 En los proyectos de complemento VSTO, puede generar en tiempo de ejecución un elemento host <xref:Microsoft.Office.Tools.Word.Document> para cualquier documento que esté abierto en Word. Puede usar el elemento host <xref:Microsoft.Office.Tools.Word.Document> para agregar controles al documento asociado, o para administrar los eventos que no estén disponibles en los objetos <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Para generar un elemento host <xref:Microsoft.Office.Tools.Word.Document>, use el método GetVstoObject. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Vea también  
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  