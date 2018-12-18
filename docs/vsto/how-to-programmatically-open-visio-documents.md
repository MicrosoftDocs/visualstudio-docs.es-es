---
title: 'Cómo: abrir documentos de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 28f882510e2370c0fb31645da5023e865afd667e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672683"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Cómo: abrir documentos de Visio mediante programación
  Hay dos métodos para abrir documentos existentes de Microsoft Office Visio: abrir y OpenEx. El método OpenEx es idéntico al método Open, excepto que proporciona argumentos en el que el llamador puede especificar cómo se abre el documento.  
  
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
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  