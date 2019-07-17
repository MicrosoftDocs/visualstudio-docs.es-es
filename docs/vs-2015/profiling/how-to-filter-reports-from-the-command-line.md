---
title: Procedimiento Filtrar informes desde la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146007"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedimiento Filtro de informes desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al usar las opciones del comando **VSPerfReport**, puede filtrar los informes a un segmento de tiempo específico del archivo de datos de generación de perfiles o restringir los datos a uno o varios procesos o subprocesos. Para obtener más información sobre este comando, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opciones|DESCRIPCIÓN|  
|-------------|-----------------|  
|**StartTime:** [*Value*]|Solo muestra los datos recopilados tras el valor (en milisegundos).|  
|**EndTime:** [*Value*]|Solo muestra los datos recopilados antes del valor (en milisegundos).|  
|**FilterFile:** `VSPFFile`|Especifica la ubicación de un archivo de filtro generado en la ventana **Informe de rendimiento de Visual Studio**.|  
|**MsFilter:** [*StartTime,Duration*]|Solo se muestran los datos de `StartTime` hasta la longitud de `Duration` (en milisegundos).|  
|**Process:** [*Pid*]|Solo muestra los datos del proceso especificado.|  
|**Thread:** [*ThreadID*]|Solo muestra los datos del subproceso especificado.|  
|**Thread:** [*ThreadID,ProcessID*]|Solo muestra los datos del subproceso especificado que está asociado al proceso especificado.|
