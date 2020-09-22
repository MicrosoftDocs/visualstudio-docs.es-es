---
title: 'Cómo: Especificar opciones de instrumentación adicional | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842582"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Cómo: Especificar opciones de instrumentación adicional
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los binarios se pueden instrumentar desde el entorno de desarrollo integrado (IDE) de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], o mediante herramientas de la línea de comandos. Si instrumenta un binario desde el IDE, puede controlar el volumen de datos que se recopila. Para ello, especifique opciones de instrumentación adicionales a la herramienta [VSInstr](../profiling/vsinstr.md). Estas opciones están disponibles por sesión o por destino. Por ejemplo, para incluir o excluir funciones concretas durante el proceso de instrumentación, utilice la opción de instrumentación adicional en el nivel de destino.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Cada análisis que se inserta modifica ligeramente el comportamiento del programa original. Esta modificación provoca una sobrecarga durante el análisis. Aunque se resta una aproximación de esta sobrecarga, afecta sutilmente al control del tiempo en las aplicaciones multiproceso. Las opciones de la herramienta [VSInstr](../profiling/vsinstr.md) ayudan a controlar la recolección de datos durante la generación de perfiles.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Para especificar la opción de instrumentación adicional  
  
1. En el **Explorador de rendimiento**, seleccione la **Sesión de rendimiento** y después haga clic con el botón derecho y seleccione **Propiedades**.  
  
2. En las **Páginas de propiedades**, haga clic en las propiedades **Avanzadas**.  
  
3. Escriba las opciones en el cuadro **Opciones de instrumentación adicionales**.  
  
     Por ejemplo, utilice /CONTROL:THREAD para especificar el nivel de generación de perfiles. Para obtener una lista completa de opciones, consulte [VSInstr](../profiling/vsinstr.md).  
  
4. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)
