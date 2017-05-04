---
title: "C&#243;mo: Crear nuevos documentos de Visio mediante programaci&#243;n | Microsoft Docs"
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
  - "Visio [desarrollo de Office en Visual Studio], crear documentos de Visio"
  - "documentos [desarrollo de Office en Visual Studio], crear documentos de Visio"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Crear nuevos documentos de Visio mediante programaci&#243;n
  Cuando se crea un nuevo documento de dibujo de Visio de Microsoft Office, debe agregarse a la colección Microsoft.Office.Interop.Visio.Documents de documentos de Visio abiertos. Por consiguiente, el método Microsoft.Office.Interop.Visio.Documents.Add crea un nuevo documento de dibujo de Visio. Para obtener más información, consulte la documentación de referencia VBA para el método [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241).  
  
## Crear nuevos documento en blanco  
  
#### Para crear un nuevo documento  
  
-   Use el método Microsoft.Office.Interop.Visio.Documents.Add para crear un nuevo documento en blanco que no se base en una plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Crear documentos copiados de documentos existentes  
 El método Microsoft.Office.Interop.Visio.Documents.Add puede crear un documento nuevo que es una copia de un documento de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa del diagrama.  
  
#### Para crear un documento nuevo copiado de uno existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso del diagrama de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Crear galerías de símbolos copiadas de otras existentes  
 El método [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241) puede crear una nueva galería de símbolos que sea una copia de una galería de símbolos de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la galería de símbolos.  
  
#### Para crear una galería de símbolos nueva copiada de una existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso de la galería de símbolos.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Crear documentos basados en plantillas existentes  
 El método Microsoft.Office.Interop.Visio.Documents.Add puede crear un nuevo documento \(un archivo .vsd\) basado en una plantilla existente de Visio \(archivo .vst\). Este método copia las galerías de símbolos, estilos y configuraciones que forman parte del área de trabajo de la plantilla. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.  
  
#### Para crear un documento nuevo basado en una plantilla existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso de la plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos \(para Windows XP y versiones anteriores\) o en la carpeta Documentos \(para Windows Vista\).  
  
-   Un documento de Visio denominado `myStencil.vss` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos \(para Windows XP y versiones anteriores\) o en la carpeta Documentos \(para Windows Vista\).  
  
-   Un documento de Visio denominado `myTemplate.vst` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos \(para Windows XP y versiones anteriores\) o en la carpeta Documentos \(para Windows Vista\).  
  
## Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  