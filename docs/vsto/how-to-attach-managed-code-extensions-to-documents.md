---
title: 'Cómo: adjuntar extensiones de código administrado a documentos'
description: Obtenga información acerca de cómo puede adjuntar un ensamblado de personalización a un documento de Microsoft Office Word existente o Microsoft Office libro de Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 1929daaa82dbfec6f58513bf94eefe01f9520601
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844393"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Cómo: adjuntar extensiones de código administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento de Microsoft Office Word existente o Microsoft Office libro de Excel. El documento o el libro puede tener cualquier formato de archivo compatible con los proyectos de Microsoft Office y las herramientas de desarrollo de Visual Studio. Para obtener más información, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para adjuntar una personalización a un documento de Word o Excel, use el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Dado que la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase está diseñada para ejecutarse en un equipo que no tiene Microsoft Office instalado, puede usar este método en soluciones que no están directamente relacionadas con el desarrollo de Microsoft Office (por ejemplo, una consola o una aplicación Windows Forms).

> [!NOTE]
> La personalización no se cargará si el código espera controles que el documento especificado no tiene.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para adjuntar extensiones de código administrado a un documento

1. En un proyecto que no requiera Microsoft Office, como una aplicación de consola o un proyecto de Windows Forms, agregue una referencia a los ensamblados *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* y *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* .

2. Agregue las siguientes instrucciones **Imports** o **using** a la parte superior del archivo de código.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Llame al <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método estático.

     En el ejemplo de código siguiente se usa la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sobrecarga. Esta sobrecarga toma la ruta de acceso completa del documento y un <xref:System.Uri> que especifica la ubicación del manifiesto de implementación para la personalización que se desea adjuntar al documento. En este ejemplo se da por supuesto que un documento de Word denominado **WordDocument1.docx** está en el escritorio y que el manifiesto de implementación se encuentra en una carpeta denominada **Publish** que también está en el escritorio.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compile el proyecto y ejecute la aplicación en el equipo en el que desea adjuntar la personalización. El equipo debe tener instalado Visual Studio 2010 Tools para Office Runtime.

## <a name="see-also"></a>Vea también
- [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
