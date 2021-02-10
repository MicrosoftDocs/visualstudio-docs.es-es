---
title: Depurador de sombreador HLSL | Microsoft Docs
description: Use el depurador de HLSL en el Analizador de gráficos para entender cómo funciona el código HLSL en la aplicación. El depurador puede simular el subproceso de HLSL exacto que le interese.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d9a51df36a21d0f5234f78f6ac23ebf65f0c414
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889244"
---
# <a name="hlsl-shader-debugger"></a>Depurador de sombreador HLSL
El depurador de HLSL en el Analizador de gráficos de Visual Studio hace que sea más fácil entender cómo funciona el código del sombreador HLSL en condiciones reales de la aplicación.

 Este es el depurador de HLSL:

 ![Depuración de HLSL mediante las ventanas Inspección y Pila de llamadas.](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>Introducción al depurador de HLSL
 El depurador de HLSL puede ayudarle a entender los problemas que surgen en el código del sombreador. Depurar código HLSL en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es similar a depurar código escrito en otros lenguajes, por ejemplo, en C++, C# o Visual Basic. Puede inspeccionar el contenido de las variables, establecer puntos de interrupción, ejecutar el código paso a paso y recorrer la pila de llamadas, exactamente igual que cuando depura otros lenguajes.

 Sin embargo, como con las GPU se consigue un alto rendimiento cuando se ejecuta código del sombreador en cientos de subprocesos al mismo tiempo, el depurador de HLSL se ha diseñado para que funcione con las demás herramientas del Analizador de gráficos para presentar toda la información de forma que tenga sentido. Analizador de gráficos vuelve a crear los fotogramas capturados usando la información que se recopiló en un registro de gráficos; el depurador de HLSL no supervisa la ejecución de la GPU en tiempo real mientras ejecuta código de sombreador. Dado que un registro de gráficos contiene información suficiente para volver a crear cualquier parte del resultado y, como Analizador de gráficos proporciona herramientas que pueden ayudarle a aislar el píxel y el evento exactos donde se ha producido el error, el depurador de HLSL solo tiene que simular el subproceso exacto del sombreador en el que está interesado. Esto significa que el trabajo del sombreador se puede simular en la CPU, donde se puede obtener una vista completa de sus mecanismos internos. Esto es lo que proporciona al depurador de HLSL una experiencia de depuración de tipo CPU.

 Sin embargo, el depurador de HLSL tiene las siguientes limitaciones:

- El depurador de HLSL no admite operaciones de edición y continuación, pero puede realizar cambios en los sombreadores y, después, volver a generar el marco para ver los resultados.

- No es posible depurar una aplicación y su código del sombreador al mismo tiempo. Sin embargo, puede alternar entre ellos.

- Puede agregar variables y registros a la ventana Inspección, pero no se admiten expresiones.

  Sin embargo, el depurador de HLSL proporciona un uso mejor y más parecido a la depuración de tipo CPU que lo que sería posible de cualquier otra forma.

## <a name="hlsl-shader-edit--apply"></a>Edición en el sombreador HLSL y aplicación
 El depurador del sombreador HLSL no admite Editar y continuar del mismo modo que el depurador de la CPU, porque el modelo de ejecución de la GPU no permite deshacer el estado del sombreador. En su lugar, el depurador HLSL admite Editar y aplicar, lo que le permite editar archivos de origen HLSL y, luego, elegir **Aplicar** para regenerar el marco y ver el efecto de los cambios. El código del sombreador modificado se almacena en un archivo independiente para preservar la integridad del archivo de origen HLSL del proyecto original, pero una vez que esté satisfecho con los cambios, puede elegir **Copiar a…** para copiar los cambios al proyecto. Con esta característica, puede iterar rápidamente sobre el código de sombreador que contiene errores y evitar los pasos de recompilación y captura del flujo de trabajo de depuración de HLSL, con el gran coste que conllevan.

## <a name="hlsl-disassembly"></a>Desensamblado de HLSL
 El depurador del sombreador de HLSL proporciona una lista de ensamblados de sombreador HLSL a la derecha de la lista de códigos de origen HLSL.

## <a name="debugging-hlsl-code"></a>Depurar código HLSL
 Puede tener acceso al depurador de HLSL desde las ventanas Etapas de canalización o Historial de píxeles.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Para iniciar el depurador de HLSL desde la ventana Etapas de canalización de gráficos

1. En la ventana **Etapas de canalización de gráficos**, establezca la etapa de canalización asociada el sombreador que desea depurar.

2. Debajo del título de la etapa de canalización, elija **Iniciar depuración**, que aparece como una pequeña flecha verde.

    > [!NOTE]
    > Este punto de entrada en el depurador HLSL solo depura el primer subproceso del sombreador para la etapa correspondiente, es decir, el primer vértice o píxel que se procesa. Puede usar Historial de píxeles para tener acceso a otros subprocesos de estas etapas del sombreador.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Para iniciar el depurador de HLSL desde el historial de píxeles de gráfico

1. En la ventana **Historial de píxeles de gráfico**, expanda la llamada de dibujo asociada al sombreador que desea depurar. Cada llamada de dibujo se puede corresponder con varios primitivos.

2. En los detalles de la llamada de dibujo, expanda un primitivo cuya contribución de color resultante sugiera que hay un error en el código del sombreador. Si hay varios primitivos que sugieren un error, elija el primer primitivo para evitar que se acumulen los errores, lo que podría dificultar el diagnóstico del problema.

3. En los detalles de primitivos, elija si desea depurar el **Sombreador de vértices** o el **Sombreador de píxeles**. Depure el sombreador de vértices si sospecha que el sombreador de píxeles es correcto pero está generando una contribución de color incorrecta porque el sombreador de vértices le está pasando constantes incorrectas. En caso contrario, depure el sombreador de píxeles.

    A la derecha del sombreador seleccionado, elija **Iniciar depuración**, que aparece como una pequeña flecha verde.

   > [!NOTE]
   > Este punto de entrada en el depurador de HLSL depura el subproceso del sombreador de píxeles que corresponde a la llamada de dibujo, primitivo y píxel elegidos, o los subprocesos del sombreador de vértices cuyos resultados están interpolados por la llamada de dibujo, primitivo y píxel elegidos. En el caso de los sombreadores de vértices, puede delimitar aún más el punto de entrada a un vértice concreto expandiendo los detalles del sombreador de vértices.

   Para obtener ejemplos sobre cómo utilizar el depurador de HLSL para depurar errores del sombreador, vea [Ejemplos](graphics-diagnostics-examples.md) o los tutoriales que se indican en la sección Vea también.

## <a name="see-also"></a>Vea también
- [Tutorial: Objetos ausentes debido al sombreado de vértices](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Tutorial: Depuración de errores de representación debidos al sombreado](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [Tutorial: Uso de Diagnóstico de gráficos para depurar un sombreador de cálculo](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)