---
title: "Cómo: guardar documentos de Visio mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c255c481123ef4159d63ad87d9c8fa2ac97cbdae
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-visio-documents"></a>Cómo: Guardar documentos de Visio mediante programación
  Hay varias formas de guardar documentos de Microsoft Office Visio:  
  
-   Guardar cambios en un documento existente.  
  
-   Guardar un documento nuevo, o guardar un documento con un nuevo nombre.  
  
-   Guardar un documento con argumentos especificados.  
  
 Para obtener más información, vea la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) y [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="saving-an-existing-document"></a>Guardar un documento existente  
  
#### <a name="to-save-a-document"></a>Para guardar un documento  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.Save de la clase Microsoft.Office.Tools.Visio.Document de un documento que se ha guardado previamente.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
    > [!NOTE]  
    >  El método Microsoft.Office.Interop.Visio.Document.Save produce una excepción si todavía no se ha guardado un nuevo documento de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre  
 Utilice el método Microsoft.Office.Interop.Visio.Document.SaveAs para guardar un documento nuevo, o un documento que tenga un nombre nuevo. Este método requiere que especifique el nombre del archivo nuevo.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Para guardar el documento de Visio activo con un nombre nuevo  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.SaveAs del Microsoft.Office.Tools.Visio.Document que desea guardar, mediante una ruta de acceso completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Guardar un documento con un nuevo nombre y argumentos especificados  
 Utilice el método Microsoft.Office.Interop.Visio.Document.SaveAsEx para guardar un documento con un nuevo nombre y especifique cualquier argumento correspondiente para aplicar al documento.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Para guardar un documento con un nuevo nombre y argumentos especificados  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.SaveAsEx del Microsoft.Office.Tools.Visio.Document que desea guardar, mediante una ruta de acceso completa que incluya un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se generará una excepción.  
  
     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre, se marca el documento como de solo lectura y se muestra el documento en la lista de documentos usados más recientemente. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Para guardar un documento que tenga un nombre nuevo, debe haber un directorio denominado `Test` en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta Documentos (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general del modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  