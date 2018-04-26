---
title: Ordenación, filtrado y agrupación en el Explorador de esquemas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4354e58e8de2d877e726b4615bac3832bfc37d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordenar, filtrar y agrupar (Explorador de esquemas XML)

En este tema se describe las opciones que están disponibles a través de la **ordenación, filtrado y agrupación opciones** menú en la barra de herramientas del explorador de esquemas XML.

## <a name="filter-options"></a>Opciones de filtro:

 Están disponibles las opciones de filtro siguientes: De forma predeterminada, el **mostrar espacios de nombres** y **mostrar archivos de esquema** opciones están seleccionadas.

-   **Mostrar espacios de nombres**.

-   **Mostrar archivos de esquema**.

-   **Mostrar composiciones (secuencia/opción/todo)**.

## <a name="sorting-options"></a>Opciones de ordenación

 Están disponibles las opciones de ordenación siguientes: El valor predeterminado es **ordenar por tipo**. Las opciones de ordenación no se aplican a archivos ni espacios de nombres.

-   **Ordenar por tipo**.

-   **Ordenar por nombre**.

-   **Orden de documento**.

### <a name="sort-by-type"></a>Ordenar por tipo

 Cuando el **ordenar por tipo** opción está seleccionada, nodos globales se ordenan en el orden siguiente. Después, los nodos se ordenan alfabéticamente en cada grupo.

1.  nodos `import`.

2.  nodos `include`.

3.  nodos `redefine`.

4.  nodos `attribute`.

5.  nodos `attributeGroup`.

6.  nodos `complexType`.

7.  nodos `simpleType`.

8.  nodos `element`.

9. nodos `group`.

### <a name="sort-by-name"></a>Ordenar por Nombre

 Cuando el **ordenar por nombre** opción está seleccionada, nodos globales se ordenan en el orden siguiente:

1.  nodos `import` (por orden alfabético de espacios de nombres).

2.  nodos `include` (por orden alfabético de atributos `schemaLocation`).

3.  nodos `redefine` (por orden alfabético de atributos `schemaLocation`).

4.  Otros nodos globales por orden alfabético.

### <a name="document-order"></a>Orden del documento

 El **orden del documento** opción está disponible cuando la **mostrar archivos de esquema** opción está seleccionada. Cuando **orden del documento** está seleccionada, nodos globales se muestran en el orden en que aparecen en el archivo de esquema.

## <a name="persisting-sortfilter-options"></a>Opciones de ordenación y filtrado persistentes

 Las opciones de ordenación, filtrado y agrupación se guardan en el Registro para cada usuario, independientemente de la solución o de los archivos que estuvieran abiertos cuando se cambió la configuración.