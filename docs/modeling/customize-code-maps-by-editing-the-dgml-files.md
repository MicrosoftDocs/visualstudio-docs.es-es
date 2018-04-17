---
title: Personalizar mapas de código mediante la edición de los archivos DGML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2a23bc9b82941fda5a771f49a2aaf5c944a210bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Personalizar mapas de código mediante la edición de los archivos DGML
Para personalizar un mapa de código, puede editar el archivo .dgml (Directed Graph Markup Language) del mapa. Por ejemplo, puede editar los elementos para especificar estilos personalizados, asignar propiedades y categorías a elementos de código y vínculos, o vincular documentos o direcciones URL a elementos de código o vínculos. Para obtener más información acerca de los elementos DGML, vea [referencia dirigido Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md).  
  
 Edite el archivo .dgml del mapa de código en un editor XML o de texto. Si la asignación es parte de la solución de Visual Studio, selecciónela en **el Explorador de soluciones**, abra el menú contextual y elija **abrir con**, **Editor XML (texto)**.  
  
> [!NOTE]
>  Para crear mapas de código, es necesario tener Visual Studio Enterprise. Cuando se edita el mapa de código en Visual Studio, los atributos y elementos de DGML que no se usan se eliminan al guardar el archivo .dgml. Visual Studio también crea automáticamente elementos de código cuando se agregan nuevos vínculos manualmente.  Al guardar el archivo .dgml, los atributos que agregara a un elemento se podrían reorganizar en orden alfabético.  
  
##  <a name="OrganizeNodes"></a> Elementos de código de grupo  
 Puede agregar nuevos grupos o convertir los nodos existentes en un grupo.  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Para convertir un elemento de código en un grupo, busque el elemento `<Node/>` de ese elemento de código.  
  
     \- o -  
  
     Para agregar un grupo nuevo, busque la sección `<Nodes>`. Agregue un nuevo elemento `<Node/>`.  
  
3.  En el elemento `<Node/>`, agregue un atributo `Group` para especificar si el grupo aparece contraído o expandido. Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyFirstGroup" Group="Expanded" />  
       <Node Id="MySecondGroup" Group="Collapsed" />  
    </Nodes>  
    ```  
  
4.  En la sección `<Links>`, asegúrese de que existe un elemento `<Link/>` con los atributos siguientes para cada relación entre un elemento de código de grupo y sus elementos de código secundarios:  
  
    -   Un atributo `Source` que especifica el elemento de código de grupo  
  
    -   Un atributo `Target` que especifica el elemento de código secundario  
  
    -   Un atributo `Category` que especifica una relación `Contains` entre el elemento de código de grupo y su elemento de código secundario  
  
     Por ejemplo:  
  
    ```xml  
    <Links>  
       <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />  
       <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />  
       <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />  
       <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />  
    </Links>  
    ```  
  
     Para obtener más información sobre la `Category` de atributo, vea [asignar categorías a los vínculos y elementos de código](#AssignCategories).  
  
##  <a name="ChangeGraphStyle"></a> Cambiar el estilo del mapa  
 Si desea cambiar el color de fondo y el color de borde del gráfico, edite el archivo .dgml del mapa. Para cambiar el estilo de vínculos y elementos de código, vea [cambiar el estilo de vínculos y elementos de código](#Highlight).  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  En el elemento `<DirectedGraph>`, agregue cualquiera de los siguientes atributos para cambiar el estilo:  
  
     Color de fondo  
  
    ```xml  
    Background="ColorNameOrHexadecimalValue"  
    ```  
  
     Color del borde  
  
    ```xml  
    Stroke="StrokeValue"  
    ```  
  
     Por ejemplo:  
  
    ```xml  
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >  
       ...  
       ...  
    </DirectedGraph>  
    ```  
  
##  <a name="Highlight"></a> Cambiar el estilo de vínculos y elementos de código  
  
###  <a name="CreateCustomStyles"></a>   
 Puede aplicar estilos personalizados a los siguientes elementos de código:  
  
-   Elementos de código y vínculos únicos  
  
-   Grupos de elementos de código y vínculos  
  
-   Grupos de elementos de código y vínculos de acuerdo con ciertas condiciones  
  
> [!TIP]
>  Si tiene estilos que se repiten en varios elementos de código o vínculos, tiene la opción de aplicar una categoría a dichos elementos de código o vínculos y, después, aplicar un estilo a esa categoría. Para obtener más información, consulte [asignar categorías a elementos de código y vínculos](#AssignCategories) y [asignar propiedades a elementos de código y vínculos](#AssignProperties).  
  
##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Para aplicar un estilo personalizado a un único elemento de código  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Node/>` del elemento de código. Agregue cualquiera de estos atributos para personalizar su estilo:  
  
     Color de fondo  
  
    ```xml  
    Background="ColorNameOrHexadecimalValue"  
    ```  
  
     Esquema  
  
    ```xml  
    Stroke="ColorNameOrHexadecimalValue"  
    ```  
  
     Grosor del contorno  
  
    ```xml  
    StrokeThickness="StrokeValue"  
    ```  
  
     Color del texto  
  
    ```xml  
    Foreground="ColorNameOrHexadecimalValue"  
    ```  
  
     Icono  
  
    ```xml  
    Icon="IconFilePathLocation"  
    ```  
  
     Tamaño del texto  
  
    ```xml  
    FontSize="FontSizeValue"  
    ```  
  
     Tipo de texto  
  
    ```xml  
    FontFamily="FontFamilyName"  
    ```  
  
     Grosor del texto  
  
    ```xml  
    FontWeight="FontWeightValue"  
    ```  
  
     Estilo del texto  
  
    ```xml  
    FontStyle="FontStyleName"  
    ```  
  
     Por ejemplo, puede especificar `Italic` como estilo de texto.  
  
     Textura  
  
    ```xml  
    Style="Glass"  
    ```  
  
     - O  
  
    ```xml  
    Style="Plain"  
    ```  
  
     Forma  
  
     Para reemplazar la forma por un icono, establezca la propiedad `Shape` en `None` y establezca la propiedad `Icon` en la ruta de acceso con el archivo de icono.  
  
    ```xml  
    Shape="ShapeFilePathLocation"  
    ```  
  
     Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"  
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>  
    </Nodes>  
    ```  
  
##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Para aplicar un estilo personalizado a un único vínculo  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Link/>` que contiene el nombre del elemento de código de origen y el nombre del elemento de código de destino.  
  
3.  En el elemento `<Link/>`, agregue cualquiera de los siguientes atributos para personalizar el estilo:  
  
     Color de la punta de flecha y el esquema  
  
    ```xml  
    Stroke="ColorNameOrHexadecimalValue"  
    ```  
  
     Grosor del contorno  
  
    ```xml  
    StrokeThickness="StrokeValue"  
    ```  
  
     Estilo del contorno  
  
    ```xml  
    StrokeDashArray="StrokeArrayValues"  
    ```  
  
     Por ejemplo:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>  
    </Links>  
    ```  
  
##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Para aplicar estilos personalizados a un grupo de elementos de código o vínculos  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Si no existe ningún elemento `<Styles></Styles>`, agregue uno bajo el elemento `<DirectedGraph></DirectedGraph>`, detrás del elemento `<Links></Links>`.  
  
3.  En el elemento `<Styles></Styles>`, bajo el elemento `<Style/>`, especifique los atributos siguientes:  
  
    -   `TargetType="Node` &#124; `Link | Graph"`  
  
    -   `GroupLabel="` *NameInLegendBox* `"`  
  
    -   `ValueLabel="` *NameInStylePickerBox* `"`  
  
     Para aplicar un estilo personalizado a todos los tipos de destino, no use ninguna condición.  
  
##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Para aplicar un estilo condicional a los grupos de elementos de código o vínculos  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  En el elemento `<Style/>`, agregue un elemento `<Condition/>` que contenga un atributo `Expression` para especificar una expresión que devuelva un valor booleano.  
  
     Por ejemplo:  
  
    ```xml  
    <Condition Expression="MyCategory"/>  
    ```  
  
     - O  
  
    ```xml  
    <Condition Expression="MyCategory > 100"/>  
    ```  
  
     - O  
  
    ```xml  
    <Condition Expression="HasCategory('MyCategory')"/>  
    ```  
  
     Esta expresión usa la sintaxis de la forma de Backus-Naur (BNF) siguiente:  
  
     <Expression> ::= <BinaryExpression> &#124; <UnaryExpression> &#124; "("<Expression>")" &#124; <MemberBindings> &#124; <Literal> &#124; <Number>  
  
     <BinaryExpression> ::= <Expression> <Operator> <Expression>  
  
     <UnaryExpression> ::= "!" <Expression> &#124; "+" <Expression> &#124; "-" <Expression>  
  
     <Operator> :: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "o" &#124; "y" &#124; "+" &#124; "*" &#124; "/" &#124; "-"  
  
     <MemberBindings> ::= <MemberBindings> &#124; <MemberBinding> "." <MemberBinding>  
  
     <MemberBinding> ::= <MethodCall> &#124; <PropertyGet>  
  
     <MethodCall> ::= <Identifier> "(" <MethodArgs> ")"  
  
     <PropertyGet> :: = Identificador  
  
     <MethodArgs> ::= <Expression> &#124; <Expression> "," <MethodArgs> &#124; <empty>  
  
     <Identifier> ::= [^. ]*  
  
     <Literal> :: = literal de cadena único o entre comillas dobles  
  
     <Number> :: = cadena de dígitos con separador decimal opcional  
  
     Puede especificar varios `<Condition/>` elementos, que deben ser true para aplicar el estilo.  
  
3.  En la línea que sigue al elemento `<Condition/>`, agregue uno o varios elementos `<Setter/>` para especificar un atributo `Property` y un atributo `Value` fijo o un atributo `Expression` calculado para aplicarlo al mapa, a los elementos de código o a los vínculos que satisfacen la condición.  
  
     Por ejemplo:  
  
    ```xml  
    <Setter Property="BackGround" Value="Green"/>  
    ```  
  
 En este completo y sencillo ejemplo que se mostramos aquí, la condición especifica que un elemento de código debe aparecer en verde o en rojo en función de si su categoría `Passed` está establecida en `True` o `False`:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
   <Nodes>  
      <Node Id="MyFirstNode" Passed="True" />  
      <Node Id="MySecondNode" Passed="False" />  
   </Nodes>  
   <Links>  
   </Links>  
   <Styles>  
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">  
         <Condition Expression="Passed='True'"/>  
         <Setter Property="Background" Value="Green"/>  
      </Style>  
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">  
         <Condition Expression="Passed='False'"/>  
         <Setter Property="Background" Value="Red"/>  
      </Style>  
   </Styles>  
</DirectedGraph>  
```  
  
 En la tabla siguiente se incluyen algunas condiciones de ejemplo que puede usar:  
  
 Establecer el tamaño de fuente como una función del número de líneas de código, lo que también modificará el tamaño del elemento de código. En este ejemplo se usa una única expresión condicional para establecer varias propiedades: `FontSize` y `FontFamily`.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Class1" LinesOfCode ="200" />  
   <Node Id="Class2" LinesOfCode ="1000" />  
   <Node Id="Class3" LinesOfCode ="20" />  
</Nodes>  
<Properties>  
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">  
      <Condition Expression="LinesOfCode > 0" />  
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />  
      <Setter Property="FontFamily" Value="Papyrus" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
 Establecer el color de fondo de un elemento de código en función de la propiedad `Coverage`. Los estilos se evalúan en el orden en que aparecen, al igual que en las instrucciones `if-else`.  
  
 En este ejemplo:  
  
1.  Si `Coverage` es > 80, la propiedad `Background` se establece en verde.  
  
2.  En cambio, si `Coverage` es > 50, la propiedad `Background` se establece en una sombra naranja en función del valor de la propiedad `Coverage`.  
  
3.  Por otro lado, la propiedad `Background` se establece en una sombra roja en función de la propiedad `Coverage`.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Class1" Coverage="58" />  
   <Node Id="Class2" Coverage="95" />  
   <Node Id="Class3" Coverage="32" />  
</Nodes>  
<Properties>  
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">  
      <Condition Expression="Coverage > 80" />  
      <Setter Property="Background" Value="Green" />  
   </Style>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">  
      <Condition Expression="Coverage > 50" />  
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />  
   </Style>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">  
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
 Establecer la propiedad `Shape` en `None` para que el icono reemplace a la sombra. Use la propiedad `Icon` para especificar la ubicación del icono.  
  
```xml  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Automation" Category="Test" Label="Automation" />  
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />  
</Nodes>  
<Categories>  
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />  
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />  
</Categories>  
<Properties>  
   <Property Id="Icon" DataType="System.String" />  
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />  
   <Property Id="Shape" DataType="System.String" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">  
      <Condition Expression="HasCategory('Group')" />  
      <Setter Property="Background" Value="#80008080" />  
   </Style>  
   <Style TargetType="Node">  
      <Setter Property="HorizontalAlignment" Value="Center" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
##  <a name="AssignProperties"></a> Asignar propiedades a los vínculos y elementos de código  
 Los elementos de código y los vínculos se pueden organizar asignándoles propiedades. Por ejemplo, puede seleccionar elementos de código que tengan propiedades concretas para que pueda agruparlos, cambiar su estilo u ocultarlos.  
  
#### <a name="to-assign-a-property-to-a-code-element"></a>Para asignar una propiedad a un elemento de código  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Node/>` de ese elemento de código. Especifique el nombre de la propiedad y su valor. Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" MyPropertyName="PropertyValue" />  
    </Nodes>  
    ```  
  
3.  Agregue un elemento `<Property/>` a la sección `<Properties>` para especificar atributos, como el nombre visible y el tipo de datos:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
#### <a name="to-assign-a-property-to-a-link"></a>Para asignar una propiedad a un vínculo  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Link/>` que contiene el nombre del elemento de código de origen y el nombre del elemento de código de destino.  
  
3.  En el elemento `<Node/>`, especifique el nombre de la propiedad y su valor. Por ejemplo:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />  
    </Links>  
    ```  
  
4.  Agregue un elemento `<Property/>` a la sección `<Properties>` para especificar atributos, como el nombre visible y el tipo de datos:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
##  <a name="AssignCategories"></a> Asignar categorías a los vínculos y elementos de código  
 Las siguientes secciones muestran cómo se pueden organizar los elementos de código mediante categorías y cómo se pueden crear categorías jerárquicas con las que podrá organizar los elementos de código y agregar atributos a categorías secundarias mediante herencia.  
  
#### <a name="to-assign-a-category-to-a-code-element"></a>Para asignar una categoría a un elemento de código  
  
-   Abra el archivo .dgml en un editor XML o de texto.  
  
-   Busque el elemento `<Node/>` correspondiente al elemento de código que quiera.  
  
-   En el elemento `<Node/>`, agregue un atributo `Category` para especificar el nombre de la categoría. Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Category="MyCategory" />  
    </Nodes>  
    ```  
  
     Agregue un elemento `<Category/>` a la sección `<Categories>` de modo que pueda usar el atributo `Label` con el fin de especificar el texto visualizado de esa categoría:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-assign-a-category-to-a-link"></a>Para asignar una categoría a un vínculo  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Link/>` que contiene el nombre del elemento de código de origen y el nombre del elemento de código de destino.  
  
3.  En el elemento `<Link/>`, agregue un atributo `Category` para especificar el nombre de la categoría. Por ejemplo:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"  
    </Links>  
    ```  
  
4.  Agregue un elemento `<Category/>` a la sección `<Categories>` de modo que pueda usar el atributo `Label` con el fin de especificar el texto visualizado de esa categoría:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-create-hierarchical-categories"></a>Para crear categorías jerárquicas  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Agregue un elemento `<Category/>` de la categoría primaria y, a continuación, agregue el atributo `BasedOn` al elemento `<Category/>` de la categoría secundaria.  
  
     Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />  
       <Node Id="MySecondNode" Label="My Second Node" />  
    </Nodes>  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" />  
    </Links>  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>  
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>  
    </Categories>  
    ```  
  
     En este ejemplo, el fondo de `MyFirstNode` es verde porque su atributo `Category` hereda el atributo `Background` de `MyParentCategory`.  
  
##  <a name="AddReferences"></a> Vincular documentos o las direcciones URL para vínculos y elementos de código  
 Si desea vincular documentos o direcciones URL a elementos de código o vínculos, edite el archivo .dgml del mapa y agregue un atributo `Reference` al elemento `<Node/>` —para elementos de código— o el elemento `<Link/>` —para un vínculo—. Después, puede abrir y ver ese contenido del elemento de código o vínculo. El atributo `Reference` especifica la ruta de acceso del contenido. Puede tratarse de una ruta de acceso absoluta o de una ruta de acceso relativa a la ubicación del archivo .dgml.  
  
> [!CAUTION]
>  Si usa rutas de acceso relativas y el archivo .dgml se mueve a otra ubicación, esas rutas ya no se resolverán. Al intentar abrir y ver el contenido vinculado, se producirá un error que indica que el contenido no se puede ver.  
  
 Por ejemplo, puede que quiera vincular estos elementos de código:  
  
-   Para describir los cambios de una clase, puede vincular la dirección URL de un elemento de código de trabajo, documento u otro archivo .dgml al elemento de código de una clase.  
  
-   Puede vincular un diagrama de dependencia a un elemento de código de grupo que representa una capa en la arquitectura lógica del software.  
  
-   Para mostrar más información sobre un componente que expone una interfaz, puede vincular un diagrama de componentes al elemento de código de esa interfaz.  
  
-   Vincular un elemento de código en un elemento de trabajo de Team Foundation Server o error u otra información relacionada con el elemento de código.  
  
#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Para vincular un documento o una dirección URL a un elemento de código  
  
1.  Abra el archivo .dgml en un editor XML o de texto.  
  
2.  Busque el elemento `<Node/>` correspondiente al elemento de código que quiera.  
  
3.  Realice una de las tareas de la tabla siguiente:  
  
     Un elemento de código único  
  
    -   En el elemento `<Node/>` o `<Link/>`, agregue un atributo `Reference` para especificar la ubicación del elemento de código.  
  
        > [!NOTE]
        >  Solo puede tener un atributo `Reference` por cada elemento.  
  
     Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Reference="MyDocument.txt" />  
    </Nodes>  
    <Properties>  
       <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
    </Properties>  
    ```  
  
     Varios elementos de código  
  
    1.  En el elemento `<Node/>` o `<Link/>`, agregue un nuevo atributo para especificar la ubicación de cada referencia.  
  
    2.  En la sección `<Properties>`:  
  
        1.  Agregue un elemento `<Property/>` para cada nuevo tipo de referencia.  
  
        2.  Establezca al atributo `Id` en el nombre del nuevo atributo de referencia.  
  
        3.  Agregar el `IsReference` atributo y establézcalo en `True` para que la referencia aparezca en el elemento de código **ir a referencia** menú contextual.  
  
        4.  Use la `Label` atributo para especificar el texto mostrado en el elemento de código **ir a referencia** menú contextual.  
  
     Por ejemplo:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>  
    </Nodes>  
    <Properties>  
       <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />  
       <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />  
    </Properties>  
    ```  
  
     En el mapa, el nombre del elemento de código aparece subrayado. Cuando se abre el menú contextual para el elemento de código o en el vínculo, verá un **ir a referencia** menú contextual que contiene los elementos de código vinculadas para elegir.  
  
4.  Use el atributo `ReferenceTemplate` para especificar una cadena común, como una dirección URL, que se use en varias referencias en lugar de repetir esa cadena en la referencia.  
  
     El atributo `ReferenceTemplate` especifica un marcador de posición para el valor de la referencia. En el ejemplo siguiente, el marcador de posición `{0}` del atributo `ReferenceTemplate` se reemplazará por los valores de los atributos `MyFirstReference` y `MySecondReference` en el elemento `<Node/>` para generar una ruta de acceso completa:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>  
       <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>  
    </Nodes>  
    <Properties>  
       <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>  
       <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>  
    </Properties>  
    ```  
  
5.  Para ver el elemento o elementos de código a los que se hace referencia en el mapa, abra el menú contextual del elemento de código o el vínculo. Elija **ir a referencia** y, a continuación, el elemento de código.  
  
## <a name="see-also"></a>Vea también  
 [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)   
 [Referencia de Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
