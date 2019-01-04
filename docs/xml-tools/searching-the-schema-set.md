---
title: Explorador de esquemas XML - buscar el conjunto de esquemas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26be8121c679cc2614440f8e28f52b383dbe944c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836574"
---
# <a name="search-the-schema-set"></a>Buscar el conjunto de esquemas

El **Explorador de esquemas XML** permite buscar el esquema especificado en las siguientes maneras:

-   Búsqueda de palabra clave.

-   Búsqueda específica del esquema.

## <a name="keyword-search"></a>Búsqueda de palabra clave

 Realizar búsquedas de palabras clave escribiendo una subcadena en la **conjunto de esquemas de búsqueda** cuadro de texto de la **Explorador de esquemas XML** barra de herramientas.

 ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

 El **Explorador de esquemas XML** busca el esquema especificado para los siguientes atributos:

-   Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Puede buscar elementos, atributos, tipos etc. por nombre.

-   Los atributos `schemaLocation` de las instrucciones include.

-   Los atributos `namespace` de las instrucciones import.

## <a name="schema-specific-search"></a>Búsqueda específica del esquema

 El **Explorador de esquemas XML** también incluye buscadores integrados a los que puede tener acceso mediante el menú contextual de la **Explorador de esquemas XML**. Para obtener más información acerca de los menús contextuales disponibles, consulte [menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema de la vista inicio; Para obtener más información, vea la sección "esquema Detalles del conjunto" en el [vista inicio](../xml-tools/start-view.md) tema.

## <a name="display-and-navigate-search-results"></a>Mostrar y navegar por los resultados de búsqueda

 Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de búsqueda también se resaltan en la **Explorador de esquemas XML** y marcan en la barra de desplazamiento vertical. Puede navegar por los resultados de búsqueda mediante el **ir al siguiente resultado de búsqueda** y **ir al resultado de búsqueda anterior** botones en el panel de resultados de resumen de la **Explorador de esquemas XML**barra de herramientas; mediante el uso de las teclas del teclado **F3** y **MAYÚS**+**F3**; o haciendo clic en las marcas de graduación en la barra de desplazamiento.

 Puede agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

 ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Resultados de Borrar búsqueda

 Para borrar los resultados de búsqueda, haga clic en el **x** en el panel de resultados de resumen de la **Explorador de esquemas XML** barra de herramientas de búsqueda.

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)