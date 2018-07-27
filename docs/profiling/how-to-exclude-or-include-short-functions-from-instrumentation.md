---
title: 'Cómo: Excluir o incluir funciones cortas en la instrumentación | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6234db781925e8c0558513cb7e8bc608b5cfea
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814689"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Cómo: Excluir o incluir funciones cortas en la instrumentación
De forma predeterminada, las herramientas de generación de perfiles excluyen *funciones pequeñas* de la instrumentación. Las funciones pequeñas son funciones cortas que no realizan ninguna llamada de función. Excluir estas funciones pequeñas proporciona menos sobrecarga de instrumentación y, por consiguiente, mejora la velocidad de instrumentación. La exclusión de las funciones pequeñas también reduce el tamaño del archivo de datos de generación de perfiles de rendimiento (.*vsp*) y el tiempo necesario para el análisis. Si se excluyen las funciones pequeñas, el tiempo que se emplea en ellas se descuenta del tiempo inclusivo y exclusivo de sus funciones primarias. Las funciones pequeñas se pueden incluir o excluir de la instrumentación, como se describe en el siguiente procedimiento.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Para excluir o incluir funciones cortas en la instrumentación  
  
1.  En el **Explorador de rendimiento**, seleccione **Sesión de rendimiento**, después haga clic con el botón derecho y seleccione **Propiedades**.  
  
     Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
2.  En **Páginas de propiedades**, haga clic en las propiedades de **Instrumentación** .  
  
3.  Para excluir funciones cortas de la instrumentación, seleccione **Excluir funciones cortas de la instrumentación**. Ésta es la configuración predeterminada.  
  
     O bien  
  
     Para incluir funciones cortas en la instrumentación, seleccione **Incluir funciones cortas en la instrumentación**.  
  
4.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)