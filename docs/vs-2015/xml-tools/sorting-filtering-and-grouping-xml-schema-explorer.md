---
title: Ordenar, filtrar y agrupar (explorador de esquemas XML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656147"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordenar, filtrar y agrupar (Explorador de esquemas XML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen las opciones que están disponibles a través del menú de **Opciones de ordenación, filtrado y agrupación** de la barra de herramientas del Explorador de esquemas XML.

## <a name="filter-options"></a>Opciones de filtro:
 Están disponibles las opciones de filtro siguientes: De forma predeterminada, las opciones **Mostrar espacios de nombres** y **Mostrar archivos de esquema** están seleccionadas.

- **Mostrar espacios de nombres**.

- **Mostrar archivos de esquema**.

- **Mostrar compositores (en secuencia/seleccionados/todos)** .

## <a name="sorting-options"></a>Opciones de ordenación
 Están disponibles las opciones de ordenación siguientes: El valor predeterminado es **Ordenar por tipo**. Las opciones de ordenación no se aplican a archivos ni espacios de nombres.

- **Ordenar por tipo**.

- **Ordenar por nombre**.

- **Ordenar por orden de documento**.

### <a name="sort-by-type"></a>Ordenar por tipo
 Cuando se selecciona la opción **Ordenar por tipo**, los nodos globales se ordenan de la forma siguiente. Después, los nodos se ordenan alfabéticamente en cada grupo.

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
 Cuando se selecciona la opción **Ordenar por nombre**, los nodos globales se ordenan de la forma siguiente:

1. nodos `import` (por orden alfabético de espacios de nombres).

2. nodos `include` (por orden alfabético de atributos `schemaLocation`).

3. nodos `redefine` (por orden alfabético de atributos `schemaLocation`).

4. Otros nodos globales por orden alfabético.

### <a name="document-order"></a>Orden del documento
 La opción **Ordenar por orden de documento** está disponible cuando se selecciona la opción **Mostrar archivos de esquema**. Cuando se selecciona **Ordenar por orden de documento**, los nodos globales se muestran en el orden en que aparecen en el archivo de esquema.

## <a name="persisting-sortfilter-options"></a>Opciones de ordenación y filtrado persistentes
 Las opciones de ordenación, filtrado y agrupación se guardan en el Registro para cada usuario, independientemente de la solución o de los archivos que estuvieran abiertos cuando se cambió la configuración.
