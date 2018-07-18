---
title: 'Cómo: agregar formas a un documento de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32fc1b61505711cbcf353819372bcd1452bf3716
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256674"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Cómo: agregar formas a un documento de Visio mediante programación
  Puede agregar formas a un documento de Microsoft Office Visio recuperando los patrones de una galería de símbolos y colocando las formas en la página activa.  
  
 Para obtener más información, vea la documentación de referencia de VBA del método [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) , la propiedad [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) y el método [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) .  
  
## <a name="add-shapes-to-a-visio-document"></a>Agregar formas a un documento de Visio  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Para agregar formas a un documento de Visio  
  
-   Con un documento activo, recupere los patrones de la colección Documents.Masters y coloque las formas en el documento activo. Puede recuperar un patrón mediante el índice o el nombre del patrón.  
  
     En el ejemplo de código siguiente se crea un documento de Visio en blanco y, a continuación, se abre con la galería de símbolos **Formas básicas** acoplada. A continuación, el código recupera varias formas y las coloca en la página activa.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)   
 [Cómo: copiar y pegar formas en un documento de Visio mediante programación](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  