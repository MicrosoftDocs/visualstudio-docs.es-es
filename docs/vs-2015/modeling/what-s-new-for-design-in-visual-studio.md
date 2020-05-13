---
title: Lo&#39;nuevo para el diseño
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c68db12f8ecea523327250fec1f600639a2f267
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301288"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Novedades del diseño en Visual Studio en Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Esta versión de Visual Studio incluye las siguientes mejoras para ayudarle a comprender y diseñar mejor el código.

 **Mapas de código y gráficos de dependencias**

 En Visual Studio Enterprise, cree mapas de código para visualizar y comprender dependencias concretas en el código. Podrá navegar entre estas relaciones mediante el mapa, que aparece junto a su código. Con los mapas de código le será más fácil realizar un seguimiento de su posición en el código mientras trabaja o depura el código, por lo que leerá menos código al tiempo que mejora su comprensión del diseño del mismo.

 En la versión final (RTM), los menús contextuales de vínculos y elementos de código son mucho más fáciles de usar porque los comandos están agrupados en secciones relacionadas con la selección, edición y administración de grupos, y el cambio de diseño del contenido del grupo. Observe también que los proyectos de prueba se muestran en un estilo diferente al de otros proyectos, y que se han actualizado los iconos de elementos del mapa a una versión más apropiada.

 ![Mostrar los elementos seleccionados en un nuevo mapa de código](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Otras mejoras:

- **Se han mejorado los diagramas verticales**. En soluciones de Visual Studio de tamaño mediano y grande, ahora se puede usar un menú Arquitectura simplificado con el que se obtienen mapas de código de la solución más útiles. Los ensamblados de la solución se agrupan en las carpetas de la solución para que pueda verlos en contexto y aprovechar el esfuerzo invertido en la estructura de la solución. Inmediatamente se ven las referencias de proyecto y ensamblado y, a continuación, aparecen los tipos de vínculo. Además, los ensamblados externos a la solución se agrupan en una manera más compacta.

- **Los proyectos de prueba tienen un estilo diferente y se pueden filtrar**. Ahora resulta más fácil y rápido identificar proyectos de prueba en el mapa porque tienen un estilo diferente. Además, se pueden filtrar para permitir centrarse en el código de trabajo de la aplicación.

- **Los vínculos de dependencias externas se han simplificado**. Los vínculos de dependencia ya no representan la herencia de System.Object, System.ValueType, System.Enum y System.Delegate, lo que facilita ver las dependencias externas en el mapa del código.

- **La profundización en los vínculos de dependencia tiene en cuenta los filtros**. Obtenga un diagrama útil y claro cuando lo expanda para entender las contribuciones a un vínculo de dependencia. El diagrama aparece menos saturado y tiene en cuenta las opciones de filtración de vínculos que se seleccionen.

- **Los elementos de código se agregan a un mapa de código con su contexto**. Dado que los diagramas aparecen ahora con su contexto (hasta la carpeta de ensamblado y solución, que se puede filtrar en caso necesario), se obtienen diagramas más útiles al arrastrar y soltar elementos de código desde el Explorador de soluciones, la Vista de clases, el Explorador de objetos, o al seleccionar elementos en el Explorador de soluciones y elegir Mostrar en mapa de código.

- **Obtención más rápida de mapas de código reactivos**. Las operaciones de arrastrar y colocar producen un resultado inmediato y los vínculos entre los nodos se crean mucho más rápidamente, sin que ello afecte a las operaciones posteriores iniciadas por el usuario, como la expansión de un nodo o la solicitud de más nodos. Al crear mapas de código sin compilar la solución, todos los casos extremos y problemáticos—por ejemplo, cuando no se compilan los ensamblados— ahora se procesan.

- **Omisión de la recompilación de la solución**. Mejora el rendimiento en la creación y edición de diagramas.

- **Filtrado de grupos y nodos de elementos de código**. Ordene rápidamente los mapas: muestre u oculte elementos de código por categoría y agrupe elementos de código por carpetas de solución, ensamblados, espacios de nombres, carpetas de proyecto y tipos.

- **Filtrado de relaciones para facilitar la lectura de diagramas**. El filtrado de vínculos ahora también se aplica a los vínculos entre grupos, por lo que la ventana de filtros es menos intrusiva que en versiones anteriores.

- **Creación de diagramas desde la Vista de clases y el Explorador de objetos**. Arrastre y coloque los archivos y ensamblados en un mapa nuevo o existente desde las ventanas Vista de clases y Examinador de objetos.

  Vea [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

  **Otros cambios de diseño y modelado incluidos en esta versión:**

- **Diagramas de capas**. Actualice estos diagramas mediante la Vista de clases y el Explorador de objetos. A fin de cumplir los requisitos de diseño de software, use diagramas de capas para describir las dependencias deseadas para el software. Mantenga la coherencia del código con este diseño mediante la búsqueda de código que no cumpla estas restricciones y la validación de código futuro con esta línea base.

- **Diagramas de UML**. Ya no puede crear diagramas de clase UML y diagramas de secuencia a partir del código. Pero estos diagramas se pueden seguir creando usando nuevos elementos de UML.

- **Explorador de arquitectura**. El Explorador de arquitectura ya no se puede usar para crear diagramas. Pero se puede seguir usando el Explorador de soluciones.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a>Soporte de edición para herramientas de arquitectura y modelado

Visual Studio 2015 está disponible en varias ediciones. No todos estos proporcionan soporte para las herramientas de arquitectura y modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Enterprise**|**Profesional**|**Comunidad**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapas de código**|Sí|Solo admite la lectura y el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un nuevo gráfico dirigido a partir de una selección.|-|-|
|**Diagramas de claseUML**|Sí|-|-|-|
|**Diagramas de secuencia UML**|Sí|-|-|-|
|**Diagramas de casos de uso DE UML**|Sí|-|-|-|
|**Diagramas de actividad UML**|Sí|-|-|-|
|**Diagramas de componentes UML**|Sí|-|-|-|
|**Diagramas de capas**|Sí|-|-|-|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|-|-|
|**Clon de código**|Sí|-|-|-|