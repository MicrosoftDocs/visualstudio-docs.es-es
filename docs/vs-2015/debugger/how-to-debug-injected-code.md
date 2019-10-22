---
title: Procedimiento Depurar código insertado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df35a25534961c6ab94891d2da6fe54f05c37a3e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681087"
---
# <a name="how-to-debug-injected-code"></a>Procedimiento Depuración de código insertado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 El uso de atributos puede simplificar enormemente la programación en C++. Para obtener más información, consulte [conceptos](https://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). El compilador se encarga de interpretar directamente algunos atributos. Otros atributos insertan código en el archivo de código fuente del programa, que el compilador se encarga entonces de compilar. Este código insertado facilita la programación al reducir la cantidad de código que se debe escribir. Sin embargo, a veces un error puede hacer que la aplicación no funcione correctamente mientras se ejecuta el código insertado. En estos casos, debería examinarse el código insertado. Visual Studio proporciona dos modos de examinar el código insertado.  
  
- Puede ver el código insertado en la ventana **Desensamblado**.  
  
- Mediante [/Fx](https://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), se puede crear un archivo de código fuente combinado que contiene código original e insertado.  
  
  La ventana **Desensamblado** muestra instrucciones en lenguaje de ensamblado que corresponden al código fuente y al código insertado por los atributos. Además, la ventana **Desensamblado** puede mostrar la anotación del código fuente.  
  
### <a name="to-turn-on-source-annotation"></a>Para activar la anotación del código fuente  
  
- Haga clic con el botón derecho en la ventana **Desensamblado** y elija **Mostrar código fuente** en el menú contextual.  
  
     Si conoce la ubicación de un atributo en una ventana de código fuente, puede utilizar el menú contextual para buscar el código insertado en la ventana **Desensamblado**.  
  
### <a name="to-view-injected-code"></a>Para ver el código insertado  
  
1. El depurador debe hallarse en modo de interrupción.  
  
2. En una ventana de código fuente, coloque el cursor delante de los atributos cuyo código insertado desea ver.  
  
3. Haga clic con el botón derecho y seleccione **Ir al desensamblado** en el menú contextual.  
  
     Si la ubicación del atributo está cerca del punto de ejecución actual, puede seleccionar la ventana **Desensamblado** en el menú **Depurar**.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Para ver el código de desensamblado en el punto de ejecución actual  
  
1. El depurador debe hallarse en modo de interrupción.  
  
2. En el menú **Depurar**, elija **Ventanas** y después haga clic en **Desensamblado**.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)
