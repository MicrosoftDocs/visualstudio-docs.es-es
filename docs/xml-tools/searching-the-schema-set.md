---
title: "Buscar en el conjunto de esquemas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Buscar en el conjunto de esquemas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Explorador de esquemas XML permite buscar en el conjunto de esquemas de las maneras siguientes:  
  
-   Búsqueda de palabra clave.  
  
-   Búsqueda específica del esquema.  
  
## Búsqueda de palabra clave  
 Las búsquedas de palabra clave se realizan escribiendo una subcadena en el cuadro de texto **Buscar en el conjunto de esquemas** de la barra de herramientas del Explorador de esquemas XML.  
  
 ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 El Explorador de esquemas XML busca en el conjunto de esquemas lo siguiente:  
  
-   Cualquier atributo `name` o `ref` que coincida con la palabra clave especificada.Esto permite buscar elementos, atributos, tipos, etc. por nombre.  
  
-   Los atributos `schemaLocation` de las instrucciones include.  
  
-   Los atributos `namespace` de las instrucciones import.  
  
## Búsqueda específica del esquema  
 El Explorador de esquemas XML también incluye buscadores integrados a los que se tiene acceso mediante el menú contextual del explorador.Para obtener más información sobre los menús contextuales disponibles, vea [Menús contextuales](../xml-tools/context-menus-xml-schema-explorer.md).También puede realizar una búsqueda específica del esquema en la vista Inicio; para obtener más información, vea la sección "Detalles del conjunto de esquemas" en el tema [Vista Inicio](../xml-tools/start-view.md).  
  
## Mostrar y navegar en los resultados de la búsqueda  
 Una vez finalizada la búsqueda, se agrega el panel de resumen de resultados a la barra de herramientas con los resultados de la búsqueda.Los resultados de la búsqueda también se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical.Puede navegar por los resultados de la búsqueda mediante los botones **Ir al siguiente resultado de la búsqueda** e **Ir al resultado anterior de la búsqueda** del panel de resumen de resultados y de la barra de herramientas del Explorador de esquemas XML, mediante las teclas F3 y Mayús\-F3 o haciendo clic en las marcas de graduación de la barra de desplazamiento.  
  
 Puede agregar los resultados de la búsqueda al área de trabajo; para ello, haga clic en el botón **Agregar nodos resaltados al área de trabajo** en el panel de resumen de resultados.  
  
 ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## Borrar los resultados de una búsqueda  
 Para borrar los resultados de una búsqueda, haga clic en el botón **x** del panel de resumen de resultados de la barra de herramientas de búsqueda del Explorador de esquemas XML.  
  
## Vea también  
 [Explorador de esquema XML](../xml-tools/xml-schema-explorer.md)