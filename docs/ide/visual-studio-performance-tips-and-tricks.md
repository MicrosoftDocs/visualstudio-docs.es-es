---
title: Consejos para mejorar el rendimiento
ms.date: 08/13/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4aefa741352e80f4a20a51fa1ab36e617403c9c
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427007"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Sugerencias y trucos de rendimiento de Visual Studio

Las recomendaciones de rendimiento de Visual Studio están previstas para situaciones de memoria insuficiente, que se pueden plantear en algunos casos. En estas situaciones, puede optimizar determinadas características de Visual Studio que puede que no esté usando. Las sugerencias siguientes no están planteadas como recomendaciones generales.

> [!NOTE]
> Si tiene dificultades para usar el producto debido a problemas de memoria, háganoslo saber a través de la herramienta de [comentarios](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Uso de un sistema operativo de 64 bits

Si actualiza el sistema desde una versión de Windows de 32 bits a una de 64 bits, se amplía la cantidad de memoria virtual disponible para Visual Studio de 2 GB a 4 GB. Esto permite a Visual Studio gestionar cargas de trabajo considerablemente mayores, aunque sea un proceso de 32 bits.

Para obtener más información, vea [Memory limits](/windows/desktop/Memory/memory-limits-for-windows-releases) (Límites de memoria) y [Using /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/) (Uso de /LARGEADDRESSAWARE en Windows de 64 bits).

## <a name="disable-automatic-file-restore"></a>Desactivación de la restauración automática de archivos

En Visual Studio, los documentos que se hayan dejado abiertos en la sesión anterior se vuelven a abrir automáticamente. Esto puede prolongar el tiempo que tarda en cargar una solución en hasta un 30 % o más, dependiendo del tipo de proyecto y los documentos que se están abriendo. Los diseñadores como Windows Forms y XAML, así como algunos archivos de JavaScript y typeScript, pueden tardar bastante en abrirse.

Visual Studio lo notifica con una barra amarilla de que la restauración de documentos está provocando que una solución cargue de forma notablemente más lenta. Puede deshabilitar esta función con las instrucciones siguientes:

1. Seleccione **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**.

1. En la página **Proyectos y soluciones** > **General**, desmarque la opción **Reopen documents on solution load** (Volver a abrir documentos al cargar la solución).

Si deshabilita la restauración automática de archivos, puede acceder a archivos rápidamente usando uno de los comandos de [Ir a](../ide/go-to.md):

- Para la función general **Ir a**, seleccione **Edición** > **Ir a** > **Ir a todo**, o bien presione **Ctrl**+**T**.

- Vaya a la última ubicación de edición de una solución mediante **Edición** > **Ir a** > **Ir a última ubicación de edición**, o bien presione **Ctrl**+**Mayús**+**Retroceso**.

- Use **Ir a archivo reciente** para ver una lista de archivos visitados recientemente en una solución. Seleccione **Edición** > **Ir a** > **Ir a archivo reciente**, o bien presione **Ctrl**+**1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Configuración de opciones de depuración

Si es habitual que se quede sin memoria durante las sesiones de depuración, puede optimizar el rendimiento si realiza uno o más cambios de configuración.

- **Habilite Solo mi código**

    La optimización más sencilla consiste en habilitar la característica **Solo mi código**, que solo carga los símbolos del proyecto. La habilitación de esta característica puede traducirse en un considerable ahorro de memoria para depurar aplicaciones administradas (.NET). Esta opción ya está habilitada de forma predeterminada en algunos tipos de proyecto.

    Para habilitar **Solo mi código**, elija **Herramientas** > **Opciones** > **Depuración** > **General** y luego seleccione **Habilitar solo mi código**.

- **Especifique los símbolos que se van a cargar**

    En la depuración nativa, la carga de archivos de símbolos ( *.pdb*) resulta costosa en términos de recursos de memoria. Puede establecer la configuración de símbolos del depurador de modo que se ahorre memoria. Por lo general, la solución se configura para cargar únicamente los módulos del proyecto.

    Para especificar la carga de símbolos, elija **Herramientas** > **Opciones** > **Depuración** > **Símbolos**.

    Establezca las opciones en **Solo los módulos especificados** en lugar de **Todos los módulos** y luego especifique qué módulos quiere cargar. Durante la depuración, también puede hacer clic con el botón derecho en módulos concretos de la ventana **Módulos** para incluir explícitamente un módulo en la carga de símbolos. (Para abrir la ventana durante la depuración, elija **Depurar** > **Ventanas** > **Módulos**).

    Para obtener más información, vea [Understanding symbol files](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019) (Introducción a los archivos de símbolos).

- **Deshabilite las herramientas de diagnóstico**

    Se recomienda deshabilitar la generación de perfiles de CPU después de su uso. Esta característica puede consumir grandes cantidades de recursos. Una vez habilitada la generación de perfiles de CPU, este estado se mantiene en las sesiones de depuración posteriores, por lo que merece la pena desactivarla de forma explícita al terminar. Puede ahorrar algunos recursos si deshabilita las herramientas de diagnóstico durante la depuración si no necesita las características proporcionadas.

    Para deshabilitar las **herramientas de diagnóstico**, inicie una sesión de depuración, elija **Herramientas** > **Opciones** > **Habilitar herramientas de diagnóstico** y anule la selección de la opción.

    Para más información, vea [Herramientas de generación de perfiles](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Deshabilitación de herramientas y extensiones

Algunas herramientas o extensiones se pueden desactivar para mejorar el rendimiento.

> [!TIP]
> A menudo se pueden aislar los problemas de rendimiento si se desactivan las extensiones de una en una y se vuelve a comprobar el rendimiento.

### <a name="managed-language-service-roslyn"></a>Servicios de lenguaje administrados (Roslyn)

Para más información sobre las consideraciones de rendimiento de .NET Compiler Platform ("Roslyn"), vea [Performance considerations for large solutions](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md) (Consideraciones de rendimiento para soluciones de gran tamaño).

- **Deshabilitar el análisis completo de la solución**

    Visual Studio realiza un análisis de toda la solución con el fin de proporcionar una experiencia completa sobre errores antes de invocar una compilación. Esta característica es útil para identificar los errores lo antes posible. Sin embargo, en el caso de las soluciones de gran tamaño, esta característica puede consumir considerables recursos de memoria. Si experimenta problemas de memoria o similares, puede deshabilitar esta experiencia para liberar estos recursos. De forma predeterminada, esta opción está habilitada para Visual Basic y deshabilitada para C#.

    Para deshabilitar **Análisis completo de la solución**, elija **Herramientas** > **Opciones** > **Editor de texto** y, a continuación seleccione **Visual Basic** o **C#** . Elija **Avanzadas** y desmarque la opción **Habilitar análisis de la solución completa**.

- **Deshabilite CodeLens**

    Visual Studio realiza una tarea **Buscar todas las referencias** en cada método cuando este se muestra. CodeLens proporciona características como la presentación en línea del número de referencias. El trabajo se realiza en un proceso independiente, como *ServiceHub.RoslynCodeAnalysisService32*. En soluciones de gran tamaño o en sistemas con recursos limitados, esta característica puede tener un impacto considerable sobre el rendimiento. Si experimenta problemas de memoria, por ejemplo, al cargar una solución de gran tamaño en un equipo de 4 GB, o un uso elevado de la CPU en este proceso, puede deshabilitar CodeLens para liberar recursos.

    Para deshabilitar **CodeLens**, elija **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **CodeLens** y anule la selección de la característica.

    > [!NOTE]
    > CodeLens está disponible en las ediciones Professional y Enterprise de Visual Studio.

### <a name="other-tools-and-extensions"></a>Otras herramientas y extensiones

- **Deshabilite extensiones**

    Las extensiones son componentes de software adicionales agregados a Visual Studio para proporcionar nueva funcionalidad o extender la funcionalidad existente. Las extensiones suelen ser una fuente de problemas de recursos de memoria. Si experimenta problemas de recursos de memoria, intente deshabilitar extensiones de una en una para ver cómo repercuten en el escenario o el flujo de trabajo.

   ::: moniker range="vs-2017"

    Para deshabilitar extensiones, vaya a **Herramientas** > **Extensiones y actualizaciones** y deshabilite una extensión determinada.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Para deshabilitar extensiones, vaya a **Extensiones** > **Administrar extensiones** y deshabilite una extensión determinada.

   ::: moniker-end

- **Deshabilitar el modo de mapa**

    El [**modo de mapa**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) muestra líneas de código en miniatura en la barra de desplazamiento. El modo de mapa está habilitado de forma predeterminada.

    Para deshabilitar el modo de mapa, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Todos los idiomas** > **Barras de desplazamiento** y, en la sección **Comportamiento**, desactive la opción **Usar el modo Mapa para la barra de desplazamiento vertical**.

- **Deshabilitar el ajuste de línea**

    El [**ajuste de línea**](./reference/how-to-manage-word-wrap-in-the-editor.md) muestra la parte de una línea de código larga que se extiende más allá del ancho actual de la ventana del editor de código. El ajuste de línea está habilitado de manera predeterminada.

    Para deshabilitar el ajuste de línea para un proyecto en el que está trabajando actualmente, vaya a **Editar** > **Avanzadas** > **Ajuste de línea**. (Use los mismos comandos de menú para cambiar esta configuración).

    Para deshabilitar el ajuste de línea en todos los proyectos, vaya a **Herramientas** > **Opciones** > **General** > **Editor de texto** > **Todos los idiomas** > **General** y, en la sección **Configuración**, deshabilite la opción **Ajuste de línea**.

- **Deshabilite el diseñador XAML**

    El diseñador XAML está habilitado de forma predeterminada, pero solo consume recursos si se abre un archivo *.xaml*. Si trabaja con archivos XAML pero no quiere usar la funcionalidad del diseñador, deshabilite esta característica para liberar memoria.

    Para deshabilitar el diseñador XAML, vaya a **Herramientas** > **Opciones** > **Diseñador XAML** > **Habilitar diseñador XAML** y anule la selección de la opción.

- **Quite cargas de trabajo**

    Puede usar el instalador de Visual Studio para quitar las cargas de trabajo que ya no se usen. Esta acción puede simplificar el costo de inicio y en tiempo de ejecución al omitir paquetes y ensamblados que ya no se necesitan.

## <a name="force-a-garbage-collection"></a>Aplicación de recolección de elementos no utilizados

CLR usa un sistema de administración de memoria de recopilación de elementos no utilizados. En este sistema, a veces hay objetos que ya no son necesarios pero que usan memoria. Este estado es temporal; el recolector de elementos no utilizados libera esta memoria en función de su rendimiento y heurística de uso de recursos. Puede forzar a CLR a que recopile la memoria sin usar mediante una tecla de acceso rápido en Visual Studio. Si hay una cantidad considerable de elementos no utilizados en espera de recolección y se fuerza esta, debería ver cómo se reduce el uso de memoria del proceso *devenv.exe* en el **Administrador de tareas**. Es raro tener que recurrir a este método. Pero después de que se haya completado una operación costosa (por ejemplo, una compilación completa, una sesión de depuración o un evento de apertura de solución), puede ayudar a determinar cuánta memoria está usando realmente el proceso. Dado que Visual Studio es mixto (administrado y nativo), a veces es posible que el asignador nativo y el recolector de elementos no utilizados compitan por recursos de memoria limitados. En condiciones de elevado uso de memoria, puede ser útil forzar la ejecución del recolector de elementos no utilizados.

Para forzar una recolección de elementos no utilizados, use la tecla de acceso rápido: **Ctrl**+**Alt**+**Mayús**+**F12**, **Ctrl**+**Alt**+**Mayús**+**F12** (presionar dos veces).

Si la aplicación de la recolección de elementos no utilizados hace que el escenario funcione mejor, rellene un informe a través de la herramienta de comentarios de Visual Studio, ya que este comportamiento probablemente sea un error.

Para obtener una descripción detallada del recolector de elementos no utilizados de CLR, vea [Fundamentals of Garbage Collection](/dotnet/standard/garbage-collection/fundamentals) (Aspectos básicos de la recolección de elementos no utilizados).

## <a name="see-also"></a>Consulte también

- [Optimización del rendimiento de Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Load solutions faster (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/) [Carga más rápida de las soluciones (blog de Visual Studio)]
