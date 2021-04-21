---
title: 'Cómo: Exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta'
description: Obtenga información sobre que, para personalizar la cinta de opciones, puede exportar la cinta desde el diseñador al XML de la cinta de opciones y editar el XML directamente.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1514410094deaf9c77e088c3b69e2d39d29175c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825594"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Cómo: Exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta
  El **elemento Cinta de opciones (Diseñador visual)** no admite todos los tipos posibles de personalización de la cinta de opciones. Para personalizar la cinta de opciones de formas avanzadas, puede exportar la cinta desde el diseñador al XML de la cinta de opciones y editar el XML directamente.

> [!NOTE]
> No todos los valores de propiedad aparecen en el archivo XML de la cinta de opciones. Para obtener más información, vea Información general [de la cinta de opciones.](../vsto/ribbon-overview.md)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Para exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta

1. Haga clic con el botón derecho en el archivo de código de la **cinta Explorador de soluciones** y, a continuación, haga clic **Diseñador de vistas**.

2. Haga clic con el botón derecho en el Diseñador de la cinta de opciones y, a continuación, haga clic **en Exportar cinta de opciones a XML.**

     Visual Studio agrega un archivo XML de cinta de opciones y un archivo de código XML de cinta de opciones al proyecto.

3. En la clase de código Ribbon, busque los comentarios que empiezan por `TODO:` .

4. Copie el bloque de código de estos comentarios en la **clase ThisAddin**, **ThisWorkbook** o **ThisDocument,** en función del tipo de solución que desarrolle.

     Este código permite que Microsoft Office aplicación detecte y cargue la cinta de opciones personalizada. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).

5. En la **clase ThisAddin**, **ThisWorkbook** o **ThisDocument,** descomprima el bloque de código.

     Después de descomprimenciar el código, debería ser similar al ejemplo siguiente. En este ejemplo, la clase Ribbon se denomina `MyRibbon` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. Cambie al archivo de código XML de la cinta de opciones y busque la `Ribbon Callbacks` región.

     Aquí es donde se escriben métodos de devolución de llamada para controlar las acciones del usuario, como hacer clic en un botón.

7. Cree un método de devolución de llamada para cada controlador de eventos que escribió en el código del Diseñador de cinta de opciones.

8. Mueva todo el código del controlador de eventos de los controladores de eventos a los métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta de opciones (RibbonX).

     Para obtener información sobre cómo escribir métodos de devolución de llamada y usar el modelo de programación RibbonX, vea XML de la cinta de [opciones.](../vsto/ribbon-xml.md)

## <a name="see-also"></a>Consulte también
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Creación de una pestaña personalizada mediante XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
