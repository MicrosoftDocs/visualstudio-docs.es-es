---
title: Caché de origen de datos en el documento de Office mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e63b478fb16965f639a76dad0cbc3b2715bc7e2
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401401"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Procedimiento Almacenar en caché mediante programación un origen de datos en un documento de Office
  Puede agregar mediante programación un objeto de datos a la caché de datos en un documento mediante una llamada a la `StartCaching` elemento de método de un host, como un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, o <xref:Microsoft.Office.Tools.Excel.Worksheet>. Quitar un objeto de datos de la caché de datos mediante una llamada a la `StopCaching` método de un elemento host.

 El `StartCaching` método y el `StopCaching` método son privados, pero aparecen en IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Cuando se usa el `StartCaching` para agregar un objeto de datos a la caché de datos, el objeto de datos no necesita declararse con el <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo. Sin embargo, el objeto de datos debe cumplir ciertos requisitos que se agregarán a la caché de datos. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Para almacenar en caché mediante programación un objeto de datos

1. Declare el objeto de datos en el nivel de clase, no dentro de un método. En este ejemplo se da por supuesto que está declarando un <xref:System.Data.DataSet> denominado `dataSet1` que desea almacenar en caché mediante programación.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Una instancia del objeto de datos y, a continuación, llame a la `StartCaching` método de la instancia de documento u hoja de cálculo y pase el nombre del objeto de datos.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Para detener el almacenamiento en caché un objeto de datos

1. Llame a la `StopCaching` método de la instancia de documento u hoja de cálculo y pase el nombre del objeto de datos. En este ejemplo se supone que tiene un <xref:System.Data.DataSet> denominado `dataSet1` que desea detener el almacenamiento en caché.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > No llame a `StopCaching` desde el controlador de eventos para el `Shutdown` eventos de un documento u hoja de cálculo. En el momento en el `Shutdown` provoca el evento, es demasiado tarde para modificar la caché de datos. Para obtener más información sobre la `Shutdown` eventos, consulte [Events in Office Projects](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Vea también

- [Almacenar datos en caché](../vsto/caching-data.md)
- [Cómo: Almacenar en caché datos para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Acceder a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)
- [Guardar datos](../data-tools/saving-data.md)
