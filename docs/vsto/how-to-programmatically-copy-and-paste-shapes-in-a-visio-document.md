---
title: Copiar y pegar formas en un documento de Visio mediante programación
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 05b0d20ba7bd560fc60090bba84b78691bb3e753
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546099"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Cómo: copiar y pegar formas en un documento de Visio mediante programación
  Puede copiar formas de la página de un documento y pegarlas en una nueva página en ese mismo documento, mediante programación. Puede decidir pegarlas en la ubicación predeterminada (el centro de la ventana activa) o en las mismas ubicaciones de coordenadas de la página original.

## <a name="copy-and-paste-shapes"></a>Copiar y pegar formas
 Para obtener detalles acerca del modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)y [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Copiar formas en el centro de otra página

- En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en el centro de la segunda página.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiar y pegar formas con las mismas posiciones
 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)y [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Si necesita controlar el formato de la información pegada y, opcionalmente, establecer un vínculo a un archivo de origen (por ejemplo, un documento de Microsoft Office Word), use el método PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Copiar las formas y sus ubicaciones en otra página

- En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en la segunda página junto a sus ubicaciones de coordenadas originales.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)
- [Cómo: agregar formas a un documento de Visio mediante programación](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
