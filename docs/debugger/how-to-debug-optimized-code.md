---
title: "C&#243;mo: Depurar c&#243;digo optimizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "puntos de interrupción, en código optimizado"
  - "compilaciones de depuración, optimizar"
  - "depurar [C++], código optimizado"
  - "optimización, compilaciones de depuración"
  - "código optimizado, depurar"
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar c&#243;digo optimizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  La opción de compilador [\/Zo \(Mejorar la depuración optimizada\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging) \(introducida en Visual Studio Update 3\) genera información de depuración más enriquecida para código optimizado \(proyectos que no se compilan con la opción de compilador **\/Od**.  Consulte [\/O \(Opciones\) \(Optimizar código\)](/visual-cpp/build/reference/o-options-optimize-code).  Esto incluye compatibilidad mejorada para la depuración de las variables locales y las funciones insertadas.  
>   
>  [Editar y continuar](../debugger/edit-and-continue-visual-csharp.md) está deshabilitado cuando se utiliza la opción de compilador **\/zo**.  
  
 Cuando el compilador optimiza el código, cambia de posición y reorganiza las instrucciones.  Esto produce el código compilado más eficaz.  Debido a esta reorganización, el depurador no siempre puede identificar el código fuente que corresponde a un conjunto de instrucciones.  
  
 La optimización puede afectar a:  
  
-   Las variables locales, las cuales puede quitar el optimizador o moverlas a ubicaciones que el depurador no reconoce.  
  
-   Las posiciones dentro de una función, que cambian cuando el optimizador combina bloques de código.  
  
-   Nombres de función de los marcos en la pila de llamadas, que podrían ser incorrectos si el optimizador combina dos funciones.  
  
 Sin embargo, los marcos que aparecen en la pila de llamadas casi siempre son correctos, suponiendo que se dispone de símbolos para todos los marcos.  Los marcos de la pila de llamadas serán incorrectos si la pila está dañada, si tiene funciones escritas en lenguaje de ensamblado o hay marcos del sistema operativo sin su símbolo correspondiente en la pila de llamadas.  
  
 Siempre se muestran correctamente las variables globales y estáticas.  Igual sucede con el diseño de estructuras.  Si hay un puntero que señala a una estructura y el valor del puntero es correcto, todas las variables miembro de la estructura mostrarán el valor correcto.  
  
 Debido a estas limitaciones, se debería depurar con una versión sin optimizar del programa, siempre que sea posible.  De forma predeterminada, la optimización está desactivada en la configuración Debug de un programa de Visual C\+\+ y está activada en la configuración Release.  
  
 Sin embargo, los errores solo aparecen en la versión optimizada de un programa.  En ese caso, se debe depurar el código optimizado.  
  
### Para activar la optimización en una configuración de compilación Debug  
  
1.  Cuando vaya a crear un proyecto nuevo, seleccione el destino `Win32 Debug`.  Utilice como destino `Win32``Debug` hasta que el programa esté depurado por completo y pueda compilar un destino `Win32 Release`.  El compilador no optimiza el destino `Win32 Debug`.  
  
2.  Seleccione el proyecto en el Explorador de soluciones.  
  
3.  En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
4.  En el cuadro de diálogo **Páginas de propiedades**, asegúrese de que `Debug` está seleccionado en el cuadro de lista desplegable **Configuración**.  
  
5.  En la vista de carpetas de la izquierda, seleccione la carpeta **C\/C\+\+**.  
  
6.  En la carpeta **C\+\+**, seleccione `Optimization`.  
  
7.  En la lista de propiedades de la derecha, busque `Optimization`.  El valor de configuración correspondiente probablemente indica `Disabled (`[\/Od](/visual-cpp/build/reference/od-disable-debug)`)`.  Elija una de las otras opciones \(`Minimum Size``(`[\/O1](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(`[\/O2](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(`[\/Ox](/visual-cpp/build/reference/ox-full-optimization)`)` o `Custom`\).  
  
8.  Si elige la opción `Custom` para `Optimization`, puede definir opciones para cualquiera de las demás propiedades que se muestran en la lista de propiedades.  
  
9. Seleccione Propiedades de configuración, C\/C\+\+, nodo de línea de comandos de la página de propiedades del proyecto y agregue `(`[\/Zo](/visual-cpp/build/reference/zo-enhance-optimized-debugging)`)` al cuadro de texto **Opciones adicionales**.  
  
    > [!WARNING]
    >  `/Zo` requiere Visual Studio 2013 Update 3 o una versión posterior.  
    >   
    >  Si se agrega `/Zo`, se deshabilitará [Editar y continuar](../debugger/edit-and-continue-visual-csharp.md).  
  
 Cuando depure el código optimizado, use la ventana **Desensamblado** para ver qué instrucciones se crean y se ejecutan realmente.  Al establecer los puntos de interrupción, debe saber que un punto de interrupción se puede desplazar junto con una instrucción.  Por ejemplo, considere el siguiente código:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Suponga que se establece un punto de interrupción en esta línea.  Podría pensarse que el punto de interrupción se va a alcanzar 10 veces, pero, si el código está optimizado, el punto de interrupción sólo se ejecutará una vez.  Esto se debe a que la primera instrucción establece el valor de `x` en 0.  El compilador reconoce que esto sólo se tiene que hacer una vez y lo saca del bucle.  El punto de interrupción se traslada con ella.  Las instrucciones que comparan e incrementan `x` permanecen dentro del bucle.  En la ventana **Desensamblado**, la [unidad de incremento](http://msdn.microsoft.com/es-es/8791dac9-64d1-4bb9-b59e-8d59af1833f9) se establece automáticamente como Instrucción para obtener un mayor control, lo cual resulta útil cuando se ejecuta el código optimizado paso a paso.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)