---
title: Menús contextuales en el Explorador de esquemas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faf28fc44acd530cbc379c4a400c3488f98405ea
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
# <a name="context-menus-xml-schema-explorer"></a>Menús contextuales (Explorador de esquemas XML)

Los elementos de menú contextual siguientes se usan para realizar búsquedas específicas del esquema y otras operaciones.

## <a name="node-type-schema-set"></a>Tipo de nodo: conjunto de esquemas

En la tabla siguiente se describen las opciones disponibles para un nodo de conjunto de esquemas.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar elementos raíz más probables**|Busca y resalta todos los elementos globales a los que no hacen referencia más elementos globales que ellos mismos.|
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales existentes en el esquema establecido.|
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales existentes en el esquema establecido.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

## <a name="node-type-namespace"></a>Tipo de nodo: Namespace
 En la tabla siguiente se describen las opciones disponibles para un nodo de espacio de nombres.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar todas las referencias de entrada**|Busca y resalta los archivos que importan el espacio de nombres seleccionado.|
|**Mostrar todas las referencias de salida**|Para cada archivo del espacio de nombres seleccionado, busca y resalta lo siguiente:<br /><br /> -Todos los espacios de nombres al que hace referencia en importación instrucciones sin un `schemaLocation` atributo.<br />-Todos los archivos de los espacios de nombres distintos del seleccionado que se especifican en el `schemaLocation` atributo durante la importación e incluya las instrucciones.|
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales existentes en el espacio de nombres seleccionado.|
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales existentes en el espacio de nombres seleccionado.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

## <a name="node-type-file"></a>Tipo de nodo: archivo
 En la tabla siguiente se describen las opciones disponibles para un nodo de archivo.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar todas las referencias de entrada**|Busca y resalta todos los archivos que especifican el archivo seleccionado en los atributos `schemaLocation` de las instrucciones de importación y de inclusión.|
|**Mostrar todas las referencias de salida**|Busca y resalta lo siguiente:<br /><br /> -Todos los espacios de nombres especificados en los atributos de espacio de nombres de todas las instrucciones de importación que no tiene la `schemaLocation` atributo.<br />-Todos los archivos especificados en la `schemaLocation` atributos de todos los importar e incluir instrucciones.|
|**Mostrar tipos globales**|Busca y resalta todos los tipos globales de este archivo.|
|**Mostrar elementos globales**|Busca y resalta todos los elementos globales de este archivo.|
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML. El elemento que está seleccionado en el Explorador de esquemas XML también estará seleccionado en el Editor XML.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

## <a name="all-global-node-types"></a>Todos los tipos de nodo global
 En la tabla siguiente se describen las opciones disponibles para todos los nodos globales.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar en vista de gráfico**|Abre la vista Gráfico. Si el nodo seleccionado no está en el área de trabajo, lo agrega a esta y lo selecciona.|
|**Mostrar en vista de modelo de contenido**|Abre la vista Modelo de contenido. Si el nodo seleccionado no está en el área de trabajo, lo agrega a esta y lo selecciona.|
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML. El elemento que está seleccionado en el Explorador de esquemas XML también estará seleccionado en el Editor XML.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

## <a name="node-type-element"></a>Tipo de nodo: elemento
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de elemento tiene las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Ir a la definición de tipo**|Navega a la definición de tipo del elemento seleccionado. Se aplica cuando el tipo utilizado para el elemento es un tipo global.|
|**Vaya al elemento Original**|Para las referencias de elemento, navega a la definición efectiva del elemento.|
|**Mostrar todas las referencias**|Para los elementos globales, busca y resalta todas las referencias (los elementos con `ref="selectedElement"`) al elemento seleccionado.|
|**Mostrar a los miembros del grupo de sustitución**|Para los encabezados de un grupo de sustitución, busca y resalta todos los elementos que son miembros del grupo de sustitución al que pertenece el elemento seleccionado. Muestra los participantes directos e indirectos.|
|**Encabezados del grupo de sustitución de presentación**|Para los elementos globales que son miembros de un grupo de sustitución, busca y resalta todos los encabezados directos e indirectos del elemento seleccionado, como los siguientes:<br /><br /> : Un encabezado de grupo de sustitución especificado en el elemento seleccionado.<br />: Un encabezado de grupo de sustitución especificado en su elemento principal.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|

## <a name="node-type-global-types"></a>Tipo de nodo: tipos globales
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de tipo global tiene las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Mostrar tipo Base**|Si el tipo seleccionado se deriva de un tipo global, navega al tipo base del tipo seleccionado.|
|**Mostrar todas las referencias**|Busca y resalta todas las referencias al tipo seleccionado. Incluye elementos y atributos del tipo seleccionado y los tipos derivados del tipo seleccionado.|
|**Mostrar todos los tipos derivados**|Busca y resalta todos los tipos derivados directa o indirectamente del tipo seleccionado.|
|**Mostrar todos los antecesores**|Muestra todos los tipos primarios (base).|

## <a name="node-type-attribute"></a>Tipo de nodo: atributo
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de atributo tiene las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Ir a la definición de tipo**|Cuando el tipo que se usa para el atributo es un tipo global, navega a la definición de tipo del atributo seleccionado.|
|**Vaya al atributo Original**|Para las referencias de atributo, navega a la definición efectiva del atributo.|
|**Mostrar todas las referencias**|Para los atributos globales, busca y resalta todas las referencias (otros atributos con `ref="selectedAttribute"`) al atributo seleccionado.|

## <a name="node-type-attribute-group"></a>Tipo de nodo: grupo de atributos
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de grupo de atributos tiene las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Ir a definición**|Para las referencias, navega a la definición efectiva del atributo.|
|**Mostrar todos los miembros**|Busca y resalta todos los miembros del grupo de atributos.|
|**Mostrar todas las referencias**|Busca y resalta todas las referencias (los grupos de atributos con `ref="selectedAttributeGroup"`) al grupo de atributos seleccionado.|

## <a name="node-type-named-group"></a>Tipo de nodo: grupo con nombre
 Además de las opciones de nodo global descritas anteriormente, el menú contextual para los nodos de grupo con nombre tiene las siguientes opciones:

|Opción|Descripción|
|------------|-----------------|
|**Ir a definición**|Para las referencias, navega a la definición efectiva del atributo.|
|**Mostrar todos los miembros**|Busca y resalta todos los miembros del grupo con nombre.|
|**Mostrar todas las referencias**|Busca y resalta todas las referencias (los grupos con `ref="selectedGroup"`) al grupo seleccionado.|

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
- [Buscar el conjunto de esquemas](../xml-tools/searching-the-schema-set.md)