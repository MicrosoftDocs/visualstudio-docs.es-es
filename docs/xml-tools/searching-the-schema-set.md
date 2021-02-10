---
title: 'Explorador de esquemas XML: búsqueda en el conjunto de esquemas'
description: Aprenda a realizar una búsqueda de palabra clave y una búsqueda específica del esquema del conjunto de esquemas en el Explorador de esquemas XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f924e46fa4d32fbea9071bd8a19268f2ee1652e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891883"
---
# <a name="search-the-schema-set"></a>Búsqueda en el conjunto de esquemas

El **Explorador de esquemas XML** permite buscar en el conjunto de esquemas de las maneras siguientes:

- Búsqueda de palabra clave.

- Búsqueda específica del esquema.

## <a name="keyword-search"></a>Búsqueda de palabra clave

Las búsquedas de palabra clave se realizan escribiendo una subcadena en el cuadro de texto **Buscar en el conjunto de esquemas** de la barra de herramientas del **Explorador de esquemas XML**.

![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

El **Explorador de esquemas XML** busca en el conjunto de esquemas los atributos siguientes:

- Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Puede encontrar elementos, atributos, tipos, etc. por nombre.

- Los atributos `schemaLocation` de las instrucciones include.

- Los atributos `namespace` de las instrucciones import.

## <a name="schema-specific-search"></a>Búsqueda específica del esquema

El **Explorador de esquemas XML** también incluye buscadores integrados a los que se tiene acceso mediante el menú contextual (con el botón derecho) del **Explorador de esquemas XML**. Para más información sobre los menús contextuales disponibles, consulte [Menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema en la vista Inicio. Para más información, consulte la sección "Detalles del conjunto de esquemas" en el tema [vista Inicio](../xml-tools/start-view.md).

## <a name="display-and-navigate-search-results"></a>Visualización y navegación por los resultados de la búsqueda

Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de la búsqueda también se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical. Puede navegar por los resultados de búsqueda con los botones **Ir al resultado de búsqueda siguiente** e **Ir al resultado de búsqueda anterior** del panel de resumen de resultados de la barra de herramientas del **Explorador de esquemas XML**, mediante las teclas **F3** y **Mayús**+**F3** o con un clic en las marcas de graduación de la barra de desplazamiento.

Puede agregar los resultados de la búsqueda al área de trabajo; para ello, haga clic en el botón **Agregar nodos resaltados al área de trabajo** en el panel de resumen de resultados.

![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Eliminación de los resultados de la búsqueda

Para borrar los resultados de la búsqueda, haga clic en el botón **x** del panel de resumen de resultados de la barra de herramientas de búsqueda del **Explorador de esquemas XML**.

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
