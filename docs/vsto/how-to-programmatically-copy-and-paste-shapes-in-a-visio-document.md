---
title: 'Cómo: copiar y pegar formas en un documento de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29dada62bb1e51c9cafb41d4eae08ce10e9a930c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257090"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Cómo: copiar y pegar formas en un documento de Visio mediante programación
  Puede copiar formas de la página de un documento y pegarlas en una nueva página en ese mismo documento, mediante programación. Puede decidir pegarlas en la ubicación predeterminada (el centro de la ventana activa) o en las mismas ubicaciones de coordenadas de la página original.  
  
## <a name="copy-and-paste-shapes"></a>Copiar y pegar formas  
 Para obtener detalles acerca del modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)y [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Copiar formas en el centro de otra página  
  
-   En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en el centro de la segunda página.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiar y pegar formas con las mismas posiciones  
 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)y [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) , y de la marca [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Si necesita controlar el formato de la información pegada y (opcionalmente) establecer un vínculo a un archivo de código fuente (por ejemplo, un documento de Microsoft Office Word), utilice el método PasteSpecial.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Copiar las formas y sus ubicaciones en otra página  
  
-   En el ejemplo siguiente se muestra cómo copiar las formas de la primera página y pegarlas en la segunda página junto a sus ubicaciones de coordenadas originales.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)   
 [Cómo: agregar formas a un documento de Visio mediante programación](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  