---
title: "Men&#250;s contextuales (Explorador de esquemas XML) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Men&#250;s contextuales (Explorador de esquemas XML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los elementos de menú contextual siguientes se usan para realizar búsquedas específicas del esquema y otras operaciones.  
  
## Tipo de nodo: conjunto de esquemas  
 En la tabla siguiente se describen las opciones disponibles para un nodo de conjunto de esquemas.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Mostrar elementos raíz más probables**|Busca y resalta todos los elementos globales a los que no hacen referencia más elementos globales que ellos mismos.|  
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales existentes en el esquema establecido.|  
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales existentes en el esquema establecido.|  
|**Ventana Propiedades**|Abre la ventana **Propiedades** \(si aún no está abierta\).Esta ventana muestra información sobre el nodo.|  
  
## Tipo de nodo: espacio de nombres  
 En la tabla siguiente se describen las opciones disponibles para un nodo de espacio de nombres.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Mostrar todas las referencias de entrada**|Busca y resalta los archivos que importan el espacio de nombres seleccionado.|  
|**Mostrar todas las referencias de salida**|Para cada archivo del espacio de nombres seleccionado, busca y resalta lo siguiente:<br /><br /> -   Todos los espacios de nombres a los que se hace referencia en las instrucciones de importación que no tienen un atributo `schemaLocation`.<br />-   Todos los archivos de los espacios de nombres distintos del seleccionado que se especifican en el atributo `schemaLocation` de las instrucciones de importación y de inclusión.|  
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales existentes en el espacio de nombres seleccionado.|  
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales existentes en el espacio de nombres seleccionado.|  
|**Ventana Propiedades**|Abre la ventana **Propiedades** \(si aún no está abierta\).Esta ventana muestra información sobre el nodo.|  
  
## Tipo de nodo: archivo  
 En la tabla siguiente se describen las opciones disponibles para un nodo de archivo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Mostrar todas las referencias de entrada**|Busca y resalta todos los archivos que especifican el archivo seleccionado en los atributos `schemaLocation` de las instrucciones de importación y de inclusión.|  
|**Mostrar todas las referencias de salida**|Busca y resalta lo siguiente:<br /><br /> -   Todos los espacios de nombres especificados en los atributos de espacio de nombres de todas las instrucciones de importación que no tienen el atributo `schemaLocation`.<br />-   Todos los archivos especificados en los atributos `schemaLocation` de todas las instrucciones de importación y de inclusión.|  
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales de este archivo.|  
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales de este archivo.|  
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML.El elemento que está seleccionado en el Explorador de esquemas XML también estará seleccionado en el Editor XML.|  
|**Ventana Propiedades**|Abre la ventana **Propiedades** \(si aún no está abierta\).Esta ventana muestra información sobre el nodo.|  
  
## Todos los tipos de nodos globales  
 En la tabla siguiente se describen las opciones disponibles para todos los nodos globales.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Mostrar en la vista Gráfico**|Abre la vista Gráfico.Si el nodo seleccionado no está en el área de trabajo, lo agrega a esta y lo selecciona.|  
|**Mostrar en la vista Modelo de contenido**|Abre la vista Modelo de contenido.Si el nodo seleccionado no está en el área de trabajo, lo agrega a esta y lo selecciona.|  
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML.El elemento que está seleccionado en el Explorador de esquemas XML también estará seleccionado en el Editor XML.|  
|**Ventana Propiedades**|Abre la ventana **Propiedades** \(si aún no está abierta\).Esta ventana muestra información sobre el nodo.|  
  
## Tipo de nodo: elemento  
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de elemento tiene las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ir a definición de tipo**|Navega a la definición de tipo del elemento seleccionado.Se aplica cuando el tipo utilizado para el elemento es un tipo global.|  
|**Ir al elemento original**|Para las referencias de elemento, navega a la definición efectiva del elemento.|  
|**Mostrar todas las referencias**|Para los elementos globales, busca y resalta todas las referencias \(los elementos con `ref="selectedElement"`\) al elemento seleccionado.|  
|**Mostrar miembros del grupo de sustitución**|Para los encabezados de un grupo de sustitución, busca y resalta todos los elementos que son miembros del grupo de sustitución al que pertenece el elemento seleccionado.Muestra los participantes directos e indirectos.|  
|**Mostrar encabezados del grupo de sustitución**|Para los elementos globales que son miembros de un grupo de sustitución, busca y resalta todos los encabezados directos e indirectos del elemento seleccionado, como los siguientes:<br /><br /> -   Un encabezado de grupo de sustitución especificado en el elemento seleccionado.<br />-   Un encabezado de grupo de sustitución especificado en su elemento de encabezado.|  
|**Generar XML de muestra**|Disponible solo para los elementos globales.Genera un archivo XML de ejemplo para el elemento global.|  
  
## Tipo de nodo: tipos globales  
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de tipo global tiene las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Mostrar tipo base**|Si el tipo seleccionado se deriva de un tipo global, navega al tipo base del tipo seleccionado.|  
|**Mostrar todas las referencias**|Busca y resalta todas las referencias al tipo seleccionado.Incluye elementos y atributos del tipo seleccionado y los tipos derivados del tipo seleccionado.|  
|**Mostrar todos los tipos derivados**|Busca y resalta todos los tipos derivados directa o indirectamente del tipo seleccionado.|  
|**Mostrar todos los antecesores**|Muestra todos los tipo primarios \(base\).|  
  
## Tipo de nodo: atributo  
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de atributo tiene las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ir a definición de tipo**|Cuando el tipo que se usa para el atributo es un tipo global, navega a la definición de tipo del atributo seleccionado.|  
|**Ir al atributo original**|Para las referencias de atributo, navega a la definición efectiva del atributo.|  
|**Mostrar todas las referencias**|Para los atributos globales, busca y resalta todas las referencias \(otros atributos con `ref="selectedAttribute"`\) al atributo seleccionado.|  
  
## Tipo de nodo: grupo de atributos  
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de grupo de atributos tiene las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ir a definición**|Para las referencias, navega a la definición efectiva del atributo.|  
|**Mostrar todos los miembros**|Busca y resalta todos los miembros del grupo de atributos.|  
|**Mostrar todas las referencias**|Busca y resalta todas las referencias \(los grupos de atributos con `ref="selectedAttributeGroup"`\) al grupo de atributos seleccionado.|  
  
## Tipo de nodo: grupo con nombre  
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de grupo con nombre tiene las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ir a definición**|Para las referencias, navega a la definición efectiva del atributo.|  
|**Mostrar todos los miembros**|Busca y resalta todos los miembros del grupo con nombre.|  
|**Mostrar todas las referencias**|Busca y resalta todas las referencias \(los grupos con `ref="selectedGroup"`\) al grupo seleccionado.|  
  
## Vea también  
 [Explorador de esquema XML](../xml-tools/xml-schema-explorer.md)   
 [Buscar en el conjunto de esquemas](../xml-tools/searching-the-schema-set.md)