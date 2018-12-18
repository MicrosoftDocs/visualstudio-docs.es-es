---
title: 'Tutorial: Objetos ausentes debido al sombreado de vértices | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3ee92eb8418fce37182b78364d08c2570f32da9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861571"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Tutorial: Objetos ausentes debido al sombreado de vértices
En este tutorial se muestra cómo usar las herramientas de Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para investigar un objeto que falta como consecuencia de un error que se ha producido durante la etapa del sombreador de vértices.  
  
 En el tutorial se muestran las tareas siguientes:  
  
-   Uso de la **Lista de eventos gráficos** para buscar los posibles orígenes del problema.  
  
-   Uso de la ventana **Etapas de canalización de gráficos** para comprobar el efecto de la llamada a la API de Direct3D `DrawIndexed` .  
  
-   Uso del **Depurador de HLSL** para examinar el sombreador de vértices.  
  
-   Uso de la **Pila de llamadas de eventos gráficos** para ayudar a encontrar el origen de una constante de HLSL incorrecta.  
  
## <a name="scenario"></a>Escenario  
 Una de las causas habituales por las que puede faltar un objeto en una aplicación 3D se produce cuando el sombreador de vértices transforma los vértices del objeto de un modo incorrecto o inesperado; por ejemplo, el objeto podría haberse escalado a un tamaño muy pequeño, o haberse transformado de forma que aparezca detrás de la cámara, en lugar de delante.  
  
 En este escenario, cuando se ejecute la aplicación para probarla, el fondo se representará de la manera prevista, pero no aparecerá uno de los objetos. Con el Diagnóstico de gráficos puede capturar el problema en un registro de gráficos para poder depurar la aplicación. El problema tiene este aspecto en la aplicación:  
  
 ![No se puede ver el objeto. ](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Investigación  
 Mediante las herramientas de Diagnóstico de gráficos, puede cargar el archivo de registro de gráficos para inspeccionar los fotogramas que se capturaron durante la prueba.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos  
  
1. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un registro de gráficos que contenga un fotograma que muestre el objeto que falta. Aparecerá una nueva pestaña de registro de gráficos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En la parte superior de esta pestaña está la salida del destino de representación del fotograma seleccionado. En la parte inferior está la **Lista de fotogramas**, que muestra cada fotograma capturado como imagen en miniatura.  
  
2. En la **Lista de fotogramas**, seleccione un fotograma que muestre que no aparece el objeto. El destino de representación se actualiza para reflejar el fotograma seleccionado. En este escenario, la pestaña de registro de gráficos tiene el aspecto siguiente:  
  
    ![Documento de registro de gráficos en Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
   Cuando haya seleccionado un fotograma en el que se muestre el problema, puede comenzar a diagnosticarlo con la **Lista de eventos gráficos**. La **Lista de eventos gráficos** contiene cada una de las llamadas a la API de Direct3D que se realizaron para representar el fotograma activo; por ejemplo, las llamadas a la API para configurar el estado del dispositivo, para crear y actualizar búferes, y para dibujar los objetos que aparecen en el fotograma. Muchos tipos de llamadas son interesantes porque, a menudo (aunque no siempre), hay un cambio correspondiente en el destino de representación cuando la aplicación funciona según lo esperado; por ejemplo, llamadas a Draw, Dispatch, Copy o Clear. Las llamadas a Draw son especialmente interesantes porque cada una de ellas representa la geometría que representaba la aplicación (las llamadas a Dispatch también pueden representar geometría).  
  
   Como sabe que (en este caso) el objeto que falta no se dibuja en el destino de representación, puede usar la **Lista de eventos gráficos** junto con la herramienta **Etapas de canalización de gráficos** para determinar la llamada a Draw que se corresponde con la geometría del objeto que falta. La ventana **Etapas de canalización de gráficos** muestra la geometría que se envió a cada llamada a draw, independientemente de su efecto en el destino de representación. A medida que se desplaza por las llamadas a Draw, las etapas de canalización se actualizan para mostrar la geometría asociada a esa llamada y la salida de destino se actualiza para mostrar el estado de destino de representación después de que se complete la llamada.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para encontrar la llamada a draw para la geometría que falta  
  
1. Abra la ventana **Lista de eventos de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Lista de eventos**.  
  
2. Abra la ventana **Etapas de canalización de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Etapas de canalización**.  
  
3. A medida que se desplaza por cada llamada a draw en la ventana **Lista de eventos gráficos** , examine la ventana **Etapas de canalización de gráficos** para ver el objeto que falta. Para facilitar esta tarea, escriba "Draw" en el cuadro de **Búsqueda** que está ubicado en la esquina superior derecha de la ventana **Lista de eventos gráficos** . Con esto se filtra la lista para que solo incluya los eventos que tienen la palabra “Draw” en sus títulos.  
  
    En la ventana **Etapas de canalización de gráficos** , la etapa **Ensamblador de entrada** muestra la geometría del objeto antes de que se transforme y la etapa **Sombreador de vértices** muestra el mismo objeto después de transformarse. En este escenario, sabrá que ha encontrado el objeto que falta cuando se muestre en la etapa **Ensamblador de entrada** y no se muestre nada en la etapa **Sombreador de vértices** .  
  
   > [!NOTE]
   >  Si otras etapas de geometría (por ejemplo, las etapas del sombreador de casco, el sombreador de dominios o el sombreador de geometría) procesan el objeto, cualquiera de ellas podría ser la causa del problema. Normalmente, el problema está relacionado con la primera etapa en la que no se muestra el resultado o se muestra de forma inesperada.  
  
4. Deténgase cuando llegue a la llamada a draw que se corresponde con el objeto que falta. En este escenario, en la ventana **Etapas de canalización de gráficos** se indica que la geometría se emitió a la GPU (como informa la miniatura del ensamblador de entrada), pero no aparece en el destino de representación porque parece que hubo algún problema durante la etapa del sombreador de vértices (como indica la miniatura del sombreador de vértices).  
  
    ![Un evento DrawIndexed y su efecto en la canalización](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
   Después de confirmar que la aplicación emitió una llamada a Draw para la geometría del objeto que falta y detectó que el problema se produce durante la etapa del sombreador de vértices, puede utilizar el depurador de HLSL para examinar el sombreador de vértices y descubrir qué ha ocurrido con la geometría del objeto. Puede utilizar el depurador de HLSL para examinar el estado de las variables de HLSL durante la ejecución, recorrer el código de HLSL y establecer puntos de interrupción que le ayuden a diagnosticar el problema.  
  
#### <a name="to-examine-the-vertex-shader"></a>Para examinar el sombreador de vértices  
  
1. Inicie la depuración de la etapa del sombreador de vértices. En la ventana **Etapas de canalización de gráficos** , en la etapa **Sombreador de vértices** , elija el botón **Iniciar depuración** .  
  
2. Como parece que la etapa **Ensamblador de entrada** proporciona datos correctos para el sombreador de vértices y que la etapa **Sombreador de vértices** no produce ningún resultado, deberá examinar la estructura de salida del sombreador de vértices, `output`. A medida que recorre paso a paso el código de HLSL, observe de forma más detallada cuando se modifique el valor de `output` .  
  
3. La primera vez que se modifique el valor de `output` , se escribe en el miembro `worldPos` .  
  
    ![El valor de "output.worldPos" parece razonable](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
    Como su valor parece razonable, continúe recorriendo el código hasta la siguiente línea que modifique el valor de `output`.  
  
4. La siguiente vez que se modifica el valor de `output` , se escribe en el miembro `pos` .  
  
    ![El valor de "output.pos" se ha establecido en cero](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
    Esta vez, el valor del miembro `pos` (todo ceros) parece sospechoso. A continuación, querrá determinar cómo es posible que el valor de `output.pos` solo incluya ceros.  
  
5. Observe que `output.pos` toma su valor de una variable denominada `temp`. En la línea anterior, verá que el valor de `temp` es el resultado de multiplicar su valor anterior por una constante denominada `projection`. Sospechará que el valor sospechoso de `temp`es el resultado de esta multiplicación. Cuando sitúe el puntero en `projection`, verá que su valor también contiene solo ceros.  
  
    ![La matriz de proyección incluye una transformación errónea](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
    En este escenario, el examen revela que el valor sospechoso de `temp`probablemente se debe a la multiplicación por `projection`, y como `projection` es una constante que está pensada para contener una matriz de proyección, sabrá que no debe contener solamente ceros.  
  
   Después de determinar que la constante de HLSL `projection`(que la aplicación pasó al sombreador de la aplicación) es el origen probable del problema, el siguiente paso es buscar la ubicación del código fuente de la aplicación donde se rellena el búfer de constantes. Puede usar la **Pila de llamadas de eventos gráficos** para encontrar esta ubicación.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Para encontrar el lugar donde se establece esta constante en el código fuente de la aplicación  
  
1. Abra la ventana **Pila de llamadas de eventos gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Pila de llamadas de eventos de gráficos**.  
  
2. Suba por la pila de llamadas hasta llegar al código fuente de la aplicación. En la ventana **Pila de llamadas de eventos de gráficos** , elija la llamada superior para ver si el búfer de constantes se llena ahí. Si no es así, siga subiendo por la pila de llamadas hasta que encuentre dónde se llena. En este escenario, detectará que el búfer de constantes se llena (mediante la API de Direct3D `UpdateSubresource` ) más arriba en la pila de llamadas, en una función que se denomina `MarbleMaze::Render`y cuyo valor procede de un objeto de búfer de constantes que se denomina `m_marbleConstantBufferData`:  
  
    ![El código que establece el búfer de constantes del objeto](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
   > [!TIP]
   >  Si está depurando la aplicación al mismo tiempo, puede establecer un punto de interrupción en esta ubicación, al que se llegará al representar el siguiente fotograma. Después, puede examinar los miembros de `m_marbleConstantBufferData` para confirmar que el valor del miembro `projection` está establecido en todo ceros cuando se llena el búfer de constantes.  
  
   Después de encontrar la ubicación donde se llena el búfer de constantes y detectar que sus valores proceden de la variable `m_marbleConstantBufferData`, el siguiente paso es averiguar dónde el `m_marbleConstantBufferData.projection` miembro está establecido en todo ceros. Puede usar **Buscar todas las referencias** para buscar rápidamente código que cambie el valor de `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Para encontrar el lugar donde se establece el miembro de proyección en el código fuente de la aplicación  
  
1. Busque referencias para `m_marbleConstantBufferData.projection`. Abra el menú contextual de la variable `m_marbleConstantBufferData`y luego elija **Buscar todas las referencias**.  
  
2. Para navegar a la ubicación de la línea del código fuente de la aplicación en la que se modifica el valor del miembro `projection` , seleccione esa línea en la ventana **Resultados de la búsqueda de símbolos** . Como el primer resultado que modifica el miembro de proyección no puede ser la causa del problema, es posible que deba examinar varias áreas del código fuente de la aplicación.  
  
   Después de encontrar la ubicación donde se establece `m_marbleConstantBufferData.projection` , puede examinar el código fuente de alrededor para determinar el origen del valor incorrecto. En este escenario, detectará que el valor de `m_marbleConstantBufferData.projection` se establece en una variable local denominada `projection` antes de que se haya inicializado en un valor que proporciona el código `m_camera->GetProjection(&projection);` en la línea siguiente.  
  
   ![La proyección de marble se establece antes de la inicialización](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
   Para corregir el problema, mueva la línea de código que establece el valor de `m_marbleConstantBufferData.projection` después de la línea que inicializa el valor de la variable local `projection`.  
  
   ![La C corregido&#43; &#43; código fuente](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
   Después de corregir el código, puede volver a compilarlo y ejecutar la aplicación de nuevo para comprobar que se ha resuelto el problema de representación:  
  
   ![Muestra el objeto ahora. ](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")