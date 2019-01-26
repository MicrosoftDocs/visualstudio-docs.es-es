---
title: Procedimiento Abrir documentos de Visio mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8c9e9eb6a298270deb4f66c38662b0c52d7ee76f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864454"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedimiento Abrir documentos de Visio mediante programación
  Hay dos métodos para abrir documentos existentes de Microsoft Office Visio: Abra y OpenEx. El método OpenEx es idéntico al método Open, excepto que proporciona argumentos en el que el llamador puede especificar cómo se abre el documento.  
  
 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA para el método [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) y el método [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .  
  
## <a name="open-a-visio-document"></a>Abra un documento de Visio  
  
### <a name="to-open-a-visio-document"></a>Para abrir un documento de Visio  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Documents.Open` y facilite la ruta de acceso completa del documento de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Abra un documento de Visio con argumentos especificados  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir un documento de Visio como de solo lectura y acoplado  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Documents.OpenEx`, facilite la ruta de acceso completa del documento de Visio e incluya los argumentos que desea utilizar; en este caso, Docked y Read-only.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
