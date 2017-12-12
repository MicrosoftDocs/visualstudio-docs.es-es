---
title: "Cómo: Filtrar informes desde la línea de comandos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff4bae4f3071755149acdea49d312f8a9efcf31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Cómo: Filtrar informes desde la línea de comandos
Al usar las opciones del comando **VSPerfReport**, puede filtrar los informes a un segmento de tiempo específico del archivo de datos de generación de perfiles o restringir los datos a uno o varios procesos o subprocesos. Para obtener más información sobre este comando, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opciones|Descripción|  
|-------------|-----------------|  
|**StartTime:**[*Value*]|Solo muestra los datos recopilados tras el valor (en milisegundos).|  
|**EndTime:**[*Value*]|Solo muestra los datos recopilados antes del valor (en milisegundos).|  
|**FilterFile:** `VSPFFile`|Especifica la ubicación de un archivo de filtro generado en la ventana **Informe de rendimiento de Visual Studio**.|  
|**MsFilter:**[*StartTime,Duration*]|Solo se muestran los datos de `StartTime` hasta la longitud de `Duration` (en milisegundos).|  
|**Process:**[*Pid*]|Solo muestra los datos del proceso especificado.|  
|**Thread:**[*ThreadID*]|Solo muestra los datos del subproceso especificado.|  
|**Thread:**[*ThreadID,ProcessID*]|Solo muestra los datos del subproceso especificado que está asociado al proceso especificado.|