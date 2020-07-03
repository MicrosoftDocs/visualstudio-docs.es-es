---
title: Procedimiento para filtrar informes desde la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3461965f0944200c44570cff5362aeeb143ed43c
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332251"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedimiento Filtrar informes desde la línea de comandos
Al usar las opciones del comando **VSPerfReport**, puede filtrar los informes a un segmento de tiempo específico del archivo de datos de generación de perfiles o restringir los datos a uno o varios procesos o subprocesos. Para obtener más información sobre este comando, vea [VSPerfReport](../profiling/vsperfreport.md).

|Opciones|Descripción|
|-------------|-----------------|
|**StartTime:** [*Value*]|Solo muestra los datos recopilados tras el valor (en milisegundos).|
|**EndTime:** [*Value*]|Solo muestra los datos recopilados antes del valor (en milisegundos).|
|**FilterFile:** `VSPFFile`|Especifica la ubicación de un archivo de filtro generado en la ventana **Informe de rendimiento de Visual Studio**.|
|**MsFilter:** [*StartTime,Duration*]|Solo se muestran los datos de `StartTime` hasta la longitud de `Duration` (en milisegundos).|
|**Process:** [*Pid*]|Solo muestra los datos del proceso especificado.|
|**Thread:** [*ThreadID*]|Solo muestra los datos del subproceso especificado.|
|**Thread:** [*ThreadID,ProcessID*]|Solo muestra los datos del subproceso especificado que está asociado al proceso especificado.|
