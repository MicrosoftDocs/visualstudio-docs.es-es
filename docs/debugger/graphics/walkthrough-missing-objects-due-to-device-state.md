---
title: 'Tutorial: Objetos ausentes debido al estado del dispositivo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc1fd83b468318f2c8dfe010548b9e94eb2d0755
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Tutorial: Objetos ausentes debido al estado del dispositivo
En este tutorial se muestra cómo usar el Diagnóstico de gráficos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para investigar un objeto que falta como consecuencia de un estado de dispositivo mal configurado.  
  
 En este tutorial se muestra:  
  
-   El uso de la **Lista de eventos gráficos** para buscar los posibles orígenes del problema.  
  
-   El uso de la ventana **Etapas de canalización de gráficos** para comprobar el efecto de la llamada a la API de Direct3D `DrawIndexed` .  
  
-   El uso de la ventana **Historial de píxeles de gráfico** para localizar el problema de forma más concreta.  
  
-   Cómo inspeccionar el estado del dispositivo en busca de posibles problemas o errores de configuración.  
  
## <a name="scenario"></a>Escenario  
 Uno de los motivos por los que los objetos podrían no aparecer donde se espera en una aplicación 3D es una configuración incorrecta del dispositivo gráfico que provoque que los objetos se excluyan de la representación; por ejemplo, si el orden de generación hace que se llame por error a los triángulos o si la función de prueba de profundidad provoca que se rechacen todos los píxeles del objeto.  
  
 En el escenario descrito en este tutorial, ha llegado al primer hito en el desarrollo de la aplicación 3D y todo está listo para probarla por primera vez. Sin embargo, al ejecutar la aplicación, solo se representa la interfaz de usuario en la pantalla. Mediante el Diagnóstico de gráficos, puede capturar el problema en un archivo de registro de gráficos para poder depurar la aplicación. El problema tiene este aspecto en la aplicación:  
  
 ![La aplicación antes de corregir el problema](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")  
  
 Para obtener información sobre cómo capturar los problemas de gráficos en un registro de gráficos, vea [Capturing Graphics Information](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Investigación  
 Mediante las herramientas de Diagnóstico de gráficos, puede cargar el archivo de registro de gráficos para inspeccionar los fotogramas que se capturaron durante la prueba.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos  
  
1.  En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un registro de gráficos que contenga un fotograma que muestre el modelo que falta. Aparece una nueva pestaña de Diagnóstico de gráficos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En la parte superior de esta pestaña está la salida del destino de representación del fotograma seleccionado. En la parte inferior está la **Lista de fotogramas**, que muestra cada fotograma capturado como imagen en miniatura.  
  
2.  En la **Lista de fotogramas**, seleccione un fotograma que muestre que no aparece el modelo. El destino de representación se actualiza para reflejar el fotograma seleccionado. En este escenario, la pestaña de registro de gráficos tiene el aspecto siguiente:  
  
     ![La lista de marcos y vista previa del búfer de fotogramas de fichas de .vsglog](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")  
  
 Después de seleccionar un fotograma en el que se muestre el problema, puede usar la **Lista de eventos gráficos** para diagnosticarlo. La **Lista de eventos gráficos** contiene cada una de las llamadas a la API de Direct3D que se realizaron para representar el fotograma activo; por ejemplo, las llamadas a la API para configurar el estado del dispositivo, para crear y actualizar búferes, y para dibujar los objetos que aparecen en el fotograma. Muchos tipos de llamadas son interesantes porque, a menudo (aunque no siempre), hay un cambio correspondiente en el destino de representación cuando la aplicación funciona según lo esperado; por ejemplo, llamadas a Draw, Dispatch, Copy o Clear. Las llamadas a Draw son especialmente interesantes porque cada una de ellas representa la geometría que representaba la aplicación (las llamadas a Dispatch también pueden representar geometría).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Para asegurarse de que se realizan las llamadas a Draw  
  
1.  Abra la ventana **Lista de eventos de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Lista de eventos**.  
  
2.  Inspeccione la **Lista de eventos gráficos** y busque las llamadas a Draw. Para facilitar esta tarea, escriba "Draw" en el cuadro de **Búsqueda** que está ubicado en la esquina superior derecha de la ventana **Lista de eventos gráficos** . Con esto se filtra la lista para que solo incluya los eventos que tienen la palabra “Draw” en sus títulos. En este escenario, se descubre que se realizaron varias llamadas a Draw:  
  
     ![Lista de eventos de gráficos que muestra los eventos capturados](media/vsg_walkthru1_.png "vsg_walkthru1_")  
  
 Después de confirmar que se están realizando llamadas a Draw, puede determinar cuál corresponde a la geometría que falta. Como sabe que la geometría que falta no se dibuja en el destino de representación (en este caso), puede usar la ventana **Etapas de canalización de gráficos** para determinar la llamada a Draw que corresponde a la geometría que falta. La ventana **Etapas de canalización de gráficos** muestra la geometría que se envió a cada llamada a draw, independientemente de su efecto en el destino de representación. A medida que se desplaza por las llamadas a Draw, las etapas de canalización se actualizan para mostrar la geometría asociada a esa llamada y la salida de destino se actualiza para mostrar el estado de destino de representación después de que se complete la llamada.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Para encontrar la llamada a draw para la geometría que falta  
  
1.  Abra la ventana **Etapas de canalización de gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Etapas de canalización**.  
  
2.  Desplácese por cada llamada a Draw mientras visualiza la ventana **Etapas de canalización de gráficos** del modelo que falta. La etapa **Ensamblador de entrada** muestra los datos del modelo sin procesar. La etapa **Sombreador de vértices** muestra los datos del modelo transformado. La etapa **Sombreador de píxeles** muestra la salida del sombreador de píxeles. La etapa **Fusión de salida** muestra el destino de representación fusionada de esta llamada a Draw y todas las anteriores.  
  
3.  Deténgase cuando llegue a la llamada a Draw que corresponde al modelo que falta. En este escenario, la ventana **Etapas de canalización de gráficos** indica que la geometría se representó, pero no aparece en el destino de representación:  
  
     ![Visor de canalización que muestra el objeto que falta](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")  
  
 Después de confirmar que la aplicación representó la geometría que falta y de buscar la llamada a Draw correspondiente, puede seleccionar una parte de la salida de destino de representación que debería mostrar la geometría que falta y luego usar la ventana **Historial de píxeles de gráfico** para averiguar por qué se han excluido los píxeles. El historial de píxeles contiene una lista de cada llamada a Draw que puede haber tenido un efecto en un píxel determinado. Cada llamada a Draw de la ventana **Historial de píxeles de gráfico** se identifica mediante un número que también se muestra también en la ventana **Lista de eventos gráficos** . Esto le ayudará a confirmar que el píxel debería mostrar la geometría que falta y a averiguar por qué se excluyó el píxel.  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Para determinar por qué se excluyó el píxel  
  
1.  Abra la ventana del **Historial de píxeles de gráfico** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Historial de píxeles**.  
  
2.  Según la miniatura del **Sombreador de píxeles** , seleccione un píxel de la salida del búfer de fotogramas que debería contener una parte de la geometría que falta. En este escenario, la salida del sombreador de píxeles debería cubrir la mayor parte del destino de representación; después de seleccionar un píxel, la ventana **Historial de píxeles de gráfico** tiene el siguiente aspecto:  
  
     ![Ventana de historial de píxeles que muestra relacionadas llamadas a draw](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")  
  
3.  Confirme que el píxel del destino de representación seleccionado contiene una parte de la geometría, comparando el número de la llamada a Draw que está inspeccionando (en la ventana **Lista de eventos gráficos** ) con una de las llamadas a Draw de la ventana **Historial de píxeles de gráfico** . Si ninguna de las llamadas de la ventana **Historial de píxeles de gráfico** coincide con la llamada a Draw que está inspeccionando, repita estos pasos (excepto el paso 1) hasta que encuentre una coincidencia. En este escenario, la llamada a Draw coincidente tiene el siguiente aspecto:  
  
     ![Ventana de historial de píxeles que muestra información sobre el fragmento](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")  
  
4.  Cuando encuentre una coincidencia, expanda la llamada a Draw coincidente en la ventana **Historial de píxeles de gráfico** y confirme que se excluyó el píxel. Cada llamada a Draw de la ventana **Historial de píxeles de gráfico** corresponde a una o varias primitivas geométricas (puntos, líneas o triángulos) que se intersecan con ese píxel como resultado de la geometría del objeto correspondiente. Cada una de esas intersecciones podría contribuir al color final del píxel. Una primitiva que se excluye porque no ha superado la prueba de profundidad se representa con un icono que muestra la letra Z sobre una flecha que apunta en sentido descendiente hacia la derecha.  
  
5.  Expanda una primitiva excluida para examinar más detenidamente el estado que ha provocado que se excluya. En el grupo **Fusión de salida** , sitúe el puntero sobre **Resultado**. Una información sobre herramientas indica por qué se excluyó la primitiva. En este escenario, el examen revela que la primitiva se excluyó porque no pasó la prueba de profundidad y, por lo tanto, no afectó al color final del píxel.  
  
 Después de determinar que la geometría no aparece porque sus primitivas no han superado la prueba de profundidad, quizás sospeche que este problema esté relacionado con un estado de dispositivo mal configurado. Es posible examinar el estado del dispositivo y datos de objetos de Direct3D mediante la **Tabla de objetos gráficos**.  
  
#### <a name="to-examine-device-state"></a>Para examinar el estado del dispositivo  
  
1.  Abra la ventana **Tabla de objetos gráficos** . En la barra de herramientas **Diagnóstico de gráficos** , elija **Tabla de objetos**.  
  
2.  Busque el objeto **Dispositivo D3D10** en la **Tabla de objetos gráficos**y luego abra el objeto **Dispositivo D3D10** . Se abrirá una nueva pestaña **dispositivo d3d10** en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para facilitar esta tarea, puede ordenar la **Tabla de objetos gráficos** por **Tipo**:  
  
     ![Tabla de objetos gráficos y estado del dispositivo relacionado](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")  
  
3.  Examine el estado del dispositivo que se muestra en la pestaña **dispositivo d3d10** para detectar posibles problemas. Como la geometría no aparece porque sus primitivas no han superado la prueba de profundidad, puede centrarse en el estado del dispositivo, como la galería de símbolos de profundidad, que afecta a la prueba de profundidad. En este escenario, la **galería de símbolos de profundidad** (en **Estado de fusión de salida**) contiene un valor poco habitual para el miembro **función de profundidad** , `D3D10_COMPARISON_GREATER`:  
  
     ![Ventana de dispositivo D3D10 que muestra información de la Galería de símbolos de profundidad](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")  
  
 Después de determinar que la causa del problema de representación podría ser una función de profundidad mal configurada, puede usar esta información junto con su conocimiento del código para buscar el lugar en que se estableció incorrectamente la función de profundidad y, a continuación, corregirlo. Si no está familiarizado con el código, podría buscar el problema siguiendo las pistas que ha recopilado mientras depuraba; por ejemplo, basándose en la **Descripción de la galería de símbolos de profundidad** de este escenario, puede buscar en el código palabras como "depth" o "GREATER". Después de corregir el código, vuelva a compilarlo y ejecute de nuevo la aplicación para comprobar que se ha resuelto el problema de representación:  
  
 ![Aplicación después de corregirse el problema](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")