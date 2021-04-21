---
title: Almacenar en caché el origen de datos en un documento de Office mediante programación
description: Obtenga información sobre cómo agregar mediante programación un objeto de datos a la caché de datos de un documento mediante una llamada al método StartCaching de un elemento host.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070253fb7ec57bedad628e116ce193fa2d9cf50b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827596"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Cómo: Almacenar en caché mediante programación un origen de datos en un documento de Office
  Puede agregar mediante programación un objeto de datos a la caché de datos de un documento llamando al método de un elemento host, como `StartCaching` <xref:Microsoft.Office.Tools.Word.Document> , o <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> . Quite un objeto de datos de la caché de datos mediante una llamada al `StopCaching` método de un elemento host.

 Tanto `StartCaching` el método como el método son `StopCaching` privados, pero aparecen en IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Cuando se usa el método para agregar un objeto de datos a la caché de datos, no es necesario declarar el objeto `StartCaching` de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Sin embargo, el objeto de datos debe cumplir ciertos requisitos para agregarse a la caché de datos. Para obtener más información, vea Almacenar [en caché los datos](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Para almacenar en caché mediante programación un objeto de datos

1. Declare el objeto de datos en el nivel de clase, no dentro de un método . En este ejemplo se da por supuesto que está declarando un con nombre <xref:System.Data.DataSet> que desea almacenar en caché mediante `dataSet1` programación.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Cree una instancia del objeto de datos y, a continuación, llame al método de la instancia de documento o hoja de cálculo y `StartCaching` pase el nombre del objeto de datos.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Para detener el almacenamiento en caché de un objeto de datos

1. Llame al método de la instancia del documento o de `StopCaching` la hoja de cálculo y pase el nombre del objeto de datos. En este ejemplo se supone que tiene un <xref:System.Data.DataSet> nombre con el que desea detener el almacenamiento en `dataSet1` caché.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > No llame al `StopCaching` controlador de eventos para el evento de un documento o hoja de `Shutdown` cálculo. En el momento en `Shutdown` que se genera el evento, es demasiado tarde para modificar la caché de datos. Para obtener más información sobre el `Shutdown` evento, vea [Eventos en proyectos de Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Consulte también

- [Datos de caché](../vsto/caching-data.md)
- [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: Almacenar en caché datos en un documento protegido con contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Acceso a datos en documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Guardar datos](../data-tools/save-data-back-to-the-database.md)
