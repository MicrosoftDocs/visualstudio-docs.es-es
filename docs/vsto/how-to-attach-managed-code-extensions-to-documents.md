---
title: Procedimiento Adjuntar extensiones de código administrado a documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18ca5e0cbf341f27454377c544e20cd2aba1388f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044269"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Procedimiento Adjuntar extensiones de código administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento existente de Microsoft Office Word o un libro de Microsoft Office Excel. El documento o libro puede estar en cualquier formato de archivo que es compatible con los proyectos de Microsoft Office y herramientas de desarrollo en Visual Studio. Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para adjuntar una personalización a un documento de Word o Excel, use el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Dado que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase está diseñada para ejecutarse en un equipo que no tiene instalado Microsoft Office, puede usar este método en soluciones que no están directamente relacionados con el desarrollo de Microsoft Office (por ejemplo, una consola o aplicación de Windows Forms).

> [!NOTE]
>  La personalización no se cargará si el código espera que los controles que no tienen el documento especificado.

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: Adjuntar o separar un ensamblado de VSTO desde un documento de Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para asociar extensiones de código administrado a un documento

1. En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un proyecto de Windows Forms, agregue una referencia a la *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* y  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* ensamblados.

2. Agregue el siguiente **importaciones** o **mediante** instrucciones a la parte superior del archivo de código.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Llamar a estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método.

     El siguiente ejemplo de código utiliza el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sobrecargar. Esta sobrecarga toma la ruta de acceso completa del documento y un <xref:System.Uri> que especifica la ubicación del manifiesto de implementación para la personalización que desee asociar al documento. En este ejemplo se supone que un documento de Word llamado **WordDocument1.docx** está en el escritorio, y que se encuentra el manifiesto de implementación en una carpeta que se denomina **publicar** que también está en el escritorio.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compile el proyecto y ejecutar la aplicación en el equipo donde desea adjuntar la personalización. El equipo debe tener Visual Studio 2010 Tools para Office Runtime instalado.

## <a name="see-also"></a>Vea también
- [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
