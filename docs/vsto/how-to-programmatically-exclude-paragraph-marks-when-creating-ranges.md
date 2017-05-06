---
title: "C&#243;mo: Excluir marcas de p&#225;rrafo al crear intervalos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], excluir párrafos"
  - "intervalos, excluir marcas de párrafo en Word"
  - "documentos [desarrollo de Office en Visual Studio], marcas de párrafo"
  - "párrafos, controlar la estructura"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# C&#243;mo: Excluir marcas de p&#225;rrafo al crear intervalos mediante programaci&#243;n
  Siempre que se crea un objeto <xref:Microsoft.Office.Interop.Word.Range> basado en un párrafo, todos los caracteres no imprimibles \(como las marcas de párrafo\), se incluirán en el intervalo. Es posible que desee insertar el texto de un párrafo de origen en un párrafo de destino. Si no desea dividir el párrafo de destino en párrafos independientes, en primer lugar, tendrá que quitar la marca de párrafo del párrafo de origen. Además, dado que la información de formato de párrafo se almacena en la marca de párrafo, es posible que no desee incluirla cuando inserte el intervalo en un párrafo existente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El siguiente procedimiento de ejemplo declara dos variables de cadena, recupera el contenido del primer y del segundo párrafo del documento activo y, a continuación, intercambia su contenido. A continuación, el ejemplo muestra cómo se elimina la marca de párrafo del intervalo mediante el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>, y cómo se inserta el texto dentro del párrafo.  
  
### Controlar la estructura de un párrafo cuando se inserta texto  
  
1.  Cree dos variables de intervalo para los párrafos primero y segundo y recupere su contenido mediante la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A>.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     El siguiente ejemplo de código se puede usar en un complemento VSTO de nivel de aplicación. Este código usa el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  Asigne la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A>, intercambiando el texto entre los dos párrafos.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  Seleccione los intervalos por turnos y haga una pausa para mostrar los resultados en un cuadro de mensaje.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  Ajuste `firstRange` con el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>, de forma que la marca de párrafo deje de formar parte del elemento `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  Sustituya el resto del texto del primer párrafo, asignando una cadena nueva a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del intervalo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  Sustituya el texto en `secondRange`, incluyendo la marca de párrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  Seleccione `firstRange` y haga una pausa para mostrar los resultados en un cuadro de mensaje. A continuación, proceda de igual forma con `secondRange`.  
  
     Dado que `firstRange` se ha redefinido para excluir la marca de párrafo, el formato original del párrafo se conserva. Sin embargo, se insertó una frase sobre la marca de párrafo en `secondRange`, lo cual elimina el párrafo independiente.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     El contenido original de los dos intervalos se guardó como cadenas, lo que permite restaurar el estado original del documento.  
  
8.  Vuelva a ajustar `firstRange` para que incluya la marca de párrafo mediante el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> y así indicar la posición de un carácter.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. Elimine `secondRange`. De esta forma se restablece la posición original del tercer párrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. Restaure el texto del párrafo original en `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. Use el método <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar el contenido del segundo párrafo original después de `firstRange` y, a continuación, seleccione `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## Ejemplo de personalización de nivel de documento  
  
#### Controlar la estructura de un párrafo cuando se inserta texto en las personalizaciones de nivel de documento  
  
1.  En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## Ejemplo para complemento de VSTO  
  
#### Controlar la estructura de un párrafo cuando se inserta texto en un complemento VSTO  
  
1.  En el siguiente ejemplo se muestra el método completo de un complemento VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## Vea también  
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Contraer intervalos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Cómo: Restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  