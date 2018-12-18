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
ms.openlocfilehash: 94e8b43830c26aad82937cc0533ca19e109f33d0
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671877"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Cómo: agregar formas a un documento de Visio mediante programación
  Puede agregar formas a un documento de Microsoft Office Visio recuperando los patrones de una galería de símbolos y colocando las formas en la página activa.  
  
 Para obtener más información, vea la documentación de referencia de VBA del método [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) , la propiedad [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) y el método [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .  
  
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
  
  