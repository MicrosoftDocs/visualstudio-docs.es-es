---
title: Filtro de vista Informe de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4c5281386cb43d4dddb55db8578aea7515dce1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620907"
---
# <a name="performance-report-view-filter"></a>Filtro de vista Informe de rendimiento
La ventana **Filtro de vista Informe de rendimiento** se encuentra en la parte superior de la ventana **Informe de generador de perfiles**. Si no la ve, haga clic en el botón **Mostrar filtro**.

 Puede modificar cada cláusula de filtro para restringir los resultados. Las siguientes columnas están disponibles en el generador de filtros.

|Elemento de filtro|Descripción|
|-----------------|-----------------|
|Y/O|Elija **Y** si tanto esta cláusula como la siguiente deben ser true para coincidir con un resultado. Elija **O** si esta cláusula o la siguiente pueden ser true para coincidir con un resultado.|
|Campo|Seleccione el campo que se utilizará en la cláusula de filtro de la lista de campos de datos que están disponibles en el archivo de informe actual.|
|Operador|Elija el operador que especifica la relación que desea entre el campo y el valor.<br /><br /> =    Igual a<br /><br /> <>  No es igual a<br /><br /> <    Menor que<br /><br /> >    Mayor que<br /><br /> <=  Menor o igual que<br /><br /> >=  Mayor o igual que|
|Valor|Seleccione o especifique el valor que desea buscar. Algunos campos enumeran los valores disponibles para el campo.|

 Puede agregar cláusulas de filtro hasta que sienta que el filtro le dará los mejores resultados. Haga clic en **Ejecutar filtro** para aplicar el filtro al archivo de datos.

 Desde la vista de informe **Marcas**, puede generar cláusulas de filtro para limitar la vista de datos del informe a los datos recopilados entre dos marcas. Seleccione las marcas que en las que desea que comience y finalice el informe de datos, después haga clic con el botón derecho y seleccione **Agregar filtro a marcas** o **Agregar filtro a marcas de tiempo**. Ambos filtros limitan los datos en el archivo de datos actual al mismo alcance; **Agregar filtro a marcas** se puede aplicar a otros archivos .vsp.

 Para guardar el filtro, haga clic en **Exportar filtro** en la barra de herramientas de **Informe de rendimiento** y después especifique una ubicación y un nombre para el archivo .*vspf*. Para cargar un filtro previamente guardado, haga clic en **Importar filtro** y busque el archivo de filtro guardado. Los archivos de filtro también pueden utilizarse para filtrar archivos de datos en equipos que tengan instaladas las herramientas independientes de generación de perfiles. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Vea también
- [Análisis de datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)