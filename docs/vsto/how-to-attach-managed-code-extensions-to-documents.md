---
title: 'Cómo: Adjuntar extensiones de código administrado a documentos'
description: Obtenga información sobre cómo adjuntar un ensamblado de personalización a un documento Microsoft Office Word existente o Microsoft Office libro de Excel.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 60fc27345ef148fd47fdcee15924917ce63f8d68
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825503"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Cómo: Adjuntar extensiones de código administrado a documentos
  Puede adjuntar un ensamblado de personalización a un documento Microsoft Office word existente o Microsoft Office libro de Excel. El documento o libro puede estar en cualquier formato de archivo que sea compatible con los proyectos de Microsoft Office y las herramientas de desarrollo de Visual Studio. Para obtener más información, vea [Arquitectura de personalizaciones de nivel de documento.](../vsto/architecture-of-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para adjuntar una personalización a un documento de Word o Excel, use el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> . Dado que la clase está diseñada para ejecutarse en un equipo que no tiene instalado Microsoft Office, puede usar este método en soluciones que no están directamente relacionadas con el desarrollo de Microsoft Office (como una consola o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> una Windows Forms).

> [!NOTE]
> La personalización no se cargará si el código espera controles que el documento especificado no tiene.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para adjuntar extensiones de código administrado a un documento

1. En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un  proyecto de Windows Forms, agregue una referencia a losMicrosoft.VisualStudio.Tools.Applications.ServerDocument.dlly *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* ensamblados.

2. Agregue las siguientes **instrucciones Imports** o **using** a la parte superior del archivo de código.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet4":::

3. Llame al método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> estático.

     En el ejemplo de código siguiente se usa la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sobrecarga . Esta sobrecarga toma la ruta de acceso completa del documento y un que especifica la ubicación del manifiesto de implementación para la personalización <xref:System.Uri> que desea asociar al documento. En este ejemplo se supone que un documento de Word denominado **WordDocument1.docx** está en el escritorio y que el manifiesto de implementación se encuentra en una carpeta denominada **Publicar** que también se encuentra en el escritorio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet3":::

4. Compile el proyecto y ejecute la aplicación en el equipo donde desea adjuntar la personalización. El equipo debe tener instalado Visual Studio 2010 Tools for Office Runtime.

## <a name="see-also"></a>Consulte también
- [Administración de documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifiestos de aplicación e implementación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
