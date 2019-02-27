---
title: 'Tutorial: Objetos ausentes debido al canalización mal configurada | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32b76a4f063cd15d5f36db6ea8b672dbeda4d54
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698058"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Tutorial: Objetos ausentes debido a una canalización mal configurada
En este tutorial se muestra cómo usar las herramientas de diagnóstico de gráficos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para investigar un objeto que falta como consecuencia de un sombreador de píxeles sin establecer.

 En el tutorial se muestran las tareas siguientes:

-   Uso de la **Lista de eventos gráficos** para buscar los posibles orígenes del problema.

-   Uso de la ventana **Etapas de canalización de gráficos** para examinar el efecto de la llamada API de Direct3D `DrawIndexed` .

-   Inspección del contexto del dispositivo para confirmar que no se estableció una etapa de sombreador.

-   Uso de la ventana **Etapas de canalización de gráficos** junto con la **Pila de llamadas de eventos gráficos** para ayudar a encontrar el origen del sombreador de píxeles sin establecer.

## <a name="scenario"></a>Escenario
 Cuando falta un objeto en una aplicación 3D, a veces se debe a que no se establece una de las etapas del sombreador antes de que se represente el objeto. En el caso de las aplicaciones que tienen necesidades de representación sencillas, el origen de este error se encuentra normalmente en algún lugar de la pila de llamadas de la llamada a draw del objeto. Sin embargo, como optimización, algunas aplicaciones procesan juntos objetos con programas de sombreador, texturas u otros datos en común para minimizar la sobrecarga del cambio de estado. En estas aplicaciones, el origen del error se podría incluir en el sistema de procesamiento por lotes, en lugar de encontrarse en la pila de llamadas de la llamada a draw. En el escenario de este tutorial se muestra una aplicación con necesidades de representación sencillas y, por tanto, el origen del error se puede encontrar en la pila de llamadas.

 En este escenario, cuando se ejecute la aplicación para probarla, se representará el fondo de la manera prevista, pero no aparecerá uno de los objetos. Con el Diagnóstico de gráficos puede capturar el problema en un registro de gráficos para poder depurar la aplicación. El problema tiene este aspecto en la aplicación:

 ![No se puede ver el objeto](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Investigación
 Mediante las herramientas de Diagnóstico de gráficos, puede cargar el documento del registro de gráficos para inspeccionar los fotogramas que se capturaron durante la prueba.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos

1. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un documento de registro de gráficos que contenga un fotograma que muestra el objeto que falta. Aparecerá una nueva pestaña de registro de gráficos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En la parte superior de esta pestaña está la salida del destino de representación del fotograma seleccionado. En la parte inferior está la **Lista de fotogramas**, que muestra cada fotograma capturado como imagen en miniatura.

2. En la **Lista de fotogramas**, seleccione un fotograma que muestre que no aparece el objeto. El destino de representación se actualiza para reflejar el fotograma seleccionado. En este escenario, la pestaña de registro de gráficos tiene el aspecto siguiente:

    ![Documento de registro de gráficos en Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Después de seleccionar un fotograma en el que se muestre el problema, puede comenzar a diagnosticarlo con la **Lista de eventos gráficos**. La **Lista de eventos gráficos** contiene cada llamada API de Direct3D que se realizó para representar el fotograma activo, como, por ejemplo, para configurar el estado del dispositivo, para crear y actualizar búferes, y para dibujar los objetos que aparecen en el fotograma. Muchos tipos de llamadas (por ejemplo, las llamadas a Draw, Dispatch, Copy o Clear) son interesantes, porque a menudo hay (aunque no siempre) un cambio correspondiente en el destino de representación cuando la aplicación funciona según lo esperado. Las llamadas a draw son especialmente interesantes porque cada una de ellas representa la geometría que representaba la aplicación.

   Dado que sabe que el destino de representación no contiene el objeto que falta, sino también que no parece que haya otros errores, puede usar la **Lista de eventos gráficos** junto con la herramienta **Etapas de canalización de gráficos** para determinar que la llamada a draw se corresponda con la geometría del objeto que falta. La ventana **Etapas de canalización de gráficos** muestra la geometría que se envió a cada llamada a draw, independientemente de su efecto en el destino de representación. Conforme se desplaza por las llamadas a draw, las etapas de canalización se actualizan para mostrar la geometría asociada a cada llamada a medida que fluye a través de cada etapa habilitada y la salida de destino se actualiza para mostrar el estado de destino de representación después de que se complete la llamada.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para encontrar la llamada a draw para la geometría que falta

1. Abra la ventana **Lista de eventos de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Lista de eventos**.

2. Abra la ventana **Etapas de canalización de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Etapas de canalización**.

3. A medida que se desplaza por cada llamada a draw en la ventana **Lista de eventos gráficos** , examine la ventana **Etapas de canalización de gráficos** para ver el objeto que falta. Para facilitar esta tarea, escriba "Draw" en el cuadro de **Búsqueda** que está ubicado en la esquina superior derecha de la ventana **Lista de eventos gráficos** . Con esto se filtra la lista para que solo incluya los eventos que tienen la palabra “Draw” en sus títulos.

    En la ventana **Etapas de canalización de gráficos** , la etapa **Ensamblador de entrada** muestra la geometría del objeto antes de que se transforme y la etapa **Sombreador de vértices** muestra el mismo objeto después de que se transforme. En este escenario, observe que en la ventana **Etapas de canalización de gráficos** se muestran las etapas **Ensamblador de entrada** y  **Sombreador de vértices** , pero no la etapa **Sombreador de píxeles** para una de las llamadas a draw.

   > [!NOTE]
   >  Si otras etapas de canalización (por ejemplo, las etapas del sombreador de casco, del sombreador de dominios o del sombreador de geometría) procesan el objeto, cualquiera de ellas podría ser la causa del problema. Normalmente, el problema está relacionado con la primera etapa en la que no se muestra el resultado o se muestra de forma inesperada.

4. Deténgase cuando llegue a la llamada a draw que se corresponde con el objeto que falta. En este escenario, en la ventana **Etapas de canalización de gráficos** se indica que la geometría se emitió a la GPU (que se indica por la presencia de la etapa **Ensamblador de entrada** ) y que se transformó (que se indica por la etapa **Sombreador de vértices** ), pero no aparece en el destino de representación porque no parece ser un sombreador de píxeles activo (que se indica por la ausencia de la etapa **Sombreador de píxeles** ). En este escenario, incluso puede ver la silueta del objeto que falta en la etapa **Fusión de salida** :

    ![Un evento DrawIndexed y su efecto en la canalización](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Después de confirmar que la aplicación emitió una llamada a draw para la geometría del objeto que falta y detectar que la fase del sombreador de píxeles estaba inactiva, puede examinar el estado del dispositivo para confirmar sus conclusiones. Puede usar la **Tabla de objetos gráficos** para examinar el contexto del dispositivo y otros datos de objetos de Direct3D.

#### <a name="to-examine-device-context"></a>Para examinar el contexto del dispositivo

1. Abra el **contexto del dispositivo d3d11**. En la ventana **Etapas de canalización de gráficos** , elija el vínculo **ID3D11DeviceContext** que forma parte de la llamada `DrawIndexed` que se muestra en la parte superior de la ventana.

2. Examine el estado del dispositivo que se muestra en el **contexto del dispositivo d3d11** para confirmar que no había ningún sombreador de píxeles activo durante la llamada a draw. En este escenario, la **información general del sombreador**, que aparece debajo del **estado del sombreador de píxeles**, indica que el sombreador es **NULL**:

    ![El contexto de dispositivo D3D 11 muestra el estado del sombreador de píxeles](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Después de confirmar que su aplicación estableció en NULL el sombreador de píxeles, el siguiente paso será encontrar la ubicación en el código fuente de la aplicación donde se establece el sombreador. Puede usar la **Lista de eventos gráficos** junto con la **Pila de llamadas de eventos gráficos** para encontrar esta ubicación.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Para encontrar el lugar donde se establece el sombreador de píxeles en el código fuente de la aplicación

1. Encuentre la llamada `PSSetShader` que se corresponde con el objeto que falta. En la ventana **Lista de eventos gráficos** , escriba "Draw;PSSetShader" en el cuadro de **Búsqueda** que se encuentra en la esquina superior derecha de la ventana **Lista de eventos gráficos** . Con esto se filtra la lista para que solo incluya los eventos "PSSetShader" y los eventos que tienen la palabra "Draw" en sus títulos. Elija la primera llamada `PSSetShader` que aparece antes de la llamada a draw del objeto que falta.

   > [!NOTE]
   >  `PSSetShader` no aparecerá en la ventana **Lista de eventos gráficos** si no se estableció durante este fotograma. Normalmente esto solo sucede si se usa un sombreador de píxeles para todos los objetos o si la llamada `PSSetShader` se omitió involuntariamente durante este fotograma. En cualquier caso, se recomienda buscar el código fuente de la aplicación para las llamadas `PSSetShader` y usar técnicas de depuración tradicionales para examinar el comportamiento de estas llamadas.

2. Abra la ventana **Pila de llamadas de eventos gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Pila de llamadas de eventos de gráficos**.

3. Use la pila de llamadas para buscar la llamada `PSSetShader` en el código fuente de la aplicación. En la ventana **Pila de llamadas de eventos gráficos** , elija la llamada que se encuentra más arriba y examine el valor en el que se establece el sombreador de píxeles. El sombreador de píxeles se puede establecer directamente en NULL o el valor NULL se podría producir debido a un argumento que se pasó a la función o a otro estado. Si no se establece directamente, podría encontrar el origen del valor NULL en algún lugar de la parte superior de la pila de llamadas. En este escenario, descubrirá que el sombreador de píxeles se establece directamente en `nullptr` en la función que se encuentra más arriba, que se denomina `CubeRenderer::Render`:

    ![El código que no inicializa el sombreador de píxeles](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   >  Si no encuentra el origen del valor NULL al examinar la pila de llamadas, se recomienda que establezca un punto de interrupción condicional en la llamada `PSSetShader` , de manera que esa ejecución del programa se interrumpa cuando el sombreador de píxeles se establezca en NULL. Después, reinicie la aplicación en el modo de depuración y use técnicas de depuración tradicionales para encontrar el origen del valor NULL.

   Para solucionar el problema, asigne el sombreador de píxeles correcto mediante el primer parámetro de la llamada de API `ID3D11DeviceContext::PSSetShader` .

   ![La C corregido&#43; &#43; código fuente](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Después de corregir el código, puede volver a compilarlo y ejecutar la aplicación de nuevo para comprobar que se resuelve el problema de representación:

   ![Ahora se muestra el objeto](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")