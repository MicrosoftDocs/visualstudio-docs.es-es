---
title: 'Cómo: Filtrar informes desde la línea de comandos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14be02ecf293cfb141b671917a715c8013009d2e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573807"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Cómo: Filtrar informes desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: filtrar informes desde la línea de comandos](https://docs.microsoft.com/visualstudio/profiling/how-to-filter-reports-from-the-command-line).  
  
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



