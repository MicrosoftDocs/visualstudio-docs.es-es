---
title: 'Cómo: Comprobar la ortografía en documentos mediante programación'
description: Obtenga información sobre que, para comprobar mediante programación la ortografía de un documento, puede usar el método CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7e04c542f91b9d7675eb81e7a3178e3427c52a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828857"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Cómo: Comprobar la ortografía en documentos mediante programación
  Para comprobar la ortografía de un documento, use el <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método . Este método devuelve un valor booleano que indica si el parámetro proporcionado está escrito correctamente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para comprobar la ortografía y mostrar los resultados en un cuadro de mensaje

1. Llame al <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método y pásle un intervalo de texto para comprobar si hay errores ortográficos. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet113":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet113":::

## <a name="see-also"></a>Consulte también
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
