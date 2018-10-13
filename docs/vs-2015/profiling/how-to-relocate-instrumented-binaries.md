---
title: 'Cómo: Cambiar la ubicación de binarios instrumentados | Microsoft Docs'
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
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d0ddfb3cd52e212965ebf928bf087519f38b0bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240986"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Cómo: Cambiar la ubicación de binarios instrumentados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durante la instrumentación, se insertan análisis en el binario para medir el rendimiento de la aplicación. Si opta por reubicar el binario instrumentado, se instrumenta una copia del binario original y se coloca en la ubicación especificada. Esta opción es útil si no desea que el generador de perfiles cambie el nombre del binario original. Si el binario no se reubica, se sobrescribe su versión original.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Para reubicar un binario instrumentado  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  En **Páginas de propiedades**, haga clic en las propiedades de **Binario** .  
  
3.  Active la casilla **Reubicar archivos binarios instrumentados** .  
  
4.  Especifique la ubicación del binario instrumentado.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



