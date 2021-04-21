---
title: 'Cómo: Quitar extensiones de código administrado de documentos'
description: Quite mediante programación el ensamblado de personalización de un documento o libro que forma parte de una personalización de nivel de documento para Microsoft Word o Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129b1bda44abf7283efe1996f1898491025ee9d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825451"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Cómo: Quitar extensiones de código administrado de documentos
  Puede quitar mediante programación el ensamblado de personalización de un documento o libro que forma parte de una personalización de nivel de documento para Microsoft Office Word o Microsoft Office Excel. A continuación, los usuarios pueden abrir los documentos y ver el contenido, pero cualquier interfaz de usuario personalizada (UI) que agregue a los documentos no aparecerá y el código no se ejecutará.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede quitar el ensamblado de personalización mediante uno de los `RemoveCustomization` métodos proporcionados por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . El método que use dependerá de si desea quitar la personalización en tiempo de ejecución (es decir, mediante la ejecución de código en la personalización mientras el documento de Word o el libro de Excel está abierto), o si desea quitar la personalización de un documento cerrado o un documento que se encuentra en un servidor que no Microsoft Office instalado.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Para quitar el ensamblado de personalización en tiempo de ejecución

1. En el código de personalización, llame al <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> método (para Word) o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> al método (para Excel). Solo se debe llamar a este método después de que la personalización ya no sea necesaria.

     La forma en que se llama a este método en el código depende de cómo se utilice la personalización. Por ejemplo, si los clientes usan las características de la personalización hasta que están listos para enviar el documento a otros clientes que solo necesitan el propio documento (no la personalización), puede proporcionar alguna interfaz de usuario que llame a cuando el cliente haga clic en `RemoveCustomization` él. Como alternativa, si la personalización rellena el documento con datos cuando se abre por primera vez, pero la personalización no proporciona otras características a las que los clientes acceden directamente, puede llamar a RemoveCustomization en cuanto la personalización termine de inicializar el documento.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Para quitar el ensamblado de personalización de un documento cerrado o un documento en un servidor

1. En un proyecto que no requiere Microsoft Office, como una aplicación de consola o Windows Forms proyecto, agregue una referencia alMicrosoft.VisualStudio.Tools.Applications.ServerDocument.dll *ensamblado.*

2. Agregue la siguiente **instrucción Imports** o **using** a la parte superior del archivo de código.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. Llame al método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> estático de la clase y especifique la ruta de acceso del documento de solución para el parámetro <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

     En el ejemplo de código siguiente se supone que va a quitar la personalización de un documento *denominadoWordDocument1.docx* que se encuentra en el escritorio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Compile el proyecto y ejecute la aplicación en el equipo donde desea quitar la personalización. El equipo debe tener instalado el Visual Studio 2010 Tools for Office runtime.

## <a name="see-also"></a>Consulte también
- [Administración de documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
