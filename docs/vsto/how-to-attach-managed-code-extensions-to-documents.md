---
title: "Cómo: Adjuntar extensiones de código administrado a documentos | Documentos de Microsoft"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe976923c77902a4e3e42fc634a3227cadccdfc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Cómo: Adjuntar extensiones de código administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento existente de Microsoft Office Word o un libro de Microsoft Office Excel. El documento o libro puede estar en cualquier formato de archivo que sea compatible con los proyectos de Microsoft Office y herramientas de desarrollo de Visual Studio. Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para adjuntar una personalización a un documento de Word o Excel, use la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Dado que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase está diseñada para ejecutarse en un equipo que no tiene instalado Microsoft Office, puede utilizar este método en soluciones que no están directamente relacionados con el desarrollo de Microsoft Office (como una aplicación de formularios Windows Forms o de consola).  
  
> [!NOTE]  
>  Se producirá un error en la personalización cargar si el código espera controles que no tienen el documento especificado.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [¿cómo adjuntar I: o separar un ensamblado de VSTO desde un documento de Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para asociar extensiones de código administrado a un documento  
  
1.  En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un proyecto de formularios Windows Forms, agregue una referencia a la Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll y Microsoft.VisualStudio.Tools.Applications.Runtime.dll ensamblados.  
  
2.  Agregue el siguiente **importaciones** o **con** instrucciones a la parte superior del archivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Llame el método estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método.  
  
     El siguiente ejemplo de código utiliza el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sobrecarga. Esta sobrecarga toma la ruta de acceso completa del documento y un <xref:System.Uri> que especifica la ubicación del manifiesto de implementación para la personalización que desea asociar al documento. En este ejemplo se supone que un documento de Word llamado **WordDocument1.docx** se encuentra en el escritorio, y que el manifiesto de implementación se encuentra en una carpeta que se denomina **publicar** que se encuentra también en el escritorio.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Compile el proyecto y ejecutar la aplicación en el equipo donde desea adjuntar la personalización. El equipo debe tener Visual Studio 2010 Tools para Office Runtime instalado.  
  
## <a name="see-also"></a>Vea también  
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  