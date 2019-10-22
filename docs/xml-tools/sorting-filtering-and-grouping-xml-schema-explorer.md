---
title: Ordenar, filtrar y agrupar en el explorador de esquemas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf9226f3b491a39c7ef5936667cabd789c6a457
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604579"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordenar, filtrar y agrupar (explorador de esquemas XML)

En este tema se describen las opciones que están disponibles a través del menú **Opciones de ordenación, filtrado y agrupación** en la barra de herramientas del **Explorador de esquemas XML** .

## <a name="filter-options"></a>Opciones de filtro

Están disponibles las opciones de filtro siguientes: De forma predeterminada, las opciones **Mostrar espacios de nombres** y **Mostrar archivos de esquema** están seleccionadas.

- **Mostrar espacios de nombres**.

- **Mostrar archivos de esquema**.

- **Mostrar compositores (secuencia/opción/todo)** .

## <a name="sorting-options"></a>Opciones de ordenación

Están disponibles las opciones de ordenación siguientes: El valor predeterminado es **ordenar por tipo**. Las opciones de **ordenar por** no se aplican a los archivos y espacios de nombres.

- **Ordenar por tipo**.

- **Ordenar por nombre**.

- **Orden del documento**.

### <a name="sort-by-type"></a>Ordenar por tipo

Cuando se selecciona la opción **ordenar por tipo** , los nodos globales se ordenan en el orden siguiente. Después, los nodos se ordenan alfabéticamente en cada grupo.

1. nodos `import`.

2. nodos `include`.

3. nodos `redefine`.

4. nodos `attribute`.

5. nodos `attributeGroup`.

6. nodos `complexType`.

7. nodos `simpleType`.

8. nodos `element`.

9. nodos `group`.

### <a name="sort-by-name"></a>Ordenar por Nombre

Cuando se selecciona la opción **ordenar por nombre** , los nodos globales se ordenan en el siguiente orden:

1. nodos `import` (por orden alfabético de espacios de nombres).

2. nodos `include` (por orden alfabético de atributos `schemaLocation`).

3. nodos `redefine` (por orden alfabético de atributos `schemaLocation`).

4. Otros nodos globales por orden alfabético.

### <a name="document-order"></a>Orden del documento

La opción **orden del documento** está disponible cuando se selecciona la opción **Mostrar archivos de esquema** . Cuando se selecciona el **orden del documento** , los nodos globales se muestran en el orden en que aparecen en el archivo de esquema.

## <a name="persisting-sortfilter-options"></a>Opciones de ordenación y filtrado persistentes

Las opciones de ordenación, filtrado y agrupación se guardan en el Registro para cada usuario, independientemente de la solución o de los archivos que estuvieran abiertos cuando se cambió la configuración.