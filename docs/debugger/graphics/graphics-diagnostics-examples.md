---
title: Ejemplos de diagnóstico de gráficos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6816cced178e6e76a8fe33e37bbb075d1318c999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474309"
---
# <a name="graphics-diagnostics-examples"></a>Ejemplos de diagnóstico de gráficos
Estos ejemplos muestran cómo depurar problemas de presentación en aplicaciones basadas en DirectX utilizando Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="capturing-graphics-information"></a>Capturar información de gráficos  
 Antes de poder utilizar Diagnóstico de gráficos para diagnosticar problemas de presentación en la aplicación, debe capturar información de gráficos de la aplicación mientras se ejecuta. La información de gráficos se puede capturar desde una aplicación que está ejecutándose localmente o desde una aplicación que está ejecutándose en un equipo remoto o en otro dispositivo. Estos tutoriales explican cómo puede capturar información de gráficos desde una aplicación manualmente o mediante programación:  
  
-   [Tutorial: Capturar información de gráficos](walkthrough-capturing-graphics-information.md)  
  
-   [Tutorial: Capturar información de gráficos mediante programación](walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Utilice el Diagnóstico de gráficos con un dispositivo basado en ARM  
 Puede utilizar el Diagnóstico de gráficos para depurar la aplicación Direct3D en un dispositivo basado en ARM mediante la depuración remota. Para obtener más información, consulte [Cómo: usar diagnóstico de gráficos con un dispositivo ARM](how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Reproducción de la información de gráficos  
 Después de capturar información de gráficos desde una aplicación en ejecución, puede reproducir los eventos capturados para diagnosticar problemas de presentación. Para reproducirlos, puede utilizar su equipo de desarrollo o un equipo o dispositivo remoto al que esté conectado. Para obtener más información, consulte [Cómo: cambiar la máquina de reproducción de diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Depuración de objetos ausentes  
 Un objeto (u objetos) ausente es uno de los problemas de presentación más habituales con los que se encuentran los desarrolladores de gráficos. Este tipo de problema puede ser difícil de diagnosticar porque hay varios tipos de errores que pueden causar que parezca que un objeto que ha desaparecido. Las causas habituales de los objetos ausentes incluyen un estado del dispositivo mal configurado, problemas en la transformación de la geometría de los objetos o una canalización de gráficos mal configurada.  
  
 Estos escenarios demuestran cómo puede utilizar el diagnóstico de gráficos para determinar por qué falta un objeto y encontrar el código que se encarga.  
  
-   [Tutorial: Objetos ausentes debido al estado del dispositivo](walkthrough-missing-objects-due-to-device-state.md)  
  
-   [Tutorial: Objetos ausentes debido al sombreado de vértices](walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [Tutorial: Objetos ausentes debido a una canalización mal configurada](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Depuración de errores de presentación  
 Un objeto (u objetos) que no tiene la apariencia correcta es otro problema habitual de los desarrolladores de gráficos. Este tipo de problema puede ser difícil de diagnosticar porque la apariencia incorrecta y su causa pueden ser muy obvias, un enlace de una textura errónea, o muy sutiles, un problema en el código del sombreador o una interacción inesperada entre sombreadores. La causa de algunos problemas puede ser una combinación de errores.  
  
 A continuación se muestra un escenario que demuestra cómo puede utilizar el Diagnóstico de gráficos para determinar un problema de depuración no muy sutil causado por un problema menor del sombreador:  
  
-   [Tutorial: Depurar errores de representación debidos al sombreado](walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Depuración de sombreadores de cálculo  
 Puede utilizar el Diagnóstico de gráficos para depurar los kernels de sombreadores de cálculo DirectCompute que generan resultados incorrectos. Con DirectCompute, puede utilizar la potencia de cálculo de la GPU para realizar cálculos en un gran número de elementos de datos en paralelo. Para algunos tipos de problemas, utilizar la GPU puede rendir mucho más rápidamente que un código de CPU bien optimizado. Sin embargo, los depuradores tradicionales no pueden detectar código que se ejecute en la GPU. Depurar este tipo de código requiere herramientas especializadas que a menudo son propias del proveedor y es posible que no se integren bien en Visual Studio. Para que la depuración de sombreadores de cálculo sea más homogénea en un gran abanico de GPU, el Diagnóstico de gráficos captura los eventos de envío DirectCompute, además de los eventos de presentación de Direct3D, para que pueda utilizar herramientas con las que esté familiarizado para depurar problemas en el código de los sombreadores de cálculo.  
  
 Para un escenario que demuestra cómo depurar un problema de simulación que se debe a un error en un sombreador de cálculo, consulte [Tutorial: usar diagnóstico de gráficos para depurar un sombreador de cálculo](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).