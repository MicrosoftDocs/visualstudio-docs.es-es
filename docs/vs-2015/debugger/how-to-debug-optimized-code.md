---
title: 'Cómo: depurar código optimizado | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37cf0911023dcea501536b934ae9b6d84570e98b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568133"
---
# <a name="how-to-debug-optimized-code"></a>Cómo: Depurar código optimizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar código optimizado](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-optimized-code).  
  
NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  El [/Zo (mejorar la depuración optimizada)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)opción del compilador (introducida en Visual Studio Update 3) genera información de depuración más enriquecida para código optimizado (proyectos que no se compilan con la **/Od** opción del compilador. Consulte [opciones /O (optimizar código)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). Esto incluye compatibilidad mejorada para la depuración de las variables locales y las funciones insertadas.  
>   
>  [Editar y continuar](../debugger/edit-and-continue-visual-csharp.md) está deshabilitada cuando el **/Zo** se usa la opción de compilador.  
  
 Cuando el compilador optimiza el código, cambia de posición y reorganiza las instrucciones. Esto produce el código compilado más eficaz. Debido a esta reorganización, el depurador no siempre puede identificar el código fuente que corresponde a un conjunto de instrucciones.  
  
 La optimización puede afectar a:  
  
-   Las variables locales, las cuales puede quitar el optimizador o moverlas a ubicaciones que el depurador no reconoce.  
  
-   Las posiciones dentro de una función, que cambian cuando el optimizador combina bloques de código.  
  
-   Nombres de función de los marcos en la pila de llamadas, que podrían ser incorrectos si el optimizador combina dos funciones.  
  
 Sin embargo, los marcos que aparecen en la pila de llamadas casi siempre son correctos, suponiendo que se dispone de símbolos para todos los marcos. Los marcos de la pila de llamadas serán incorrectos si la pila está dañada, si tiene funciones escritas en lenguaje de ensamblado o hay marcos del sistema operativo sin su símbolo correspondiente en la pila de llamadas.  
  
 Siempre se muestran correctamente las variables globales y estáticas. Igual sucede con el diseño de estructuras. Si hay un puntero que señala a una estructura y el valor del puntero es correcto, todas las variables miembro de la estructura mostrarán el valor correcto.  
  
 Debido a estas limitaciones, se debería depurar con una versión sin optimizar del programa, siempre que sea posible. De forma predeterminada, la optimización está desactivada en la configuración Debug de un programa de Visual C++ y está activada en la configuración Release.  
  
 Sin embargo, los errores solo aparecen en la versión optimizada de un programa. En ese caso, se debe depurar el código optimizado.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Para activar la optimización en una configuración de compilación Debug  
  
1.  Cuando vaya a crear un proyecto nuevo, seleccione el destino `Win32 Debug`. Use la `Win32``Debug` de destino hasta que el programa esté depurado por completo y listo para compilar un `Win32 Release` destino. El compilador no optimiza el destino `Win32 Debug`.  
  
2.  Seleccione el proyecto en el Explorador de soluciones.  
  
3.  En el **vista** menú, haga clic en **páginas de propiedades**.  
  
4.  En el **páginas de propiedades** diálogo cuadro, asegúrese de que `Debug` está seleccionado en el **configuración** lista desplegable.  
  
5.  En la vista de carpetas de la izquierda, seleccione el **C o C++** carpeta.  
  
6.  En el **C++** carpeta, seleccione `Optimization`.  
  
7.  En la lista de propiedades de la derecha, busque `Optimization`. El valor de configuración correspondiente probablemente indica `Disabled (` [/Od](http://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5)`)`. Elija una de las otras opciones (`Minimum Size``(`[/O1](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Maximum Speed``(` [/O2](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Full Optimization``(` [/Ox](http://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760) `)`, o `Custom`).  
  
8.  Si elige la opción `Custom` para `Optimization`, puede definir opciones para cualquiera de las demás propiedades que se muestran en la lista de propiedades.  
  
9. Seleccione las propiedades de configuración, C/C ++, nodo de línea de comandos de la página de propiedades del proyecto y agregue `(` [/Zo](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` a la **opciones adicionales** cuadro de texto.  
  
    > [!WARNING]
    >  `/Zo` requiere Visual Studio 2013 Update 3 o una versión posterior.  
    >   
    >  Agregar `/Zo` deshabilitará [editar y continuar](../debugger/edit-and-continue-visual-csharp.md).  
  
 Cuando se depura código optimizado, use la **desensamblado** ventana para ver qué instrucciones se crean y se ejecuta realmente. Al establecer los puntos de interrupción, debe saber que un punto de interrupción se puede desplazar junto con una instrucción. Por ejemplo, considere el siguiente código:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Suponga que se establece un punto de interrupción en esta línea. Podría pensarse que el punto de interrupción se va a alcanzar 10 veces, pero, si el código está optimizado, el punto de interrupción sólo se ejecutará una vez. Esto se debe a que la primera instrucción establece el valor de `x` en 0. El compilador reconoce que esto sólo se tiene que hacer una vez y lo saca del bucle. El punto de interrupción se traslada con ella. Las instrucciones que comparan e incrementan `x` permanecen dentro del bucle. Cuando ve el **desensamblado** ventana, el [unidad paso](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) se establece automáticamente en la instrucción para un mayor control, lo que resulta útil cuando se recorra el código optimizado.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



