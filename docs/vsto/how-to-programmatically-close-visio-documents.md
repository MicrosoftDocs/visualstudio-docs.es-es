---
title: 'Cómo: cerrar documentos de Visio mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 478905a8ba4dacd2102c4b19fe091016a7409773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547490"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Cómo: cerrar documentos de Visio mediante programación
  Puede cerrar el documento de Microsoft Office Visio activo con el método `Microsoft.Office.Interop.Visio.Document.Close`.

 Para obtener información más detallada sobre este método, vea la documentación de referencia de VBA del método [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Cerrar el documento activo

### <a name="to-close-the-active-document"></a>Para cerrar el documento activo

- Llame al método `Microsoft.Office.Interop.Visio.Document.Close` para cerrar el documento activo.

     Para usar el ejemplo de código siguiente, ejecútelo en la `ThisAddIn` clase en un proyecto de complemento de VSTO para Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
- [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)
