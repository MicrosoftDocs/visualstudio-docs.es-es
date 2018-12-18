---
title: 'Cómo: Iniciar y finalizar la recopilación de datos de rendimiento | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 393cb5776043f3e9543cc9fe2c45773e36c09dd7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790037"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Cómo: Iniciar y finalizar la recopilación de datos de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe agregar el binario de destino del que desee generar perfiles a la sesión de rendimiento antes de iniciar la generación de perfiles. Para agregar un destino, haga clic con el botón derecho en **Destinos** en el **Explorador de rendimiento** y después haga clic en **Agregar binario de destino**. En el cuadro de diálogo **Agregar binario de destino**, seleccione el nombre de archivo y después haga clic en **Abrir**. Se agrega un nuevo binario.  
  
### <a name="to-start-profiling"></a>Para iniciar la generación de perfiles  
  
1.  Haga clic con el botón derecho en el nombre de la sesión de rendimiento en la ventana **Explorador de rendimiento** y elija una de las siguientes opciones:  
  
    -   **Iniciar con generación de perfiles**: inicia la aplicación y comienza inmediatamente la generación de perfiles.  
  
    -   **Iniciar con la generación de perfiles pausada**: inicia la aplicación pero no comienza a generar perfiles. Puede iniciar la generación de perfiles seleccionando **Reanudar recolección** en la ventana **Control de recolección de datos**. Para obtener más información, consulte [Cómo: Pausar y reanudar la recolección de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Para finalizar la generación de perfiles  
  
-   El método preferido para finalizar una sesión de generación de perfiles es salir de la aplicación. Para detener inmediatamente la generación de perfiles, vaya a la barra de herramientas del **Explorador de rendimiento** y haga clic en **Detener**.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Pausar y reanudar la recolección de datos de rendimiento](../profiling/how-to-pause-and-resume-performance-data-collection.md)



