---
title: Los mapas de código son lentos
description: Obtenga información sobre cómo mejorar el rendimiento del mapa de código y cómo puede minimizar el tiempo necesario para finalizar la representación.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5a279a04b1bd76933df335bc0b2527ab4b2418f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389649"
---
# <a name="improve-performance-for-code-maps"></a>Mejora del rendimiento de los mapas de código

Al generar por primera vez un mapa, Visual Studio indiza todas las dependencias que encuentra. Este proceso puede tardar algún tiempo, especialmente para soluciones de gran tamaño, pero mejora el rendimiento posterior. Si el código cambia, Visual Studio solo vuelve a crear índices para el código actualizado. Para minimizar el tiempo que se necesita para que el mapa termine de representarse, tenga en cuenta las sugerencias siguientes:

- Asigne solo las dependencias que le interesan.

- Antes de generar el mapa de toda una solución, reduzca el ámbito de dicha solución.

- Desactive la compilación automática de la solución seleccionando **Omitir compilación en** la barra de herramientas del mapa de código.

- Desactive la adición automática de elementos primarios seleccionando Incluir elementos **primarios** en la barra de herramientas del mapa de código.

   ![Omitir la compilación e incluir botones de elemento primario](../modeling/media/codemapsfilterskipbuildicons.png)

- Edite directamente el mapa de código para quitar los nodos y los vínculos que no necesite. Cambiar el mapa no afecta al código subyacente. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Puede tardar más tiempo en crear asignaciones o agregar elementos a un mapa desde **Explorador de soluciones** cuando la propiedad **Copiar** en directorio de salida de un elemento de proyecto está establecida en **Copiar siempre**. Para mejorar el rendimiento, cambie esta propiedad a **Copiar si es posterior** o `PreserveNewest`. Vea [Compilaciones incrementales.](../msbuild/incremental-builds.md)

El mapa completado muestra las dependencias solo para el código creado correctamente. Si se producen errores de compilación de determinados componentes, dichos errores se mostrarán en mapa. Asegúrese de que un componente se compila realmente y de que tiene dependencias antes de tomar decisiones sobre la arquitectura en función del mapa.
