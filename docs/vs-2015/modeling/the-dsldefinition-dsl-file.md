---
title: El archivo DslDefinition.dsl | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c62483ad8edac88fe3d14c6590dfb7e6d17285f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999361"
---
# <a name="the-dsldefinitiondsl-file"></a>El archivo DslDefinition.dsl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tema describe la estructura del archivo DslDefinition.dsl en el proyecto Dsl de un [!INCLUDE[dsl](../includes/dsl-md.md)] solución, que define un *lenguajes específicos de dominio*. El archivo DslDefinition.dsl describe las clases y relaciones de un lenguaje específico de dominio, junto con el diagrama, formas, conectores, formato de serialización y **cuadro de herramientas** del lenguaje específico de dominio y su herramientas de edición. En una solución de lenguaje específico de dominio, el código que define esas herramientas se genera conforme a la información del archivo DslDefinition.dsl.  
  
 Por lo general, usa el *Diseñador de lenguaje específico de dominio* para editar el archivo DslDefinition.dsl. Sin embargo, el formato sin procesar es XML por lo que puede abrir un archivo DslDefinition.dsl en un editor XML. Para fines de depuración y extensión, quizás le resulte útil comprender qué información contiene el archivo y cómo está organizada.  
  
 Los ejemplos de este tema se toman de la plantilla de solución Diagrama de componentes. Para ver un ejemplo, cree una solución de lenguaje específico de dominio basada en la plantilla de solución Component Models (Modelos de componentes). Después de crear la solución, el archivo DslDefinition.dsl aparece en el diseñador de lenguaje específico de dominio. Cierre el archivo, haga clic en él en **el Explorador de soluciones**, apunte a **abrir con**, haga clic en **Editor XML**y, a continuación, haga clic en **Aceptar**.  
  
## <a name="sections-of-the-dsldefinitiondsl-file"></a>Secciones del archivo DslDefinition.dsl  
 El elemento raíz es \<Dsl > y sus atributos identifican el nombre del lenguaje específico de dominio, el espacio de nombres y números de versión principal y secundaria para el control de versiones. El esquema `DslDefinitionModel` define el contenido y la estructura de un archivo DslDefinition.dsl válido.  
  
 Los elementos secundarios de la \<Dsl > elemento raíz son los siguientes:  
  
 Clases  
 En esta sección se define cada clase de dominio que genera una clase en el código generado.  
  
 Relaciones  
 En esta sección se define cada relación del modelo. El origen y el destino representan los dos lados de una relación.  
  
 Tipos  
 En esta sección se define cada tipo y su espacio de nombres. Las propiedades de dominio tienen dos tipos. `DomainEnumerations` se definen en el modelo y generan tipos en DomainModel.cs. `ExternalTypes` hacen referencia a los tipos que se definen en otras partes (como `String` o `Int32`) y no generan nada.  
  
 Formas  
 En esta sección se definen las formas que describen cómo aparece el modelo en un diseñador. Estas formas geométricas se corresponden con las clases del modelo en la sección Diagrama.  
  
 Conectores  
 En esta sección se define el aspecto de los conectores que aparecen en un diseñador. Estas descripciones de estilos geométricos se corresponden con relaciones específicas del modelo en la sección Diagrama.  
  
 XmlSerializationBehavior  
 En esta sección se define un esquema de serialización y se proporciona información adicional sobre cómo se guarda cada clase en un archivo.  
  
 ExplorerBehavior  
 Esta sección se define cómo el **DSL Explorer** ventana aparece cuando el usuario está editando un modelo.  
  
 ConnectionBuilders  
 En esta sección se define un generador de conexiones para cada herramienta de conector (la herramienta que se usa para crear vínculos entre dos clases cualquiera que se puedan conectar). En esta sección se determina si se puede conectar una clase de origen y una de destino.  
  
 Diagram  
 En esta sección se define un diagrama y se usa para especificar propiedades, como el color de fondo, y la clase raíz. (La clase raíz es la clase de dominio que el diagrama representa como un todo). La sección Diagram también contiene elementos ShapeMap y ConnectorMap, que especifican la forma o el conector que representa cada clase o relación de dominio.  
  
 Diseñador  
 Esta sección define un diseñador (editor), que reúne un **cuadro de herramientas**, configuración de la validación, un diagrama y un esquema de serialización. En la sección Designer también se define la clase raíz del modelo, que normalmente es también la clase raíz del diagrama.  
  
 Explorer  
 Esta sección se identifican los **DSL Explorer** comportamiento (definido en la sección XmlSerializationBehavior).  
  
## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikers en el archivo DslDefinition.dsl  
 En todo el archivo DslDefinition.dsl se pueden usar monikers para hacer referencias cruzadas a elementos específicos. Por ejemplo, cada definición Relationship contiene una subsección Source y una subsección Target. Cada subsección contiene el moniker de la clase de objeto que se puede vincular con esa relación:  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 Normalmente, el espacio de nombres del elemento referenciado (en este ejemplo, la clase de dominio `Library`) es el mismo que el del elemento referenciador (en este caso, la relación de dominio LibraryHasMembers). En estos casos, el moniker solo tiene que dar el nombre de la clase. De lo contrario, debe usar el formato completo /espacioDeNombres/Nombre:  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 El sistema de moniker requiere que los elementos del mismo nivel en el árbol XML tengan nombres distintos. Por este motivo, se producen errores de validación si intenta guardar una definición específica de dominio que tenga, por ejemplo, dos clases con el mismo nombre. Debe corregir siempre estos errores de nombres duplicados antes de guardar el archivo DslDefinition.dsl para que pueda volver a cargarlo correctamente más adelante.  
  
 Cada tipo tiene su propio tipo de moniker: DomainClassMoniker, DomainRelationshipMoniker, etc.  
  
## <a name="types"></a>Tipos  
 En la sección Types se especifican todos los tipos que el archivo DslDefinition.dsl contiene como tipos de propiedades. Estos tipos se dividen en dos tipos: tipos externos, como System.String y los tipos enumerados.  
  
### <a name="external-types"></a>Tipos externos  
 El ejemplo Component Diagram (Diagrama de componentes) muestra un conjunto de tipos primitivos estándar, aunque solo se usan algunos de ellos.  
  
 Cada definición de tipo externo consta de un nombre y un espacio de nombres, por ejemplo, String y System:  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 Se usan los nombres completos de los tipos en lugar de palabras clave del compilador equivalentes, como "string".  
  
 Los tipos externos no se limitan a los tipos de la biblioteca estándar.  
  
### <a name="enumerations"></a>Enumeraciones  
 Una especificación de enumeración típica se parece a la de este ejemplo:  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 El atributo `IsFlags` controla si el atributo de Common Language Runtime (CLR) `[Flags]` asigna un prefijo al código generado, que determina si los valores de la enumeración se pueden combinar bit a bit. Si este atributo se establece en True, debe especificar valores potencia de dos para los valores literales.  
  
## <a name="classes"></a>Clases  
 La mayoría de los elementos de cualquier definición de lenguaje específico de dominio son directa o indirectamente instancias de `DomainClass`. Las subclases de `DomainClass` incluyen `DomainRelationship`, `Shape`, `Connector` y `Diagram`. La sección `Classes` del archivo DslDefinition.dsl enumera las clases de dominio.  
  
 Cada clase tiene un conjunto de propiedades y podría tener una clase base. En el ejemplo Component Diagram (Diagrama de componentes), `NamedElement` es una clase abstracta que tiene una propiedad `Name`, cuyo tipo es String:  
  
```  
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">  
  <Properties>  
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
</DomainClass>  
```  
  
 `NamedElement` es la base de varias de las demás clases, como `Component`, que tiene sus propias propiedades además de la propiedad `Name`, que heredó de `NamedElement`. El nodo secundario BaseClass contiene una referencia de moniker. Como la clase referenciada está en el mismo espacio de nombres, en el moniker solo se necesita su nombre.  
  
```  
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">  
  <BaseClass>  
    <DomainClassMoniker Name="NamedElement" />  
  </BaseClass>  
  <Properties>  
    <DomainProperty Name="Kind" DisplayName="Kind" >  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
```  
  
 Todas las clases de dominio (incluidas relaciones, formas, conectores y diagramas) pueden tener estos atributos y nodos secundarios:  
  
-   **Id.** Este atributo es un GUID. Si no proporciona un valor en el archivo, el diseñador de lenguaje específico de dominio creará un valor. (En las ilustraciones de este documento, este atributo se suele omitir para ahorrar espacio).  
  
-   **Nombre y Namespace.** Estos atributos especifican el nombre y espacio de nombres de la clase en el código generado. Juntos deben ser únicos en el lenguaje específico de dominio.  
  
-   **InheritanceModifier.** Este atributo es "abstract", "sealed" o ninguno.  
  
-   **DisplayName.** Este atributo es el nombre que aparece en el **propiedades** ventana. El atributo DisplayName puede contener espacios y otros signos de puntuación.  
  
-   **GeneratesDoubleDerived.** Si este atributo se establece en true, se generan dos clases, y uno es una subclase del otro. Todos los métodos generados están en la clase base y los constructores están en la subclase. Al establecer este atributo puede invalidar los métodos generados en el código personalizado.  
  
-   **HasCustomConstructor**. Si este atributo se establece en True, el constructor se omite del código generado para que pueda escribir su propia versión.  
  
-   **Atributos**. Este atributo contiene los atributos de CLR de la clase generada.  
  
-   **BaseClass**. Si especifica una clase base, debe ser del mismo tipo. Por ejemplo, una clase de dominio debe tener otra clase de dominio como base y una forma de compartimiento debe tener una forma de compartimiento. Si no especifica una clase base, la clase del código generado deriva de una clase de marco estándar. Por ejemplo, una clase de dominio deriva de `ModelElement`.  
  
-   **Propiedades**. Este atributo contiene las propiedades que se mantienen bajo el control de transacciones y se conservan cuando el modelo se guarda.  
  
-   **ElementMergeDirectives**. Cada directiva de combinación de elementos controla cómo se agrega una instancia diferente de otra clase a una instancia de la clase primaria. Encontrará información más detallada sobre las directivas de combinación de elementos más adelante en este tema.  
  
-   Se genera una clase de C# para cada clase de dominio enumerada en la sección `Classes`. Las clases de C# se generan en Dsl\GeneratedCode\DomainClasses.cs.  
  
### <a name="properties"></a>Propiedades  
 Cada propiedad de dominio tiene un nombre y un tipo. El nombre debe ser único dentro de la clase de dominio y sus bases transitivas.  
  
 El tipo debe ser uno de los que se enumeran en la sección `Types`. Por lo general, el moniker debe incluir el espacio de nombres.  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 Cada propiedad de dominio puede tener también estos atributos:  
  
-   **IsBrowsable**. Este atributo determina si la propiedad aparece en la **propiedades** ventana cuando el usuario hace clic en un objeto de la clase primaria.  
  
-   **IsUIReadOnly**. Este atributo determina si el usuario puede cambiar la propiedad en el **propiedades** ventana o a través de un elemento decorator en el que se presenta la propiedad.  
  
-   **Tipo**. Este atributo se puede establecer en Normal, Calculated o CustomStorage. Si establece este atributo en Calculated, debe proporcionar código personalizado que determine el valor, y la propiedad será de solo lectura. Si establece este atributo en CustomStorage, debe proporcionar código que obtenga y establezca los valores.  
  
-   **IsElementName**. Si este atributo se establece en True, su valor se establece automáticamente en un valor único cuando se crea una instancia de la clase primaria. Este atributo se puede establecer en True solo para una propiedad en cada clase, que debe tener un tipo String. En el ejemplo Component Diagram (Diagrama de componentes), la propiedad `Name` de `NamedElement` tiene `IsElementName` establecido en True. Siempre que un usuario crea un elemento `Component` (que hereda de `NamedElement`), el nombre se inicializa automáticamente en algo como "Component6".  
  
-   `DefaultValue`. Si ha especificado este atributo, el valor que especificó se asigna a este atributo para las nuevas instancias de esta clase. Si `IsElementName` está establecido, el atributo DefaultValue especifica la parte inicial de la nueva cadena.  
  
-   **Categoría** es el encabezado en la que la propiedad aparecerá en el **propiedades** ventana.  
  
## <a name="relationships"></a>Relaciones  
 La sección `Relationships` enumera todas las relaciones del lenguaje específico de dominio. Cada `Domain Relationship` es binaria y dirigida, y vincula miembros de una clase de origen con miembros de una clase de destino. Las clases de origen y de destino suelen ser clases de dominio, pero también se permiten relaciones con otras relaciones.  
  
 Por ejemplo, la relación Connection vincula miembros de la clase OutPort con miembros de la clase InPort. Cada instancia de vínculo de la relación conecta una instancia de un OutPort con una instancia de un InPort. Como la relación es de varios a varios, cada OutPort puede contener muchos vínculos Connection de los que es el origen, y cada instancia de InPort puede tener muchos vínculos Connection de los que es el destino.  
  
### <a name="source-and-target-roles"></a>Roles de origen y destino  
 Cada relación contiene roles de origen y de destino que tienen los siguientes atributos:  
  
-   El atributo `RolePlayer` hace referencia a la clase de dominio de las instancias vinculadas: OutPort para el origen, InPort para el destino.  
  
-   El atributo `Multiplicity` tiene cuatro valores posibles (ZeroMany, ZeroOne, One y OneMany). Este atributo hace referencia al número de vínculos de esta relación que se pueden asociar con un encargado de rol.  
  
-   El atributo `PropertyName` especifica el nombre que se usa en la clase encargada del rol para acceder a los objetos en el otro extremo. Este nombre se usa en código de plantilla o personalizado para atravesar la relación. Por ejemplo, el atributo `PropertyName` del rol de origen se establece en `Targets`. Por consiguiente, el código siguiente funcionará:  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     Por convención, los nombres de propiedad son plurales si la multiplicidad es ZeroMany o OneMany.  
  
     La multiplicidad de un rol hace referencia a cuántos roles opuestos se pueden asociar a cada instancia de este rol. Por ejemplo, en la relación ComponentHasPorts, el rol de destino tiene el atributo `RolePlayer` establecido en Port, el atributo `PropertyName` establecido en Component y el atributo `Multiplicity` establecido en ZeroOne. Por lo tanto, el código apropiado para usar este rol es:  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
-   El `Name` del rol es el nombre que se usa con la clase Relationship para hacer referencia a ese extremo de un vínculo. Por convención, un nombre de rol es siempre singular, porque cada vínculo solo tiene una instancia en cada extremo. El siguiente código funcionará:  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
-   De forma predeterminada, el atributo `IsPropertyGenerator` está establecido en True. Si se establece en False, no se crea ninguna propiedad en la clase encargada del rol. (En ese caso, `op.Targets`, por ejemplo, no funcionaría). Sin embargo, aún es posible usar código personalizado para atravesar la relación o para obtener acceso a los propios vínculos, si el código personalizado usa la relación explícitamente:  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### <a name="relationship-attributes"></a>Atributos de relación  
 Además de los atributos y nodos secundarios de que disponen todas las clases, cada relación tiene estos atributos:  
  
-   **IsEmbedding**. Este atributo booleano especifica si la relación forma parte del árbol de incrustación. Cada modelo debe formar un árbol con sus relaciones de incrustación. Por lo tanto, cada clase de dominio debe ser el destino de, al menos, una relación de incrustación, a menos que sea la raíz del modelo.  
  
-   **AllowsDuplicates**. Este atributo booleano, cuyo valor es False de forma predeterminada, se aplica solo a relaciones que tienen una multiplicidad "Many" en el origen y el destino. Determina si los usuarios del lenguaje pueden conectar un único par de elementos de origen y destino con más de un vínculo de la misma relación.  
  
## <a name="designer-and-toolbox-tabs"></a>Pestañas del diseñador y del cuadro de herramientas  
 La parte principal de la **diseñador** sección del archivo DslDefinition.dsl es el **ToolboxTab** elementos. Un diseñador puede tener varios de estos elementos, cada uno de los cuales representa una sección con encabezado en el diseñador generado **cuadro de herramientas**. Cada **ToolboxTab** elemento puede contener uno o varios **ElementTool** elementos, **ConnectionTool** elementos, o ambos.  
  
 Las herramientas de elemento pueden crear instancias de una clase de dominio específica. Cuando el usuario arrastra una herramienta de elemento al diagrama, el resultado está determinado por las directivas de combinación de elementos, tal y como se describe en la sección sobre las directivas de combinación de elementos más adelante en este tema.  
  
 Cada herramienta de conexión puede invocar un generador de conexiones específico. Un generador de conexiones puede crear más de un tipo de relación, según dónde el usuario haga clic con el mouse, tal y como se describe en la sección sobre generadores de conexiones.  
  
 Ninguno de los tipos de herramienta construye directamente formas o conectores. Cada uno crea una instancia de una clase de dominio o una relación de dominio; después, las asignaciones de formas y conectores determinan cómo se muestra esa relación de dominio o clase de dominio.  
  
## <a name="paths"></a>Rutas de acceso  
 Las rutas de dominio aparecen en varios lugares del archivo DslDefinition.dsl. Estas rutas especifican una serie de vínculos desde un elemento del modelo (es decir, una instancia del lenguaje específico de dominio) a otro. La sintaxis de la ruta es simple pero detallada.  
  
 Las rutas aparecen en el archivo DslDefinition.dsl en las etiquetas `<DomainPath>…</DomainPath>`. Aunque las rutas pueden navegar por varios vínculos, en la mayoría de los ejemplos solo atraviesan un vínculo.  
  
 Una ruta está compuesta por una secuencia de segmentos. Cada segmento es un salto desde un objeto a un vínculo o desde un vínculo a un objeto. Por lo tanto, los saltos suelen alternarse en una ruta larga. El primer salto se realiza desde un objeto a un vínculo, el segundo salto desde el objeto al otro extremo del vínculo, el tercer salto hacia el siguiente vínculo, etc. La excepción ocasional a esta secuencia es cuando una relación es ella misma el origen o el destino de otra relación.  
  
 Cada segmento comienza por un nombre de relación. En un salto de vínculo de objeto, la relación precede a un punto y el nombre de propiedad: "`Relationship . Property`". En un salto de objeto de vínculo, la relación precede a una marca de exclamación y el nombre del rol: "`Relationship ! Role`".  
  
 El ejemplo Component Diagram (Diagrama de componentes) contiene una ruta en la ParentElementPath del ShapeMap para InPort. Esta ruta comienza de la siguiente manera:  
  
```  
    ComponentHasPorts.Component  
```  
  
 En este ejemplo, InPort es una subclase de ComponentPort y tiene una relación ComponentHasPorts. La propiedad se llama Component.  
  
 Al escribir C# en este modelo, puede acceder directamente a través de un vínculo en un solo paso mediante el uso de la propiedad que la relación genera en cada una de las clases que se relación:  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 Sin embargo, debe hacer ambos saltos explícitamente en la sintaxis de la ruta. Este requisito permite acceder al vínculo intermedio más fácilmente. El código siguiente completa el salto desde el vínculo al Component:  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 (Puede omitir el nombre de la relación cuando sea igual que en el segmento anterior).  
  
## <a name="element-merge-directives"></a>Directivas de combinación de elementos  
 Cuando el usuario del lenguaje arrastra un elemento desde el **cuadro de herramientas** hasta el diagrama, se construye una instancia de clase de la herramienta. Además, se crean vínculos entre esa instancia y los elementos de modelo existentes. Algunos elementos, como componentes o los comentarios, se crean cuando el usuario del lenguaje arrastra desde el **cuadro de herramientas** a una parte en blanco del diagrama. Otros elementos se crean cuando el usuario del lenguaje los arrastra a otros elementos de host. Por ejemplo, se crea un OutPort o un InPort cuando el usuario del lenguaje lo arrastra a un componente.  
  
 Una posible clase host, como Component, aceptará un nuevo elemento solo si la clase host tiene una directiva de combinación de elementos para la clase del nuevo elemento. Por ejemplo, el nodo DomainClass con Name="Component" contiene:  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 El moniker de clase que está bajo el nodo Index hace referencia a la clase de elemento que se puede aceptar. En este caso, ComponentPort es la clase base abstracta de InPort y OutPort. Por lo tanto, se aceptará cualquiera de estos elementos.  
  
 ComponentModel, la clase raíz del lenguaje, tiene directivas de combinación de elementos para componentes y comentarios. El usuario del lenguaje puede arrastrar elementos para esas clases directamente en el diagrama porque las partes en blanco del diagrama representan la clase raíz. Sin embargo, ComponentModel no tiene ninguna directiva de combinación de elementos para ComponentPort. Por lo tanto, el usuario del lenguaje no puede arrastrar OutPorts o InPorts directamente al diagrama.  
  
 La directiva de combinación de elementos determina qué vínculo o vínculos se crean para que el nuevo elemento se pueda integrar o combinar en el modelo existente. Para un ComponentPort, se crea una instancia de ComponentHasPorts. DomainPath identifica tanto la relación como la propiedad de la clase primaria, Ports, a la que se agregará el nuevo elemento.  
  
 Puede crear más de un vínculo en una directiva de combinación de elementos, incluyendo más de una ruta de creación de vínculo. Una de las rutas debe estar incrustada.  
  
 Puede usar más de un segmento en una ruta de creación de vínculo. En este caso, el último segmento define qué vínculo se debe crear. Los primeros segmentos navegan desde la clase primaria al objeto desde el cual se debe crear el nuevo vínculo.  
  
 Por ejemplo, puede agregar esta directiva de combinación de elementos a la clase Component:  
  
```  
<DomainClass Name="Component" …> …  
  <ElementMergeDirective>  
    <Index>  
       <DomainClassMoniker Name="Comment"/>  
    </Index>  
    <LinkCreationPaths>  
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>  
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>  
    </LinkCreationPaths>  
  </ElementMergeDirective>  
```  
  
 Después, los usuarios del lenguaje pueden arrastrar un comentario a un componente y hacer que el nuevo comentario se cree automáticamente con un vínculo al componente.  
  
 La primera ruta de creación de vínculo navega desde `Component` a `ComponentModel` y, después, crea una instancia de la relación de incrustación `ComponentModelHasComments`. La segunda ruta de creación de vínculo crea un vínculo de la relación de referencia CommentsReferenceComponents desde el Component host al nuevo Comment. Todas las rutas de creación de vínculo deben comenzar con la clase host y deben terminar en un vínculo que avance a la clase cuya instancia se acaba de crear.  
  
## <a name="xmlclassdata"></a>XmlClassData  
 Cada clase de dominio (incluidas las relaciones y otros subtipos) pueden proporcionar información adicional en un nodo `XmlClassData`, que aparece en la sección `XmlSerializationBehavior` del archivo DslDefinition.dsl. Esta información define específicamente cómo se almacenan las instancias de la clase de forma serializada cuando se guarda un modelo en un archivo.  
  
 Gran parte del código generado al que `XmlSerializationBehavior` afecta está en `Dsl\GeneratedCode\Serializer.cs`.  
  
 Cada nodo `XmlClassData` incluye estos nodos secundarios y atributos:  
  
-   Un nodo moniker, que hace referencia a la clase a la que se aplican los datos.  
  
-   **XmlPropertyData** para cada propiedad que se define en la clase.  
  
-   **XmlRelationshipData** para cada relación que se origina en la clase. (Las relaciones también tienen sus propios nodos XmlClassData).  
  
-   **TypeName** atributo de cadena, que determina el nombre de la clase de aplicación auxiliar de serialización en el código generado.  
  
-   **ElementName** cadena, que determina la etiqueta XML de las instancias serializadas de esta clase. Por convención, ElementName suele ser igual que el nombre de la clase, excepto que la primera letra es minúscula. Por ejemplo, un archivo de modelo de muestra comienza con lo siguiente:  
  
    ```  
    <componentModel …  
    ```  
  
-   **MonikerElementName** en archivos de modelo serializado del usuario. Este atributo incorpora un moniker que hace referencia a esta clase.  
  
-   **MonikerAttributeName**, que identifica el nombre del atributo XML dentro de un moniker. En este fragmento del archivo serializado de un usuario, el autor del lenguaje específico de dominio definido **MonikerElementName** como "inPortMoniker" y **MonikerAttributeName** como "path":  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### <a name="connectionbuilders"></a>ConnectionBuilders  
 Para cada herramienta de conexión se define un generador de conexiones. Cada generador de conexiones consta de uno o varios elementos LinkConnectDirective, cada uno de los cuales contiene uno o varios elementos SourceDirective y uno o varios elementos TargetDirective. Después de hacer clic en la herramienta de conexión, el usuario puede iniciar una conexión desde cualquier forma asignada a un elemento de modelo que aparezca en la lista de elementos SourceDirective. Después, la conexión se puede completar en una forma asignada a un elemento que aparezca en la lista de elementos TargetDirective. La clase de relación de la cual se crea una instancia dependerá del elemento LinkConnectDirective designado por el lugar donde se inició la conexión.  
  
### <a name="xmlpropertydata"></a>XmlPropertyData  
 Un **DomainPropertyMoniker** atributo identifica la propiedad al que hace referencia los datos. Este atributo debe ser una propiedad de la clase de ClassData contenedora.  
  
 El **XmlName** atributo proporciona el nombre de atributo correspondiente como debe aparecer en el archivo XML. Por convención, esta cadena es igual que el nombre de la propiedad, excepto que la primera letra es minúscula.  
  
 De forma predeterminada, el **representación** atributo está establecido en el atributo. Si **representación** está establecido en Element, un elemento secundario se crea el nodo en el archivo XML. Si **representación** está establecido en Ignore, la propiedad no se serializa.  
  
 El **IsMonikerKey** y **IsMonikerQualifier** atributos proporcionan una propiedad de un rol en la identificación de las instancias de la clase primaria. Puede establecer **IsMonikerKey** en true para una propiedad que se defina en o heredada por una clase. Este atributo identifica una instancia individual de la clase primaria. La propiedad que establece en `IsMonikerKey` suele ser un nombre u otro identificador clave. Por ejemplo, la propiedad de cadena `Name` es la clave de moniker de NamedElement y sus clases derivadas. Cuando el usuario guarda un modelo en un archivo, este atributo debe contener valores únicos para cada instancia, entre sus elementos del mismo nivel en el árbol de relaciones de incrustación.  
  
 En el archivo de modelo serializado, el moniker completo de un elemento es una ruta desde la raíz del modelo hacia abajo en el árbol de relaciones de incrustación, y cita la clave de moniker en cada punto. Por ejemplo, InPorts se incrustan en Components que, a su vez, se incrustan en la raíz del modelo. Por lo tanto, un moniker válido es:  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 Puede establecer el **IsMonikerQualifier** para una propiedad de cadena de atributo y ofrecen una opción adicional para construir el nombre completo de un elemento. Por ejemplo, en el archivo DslDefinition.dsl **Namespace** es un calificador de moniker.  
  
### <a name="xmlrelationshipdata"></a>XmlRelationshipData  
 Dentro de un archivo de modelo serializado, los vínculos (tanto de relaciones de incrustación como de referencia) se representan mediante nodos secundarios del extremo de origen de la relación. En el caso de las relaciones de incrustación, el nodo secundario contiene un subárbol. En las relaciones de referencia, el nodo secundario contiene un moniker que hace referencia a otra parte del árbol.  
  
 El **XmlRelationshipData** atributo en un **XmlClassData** atributo define exactamente cómo se anidan los nodos secundarios dentro del elemento de origen. Todas las relaciones que sean un origen en la clase de dominio tienen una **XmlRelationshipData** atributo.  
  
 El **DomainRelationshipMoniker** atributo identifica una de las relaciones con origen en la clase.  
  
 El **RoleElementName** atributo proporciona el nombre de etiqueta XML que contiene el nodo secundario en los datos serializados.  
  
 Por ejemplo, el archivo DslDefinition.dsl contiene:  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 Por lo tanto, el archivo serializado contiene:  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 Si el **UseFullForm** atributo está establecido en true, se introduce una capa adicional de anidamiento. Este nivel representa la propia relación. El atributo se debe establecer en True si la relación tiene propiedades.  
  
```  
<XmlClassData ElementName="outPort">  
   <DomainClassMoniker Name="OutPort" />  
   <ElementData>  
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">  
       <DomainRelationshipMoniker Name="Connection" />  
     </XmlRelationshipData>  
   </ElementData>  
 </XmlClassData>  
```  
  
 El archivo serializado contiene:  
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 (La relación de conexión tiene su propios datos de clase XML, que proporcionan los nombres de elementos y atributos).  
  
 Si el **OmitElement** está establecido en true, la relación se omite el nombre de rol, que abrevia el archivo serializado y no provoca ambigüedades si las dos clases tienen no más de una relación. Por ejemplo:  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### <a name="serialization-of-a-domain-specific-language-definition"></a>Serialización de una definición de lenguaje específico de dominio  
 El archivo DslDefinition.dsl es un archivo serializado conforme a la definición de lenguaje específico de dominio. Los siguientes son algunos ejemplos de definiciones de serialización XML:  
  
-   **DSL** es el nodo RootClass y la clase del diagrama. DomainClass, DomainRelationship y otros elementos están incrustados en `Dsl`.  
  
-   **Las clases** es el **RoleElementName** de la relación entre los lenguajes específicos de dominio y DomainClass.  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
-   El **XmlSerializationBehavior** atributo está incrustado en el `Dsl` atributo, pero el **OmitElement** se ha establecido el atributo en la relación de incrustación. Por lo tanto, no interviene ningún atributo `RoleElementName`. Por el contrario, un **ClassData** atributo es el `RoleElementName` atributo de la relación de incrustación entre un **XmlSerializationBehavior** atributo y un **XmlClassData** atributo.  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
-   ConnectorHasDecorators es la relación de incrustación entre `Connector` y `Decorator`. `UseFullForm` se ha establecido de manera que el nombre de la relación aparezca con su lista de propiedades para cada vínculo desde el objeto Connector. Sin embargo, `OmitElement` también se ha establecido para ningún `RoleElementName` contenga varios vínculos que están incrustados dentro de `Connector`:  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## <a name="shapes-and-connectors"></a>Formas y conectores  
 Las definiciones de formas y conectores heredan los atributos y nodos secundarios de las clases de dominio, además de lo siguiente:  
  
-   Atributos `Color` y `Line``Style`.  
  
-   **ExposesFillColorAsProperty** y varios atributos similares. Estos atributos booleanos hacen que la propiedad correspondiente sea variable para el usuario. Por lo general, cuando un usuario del lenguaje hace clic en una forma del diagrama, las propiedades que aparecen en la **propiedades** ventana son las de la instancia de la clase de dominio al que está asignada la forma. Si `ExposesFillColorAsProperty` se establece en True, también se muestra una propiedad de la propia forma.  
  
-   **ShapeHasDecorators**. Se crea una instancia de este atributo para cada texto, icono o elemento Decorator de expansión/contracción. (En el archivo DslDefinition.dsl, `ShapeHasDecorators` es una relación con `UseFullForm` establecido en True).  
  
## <a name="shape-maps"></a>Asignaciones de formas  
 Las asignaciones de formas determinan cómo se muestran en pantalla las instancias de una clase de dominio determinada, representadas por una forma. Las asignaciones de formas y conectores aparecen en la sección `Diagram` del archivo DslDefinition.dsl.  
  
 Al igual que en el ejemplo siguiente, los elementos `ShapeMap` tienen, como mínimo, el moniker de una clase de dominio, el moniker de una forma y un elemento `ParentElementPath`:  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 La función principal del elemento `ParentElementPath` es que la misma clase de objetos pueda aparecer como formas diferentes en contextos diferentes. Por ejemplo, si un `InPort` también se puede incrustar en un comentario, el `InPort` podría aparecer como una forma diferente con esa finalidad.  
  
 En segundo lugar, la ruta determina cómo se relaciona la forma con su primaria. Entre las formas de un archivo DslDefinition.dsl no se define ninguna estructura de incrustación. Debe inferir la estructura a partir de las asignaciones de formas. La forma primaria de una forma es aquélla que está asignada al elemento de dominio que la ruta del elemento primario identifica. En este caso, la ruta identifica el componente al que pertenece el `InPort`. En otra asignación de forma, la clase Component está asignada a ComponentShape. Por lo tanto, la nueva forma `InPort` se convierte en forma secundaria de la clase `ComponentShape` de su componente.  
  
 En cambio, si asoció la forma InPort al diagrama, la ruta del elemento primario tendría que realizar otro paso, al modelo de componentes, que se asigna al diagrama:  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 La raíz del modelo no tiene una asignación de formas. En su lugar, la raíz es referenciada directamente por el diagrama, que tiene un elemento `Class`:  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### <a name="decorator-maps"></a>Asignaciones de elementos Decorator  
 Una asignación de elemento Decorator asocia una propiedad de la clase asignada a un elemento Decorator en la forma. Si la propiedad es de un tipo booleano o enumerado, su valor puede determinar si el elemento Decorator es visible. Si el elemento Decorator es de texto, el valor de la propiedad puede aparecer y el usuario puede editarla.  
  
### <a name="compartment-shape-maps"></a>Asignaciones de formas de compartimiento  
 Las asignaciones de formas de compartimiento son subtipos de las asignaciones de formas.  
  
## <a name="connector-maps"></a>Asignaciones de conectores  
 La asignación de conector mínima hace referencia a un conector y a una relación:  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 Las asignaciones de conectores también pueden contener asignaciones de elementos Decorator.  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
