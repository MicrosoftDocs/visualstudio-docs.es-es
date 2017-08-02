---
title: "C&#243;mo: Adjuntar extensiones de c&#243;digo administrado a documentos"
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
  - "documentos [desarrollo de Office en Visual Studio], extensiones de código administrado"
  - "extensiones de código administrado [desarrollo de Office en Visual Studio], adjuntar"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# C&#243;mo: Adjuntar extensiones de c&#243;digo administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento de Microsoft Office Word o un libro de Microsoft Office Excel existentes.  El documento o libro puede tener cualquier formato de archivo admitido por los proyectos y las herramientas de desarrollo de Microsoft Office en Visual Studio.  Para obtener más información, vea [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para adjuntar una personalización a un documento de Word o Excel, use el método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Dado que la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> está diseñada para ejecutarse en un equipo sin Microsoft Office, se puede utilizar este método en soluciones que no están directamente relacionadas con el desarrollo de Microsoft Office \(por ejemplo, una aplicación de consola o de Windows Forms\).  
  
> [!NOTE]  
>  La personalización no se cargará si el código espera controles que el documento especificado no tiene.  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para obtener una demostración en vídeo relacionada con este tema, vea [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Para asociar extensiones de código administrado a un documento  
  
1.  En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un proyecto de formularios Windows Forms, agregue una referencia a los ensamblados Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll y de Microsoft.VisualStudio.Tools.Applications.Runtime.dll.  
  
2.  Agregue las siguientes instrucciones **Imports** o **using** al principio del archivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  Llame al método estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  
  
     En el ejemplo de código siguiente se utiliza la sobrecarga <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  Esta sobrecarga toma la ruta de acceso completa del documento y <xref:System.Uri> que especifica la ubicación del manifiesto de implementación para la personalización que desea asociar al documento.  En este ejemplo se presupone que un documento de Word denominado **WordDocument1.docx** está en el escritorio y que el manifiesto de implementación se encuentra en una carpeta que se denomina **Publicar** que también está en el escritorio.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  Compile el proyecto y ejecute la aplicación en el equipo donde desea adjuntar la personalización.  El equipo debe tener Visual Studio 2010 Tools para Office Runtime instalado.  
  
## Vea también  
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  