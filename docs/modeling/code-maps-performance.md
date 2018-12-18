---
title: Mapas de código son lentos
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267704"
---
# <a name="improve-performance-for-code-maps"></a>Mejorar el rendimiento de mapas de código

Al generar por primera vez un mapa, Visual Studio indiza todas las dependencias que encuentra. Este proceso puede tardar algún tiempo, especialmente para soluciones de gran tamaño, pero mejora el rendimiento de una versión posterior. Si el código cambia, Visual Studio solo vuelve a crear índices para el código actualizado. Para minimizar el tiempo necesario para que la asignación de finalizar la representación, tenga en cuenta las siguientes sugerencias:

- [Asigne solo las dependencias que le interesen.](#create-a-code-map-to-see-specific-dependencies)

- Antes de generar el mapa de toda una solución, reduzca el ámbito de dicha solución.

- Desactive la compilación automática de la solución seleccionando **Skip Build** en la barra de herramientas del mapa de código.

- Desactive la inclusión automática de elementos primarios seleccionando **incluir elementos primarios** en la barra de herramientas del mapa de código.

   ![Omitir la compilación e incluir botones de elemento primario](../modeling/media/codemapsfilterskipbuildicons.png)

- Edite directamente el mapa de código para quitar los nodos y los vínculos que no necesite. Cambiar el mapa no afecta al código subyacente. Vea [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Puede tardar más tiempo crear mapas o agregar elementos a un mapa de **el Explorador de soluciones** cuando un elemento de proyecto **copiar en el directorio de salida** propiedad está establecida en **copiar siempre**. Para mejorar el rendimiento, cambie esta propiedad a **Copiar si es posterior** o `PreserveNewest`. Vea [las generaciones incrementales](../msbuild/incremental-builds.md).

El mapa completo muestra las dependencias únicamente del código generado correctamente. Si se producen errores de compilación de determinados componentes, dichos errores se mostrarán en mapa. Asegúrese de que un componente se compila realmente y de que tiene dependencias antes de tomar decisiones sobre la arquitectura en función del mapa.