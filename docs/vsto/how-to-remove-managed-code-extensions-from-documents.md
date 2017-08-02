---
title: "C&#243;mo: Quitar extensiones de c&#243;digo administrado de documentos"
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
  - "extensiones de código administrado [desarrollo de Office en Visual Studio], quitar"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Quitar extensiones de c&#243;digo administrado de documentos
  Se puede quitar mediante programación el ensamblado de personalización de un documento o libro que forma parte de una personalización de nivel de documento para Microsoft Office Word o Microsoft Office Excel.  Los usuarios pueden abrir los documentos y ver el contenido, pero cualquier interfaz de usuario personalizada que agregue no aparecerá y el código no se ejecutará.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para quitar el ensamblado de personalización, se puede usar uno de los métodos RemoveCustomization proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  El método que use depende de si desea quitar la personalización en tiempo de ejecución \(es decir, ejecutando el código de la personalización mientras está abierto el documento de Word o el libro de Excel\) o de si desea quitarla de un documento cerrado o un documento que está en un servidor que no tiene instalado Microsoft Office.  
  
 ![vínculo a vídeo](~/docs/data-tools/media/playvideo.gif "vínculo a vídeo") Para obtener una demostración en vídeo relacionada con este tema, vea [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Para quitar el ensamblado de personalización en tiempo de ejecución  
  
1.  En el código de personalización, llame al método <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> \(para Word\) o al método <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> \(para Excel\).  Este método debe invocarse únicamente cuando ya no se necesita la personalización.  
  
     La ubicación desde la que se invoca este método en el código depende de cómo se utilice la personalización.  Por ejemplo, si los clientes utilizan las características de la personalización hasta que estén preparados para enviar el documento a otros clientes que solo necesitan el documento propiamente dicho \(no la personalización\), se puede proporcionar alguna interfaz de usuario que llame a RemoveCustomization cuando el cliente hace clic en ella.  Asimismo, si la personalización rellena el documento con datos cuando se abre por primera vez, pero no proporciona ninguna otra característica a la que los clientes obtengan acceso directamente, se podrá llamar a RemoveCustomization en cuanto la personalización termine de inicializar el documento.  
  
### Para quitar el ensamblado de personalización desde un documento cerrado o desde un documento de un servidor  
  
1.  En un proyecto que no requiere Microsoft Office, como una aplicación de consola o un proyecto de formularios Windows Forms, agregue una referencia al ensamblado Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Agregue la siguiente instrucción **Imports** o **using** al principio del archivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  Llame al método estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> y especifique la ruta de acceso del documento de la solución para el parámetro.  
  
     En el ejemplo de código siguiente se supone que está quitando la personalización de un documento denominado **WordDocument1.docx** que está en el escritorio.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  Compile el proyecto y ejecute la aplicación en el equipo donde desea quitar la personalización.  El equipo debe tener Visual Studio 2010 Tools para Office Runtime instalado.  
  
## Vea también  
 [Administrar documentos en un servidor mediante la clase ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  