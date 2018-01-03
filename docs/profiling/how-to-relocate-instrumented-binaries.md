---
title: "Cómo: Cambiar la ubicación de binarios instrumentados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c15bfc5449a1dab516be217da4a76276312fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-relocate-instrumented-binaries"></a>Cómo: Cambiar la ubicación de binarios instrumentados
Durante la instrumentación, se insertan análisis en el binario para medir el rendimiento de la aplicación. Si opta por reubicar el binario instrumentado, se instrumenta una copia del binario original y se coloca en la ubicación especificada. Esta opción es útil si no desea que el generador de perfiles cambie el nombre del binario original. Si el binario no se reubica, se sobrescribe su versión original.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Para reubicar un binario instrumentado  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  En **Páginas de propiedades**, haga clic en las propiedades de **Binario** .  
  
3.  Active la casilla **Reubicar archivos binarios instrumentados** .  
  
4.  Especifique la ubicación del binario instrumentado.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)