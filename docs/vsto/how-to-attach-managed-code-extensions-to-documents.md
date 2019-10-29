---
title: 'Cómo: adjuntar extensiones de código administrado a documentos'
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
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985975"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Cómo: adjuntar extensiones de código administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento de Microsoft Office Word existente o Microsoft Office libro de Excel. El documento o el libro puede tener cualquier formato de archivo compatible con los proyectos de Microsoft Office y las herramientas de desarrollo de Visual Studio. Para obtener más información, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para adjuntar una personalización a un documento de Word o Excel, use el método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>. Dado que la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> está diseñada para ejecutarse en un equipo que no tiene Microsoft Office instalado, puede usar este método en soluciones que no están directamente relacionadas con el desarrollo de Microsoft Office (como una aplicación de consola o Windows Forms).

> [!NOTE]
> La personalización no se cargará si el código espera controles que el documento especificado no tiene.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para adjuntar extensiones de código administrado a un documento

1. En un proyecto que no requiera Microsoft Office, como una aplicación de consola o un proyecto de Windows Forms, agregue una referencia a *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* y  *Ensamblados Microsoft. VisualStudio. Tools. Applications. Runtime. dll* .

2. Agregue las siguientes instrucciones **Imports** o **using** a la parte superior del archivo de código.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Llame al método estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.

     En el ejemplo de código siguiente se usa la sobrecarga <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>. Esta sobrecarga toma la ruta de acceso completa del documento y una <xref:System.Uri> que especifica la ubicación del manifiesto de implementación para la personalización que se desea adjuntar al documento. En este ejemplo se da por supuesto que un documento de Word denominado **WordDocument1. docx** está en el escritorio y que el manifiesto de implementación se encuentra en una carpeta denominada **Publish** que también está en el escritorio.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Compile el proyecto y ejecute la aplicación en el equipo en el que desea adjuntar la personalización. El equipo debe tener instalado Visual Studio 2010 Tools para Office Runtime.

## <a name="see-also"></a>Vea también
- [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
