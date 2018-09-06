---
title: 'Cómo: guardar documentos de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675109"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Cómo: guardar documentos de Visio mediante programación
  Hay varias formas de guardar documentos de Microsoft Office Visio:  
  
-   Guardar cambios en un documento existente.  
  
-   Guardar un documento nuevo, o guardar un documento con un nuevo nombre.  
  
-   Guardar un documento con argumentos especificados.  
  
 Para obtener más información, vea la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) y [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="save-an-existing-document"></a>Guardar un documento existente  
  
### <a name="to-save-a-document"></a>Para guardar un documento  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Document.Save` método de la `Microsoft.Office.Tools.Visio.Document` clase de un documento que se ha guardado anteriormente.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
    > [!NOTE]  
    >  El `Microsoft.Office.Interop.Visio.Document.Save` método produce una excepción si todavía no se ha guardado un nuevo documento de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Guardar un documento con un nuevo nombre  
 Use el `Microsoft.Office.Interop.Visio.Document.SaveAs` método para guardar un documento nuevo, o un documento que tiene un nombre nuevo. Este método requiere que especifique el nombre del archivo nuevo.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Para guardar el documento de Visio activo con un nombre nuevo  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Document.SaveAs` método de la `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta de acceso completa, incluido un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se sobrescribe en modo silencioso.  
  
     Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Guardar un documento con un nuevo nombre y argumentos especificados  
 Use el `Microsoft.Office.Interop.Visio.Document.SaveAsEx` método para guardar un documento con un nombre nuevo y especifique cualquier argumento correspondiente para aplicar al documento.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Para guardar un documento con un nuevo nombre y argumentos especificados  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Document.SaveAsEx` método de la `Microsoft.Office.Tools.Visio.Document` que desea guardar, mediante una ruta de acceso completa, incluido un nombre de archivo. Si ya existe un archivo con ese nombre en esa carpeta, se generará una excepción.  
  
     En el ejemplo de código siguiente se guarda el documento activo con un nuevo nombre, se marca el documento como de solo lectura y se muestra el documento en la lista de documentos usados más recientemente. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Para guardar un documento que tiene un nuevo nombre, un directorio denominado `Test` debe estar ubicado en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  