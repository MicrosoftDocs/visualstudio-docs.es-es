---
title: 'Cómo: depurar código insertado | Microsoft Docs'
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04c0430140d848c3c0b2386cc4156be1dbdd47c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819789"
---
# <a name="how-to-debug-injected-code"></a>Cómo: Depurar código insertado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 El uso de atributos puede simplificar enormemente la programación en C++. Para obtener más información, consulte [conceptos](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). El compilador se encarga de interpretar directamente algunos atributos. Otros atributos insertan código en el archivo de código fuente del programa, que el compilador se encarga entonces de compilar. Este código insertado facilita la programación al reducir la cantidad de código que se debe escribir. Sin embargo, a veces un error puede hacer que la aplicación no funcione correctamente mientras se ejecuta el código insertado. En estos casos, debería examinarse el código insertado. Visual Studio proporciona dos modos de examinar el código insertado.  
  
- Puede ver código insertado en el **desensamblado** ventana.  
  
- Uso de [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), puede crear un archivo de código fuente combinado que contiene código original e insertado.  
  
  El **desensamblado** ventana muestra instrucciones de lenguaje de ensamblado que se corresponden con el código fuente y el código insertado por los atributos. Además, el **desensamblado** ventana puede mostrar la anotación del código fuente.  
  
### <a name="to-turn-on-source-annotation"></a>Para activar la anotación del código fuente  
  
-   Haga clic en el **desensamblado** ventana y elija **mostrar código fuente** en el menú contextual.  
  
     Si conoce la ubicación de un atributo en una ventana de código fuente, puede usar el menú contextual para buscar el código insertado en el **desensamblado** ventana.  
  
### <a name="to-view-injected-code"></a>Para ver el código insertado  
  
1.  El depurador debe hallarse en modo de interrupción.  
  
2.  En una ventana de código fuente, coloque el cursor delante de los atributos cuyo código insertado desea ver.  
  
3.  Haga clic en y seleccione **ir al desensamblado** en el menú contextual.  
  
     Si la ubicación del atributo está cerca del punto de ejecución actual, puede seleccionar la **desensamblado** ventana desde el **depurar** menú.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Para ver el código de desensamblado en el punto de ejecución actual  
  
1.  El depurador debe hallarse en modo de interrupción.  
  
2.  Desde el **depurar** menú, elija **Windows**y haga clic en **desensamblado**.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



