---
title: "C&#243;mo: Guardar documentos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], guardar"
  - "Word [desarrollo de Office en Visual Studio], guardar documentos"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Guardar documentos mediante programaci&#243;n
  Hay varias maneras de guardar los documentos de Microsoft Office Word.  Puede guardar un documento sin cambiarle el nombre o puede guardarlo con un nuevo nombre.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Guardar un documento sin cambiar el nombre  
  
#### Para guardar el documento asociado a una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.Save%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### Para guardar el documento activo  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.Save%2A> para el documento activo.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 Si no está seguro de si el documento que desea guardar es el documento activo, puede hacer referencia a él por su nombre.  
  
#### Para guardar un documento especificado por su nombre  
  
1.  Utilice el nombre del documento como argumento de la colección <xref:Microsoft.Office.Interop.Word.Documents>.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## Guardar un documento con un nuevo nombre  
 Utilice el método SaveAs para guardar el documento con un nombre nuevo.  Puede utilizar este método del elemento host <xref:Microsoft.Office.Tools.Word.Document> en un proyecto de nivel de documento de Word o de un objeto <xref:Microsoft.Office.Interop.Word.Document> nativo en cualquier proyecto de Word.  En este método es preciso especificar el nuevo nombre de archivo, pero hay otros argumentos opcionales.  
  
> [!NOTE]  
>  Si muestra el cuadro de diálogo **Guardar como** dentro del controlador de eventos <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> de `ThisDocument` y establece el parámetro *Cancel* en **false**, la aplicación podría cerrarse inesperadamente.  Si establece el parámetro *Cancel* en **true**, aparece un mensaje de error indicando que Autosave se ha deshabilitado.  
  
#### Para guardar el documento asociado a una personalización de nivel de documento con un nuevo nombre  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> de la clase `ThisDocument` en su proyecto, especificando la ruta de acceso completa y el nombre de archivo.  Si en la carpeta ya existe un archivo con el mismo nombre, será reemplazado sin notificación.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument`.  
  
    > [!NOTE]  
    >  El método <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> inicia una excepción si el directorio de destino no existe o si se produce algún otro problema al guardar el archivo.  Es aconsejable usar un bloque **try…catch** en torno al método <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> o dentro del método que realiza la llamada.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### Para guardar un documento nativo con un nuevo nombre  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> que desea guardar, mediante una ruta de acceso completa y un nombre de archivo.  Si en la carpeta ya existe un archivo con el mismo nombre, será reemplazado sin notificación.  
  
     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre.  Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
    > [!NOTE]  
    >  El método <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> produce una excepción si el directorio de destino no existe o si se produce algún otro problema al guardar el archivo.  Es aconsejable usar un bloque **try…catch** en torno al método <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> o dentro del método que realiza la llamada.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Compilar el código  
 Este ejemplo de código requiere lo siguiente:  
  
-   Para guardar un documento por el nombre, debe existir un documento denominado NewDocument.doc en un directorio denominado Test en la unidad C.  
  
-   Para guardar un documento con un nombre nuevo, debe existir un directorio denominado Test en la unidad C.  
  
## Vea también  
 [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)   
 [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  