---
title: Guardar y exportar datos de herramientas de rendimiento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9b96ae54c91e80fe34c817f710cb400e61f9876
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "51768503"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Guardar y exportar datos de herramientas de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe cómo guardar y exportar archivos de datos de rendimiento.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Cómo: Guardar archivos de datos de rendimiento como archivos de informe analizado  
 Puede guardar vistas filtradas o sin filtrar de los archivos de datos de generación de perfiles (.vsp) como archivos de informe analizado (.vsps). Un archivo de informe analizado puede verse en la ventana de vista de informe y es mucho más pequeño que el archivo .vsp original, pero no se puede aplicar un filtro a los datos de un archivo .vsps. Puede crear un archivo de informe analizado desde el Explorador de rendimiento sin abrir el archivo en el entorno de desarrollo integrado (IDE), o bien puede abrir y filtrar el archivo .vsp y, después, guardar los resultados.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Para guardar un informe de rendimiento analizado desde el Explorador de rendimiento  
  
1.  En **Informes**, haga clic con el botón derecho en el archivo de datos de generación de perfiles que quiere analizar y, después, haga clic en **Guardar analizados**.  
  
2.  En el cuadro de diálogo **Guardar datos analizados** , especifique el directorio y escriba el nombre de archivo.  
  
3.  Haga clic en **Guardar**.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Para guardar un informe de rendimiento analizado desde la ventana de vista de informe  
  
1.  Abra el archivo de datos de generación de perfiles (.vsp) en la ventana de vista de informe.  
  
2.  (Opcional) Aplique un filtro a los datos. Para obtener más información, vea [Filtro de vista Informe de rendimiento](../profiling/performance-report-view-filter.md).  
  
3.  Haga clic en **Guardar analizados** en la barra de herramientas de la ventana de vista de informe.  
  
4.  En el cuadro de diálogo **Guardar datos analizados** , especifique el directorio y escriba el nombre de archivo.  
  
5.  Haga clic en **Guardar**.  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Procedimiento Exportar informes de herramientas de generación de perfiles a un archivo .xml o .csv  
 Puede exportar una o más vistas de informe desde un archivo .vsp o un archivo de datos de generación de perfiles .vsps como un archivo XML o delimitado por comas. Puede filtrar los datos en la ventana de vista de informe antes de exportar, o bien puede exportar vistas de informe del archivo de datos completo desde la ventana del **Explorador de rendimiento** .  
  
> [!NOTE]
>  También puede copiar y pegar filas seleccionadas de la ventana de vista de informe como valores separados por tabulaciones.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Para exportar un informe de rendimiento desde la ventana del Explorador de rendimiento  
  
1.  En el **Explorador de rendimiento**, seleccione el informe, haga clic con el botón derecho y seleccione **Exportar**.  
  
     Aparece el cuadro de diálogo **Exportar informe** .  
  
2.  Seleccione las vistas de informe que quiere exportar.  
  
3.  En **Prefix report with**(Prefijo de informe), especifique el prefijo que quiere agregar al nombre del informe.  
  
4.  En **Ubicación del informe exportado**, especifique el directorio.  
  
5.  En **Formato del informe exportado**, seleccione (delimitado por comas) (*.csv) o Datos XML (\*.xml).  
  
6.  Haga clic en **Exportar**.  
  
     Cada vista de informe se guarda en un archivo independiente denominado \<prefijo>_\<nombre de vista de informe>.\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Para exportar informes de rendimiento desde la ventana de vista de informe  
  
1.  Abra el archivo .vsp en la ventana de vista de informe.  
  
2.  (Opcional) Aplique un filtro a los datos. Para obtener más información, vea [Filtro de vista Informe de rendimiento](../profiling/performance-report-view-filter.md).  
  
3.  Haga clic en **Exportar informe** en la barra de herramientas de la ventana de vista de informe.  
  
4.  Seleccione las vistas de informe que quiere exportar.  
  
5.  En **Prefix report with**(Prefijo de informe), especifique el prefijo que quiere agregar al nombre del informe.  
  
6.  En **Ubicación del informe exportado**, especifique el directorio.  
  
7.  En **Formato del informe exportado**, seleccione (delimitado por comas) (*.csv) o Datos XML (\*.xml).  
  
8.  Haga clic en **Exportar**.  
  
     Cada vista de informe se guarda en un archivo independiente denominado \<prefijo>_\<nombre de vista de informe>.\<csv&#124;xml>  
  
## <a name="see-also"></a>Vea también  
 [Explorador de rendimiento](../profiling/performance-explorer.md)   
 [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)   
 [Comparar archivos de datos de rendimiento](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



