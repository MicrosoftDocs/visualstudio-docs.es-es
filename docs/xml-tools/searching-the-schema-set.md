---
title: 'Explorador de esquemas XML: buscar en el conjunto de esquemas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8378ebaccefaedfcc3d83f23bcab56f7417264dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592508"
---
# <a name="search-the-schema-set"></a>Búsqueda en el conjunto de esquemas

El **Explorador de esquemas XML** permite buscar en el conjunto de esquemas de las siguientes maneras:

- Búsqueda de palabra clave.

- Búsqueda específica del esquema.

## <a name="keyword-search"></a>Búsqueda de palabra clave

Para realizar búsquedas de palabras clave, escriba una subcadena en el cuadro de texto **Buscar de búsqueda** de la barra de herramientas del **Explorador de esquemas XML** .

![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

El **Explorador de esquemas XML** busca en el conjunto de esquemas los atributos siguientes:

- Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Puede buscar elementos, atributos, tipos, etc., por nombre.

- Los atributos `schemaLocation` de las instrucciones include.

- Los atributos `namespace` de las instrucciones import.

## <a name="schema-specific-search"></a>Búsqueda específica del esquema

El **Explorador de esquemas XML** incluye también las búsquedas integradas a las que puede tener acceso mediante el menú contextual (clic con el botón derecho) del **Explorador de esquemas XML**. Para obtener más información acerca de los menús contextuales disponibles, consulte [menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema desde la vista Inicio. para obtener más información, consulte la sección "detalles del conjunto de esquemas" en el tema de la [vista Inicio](../xml-tools/start-view.md) .

## <a name="display-and-navigate-search-results"></a>Mostrar y navegar por los resultados de la búsqueda

Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de la búsqueda también se resaltan en el **Explorador de esquemas XML** y se marcan con TICs en la barra de desplazamiento vertical. Puede navegar por los resultados de la búsqueda mediante los botones **ir a siguiente resultado** de la búsqueda e **ir al resultado de la búsqueda anterior** en el panel de resultados de Resumen de la barra de herramientas del **Explorador de esquemas XML** . con las teclas de teclado **F3** y **MAYÚS**+**F3**; o bien, haga clic en las marcas de graduación de la barra de desplazamiento.

Puede Agregar los resultados de la búsqueda al área de trabajo haciendo clic en el botón **agregar nodos resaltados al área de trabajo** en el panel de resultados de resumen.

![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Borrar resultados de búsqueda

Para borrar los resultados de la búsqueda, haga clic en el botón **x** del panel de resultados de Resumen de la barra de herramientas de búsqueda del **Explorador de esquemas XML** .

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
