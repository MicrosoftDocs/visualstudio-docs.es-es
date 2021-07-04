---
title: 'Tutorial: Depuración de errores de representación debidos al sombreado | Microsoft Docs'
description: Siga una investigación que encuentre un error de sombreador. Muestra el uso de Diagnóstico de gráficos de Visual Studio, incluido el historial de píxeles de gráfico y el depurador de HLSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 218b263d7e971a0d2bdaa72020bb7cb58c31e000
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387091"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Tutorial: Depuración de errores de representación debidos al sombreado
En este tutorial se muestra cómo usar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para investigar un objeto que tiene un color incorrecto debido a un error del sombreador.

 En este tutorial se muestra cómo:

- Examinar el documento de registro de gráficos para identificar los píxeles que muestran el problema.

- Usar la ventana **Historial de píxeles de gráfico** para examinar el estado de los píxeles más en detalle.

- Usar el **Depurador de HLSL** para examinar los sombreadores de vértices y píxeles.

## <a name="scenario"></a>Escenario
 Los colores incorrectos de los objetos normalmente se dan cuando un sombreador de vértices pasa información de sombreador de píxeles incompleta o incorrecta.

 En este escenario, se ha agregado recientemente un objeto a la aplicación. También se han agregado un nuevo vértice y sombreadores de píxeles para transformar el objeto y darle una apariencia única. Cuando se ejecuta la aplicación durante una prueba, el objeto se representa en negro sólido. Con el Diagnóstico de gráficos puede capturar el problema en un registro de gráficos para poder depurar la aplicación. El problema tiene el aspecto de esta imagen en la aplicación:

 ![El objeto se presenta con colores incorrectos.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Investigación
 Mediante las herramientas de Diagnóstico de gráficos, puede cargar el documento del registro de gráficos para inspeccionar los fotogramas que se capturaron durante la prueba.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos

1. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un registro de gráficos que tenga un fotograma que muestre el modelo que falta. Aparecerá una nueva ventana de documento de registro de gráficos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En la parte superior de esta ventana está la salida del destino de representación del fotograma seleccionado. En la parte inferior está la **Lista de fotogramas**, que muestra cada fotograma capturado como imagen en miniatura.

2. En la **Lista de fotogramas**, seleccione un fotograma en el que el objeto no tenga el aspecto correcto. El destino de representación se actualiza para reflejar el fotograma seleccionado. En este escenario, la ventana de documento de registro de gráficos tiene el aspecto de esta imagen:

    ![Documento de registro de gráficos en Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Después de seleccionar un fotograma que muestre el problema, puede usar la ventana **Historial de píxeles de gráfico** para diagnosticarlo. La ventana **Historial de píxeles de gráfico** muestra las primitivas que podrían haber tenido efecto en un píxel concreto, sus sombreadores y los efectos que tuvo en el destino de representación, en orden cronológico.

#### <a name="to-examine-a-pixel"></a>Para examinar un píxel

1. Abra la ventana del **Historial de píxeles de gráfico**. En la barra de herramientas **Diagnóstico de gráficos**, elija **Historial de píxeles**.

2. Seleccione un píxel que quiera examinar. En la ventana de documento de registro de gráficos, seleccione uno de los píxeles en el objeto que se colorea incorrectamente:

    ![Al seleccionar un píxel se muestra información sobre su historial.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    La ventana **Historial de píxeles de gráfico** se actualiza para reflejar el píxel seleccionado. En este escenario, la ventana **Historial de píxeles de gráfico** tiene el aspecto siguiente:

    ![El historial de píxeles muestra un evento DrawIndexed.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Observe que el resultado del sombreador de píxeles es negro, completamente opaco (0, 0, 0, 1), y que la **Fusión de salida** combinó este sombreador de píxeles con el color **Anterior** del píxel, de manera que el **Resultado** también es negro, completamente opaco.

   Después de examinar un píxel que se colorea incorrectamente y detectar que la salida del sombreador de píxeles no es el color esperado, puede utilizar el depurador de HLSL para examinar el sombreador de píxeles y averiguar qué ha ocurrido con el color del objeto. Puede utilizar el depurador de HLSL para examinar el estado de las variables de HLSL durante la ejecución, recorrer el código de HLSL y establecer puntos de interrupción que le ayuden a diagnosticar el problema.

#### <a name="to-examine-the-pixel-shader"></a>Para examinar el sombreador de píxeles

1. Inicie la depuración del sombreador de píxeles. En la ventana **Historial de píxeles de gráfico**, en la primitiva del objeto, junto a **Sombreador de píxeles**, elija el botón **Iniciar depuración**.

2. En este escenario, como el sombreador de píxeles simplemente pasa el color a través de sombreador de vértices, es fácil observar que el sombreador de píxeles no es el origen del problema.

3. Sitúe el puntero en `input.color`. Observe que su valor es negro completamente opaco (0, 0, 0, 1).

    ![El miembro "color" de "input" es negro.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    En este escenario, el examen revela que el color incorrecto es probablemente el resultado de un sombreador de vértices que no proporciona la información de color correcta para que el sombreador de píxeles funcione bien.

   Una vez ha determinado que el sombreador de vértices probablemente no proporciona la información correcta al sombreador de píxeles, el paso siguiente es examinar el sombreador de vértices.

#### <a name="to-examine-the-vertex-shader"></a>Para examinar el sombreador de vértices

1. Inicie la depuración del sombreador de vértices. En la ventana **Historial de píxeles de gráfico**, en la primitiva del objeto, junto a **Sombreador de vértices**, elija el botón **Iniciar depuración**.

2. Busque la estructura de salida del sombreador de vértices (se trata de la entrada para el sombreador de píxeles). En este escenario, el nombre de esta estructura es `output`. Examine el código del sombreador de vértices y observe que el miembro `color` de la estructura `output` se ha establecido explícitamente en negro totalmente opaco, quizás como resultado de los esfuerzos de depuración de alguien.

3. Confirme que el miembro de color nunca se copia de la estructura de entrada. Como el valor de `output.color` se establece en negro totalmente opaco justo antes de que se devuelva la estructura `output`, le aconsejamos que compruebe que el valor de `output` no se haya inicializado correctamente en una línea anterior. Recorra el código del sombreador de vértices hasta llegar a la línea que establece `output.color` en negro mientras comprueba el valor de `output.color`. Observe que el valor de `output.color` no se inicializa hasta que se establece en negro. Esto confirma que la línea de código que establece `output.color` en negro debe modificarse, en lugar de eliminarse.

    ![El valor de "output.color" es negro.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Después de determinar que la causa del problema de representación es que el sombreador de vértices no proporciona el valor de color correcto al sombreador de píxeles, puede utilizar esta información para solucionar el problema. En este escenario, se puede corregir cambiando el código siguiente del sombreador de vértices

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 por

```hlsl
output.color = input.color;
```

 Este código simplemente pasa el color de vértice de los vértices del objeto sin modificaciones (los sombreadores de vértices más complejos podrían modificar el color antes de pasarlo). El código del sombreador de vértices corregido debería parecerse a lo siguiente:

 ![Código del sombreador de vértices corregido.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Después de corregir el código, vuelva a compilarlo y ejecute de nuevo la aplicación para comprobar que se ha resuelto el problema de representación.

 ![El objeto se presenta con los colores correctos.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
