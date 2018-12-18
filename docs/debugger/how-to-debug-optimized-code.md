---
title: 'Cómo: depurar código optimizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e212129c17ec7b4fe6cb9a6808c91cb302deb3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52387868"
---
# <a name="how-to-debug-optimized-code"></a>Cómo: Depurar código optimizado

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Restablecer configuración](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> La opción de compilador [/Zo (Mejorar la depuración optimizada)](/cpp/build/reference/zo-enhance-optimized-debugging) (introducida en Visual Studio Update 3) genera información de depuración más enriquecida para código optimizado (proyectos que no se compilan con la opción de compilador **/Od**. Vea [Opciones /O (Optimizar código)](/cpp/build/reference/o-options-optimize-code). Esto incluye compatibilidad mejorada para la depuración de las variables locales y las funciones insertadas.
>
> [Editar y continuar](../debugger/edit-and-continue-visual-csharp.md) está deshabilitado cuando se utiliza la opción de compilador **/zo**.

 Cuando el compilador optimiza el código, cambia de posición y reorganiza las instrucciones. Esto produce el código compilado más eficaz. Debido a esta reorganización, el depurador no siempre puede identificar el código fuente que corresponde a un conjunto de instrucciones.

 La optimización puede afectar a:

- Las variables locales, las cuales puede quitar el optimizador o moverlas a ubicaciones que el depurador no reconoce.

- Las posiciones dentro de una función, que cambian cuando el optimizador combina bloques de código.

- Nombres de función de los marcos en la pila de llamadas, que podrían ser incorrectos si el optimizador combina dos funciones.

  Sin embargo, los marcos que aparecen en la pila de llamadas casi siempre son correctos, suponiendo que se dispone de símbolos para todos los marcos. Los marcos de la pila de llamadas serán incorrectos si la pila está dañada, si tiene funciones escritas en lenguaje de ensamblado o hay marcos del sistema operativo sin su símbolo correspondiente en la pila de llamadas.

  Siempre se muestran correctamente las variables globales y estáticas. Igual sucede con el diseño de estructuras. Si hay un puntero que señala a una estructura y el valor del puntero es correcto, todas las variables miembro de la estructura mostrarán el valor correcto.

  Debido a estas limitaciones, se debería depurar con una versión sin optimizar del programa, siempre que sea posible. De forma predeterminada, la optimización está desactivada en la configuración Debug de un programa de Visual C++ y está activada en la configuración Release.

  Sin embargo, los errores solo aparecen en la versión optimizada de un programa. En ese caso, se debe depurar el código optimizado.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Para activar la optimización en una configuración de compilación Debug

1. Cuando vaya a crear un proyecto nuevo, seleccione el destino `Win32 Debug`. Utilice como destino `Win32``Debug` hasta que el programa esté depurado por completo y pueda compilar un destino `Win32 Release`. El compilador no optimiza el destino `Win32 Debug`.

2. Seleccione el proyecto en el Explorador de soluciones.

3. En el menú **Ver**, haga clic en **Páginas de propiedades**.

4. En el cuadro de diálogo **Páginas de propiedades**, asegúrese de que `Debug` está seleccionado en el cuadro de lista desplegable **Configuración**.

5. En la vista de carpetas de la izquierda, seleccione la carpeta **C/C++**.

6. En la carpeta **C++**, seleccione `Optimization`.

7. En la lista de propiedades de la derecha, busque `Optimization`. El valor de configuración correspondiente probablemente indica `Disabled (`[/Od](/cpp/build/reference/od-disable-debug)`)`. Elija una de las otras opciones (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(`[/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(`[/Ox](/cpp/build/reference/ox-full-optimization)`)` o `Custom`).

8. Si elige la opción `Custom` para `Optimization`, puede definir opciones para cualquiera de las demás propiedades que se muestran en la lista de propiedades.

9. Seleccione Propiedades de configuración, C/C++, nodo de línea de comandos de la página de propiedades del proyecto y agregue `(`[/Zo](/cpp/build/reference/zo-enhance-optimized-debugging)`)` al cuadro de texto **Opciones adicionales**.

    > [!WARNING]
    >  `/Zo` requiere Visual Studio 2013 Update 3 o una versión posterior.
    >
    >  Si se agrega `/Zo`, se deshabilitará [Editar y continuar](../debugger/edit-and-continue-visual-csharp.md).

   Cuando depure el código optimizado, use la ventana **Desensamblado** para ver qué instrucciones se crean y se ejecutan realmente. Al establecer los puntos de interrupción, debe saber que un punto de interrupción se puede desplazar junto con una instrucción. Por ejemplo, considere el siguiente código:

```cpp
for (x=0; x<10; x++)
```

 Suponga que se establece un punto de interrupción en esta línea. Podría pensarse que el punto de interrupción se va a alcanzar 10 veces, pero, si el código está optimizado, el punto de interrupción sólo se ejecutará una vez. Esto se debe a que la primera instrucción establece el valor de `x` en 0. El compilador reconoce que esto sólo se tiene que hacer una vez y lo saca del bucle. El punto de interrupción se traslada con ella. Las instrucciones que comparan e incrementan `x` permanecen dentro del bucle. En la ventana **Desensamblado**, la [unidad de incremento](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) se establece automáticamente como Instrucción para obtener un mayor control, lo cual resulta útil cuando se ejecuta el código optimizado paso a paso.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)