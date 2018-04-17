---
title: 'Cómo: exportar una cinta de opciones desde el Diseñador de la cinta de opciones a XML de la cinta de opciones | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7aff56d1d7ee3533a83ef3edbdd8ba9271efd862
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones
  El **cinta (diseñador Visual)** elemento no admite todos los tipos posibles de personalización de la cinta de opciones. Para personalizar la cinta de maneras avanzadas, puede exportar la cinta de opciones desde el diseñador a XML de cinta de opciones y editar el XML directamente.  
  
> [!NOTE]  
>  No todos los valores de propiedad aparecen en el archivo XML de cinta de opciones. Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Para exportar una cinta de opciones desde el Diseñador de la cinta de opciones a XML de cinta de opciones  
  
1.  Haga clic en el archivo de código de la cinta de opciones en **el Explorador de soluciones**y, a continuación, haga clic en **Diseñador de vistas**.  
  
2.  Haga clic en el Diseñador de la cinta de opciones y, a continuación, haga clic en **exportar cinta de opciones a XML**.  
  
     Visual Studio agrega un archivo XML de cinta de opciones y un archivo de código XML de cinta de opciones al proyecto.  
  
3.  En la clase de código de la cinta de opciones, busque los comentarios que comienzan con `TODO:`.  
  
4.  Copie el bloque de código de estos comentarios para el **ThisAddin**, **ThisWorkbook**, o **ThisDocument** (clase), dependiendo de qué tipo de solución que está desarrollando.  
  
     Este código permite a la aplicación de Microsoft Office detecte y cargue la cinta de opciones personalizada. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  En el **ThisAddin**, **ThisWorkbook**, o **ThisDocument** clase, quite el bloque de código.  
  
     Después de que se quite el comentario del código, debe ser similar en el siguiente ejemplo. En este ejemplo, se llama la clase Ribbon `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Cambie al archivo de código XML de la cinta y buscar la `Ribbon Callbacks` región.  
  
     Esto es donde escribir métodos de devolución de llamada para controlar las acciones del usuario, como hacer clic en un botón.  
  
7.  Cree un método de devolución de llamada para cada controlador de eventos que se escribió en el código del Diseñador de la cinta de opciones.  
  
8.  Mover todo el código de controlador de eventos de los controladores de eventos a los métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta de opciones (RibbonX).  
  
     Para obtener información sobre cómo escribir métodos de devolución de llamada y utilizar el modelo de programación de extensibilidad, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Creación de una pestaña personalizada mediante XML de la cinta](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  