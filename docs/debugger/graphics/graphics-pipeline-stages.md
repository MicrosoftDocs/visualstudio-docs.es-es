---
title: Etapas de canalización de gráficos | Microsoft Docs
description: Para solucionar los problemas de representación, vea cómo se transforma una llamada a Draw en cada fase de la canalización de gráficos de Direct3D.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61cc2737fbe6bdbcb331da4e1d27a77d356735aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888659"
---
# <a name="graphics-pipeline-stages"></a>Etapas de canalización de gráficos
La ventana Etapas de canalización de gráficos ayuda a entender cómo cada etapa de la canalización de gráficos Direct3D transforma una llamada a draw individual.

 Esta es la ventana Etapas de canalización:

 ![Un objeto 3D recorre las etapas de canalización.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Descripción de la ventana Etapas de canalización de gráficos
 La ventana Etapas de canalización visualiza el resultado de cada etapa de la canalización de gráficos por separado, para cada llamada a draw. Normalmente, los resultados de las etapas en medio de la canalización están ocultos, lo que dificulta saber en qué momento comenzó un problema de representación. Al visualizar cada etapa por separado, la ventana Etapas de canalización hace que sea más fácil ver dónde comienza el problema. Por ejemplo, puede ver fácilmente si la etapa del sombreador de vértices hace inesperadamente que un objeto se dibuje fuera de la pantalla.

 Después de identificar la etapa en la que se produce el problema, puede usar las otras herramientas del Analizador de gráficos para examinar cómo se interpretaron o se transformaron los datos. Los problemas de representación que se producen en las etapas de canalización suelen estar relacionados con errores en los descriptores de formato de los vértices, en los programas de sombreado o en la configuración de estado.

### <a name="links-to-related-graphics-objects"></a>Vínculos a objetos gráficos relacionados
 En ocasiones es necesario más contexto para determinar por qué una llamada a draw interactúa de forma particular con la canalización de gráficos. Para facilitar esta búsqueda de contexto adicional, la ventana Etapas de canalización de gráficos vincula a uno o varios objetos que proporcionan contexto adicional relacionado con lo que sucede en la canalización de gráficos.

- En Direct3D 12, este objeto suele ser una lista de comandos.

- En Direct3D 11, este objeto suele ser un contexto de dispositivo de gráficos.

  Estos vínculos son parte de la firma de evento de gráficos actual que se encuentra en la esquina superior izquierda de la ventana Etapas de canalización de gráficos. Siga cualquiera de estos vínculos para examinar los detalles adicionales del objeto.

### <a name="viewing-and-debugging-shader-code"></a>Visualización y depuración de código de sombreado
 Puede examinar y depurar código de sombreadores de vértices, casco, dominios, geometría y píxeles usando los controles de la parte inferior de sus respectivas etapas en la ventana Etapas de canalización.

#### <a name="to-view-a-shaders-source-code"></a>Para ver el código fuente de un sombreador

- En la ventana **Etapas de canalización de gráficos**, busque la etapa del sombreador que se corresponde con el sombreador que desea examinar. A continuación, debajo de la imagen de vista previa, siga el vínculo del título de la etapa del sombreador. Por ejemplo, siga el vínculo **Sombreador de vértices obj:30** para ver el código fuente del sombreador de vértices.

    > [!TIP]
    > El número de objeto, **obj:30**, identifica este sombreador en toda la interfaz del Analizador de gráficos, tal como se muestra en la ventana del historial de píxeles y la tabla de objetos.

#### <a name="to-debug-a-shader"></a>Para depurar un sombreador

- En la ventana **Etapas de canalización de gráficos**, busque la etapa del sombreador que se corresponde con el sombreador que desea depurar. A continuación, debajo de la imagen de vista previa, elija **Iniciar depuración**. Este punto de entrada en el depurador HLSL tiene como valor predeterminado la primera invocación del sombreador para la etapa correspondiente, es decir, el primer píxel, vértice o primitiva que procesa el sombreador durante esta llamada a draw. Es posible acceder a las invocaciones de este sombreador para un vértice o píxel concreto a través del **Historial de píxeles de gráfico**.

### <a name="the-pipeline-stages"></a>Etapas de canalización
 La ventana Etapas de canalización muestra solamente las etapas de canalización que estaban activas durante la llamada a draw. Cada etapa de canalización de gráficos transforma la entrada de la etapa anterior y pasa el resultado a la etapa siguiente. La primera etapa (el ensamblador de entrada) toma como entrada los datos del índice y del vértice de la aplicación; la última etapa (la fusión de salida) combina los píxeles recién representados con el contenido actual del búfer de fotogramas o destino de representación como salida para generar la imagen final que se ve en pantalla.

> [!NOTE]
> En la ventana **Etapas de canalización de gráficos**, no se admiten los sombreadores de cálculo.

 **Ensamblador de entrada** El ensamblador de entrada lee los datos del índice y del vértice que especifica la aplicación y los ensambla para el hardware de gráficos.

 En la ventana Etapas de canalización, se muestra la salida del ensamblador de entrada como un modelo de tramas de alambres. Para examinar en detalle el resultado, seleccione **Ensamblador de entrada** en la ventana **Etapas de canalización de gráficos** para ver los vértices ensamblados en 3D mediante el Editor de modelos.

> [!NOTE]
> Si la semántica `POSITION` no aparece en el resultado del ensamblador de entrada, no se mostrará nada en la fase **Ensamblador de entrada**.

 **Sombreador de vértices** La etapa del sombreador de vértices procesa los vértices, normalmente realizando operaciones como transformaciones, máscaras e iluminación. Los sombreadores de vértices producen el mismo número de vértices que toman como entrada.

 En la ventana Etapas de canalización, la salida del sombreador de vértices se muestra como una imagen de tramas de alambres. Para examinar en detalle el resultado, seleccione **Sombreador de vértices** en la ventana **Etapas de canalización de gráficos** para ver los vértices procesados en el Editor de imágenes.

> [!NOTE]
> Si las semánticas `POSITION` o `SV_POSITION` no aparecen en la salida del sombreador de vértices, no se mostrará nada en la fase **Sombreador de vértices**.

 **Sombreador de casco** (solo Direct3D 11 y Direct3D 12) La etapa del sombreador de casco procesa los puntos de control que definen una superficie de orden inferior, como una línea, un triángulo o un cuadrángulo. Como resultado produce una revisión de geometría de orden superior y constantes de revisión que se pasan a la etapa de teselación de funciones fijas.

 La etapa del sombreador de casco no se visualiza en la ventana Etapas de canalización.

 **Etapa del teselador** (solo Direct3D 11 y Direct3D 12) La etapa del teselador es una unidad de hardware de función fija (no programable) que preprocesa el dominio representado por la salida del sombreador de casco. Como salida, crean un patrón de muestreo del dominio y un conjunto de primitivas menores (puntos, líneas y triángulos) que conectan estos ejemplos.

 La etapa del teselador no se visualiza en la ventana Etapas de canalización.

 **Sombreador de dominios** (solo Direct3D 11 y Direct3D 12) La etapa del sombreador de dominios procesa revisiones de geometría de orden superior del sombreador de casco, junto con factores de teselación de la etapa de teselación. Los factores de teselación pueden incluir factores de entrada de teselador, así como factores de salida. Como salida, calcula la posición del vértice de un punto de la revisión de salida según los factores del teselador.

 La etapa del sombreador de dominios no se visualiza en la ventana Etapas de canalización.

 **Sombreador de geometría** La etapa del sombreador de geometría procesa primitivas completas (puntos, líneas o triángulos) junto con datos de vértice opcionales para primitivas adyacentes al borde. A diferencia de los sombreadores de vértices, los sombreadores de geometría pueden producir más o menos primitivas de las que toman como entrada.

 En la ventana Etapas de canalización, la salida del sombreador de geometría se visualiza como una imagen de tramas de alambres. Para examinar en detalle el resultado, seleccione **Sombreador de geometría** en la ventana **Etapas de canalización de gráficos** para ver las primitivas procesadas en el Editor de imágenes.

 **Etapa de salida de flujo** La etapa de salida de flujo puede interceptar primitivas transformadas antes de la rasterización y escribirlas en la memoria; a partir de ahí, los datos pueden volver a circular como entrada para etapas anteriores de la canalización de gráficos o ser leídas por la CPU.

 La etapa de salida de flujo no se visualiza en la ventana Etapas de canalización.

 **Etapa del rasterizador** La etapa del rasterizador es una unidad de hardware de función fija (no programable) que convierte las primitivas de vector (puntos, líneas y triángulos) en una imagen de trama realizando una conversión de línea de barrido. Durante la rasterización, los vértices se transforman en el espacio de recorte homogéneo y se recortan. Como salida, se asignan los sombreadores de píxeles y se interpolan los atributos por vértice en la primitiva, y se preparan para el sombreador de píxeles.

 La etapa del rasterizador no se visualiza en la ventana Etapas de canalización.

 **Sombreador de píxeles** La etapa del sombreador de píxeles procesa las primitivas rasterizadas junto con los datos de vértice interpolados para generar valores por píxel, como el color y la profundidad.

 En la ventana Etapas de canalización, la salida del sombreador de píxeles se visualiza como una imagen de trama a todo color. Para examinar en detalle el resultado, seleccione **Sombreador de píxeles** en la ventana **Etapas de canalización de gráficos** para ver las primitivas procesadas en el Editor de imágenes.

 **Fusión de salida** La etapa de fusión de salida combina el efecto de los píxeles recién representados junto con el contenido de los búferes correspondientes (color, profundidad y galería de símbolos) para generar nuevos valores en estos búferes.

 En la ventana Etapas de canalización, la salida de la fusión de salida se muestra como una imagen de trama a todo color. Para examinar en detalle los resultados, seleccione **Fusión de salida** en la ventana **Etapas de canalización de gráficos** para ver el búfer de fotogramas combinado.

### <a name="vertex-and-geometry-shader-preview"></a>Vista previa del sombreador de vértices y geometría
 Al seleccionar la fase de sombreador de vértices o de geometría en la ventana **Fases de canalización**, puede ver las entradas y salidas del sombreador en el panel siguiente.  Aquí encontrará detalles sobre la lista de vértices proporcionada a los sombreadores después de que se hayan ensamblado en la etapa del ensamblador de entrada.

 ![El visor de búfer de entrada de la fase de sombreador de vértices](media/gfx_diag_vertex_shader_inbuffers.png)

 Para ver el resultado de la etapa del sombreador de vértices, seleccione la miniatura de la etapa del sombreador de vértices para ver una trama de alambres rasterizada a tamaño completo de la malla después de que la transforme el sombreador de vértices.

 ![La vista previa de resultados de la fase de sombreador de vértices](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Vea también
- [Tutorial: Objetos ausentes debido al sombreado de vértices](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Tutorial: Depuración de errores de representación debidos al sombreado](walkthrough-debugging-rendering-errors-due-to-shading.md)