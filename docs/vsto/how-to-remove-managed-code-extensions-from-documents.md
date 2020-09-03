---
title: 'Cómo: quitar extensiones de código administrado de documentos'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b4f5cb3098289463cea7e650332583ec7b12258
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541315"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Cómo: quitar extensiones de código administrado de documentos
  Puede quitar mediante programación el ensamblado de personalización de un documento o un libro que forme parte de una personalización de nivel de documento para Microsoft Office Word o Microsoft Office Excel. A continuación, los usuarios pueden abrir los documentos y ver el contenido, pero cualquier interfaz de usuario personalizada que agregue a los documentos no aparecerá y el código no se ejecutará.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede quitar el ensamblado de personalización mediante uno de los `RemoveCustomization` métodos proporcionados por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . El método que use dependerá de si desea quitar la personalización en tiempo de ejecución (es decir, ejecutando el código de la personalización mientras el documento de Word o el libro de Excel está abierto) o si desea quitar la personalización de un documento cerrado o de un documento que se encuentra en un servidor que no tiene Microsoft Office instalado.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Para quitar el ensamblado de personalización en tiempo de ejecución

1. En el código de personalización, llame al <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> método (para Word) o al <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> método (para Excel). Solo se debe llamar a este método después de que ya no se necesite la personalización.

     La llamada a este método en el código depende de cómo se use la personalización. Por ejemplo, si los clientes usan las características de la personalización hasta que estén listas para enviar el documento a otros clientes que solo necesiten el propio documento (no la personalización), puede proporcionar una interfaz de usuario que llama `RemoveCustomization` cuando el cliente hace clic en él. Como alternativa, si la personalización rellena el documento con datos cuando se abre por primera vez, pero la personalización no proporciona ninguna otra característica a la que los clientes acceden directamente, puede llamar a RemoveCustomization en cuanto la personalización termine de inicializar el documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Para quitar el ensamblado de personalización de un documento cerrado o de un documento en un servidor

1. En un proyecto que no requiera Microsoft Office, como una aplicación de consola o un proyecto de Windows Forms, agregue una referencia al ensamblado *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

2. Agregue la siguiente instrucción **Imports** o **using** a la parte superior del archivo de código.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Llame al <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> método estático de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase y especifique la ruta de acceso del documento de la solución para el parámetro.

     En el ejemplo de código siguiente se da por supuesto que está quitando la personalización de un documento denominado *WordDocument1.docx* que está en el escritorio.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Compile el proyecto y ejecute la aplicación en el equipo en el que desea quitar la personalización. El equipo debe tener instalado Visual Studio 2010 Tools para Office Runtime.

## <a name="see-also"></a>Consulte también
- [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
