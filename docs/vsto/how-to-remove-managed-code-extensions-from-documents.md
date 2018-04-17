---
title: 'Cómo: quitar extensiones de código administrado de documentos | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7a5e70db36c0cd1b99a670e13a353e15f7558e7e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Cómo: Quitar extensiones de código administrado de documentos
  Puede quitar mediante programación el ensamblado de personalización de un documento o libro que forma parte de una personalización de nivel de documento para Microsoft Office Word o Microsoft Office Excel. Los usuarios, a continuación, pueden abrir los documentos y ver el contenido, pero no aparecerá ninguna interfaz de usuario personalizada (UI) se agregan a los documentos y el código no se ejecutará.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede quitar el ensamblado de personalización mediante uno de los métodos de RemoveCustomization proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Método que use depende de si desea quitar la personalización en tiempo de ejecución (es decir, cuando se ejecuta el código de la personalización mientras la palabra documento o libro de Excel está abierto), o si desea quitar la personalización de un documento cerrado o un documento que i s en un servidor que no tiene instalado Microsoft Office.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [¿cómo adjuntar I: o separar un ensamblado de VSTO desde un documento de Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Para quitar el ensamblado de personalización en tiempo de ejecución  
  
1.  En el código de personalización, llame a la <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (método) (para Word) o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (método) (para Excel). Este método se debería llamar solo después de que no sea necesaria la personalización.  
  
     Donde se llamó a este método en el código depende de cómo se utiliza la personalización. Por ejemplo, si los clientes usar características de la personalización hasta que estén listos para enviar el documento a otros clientes que solo necesitan al documento en Sí (no la personalización), puede proporcionar alguna interfaz de usuario que llama RemoveCustomization cuando el cliente hace clic en él. Como alternativa, si la personalización rellena el documento con datos cuando se abre por primera vez, pero la personalización no proporciona las demás características que son accesibles directamente por los clientes, a continuación, puede llamar a RemoveCustomization tan pronto como la personalización finaliza la inicialización del documento.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Para quitar el ensamblado de personalización de un documento cerrado o un documento en un servidor  
  
1.  En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un proyecto de formularios Windows Forms, agregue una referencia al ensamblado Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Agregue el siguiente **importaciones** o **con** instrucción al principio del archivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Llame el método estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> método de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase y especifique la ruta de acceso del documento de solución para el parámetro.  
  
     En el ejemplo de código siguiente se supone que va a quitar la personalización de un documento denominado **WordDocument1.docx** que se encuentra en el escritorio.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Compile el proyecto y ejecutar la aplicación en el equipo donde desea quitar la personalización. El equipo debe tener Visual Studio 2010 Tools para Office Runtime instalado.  
  
## <a name="see-also"></a>Vea también  
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  