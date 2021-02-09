---
title: Los mapas de código son lentos
description: Obtenga información acerca de cómo mejorar el rendimiento del mapa de código y cómo puede minimizar el tiempo necesario para finalizar la representación.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c37f07d309551ae0f8aa0062b7847722f33671be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861691"
---
# <a name="improve-performance-for-code-maps"></a>Mejorar el rendimiento de los mapas de código

Al generar por primera vez un mapa, Visual Studio indiza todas las dependencias que encuentra. Este proceso puede tardar algún tiempo, especialmente para soluciones de gran tamaño, pero mejora el rendimiento posterior. Si el código cambia, Visual Studio solo vuelve a crear índices para el código actualizado. Para minimizar el tiempo necesario para que la asignación finalice, tenga en cuenta las siguientes sugerencias:

- Asigne solo las dependencias que le interesan.

- Antes de generar el mapa de toda una solución, reduzca el ámbito de dicha solución.

- Desactive la compilación automática de la solución seleccionando **omitir compilación** en la barra de herramientas del mapa de código.

- Desactive la opción **incluir** elementos primarios en la barra de herramientas del mapa de código para desactivar la adición automática de elementos primarios.

   ![Omitir la compilación e incluir botones de elemento primario](../modeling/media/codemapsfilterskipbuildicons.png)

- Edite directamente el mapa de código para quitar los nodos y los vínculos que no necesite. Cambiar el mapa no afecta al código subyacente. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Podría llevar más tiempo crear mapas o agregar elementos a un mapa desde **Explorador de soluciones** cuando la propiedad **Copiar en el directorio de salida** de un elemento de proyecto se establece en **copiar siempre**. Para mejorar el rendimiento, cambie esta propiedad a **Copiar si es posterior** o `PreserveNewest`. Vea [compilaciones incrementales](../msbuild/incremental-builds.md).

El mapa completado solo muestra las dependencias para el código compilado correctamente. Si se producen errores de compilación de determinados componentes, dichos errores se mostrarán en mapa. Asegúrese de que un componente se compila realmente y de que tiene dependencias antes de tomar decisiones sobre la arquitectura en función del mapa.
