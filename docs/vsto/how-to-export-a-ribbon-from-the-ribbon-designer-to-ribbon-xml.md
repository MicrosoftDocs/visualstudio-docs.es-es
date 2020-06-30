---
title: 'Cómo: exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57918e8a51a3948a2c69eb0c8ab5438b147e44f0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543473"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Cómo: exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta
  El elemento **cinta (diseñador visual)** no admite todos los tipos posibles de personalización de la cinta de opciones. Para personalizar la cinta de modo avanzado, puede exportar la cinta de opciones del diseñador al XML de la cinta y editar directamente el XML.

> [!NOTE]
> No todos los valores de propiedad aparecen en el archivo XML de la cinta. Para obtener más información, vea [información general sobre la cinta](../vsto/ribbon-overview.md)de opciones.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Para exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta

1. Haga clic con el botón secundario en el archivo de código de la cinta de **Explorador de soluciones**y, a continuación, haga clic en **Ver diseñador**.

2. Haga clic con el botón secundario en el diseñador de la cinta y, a continuación, haga clic en **exportar cinta a XML**.

     Visual Studio agrega un archivo XML de la cinta de opciones y un archivo de código XML de la cinta de opciones al proyecto.

3. En la clase de código de la cinta de opciones, busque los comentarios que comienzan por `TODO:` .

4. Copie el bloque de código de estos comentarios a la clase **ThisAddIn**, **ThisWorkbook**o **ThisDocument** , en función del tipo de solución que esté desarrollando.

     Este código permite a la aplicación Microsoft Office detectar y cargar la cinta de opciones personalizada. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

5. En la clase **ThisAddIn**, **ThisWorkbook**o **ThisDocument** , quite el comentario del bloque de código.

     Después de quitar el comentario del código, debería ser similar al ejemplo siguiente. En este ejemplo, se llama a la clase Ribbon `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Cambie al archivo de código XML de la cinta de opciones y busque la `Ribbon Callbacks` región.

     Aquí es donde se escriben los métodos de devolución de llamada para controlar las acciones del usuario, como hacer clic en un botón.

7. Cree un método de devolución de llamada para cada controlador de eventos que escribió en el código del diseñador de la cinta de opciones.

8. Mueva todo el código del controlador de eventos de los controladores de eventos a los métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta de opciones (RibbonX).

     Para obtener información sobre cómo escribir métodos de devolución de llamada y cómo usar el modelo de programación RibbonX, vea [XML de la cinta](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
