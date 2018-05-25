---
title: Explorador de esquemas XML - buscar el conjunto de esquemas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c110344499281243628d633d005506af5cd801d0
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
# <a name="search-the-schema-set"></a>Buscar el conjunto de esquemas

El **Explorador de esquemas XML** permite buscar el esquema especificado en las siguientes maneras:

-   Búsqueda de palabra clave.

-   Búsqueda específica del esquema.

## <a name="keyword-search"></a>Búsqueda de palabra clave

 Realizar búsquedas de palabra clave mediante la especificación de una subcadena en la **conjunto de esquemas de búsqueda** cuadro de texto de la **Explorador de esquemas XML** barra de herramientas.

 ![Búsqueda de palabra clave de explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 El **Explorador de esquemas XML** busca el esquema especificado para los siguientes atributos:

-   Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Puede buscar elementos, atributos, tipos y así sucesivamente, por su nombre.

-   Los atributos `schemaLocation` de las instrucciones include.

-   Los atributos `namespace` de las instrucciones import.

## <a name="schema-specific-search"></a>Búsqueda específica del esquema

 El **Explorador de esquemas XML** también incluye buscadores integrados a los que se pueden tener acceso mediante el menú contextual de la **Explorador de esquemas XML**. Para obtener más información acerca de los menús contextuales disponibles, consulte [menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema de la vista inicio; Para obtener más información, vea la sección "Detalles del conjunto de esquemas" en la [vista inicio](../xml-tools/start-view.md) tema.

## <a name="display-and-navigate-search-results"></a>Mostrar y navegar por los resultados de la búsqueda

 Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de búsqueda también se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical. Puede navegar por los resultados de búsqueda mediante el uso de la **ir al resultado de búsqueda siguiente** y **ir al resultado de búsqueda anterior** botones en el panel de resultados de resumen de la **Explorador de esquemas XML**barra de herramientas; mediante el uso de las teclas del teclado **F3** y **MAYÚS**+**F3**; o haciendo clic en las marcas de graduación en la barra de desplazamiento.

 Puede agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

 ![Resultado de búsqueda del explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clear-search-results"></a>Resultados de Borrar búsqueda

 Para borrar los resultados de búsqueda, haga clic en el **x** botón en el panel de resultados de resumen de la **Explorador de esquemas XML** barra de herramientas de búsqueda.

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)