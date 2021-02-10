---
title: Iniciar y finalizar la recopilación de datos de rendimiento | Microsoft Docs
description: Obtenga información sobre cómo puede agregar el binario de destino del que quiere generar perfiles a la sesión de rendimiento antes de iniciar la generación de perfiles.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e28d582dbbe25d587611b6b3174a4d4277887a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920695"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Procedimiento Iniciar y finalizar la recopilación de datos de rendimiento
Debe agregar el binario de destino del que desee generar perfiles a la sesión de rendimiento antes de iniciar la generación de perfiles. Para agregar un destino, haga clic con el botón derecho en **Destinos** en el **Explorador de rendimiento** y después haga clic en **Agregar binario de destino**. En el cuadro de diálogo **Agregar binario de destino**, seleccione el nombre de archivo y después haga clic en **Abrir**. Se agrega un nuevo binario.

### <a name="to-start-profiling"></a>Para iniciar la generación de perfiles

1. Haga clic con el botón derecho en el nombre de la sesión de rendimiento en la ventana **Explorador de rendimiento** y elija una de las siguientes opciones:

    - **Iniciar con generación de perfiles**: inicia la aplicación y comienza inmediatamente la generación de perfiles.

    - **Iniciar con la generación de perfiles pausada**: inicia la aplicación pero no comienza a generar perfiles. Puede iniciar la generación de perfiles seleccionando **Reanudar recolección** en la ventana **Control de recolección de datos**. Para obtener más información, vea [Cómo: Pausar y reanudar la recopilación de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Para finalizar la generación de perfiles

- El método preferido para finalizar una sesión de generación de perfiles es salir de la aplicación. Para detener inmediatamente la generación de perfiles, vaya a la barra de herramientas del **Explorador de rendimiento** y haga clic en **Detener**.

## <a name="see-also"></a>Vea también
- [Control de la recopilación de datos](../profiling/controlling-data-collection.md)
- [Cómo: Pausar y reanudar la recopilación de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md)
