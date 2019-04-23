---
title: Procedimiento Exportar una cinta desde el Diseñador de cinta al XML de cinta
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: b36c149022849dd6a788bcb5ee8f58cc12ae4417
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111004"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Procedimiento Exportar una cinta desde el Diseñador de cinta al XML de cinta
  El **cinta (diseñador Visual)** elemento no admite todos los tipos posibles de personalización de la cinta. Para personalizar la cinta de maneras avanzadas, puede exportar la cinta de opciones desde el diseñador al XML de cinta y editar directamente el XML.

> [!NOTE]
>  No todos los valores de propiedad aparecen en el archivo XML de cinta de opciones. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Para exportar una cinta de opciones desde el Diseñador de cinta de opciones a XML de cinta de opciones

1. Haga clic en el archivo de código de la cinta de opciones en **el Explorador de soluciones**y, a continuación, haga clic en **Diseñador de vistas**.

2. Haga clic en el Diseñador de cinta y, a continuación, haga clic en **exportar cinta de opciones a XML**.

     Visual Studio agrega un archivo XML de cinta de opciones y un archivo de código XML de cinta de opciones al proyecto.

3. En la clase de código de la cinta de opciones, busque los comentarios que comienzan con `TODO:`.

4. Copie el bloque de código de estos comentarios para el **ThisAddin**, **ThisWorkbook**, o **ThisDocument** clase, dependiendo de qué tipo de solución que está desarrollando.

     Este código permite que la aplicación de Microsoft Office detecte y cargue la cinta de opciones personalizada. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

5. En el **ThisAddin**, **ThisWorkbook**, o **ThisDocument** class, quite el bloque de código.

     Una vez que quite el código, debe ser similar a en el ejemplo siguiente. En este ejemplo, se llama a la clase Ribbon `MyRibbon`.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Cambie al archivo de código XML de cinta de opciones y encontrar el `Ribbon Callbacks` región.

     Esto es donde se escriben métodos de devolución de llamada para controlar las acciones del usuario, como hacer clic en un botón.

7. Cree un método de devolución de llamada para cada controlador de eventos que escribió en el código del Diseñador de cinta.

8. Mover todo el código de controlador de eventos de los controladores de eventos a los métodos de devolución de llamada y modifique el código para trabajar con el modelo de programación de extensibilidad de la cinta de opciones (RibbonX).

     Para obtener información sobre cómo escribir métodos de devolución de llamada y utilizando el modelo de programación de extensibilidad, vea [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Vea también
- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de la cinta](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada usando XML de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
