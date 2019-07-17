---
title: Buscar el conjunto de esquemas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d388db50ae935ef85b720177bd31c832a353d31
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145172"
---
# <a name="searching-the-schema-set"></a>Buscar en el conjunto de esquemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Explorador de esquemas XML permite buscar en el conjunto de esquemas de las maneras siguientes:  
  
- Búsqueda de palabra clave.  
  
- Búsqueda específica del esquema.  
  
## <a name="keyword-search"></a>Búsqueda de palabra clave  
 Realizar búsquedas de palabras clave escribiendo una subcadena en la **conjunto de esquemas de búsqueda** cuadro de texto de la barra de herramientas del explorador de esquemas XML.  
  
 ![Búsqueda de palabra clave de explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 El Explorador de esquemas XML busca en el conjunto de esquemas lo siguiente:  
  
- Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada. Esto permite buscar elementos, atributos, tipos, etc. por nombre.  
  
- Los atributos `schemaLocation` de las instrucciones include.  
  
- Los atributos `namespace` de las instrucciones import.  
  
## <a name="schema-specific-search"></a>Búsqueda específica del esquema  
 El Explorador de esquemas XML también incluye buscadores integrados a los que se tiene acceso mediante el menú contextual del explorador. Para obtener más información acerca de los menús contextuales disponibles, consulte [menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md). También puede realizar una búsqueda específica del esquema de la vista inicio; Para obtener más información, vea la sección "esquema Detalles del conjunto" en el [vista inicio](../xml-tools/start-view.md) tema.  
  
## <a name="displaying-and-navigating-search-results"></a>Mostrar y navegar en los resultados de la búsqueda  
 Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda. Los resultados de la búsqueda también se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical. Puede navegar por los resultados de búsqueda mediante el **ir al siguiente resultado de búsqueda** y **ir al resultado de búsqueda anterior** botones en el panel de resultados de resumen de la barra de herramientas del explorador de esquemas XML, mediante las teclas del teclado F3 y MAYÚS + F3 o haga clic en las marcas de graduación en la barra de desplazamiento.  
  
 Puede agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.  
  
 ![Resultado de búsqueda de explorador de esquema XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Borrar los resultados de una búsqueda  
 Para borrar los resultados de búsqueda, haga clic en el **x** en el panel de resultados de resumen de la barra de herramientas de búsqueda del explorador de esquemas XML.  
  
## <a name="see-also"></a>Vea también  
 [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
