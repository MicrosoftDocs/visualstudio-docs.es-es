---
title: Referencia de Directed Graph Markup Language (DGML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c676c57d6e6e6008611133235df8d525752f16b5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849501"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Referencia de Directed Graph Markup Language (DGML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El formato DGML (Directed Graph Markup Language) describe la información que se usa para la visualización y para realizar el análisis de complejidad, y se usa para continuar los mapas de código en Visual Studio. DGML usa XML simple para describir los gráficos dirigidos cíclicos y acíclicos. Un gráfico dirigido es un conjunto de nodos que están conectados mediante vínculos, o bordes. Se pueden usar nodos y vínculos para representar estructuras de red, como elementos en un proyecto de software.

 Tenga en cuenta que algunas versiones de Visual Studio solo admiten un subconjunto de las funcionalidades de DGML, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Al editar un archivo .dgml, IntelliSense le ayuda a identificar los atributos disponibles para cada elemento y sus valores. Para especificar color en un atributo, use nombres para los colores comunes, como "Blue", o valores hexadecimales de ARGB, como "#ffa0b1c3". DGML emplea un pequeño subconjunto de los formatos de definición de color de Windows Presentation Foundation (WPF). Para obtener más información, vea [colores (clase](https://msdn.microsoft.com/library/system.windows.media.colors.aspx)).

## <a name="DGML"></a>Sintaxis de DGML
 En la tabla siguiente se describen los tipos de elementos que se emplean en DGML:

- `<DirectedGraph></DirectedGraph>`

   Este elemento es el elemento raíz de un documento de mapa de código (.dgml). Todos los demás elementos de DGML aparecen dentro del ámbito de este elemento.

   En la lista siguiente se describen atributos opcionales que puede incluir:

   `Background`: el color del fondo del mapa

   `BackgroundImage`: la ubicación de un archivo de imagen que se va a usar como fondo del mapa.

   `GraphDirection`: cuando el mapa está establecido en el diseño de árbol (`Sugiyama`), organice los nodos para que la mayoría de los vínculos fluyan en la dirección especificada: `TopToBottom`, `BottomToTop`, `LeftToRight`o `RightToLeft`. Vea [cambiar el diseño del mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout`: establezca la asignación en los diseños siguientes: `None`, `Sugiyama` (diseño de árbol), `ForceDirected` (clústeres rápidos) o `DependencyMatrix`. Vea [cambiar el diseño del mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance`: cuando el mapa está establecido en el diseño de árbol o en el diseño de clústeres rápidos, solo muestra los nodos que tienen un número especificado (1-7) de vínculos fuera de los nodos seleccionados. Vea [cambiar el diseño del mapa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Este elemento opcional contiene una lista de elementos `<Node/>`, que definen nodos del mapa. Para obtener más información, vea el elemento `<Node/>`.

  > [!NOTE]
  > Al hacer referencia a un nodo no definido en un elemento `<Link/>`, el mapa crea un elemento `<Node/>` automáticamente.

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Este elemento define un único nodo. Aparece dentro de la lista de elementos `<Nodes><Nodes/>`.

   Este elemento debe incluir los atributos siguientes:

   `Id`: el nombre único del nodo y el valor predeterminado del atributo `Label`, si no se especifica ningún atributo de `Label` independiente. Este nombre debe coincidir con el atributo `Source` o `Target` del vínculo que hace referencia a él.

   En la lista siguiente se describen algunos atributos opcionales que puede incluir:

   `Label`: el nombre para mostrar del nodo.

   Atributos de estilo. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`: el nombre de una categoría que identifica los elementos que comparten este atributo. Para obtener más información, vea el elemento `<Category/>`.

   `Property`: el nombre de una propiedad que identifica los elementos que tienen el mismo valor de propiedad. Para obtener más información, vea el elemento `<Property/>`.

   `Group`: si el nodo contiene otros nodos, establezca este atributo en `Expanded` o `Collapsed` para mostrar u ocultar su contenido. Debe haber un elemento `<Link/>` que incluya el atributo `Category="Contains"` y especifique el nodo primario como nodo de origen y el nodo secundario como nodo de destino. Vea [elementos de código de grupo](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility`: establezca este atributo en `Visible`, `Hidden`o `Collapsed`. Utilice `System.Windows.Visibility`. Consulte [ocultar o mostrar nodos y vínculos](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference`: establezca este atributo para vincular un documento o una dirección URL. Vea [vincular documentos o direcciones URL a elementos de código y vínculos](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Este elemento contiene la lista de elementos `<Link>`, que definen vínculos entre nodos. Para obtener más información, vea el elemento `<Link/>`.

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Este elemento define un único vínculo que conecta un nodo de origen con un nodo de destino. Aparece dentro de la lista de elementos `<Links></Links>`.

  > [!NOTE]
  > Si este elemento hace referencia a un nodo no definido, el documento de mapa crea automáticamente un nodo que tiene los atributos especificados, en su caso.

   Este elemento debe incluir los atributos siguientes:

   `Source`: el nodo de origen del vínculo

   `Target`: nodo de destino del vínculo.

   En la lista siguiente se describen algunos atributos opcionales que puede incluir:

   `Label`: el nombre para mostrar del vínculo

   Atributos de estilo. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`: el nombre de una categoría que identifica los elementos que comparten este atributo. Para obtener más información, vea el elemento `<Category/>`.

   `Property`: el nombre de una propiedad que identifica los elementos que tienen el mismo valor de propiedad. Para obtener más información, vea el elemento `<Property/>`.

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Este elemento contiene la lista de elementos `<Category/>`. Para obtener más información, vea el elemento `<Category/>`.

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Este elemento define un atributo `Category`, que se emplea para identificar elementos que comparten este atributo. Se puede usar un atributo `Category` para organizar elementos de mapa, proporcionar atributos compartidos a través de la herencia o definir metadatos adicionales.

   Este elemento debe incluir los atributos siguientes:

   `Id`: nombre único de la categoría y el valor predeterminado del atributo `Label`, si no se especifica ningún atributo `Label` independiente.

   En la lista siguiente se describen algunos atributos opcionales que puede incluir:

   `Label`: nombre de fácil lectura para la categoría.

   `BasedOn`: la categoría primaria de la que se hereda la `<Category/>` del elemento actual.

   En el ejemplo de este elemento, la categoría `FailedTest` hereda su atributo `Stroke` de la categoría `PassedTest`. Consulte "para crear categorías jerárquicas" en [personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Las categorías también proporcionan cierto comportamiento de plantilla básico que controla la apariencia de los nodos y vínculos cuando se muestran en un mapa. Vea [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Este elemento contiene la lista de elementos `<Property/>`. Para obtener más información, vea el elemento `<Property/>`.

   Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Este elemento define un atributo `Property` que puede usar para asignar un valor a cualquier elemento de DGML o atributo, incluyendo categorías y otras propiedades.

   Este elemento debe incluir los atributos siguientes:

  - `Id`: el nombre único de la propiedad y el valor predeterminado del atributo `Label`, si no se especifica ningún atributo de `Label` independiente.

  - `DataType`: el tipo de datos almacenados por la propiedad

    Si desea que la propiedad aparezca en la ventana **propiedades** , use la propiedad `Label` para especificar el nombre para mostrar de la propiedad.

    Vea [asignar categorías a elementos de código y vínculos](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Ejemplo:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a>Alias para rutas de acceso usadas con frecuencia
 El reemplazo de rutas de acceso usadas con frecuencia con alias ayuda a reducir el tamaño del archivo .dgml y el tiempo necesario para cargar o guardar el archivo. Para crear un alias, agregue una sección `<Paths></Paths>` al final del archivo .dgml. En esta sección, agregue un elemento `<Path/>` para definir un alias para la ruta de acceso:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

 Para hacer referencia al alias desde un elemento del archivo. DGML, incluya el `Id` del elemento \<ruta de acceso/> con un signo de dólar ($) y paréntesis (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Vea también
 [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md) [buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)
