---
title: "C&#243;mo: Guardar documentos de Visio mediante programaci&#243;n | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], guardar documentos de Visio"
  - "Visio [desarrollo de Office en Visual Studio], guardar documentos de Visio"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Guardar documentos de Visio mediante programaci&#243;n
  Hay varias formas de guardar documentos de Microsoft Office Visio:  
  
-   Guardar cambios en un documento existente.  
  
-   Guardar un documento nuevo, o guardar un documento con un nuevo nombre.  
  
-   Guardar un documento con argumentos especificados.  
  
 Para obtener más información, vea la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Document.Save](HV10071468), [Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) y [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470).  
  
## Guardar un documento existente  
  
#### Para guardar un documento  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.Save de la clase Microsoft.Office.Tools.Visio.Document de un documento que ya se ha guardado.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
    > [!NOTE]  
    >  El método Microsoft.Office.Interop.Visio.Document.Save produce una excepción si todavía no se ha guardado un nuevo documento de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## Guardar un documento con un nuevo nombre  
 Use el método Microsoft.Office.Interop.Visio.Document.SaveAs para guardar un nuevo documento, o un documento que tenga un nombre nuevo. Este método requiere que especifique el nombre del archivo nuevo.  
  
#### Para guardar el documento de Visio activo con un nombre nuevo  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.SaveAs del Microsoft.Office.Tools.Visio.Document que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Guardar un documento con un nuevo nombre y argumentos especificados  
 Use el método Microsoft.Office.Interop.Visio.Document.SaveAsEx para guardar un documento con un nuevo nombre y especifique cualquier argumento correspondiente para aplicar al documento.  
  
#### Para guardar un documento con un nuevo nombre y argumentos especificados  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.SaveAsEx del Microsoft.Office.Tools.Visio.Document que desea guardar, mediante una ruta completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se generará una excepción.  
  
     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre, se marca el documento como de solo lectura y se muestra el documento en la lista de documentos usados más recientemente. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Para guardar un documento que tenga un nombre nuevo, debe haber un directorio denominado `Test` en la carpeta Mis documentos \(para Windows XP y versiones anteriores\) o en la carpeta Documentos \(para Windows Vista\).  
  
## Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  