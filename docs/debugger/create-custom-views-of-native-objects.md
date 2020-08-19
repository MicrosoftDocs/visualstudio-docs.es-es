---
title: Creación de vistas personalizadas de objetos de C++
description: Use el marco Natvis para personalizar la forma en la que Visual Studio muestra los tipos nativos en el depurador
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 37bfd1ab57fd0e37f32a55d5bfc3787cb0c0cbd2
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248055"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Creación de vistas personalizadas de objetos C++ en el depurador mediante el marco Natvis

El marco *Natvis* de Visual Studio personaliza la forma en la que se muestran los tipos nativos en las ventanas de variables del depurador, como las ventanas **Locales** e **Inspección**, y en **Información sobre datos**. Las visualizaciones de Natvis pueden ayudar a que los tipos que cree sean más visibles durante la depuración.

Natvis sustituye el archivo *autoexp.dat* usado en versiones anteriores de Visual  Studio por una sintaxis XML, mejores diagnósticos, control de versiones y compatibilidad con varios archivos.

> [!NOTE]
> Las personalizaciones de Natvis funcionan con clases y estructuras, pero no con definiciones de tipo.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualizaciones de Natvis

Puede usar el marco Natvis para crear reglas de visualización para los tipos creados, de forma que los desarrolladores puedan verlos más fácilmente durante la depuración.

Por ejemplo, en la ilustración siguiente, se muestra una variable de tipo [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) en una ventana de depurador sin aplicarse ninguna visualización personalizada.

![Visualización predeterminada de TextBox](../debugger/media/dbg_natvis_textbox_default.png "Visualización predeterminada de TextBox")

La fila resaltada muestra la propiedad `Text` de la clase `TextBox` . La compleja jerarquía de clases dificulta la búsqueda de esta propiedad. Además, el depurador no sabe cómo interpretar el tipo de cadena personalizada, por lo que usted no podrá ver la cadena incluida en el cuadro de texto.

El mismo `TextBox` parece mucho más sencillo en la ventana de variables cuando se aplican reglas de visualizador personalizadas de Natvis. Los miembros importantes de la clase se muestran juntos y el depurador muestra el valor de cadena subyacente del tipo de cadena personalizado.

![Datos de TextBox que usan visualizador](../debugger/media/dbg_natvis_textbox_visualizer.png "Datos de TextBox que usan visualizador")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Uso de archivos .natvis en proyectos de C++

Natvis usa archivos *.natvis* para especificar las reglas de visualización. Un archivo *.natvis* es un archivo XML con la extensión *.natvis*. El esquema de Natvis se define en *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

La estructura básica de un archivo *.natvis* está formada por uno o más elementos `Type`, que representan entradas de visualización. El nombre completo de cada elemento `Type` se especifica en su atributo `Name`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio proporciona algunos archivos *.natvis* en la carpeta *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*. Estos archivos tienen reglas de visualización para muchos tipos comunes y pueden servir como ejemplo al escribir visualizaciones para nuevos tipos.

### <a name="add-a-natvis-file-to-a-c-project"></a>Agregar un archivo .natvis a un proyecto de C++

Puede agregar un archivo *.natvis* a cualquier proyecto de C++.

**Para agregar un nuevo archivo *.natvis*:**

1. Seleccione el nodo de proyecto de C++ en el **Explorador de soluciones** y seleccione **Proyecto** > **Agregar nuevo elemento** o haga clic con el botón secundario en el proyecto y seleccione **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Visual C++**  > **Utilidad** > **Archivo de visualización del depurador (.natvis)** .

1. Asigne el nombre al archivo y seleccione **Agregar**.

   El nuevo archivo se agrega al **Explorador de soluciones** y se abre en el panel de documentos de Visual Studio.

El depurador de Visual Studio carga automáticamente los archivos *.natvis* en los proyectos de C++ y, de forma predeterminada, también los incluye en el archivo *.pdb* cuando el proyecto se compila. Si depura la aplicación de compilación, el depurador carga el archivo *.natvis* desde el archivo *.pdb* aunque no tenga el proyecto abierto. Si no quiere que el archivo *.natvis* se incluya en el archivo *.pdb*, puede excluirlo del archivo *.pdb* compilado.

**Para excluir un archivo *.natvis* de uno *.pdb*:**

1. Seleccione el archivo *.natvis* en el **Explorador de soluciones** y seleccione el icono **Propiedades** o haga clic con el botón secundario en el archivo y seleccione **Propiedades**.

1. Despliegue la flecha situada junto a **Excluir de la compilación** y seleccione **Sí**. Después, seleccione **Aceptar**.

>[!NOTE]
>Para los proyectos ejecutables de depuración, use los elementos de la solución para agregar los archivos *.natvis* que no estén en ningún archivo *.pdb*, ya que no hay ningún proyecto de C++ disponible.

>[!NOTE]
>Los filtros de Natvis que se cargan desde un archivo *.pdb* solo se aplican a los tipos de los módulos a los que hace referencia el archivo *.pdb*. Por ejemplo, si *Module1.pdb* define una entrada de Natvis para un tipo denominado `Test`, solo se aplica a la clase `Test` de *Module1.dll*. Si hay otro módulo que también define una clase denominada `Test`, no se le aplica la entrada de Natvis *Module1.pdb*.

**Para instalar y registrar un archivo *.natvis* mediante un paquete VSIX:**

Un paquete VSIX puede instalar y registrar archivos *.natvis*. Independientemente de dónde se instalen, todos los archivos *.natvis* registrados se seleccionan automáticamente durante la depuración.

1. Incluya el archivo *.natvis* en el paquete VSIX. Por ejemplo, para el siguiente archivo del proyecto:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registre el archivo *.natvis* en el archivo *source.extension.vsixmanifest*:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Ubicaciones del archivo Natvis

Puede agregar archivos *.natvis* al directorio del usuario o a un directorio del sistema si quiere que se apliquen a varios proyectos.

Los archivos *.natvis* se evalúan en el orden siguiente:

1. Los archivos *.natvis* insertados en un archivo *.pdb* que esté depurando, a menos que exista un archivo con el mismo nombre en un proyecto cargado.

2. Los archivos *.natvis* que se encuentren en un proyecto de C++ cargado o en una solución de nivel superior. En este grupo se incluyen todos los proyectos de C++ cargados, incluidas las bibliotecas de clase, pero no los proyectos en otros lenguajes.

3. Los archivos *.natvis* instalados y registrados mediante un paquete VSIX.

::: moniker range="vs-2017"

4. El directorio de Natvis específico del usuario (por ejemplo, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. El directorio de Natvis específico del usuario ( *%USERPROFILE%\My Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. El directorio de Natvis de todo el sistema ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Este directorio contiene los archivos *.natvis* instalados con Visual Studio. Si tiene permisos de administrador, puede agregar archivos a este directorio.

## <a name="modify-natvis-files-while-debugging"></a>Modificación de archivos .natvis durante la depuración

Puede modificar un archivo *.natvis* en el IDE mientras se depura su proyecto. Abra el archivo en la misma instancia de Visual Studio con la que está efectuando la depuración, modifíquelo y guárdelo. Cuando haya guardado el archivo, las ventanas **Inspección** y **Locales** se actualizan para reflejar el cambio.

También puede agregar o eliminar archivos *.natvis* en una solución que esté depurando, y Visual Studio agregará o quitará las visualizaciones pertinentes.

Durante la depuración, no puede actualizar archivos de *.natvis* insertados en archivos *.pdb*.

Si modifica el archivo *.natvis* fuera de Visual Studio, los cambios no surten efecto automáticamente. Para actualizar las ventanas del depurador, puede reevaluar el comando **.natvisreload** en la ventana **Inmediato**. Después, los cambios surtirán efecto sin tener que reiniciar la sesión de depuración.

Además, puede usar el comando **.natvisreload** para actualizar el archivo *.natvis* a una versión más reciente. Por ejemplo, se puede insertar el archivo *.natvis* en el repositorio del control de código fuente y puede recopilar los cambios recientes hechos por otra persona.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Expresiones y formato
Las visualizaciones de Natvis usan expresiones de C++ para especificar los elementos de datos que se deben mostrar. Además de las mejoras y las limitaciones de las expresiones de C++ del depurador, que se describen en el [operador de contexto (C++)](../debugger/context-operator-cpp.md), tenga en cuenta lo siguiente:

- Las expresiones Natvis se evalúan en el contexto del objeto que se visualiza, no el marco de pila actual. Por ejemplo, `x` en una expresión Natvis hace referencia al campo denominado **x** del objeto visualizado, no a una variable local denominada **x** de la función actual. En las expresiones Natvis no se puede acceder a variables locales, aunque sí a variables globales.

- Las expresiones Natvis no admiten la evaluación o los efectos secundarios de las funciones. Esto significa que se omiten las llamadas de función y los operadores de asignación. Puesto que las [funciones intrínsecas del depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) no tienen efectos secundarios, pueden llamarse libremente desde cualquier expresión Natvis aunque no se permitan otras llamadas de función.

- Para controlar cómo se muestra una expresión, puede usar cualquiera de los especificadores de formatos que se describen en [Especificadores de formato en C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Los especificadores de formato se omiten cuando Natvis usa internamente la entrada, como la expresión `Size` en una [expansión ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Vistas de Natvis

Puede definir diferentes vistas de Natvis para mostrar los tipos de diferentes formas. Por ejemplo, a continuación se muestra una visualización de `std::vector`, que define una vista simplificada denominada `simple`. Los elementos `DisplayString` y `ArrayItems` se muestran en la vista predeterminada y en la vista `simple`, mientras que los elementos `[size]` y `[capacity]` no se muestran en la vista `simple`.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

En la ventana **Inspección**, use el especificador de formato **,view** para especificar una vista distinta. La vista simple se muestra como **vec,view(simple)** :

![Ventana Inspección con vista sencilla](../debugger/media/watch-simpleview.png "Ventana Inspección con vista sencilla")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Errores de Natvis

Cuando el depurador detecta errores en una entrada de visualización, los ignora. Muestra el tipo en su formato sin procesar o elige otra visualización adecuada. Puede usar el diagnóstico de Natvis para comprender por qué el depurador ha ignorado una entrada de visualización y para ver los errores de análisis y sintaxis subyacentes.

**Para activar el diagnóstico de Natvis:**

- En **Herramientas** > **Opciones** (o **Depurar** > **Opciones**) > **Depuración** > **Ventana de salida**, establezca **Mensajes de diagnóstico de Natvis (solo para C++)** en **Error**, **Advertencia** o **Detallado** y después seleccione **Aceptar**.

Los errores se muestran en la ventana **Resultados**.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Referencia de la sintaxis de Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
El elemento `AutoVisualizer` es el nodo raíz del archivo *.natvis* y contiene el atributo `xmlns:` del espacio de nombres.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

El elemento `AutoVisualizer` puede tener elementos secundarios [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer) y [CustomVisualizer](#BKMK_CustomVisualizer).

### <a name="type-element"></a><a name="BKMK_Type"></a> Elemento Type

Un elemento `Type` básico es similar al de este ejemplo:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 El elemento `Type` especifica:

1. Para qué tipo de visualización debe usarse (el atributo `Name`).

2. Cómo debe ser el valor de un objeto de ese tipo (el elemento `DisplayString` ).

3. Cómo deben ser los miembros del tipo cuando el usuario expande el tipo en una ventana de variables (el nodo `Expand`).

#### <a name="templated-classes"></a>Clases con plantilla
El atributo `Name` del elemento `Type` acepta un asterisco `*` como carácter comodín que se puede usar para los nombres de clase con plantilla.

En el ejemplo siguiente, se usa la misma visualización, independientemente de que el objeto sea un elemento `CAtlArray<int>` o un elemento `CAtlArray<float>`. Si hay una entrada específica de visualización para `CAtlArray<float>`, esta tendrá prioridad sobre la genérica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Puede consultar los parámetros de plantilla en la entrada de visualización mediante macros $T1, $T2, etc. Para buscar ejemplos de estas macros, vea los archivos *.natvis* incluidos con Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Coincidencia de tipos del visualizador
Si no se puede validar una entrada de visualización, se usará la siguiente visualización disponible.

#### <a name="inheritable-attribute"></a>Atributo heredable
El atributo opcional `Inheritable` especifica si una visualización se aplica únicamente a un tipo base o a un tipo base y a todos los tipos derivados. El valor predeterminado de `Inheritable` es `true`.

En el ejemplo siguiente, la visualización solo se aplica al tipo `BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atributo de prioridad

El atributo opcional `Priority` especifica el orden en el que se usan las definiciones alternativas si no se puede analizar una definición. Los valores posibles de `Priority` son `Low`, `MediumLow`,`Medium`, `MediumHigh` y `High`. El valor predeterminado es `Medium`. El atributo `Priority` solo distingue entre prioridades dentro del mismo archivo *.natvis*.

En el siguiente ejemplo se analiza primero la entrada que coincide con STL 2015. Si no se puede analizar, usa la entrada alternativa para la versión 2013 de STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Atributo opcional
Puede colocar un atributo `Optional` en cualquier nodo. Si una subexpresión dentro de un nodo opcional no se puede analizar, el depurador omite ese nodo, pero aplica las demás reglas `Type`. En el siguiente tipo, `[State]` no es opcional, pero `[Exception]` sí lo es.  Si `MyNamespace::MyClass` tiene un campo denominado _`M_exceptionHolder`, aparecen los nodos `[State]` y `[Exception]`, pero si no hay ningún campo `_M_exceptionHolder`, solo aparece el nodo `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atributo Condition

El atributo opcional `Condition` está disponible para muchos elementos de visualización y especifica cuándo se debe usar una regla de visualización. Si la expresión del atributo Condition se resuelve como `false`, no se aplicará la regla de visualización. Si se evalúa como `true` o no hay ningún atributo `Condition`, se aplica la visualización. Puede usar este atributo para la lógica if-else en las entradas de visualización.

Por ejemplo, la siguiente visualización tiene dos elementos `DisplayString` para un tipo de puntero inteligente. Cuando el miembro `_Myptr` está vacío, la condición del primer elemento `DisplayString` se resuelve en `true`, de manera que se muestra dicho formulario. Cuando el miembro `_Myptr` no está vacío, la condición se evalúa como `false` y se muestra el segundo elemento `DisplayString`.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Atributos IncludeView y ExcludeView

Los atributos `IncludeView` y `ExcludeView` especifican los elementos que se van a mostrar o no en vistas específicas. Por ejemplo, en la siguiente especificación de `std::vector` de Natvis, la vista `simple` no muestra los elementos `[size]` y `[capacity]`.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Puede usar los atributos `IncludeView` y `ExcludeView` en los tipos y en los miembros individuales.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Elemento Version
El elemento `Version` limita una entrada de visualización a un módulo y versión específicos. El elemento `Version` ayuda a evitar conflictos de nombres, reduce las discrepancias involuntarias y permite diferentes visualizaciones para distintas versiones de tipo.

Si un archivo de encabezado común usado por módulos diferentes define un tipo, la visualización versionada solo aparece cuando el tipo está en la versión de módulo especificada.

En el ejemplo siguiente, la visualización solo se aplica al tipo `DirectUI::Border` incluido en el objeto `Windows.UI.Xaml.dll` de las versiones 1.0 a 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

No necesita ninguno de los dos atributos `Min` y `Max`, ya que son opcionales. No se admite el uso de caracteres comodín.

El atributo `Name` tiene el formato *filename.ext*, como *hello.exe* o *some.dll*. No se permite el uso de nombres de ruta.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> Elemento DisplayString
El elemento `DisplayString` especifica una cadena que se mostrará como el valor de una variable. Acepta cadenas arbitrarias mezcladas con expresiones. Todos los datos encerrados entre llaves se interpretan como una expresión. Por ejemplo, la siguiente entrada `DisplayString`:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa que las variables de tipo `CPoint` se muestran como en esta ilustración:

 ![Uso de un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Uso de un elemento DisplayString")

En la expresión `DisplayString`, `x` e `y`, que son miembros de `CPoint`, se encuentran dentro de llaves, por lo que se evalúan sus valores. En el ejemplo también se muestra cómo se puede omitir una llave con llaves dobles (`{{` o `}}`).

> [!NOTE]
> El elemento `DisplayString` es el único que acepta cadenas arbitrarias y la sintaxis de llaves. Todos los demás elementos de visualización solo aceptan expresiones que el depurador puede evaluar.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> Elemento StringView

El elemento `StringView` define un valor que el depurador puede enviar al visualizador de texto integrado. Por ejemplo, pongamos que tenemos la visualización siguiente para el tipo `ATL::CStringT`:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

El objeto `CStringT` se muestra en una ventana de variables como en este ejemplo:

![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Elemento DisplayString CStringT")

Al agregar un elemento `StringView`, se indica al depurador que puede mostrar el valor como una visualización de texto.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante la depuración, puede seleccionar el icono de lupa situado junto a la variable y después seleccionar **Visualizador de texto** para mostrar la cadena a la que dirige **m_pszData**.

 ![Datos CStringT con visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Datos CStringT con visualizador StringView")

La expresión `{m_pszData,su}` incluye un especificador de formato de C++, **su**, para mostrar el valor como cadena Unicode. Para obtener más información, vea [Especificadores de formato en C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Elemento Expand

El nodo opcional `Expand` personaliza los elementos secundarios de un tipo visualizado al expandir el tipo en una ventana de variables. El nodo `Expand` acepta una lista de nodos secundarios que definen los elementos secundarios.

- Si no se especifica ningún nodo `Expand` en una entrada de visualización, los elementos secundarios usarán las reglas predeterminadas de expansión.

- Si se especifica un nodo `Expand` sin nodos secundarios, el tipo no se podrá expandir en las ventanas del depurador.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Expansión de Item

 El elemento `Item` es el elemento más básico y común de un nodo `Expand`. `Item` define un único elemento secundario. Por ejemplo, una clase `CRect` con los campos `top`, `left`, `right` y `bottom` tiene la siguiente entrada de visualización:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

En la ventana del depurador, el tipo `CRect` es similar al de este ejemplo:

![CRect con expansión de elementos Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con expansión de elementos Item")

El depurador evalúa las expresiones especificadas en los elementos `Width` y `Height`, y muestra los valores de la columna **Value** de la ventana variable.

El depurador crea automáticamente el nodo **[Raw View]** para cada expansión personalizada. En la captura de pantalla anterior, se muestra el nodo **[Raw View]** expandido para mostrar en qué medida la vista sin formato predeterminada del objeto difiere de la visualización de Natvis. La expansión predeterminada crea un subárbol para la clase base y muestra todos los miembros de datos de dicha clase como elementos secundarios.

> [!NOTE]
> Si la expresión del elemento Item apunta a un tipo complejo, el nodo **Item** se puede expandir.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Utilice el nodo `ArrayItems` para que el depurador de Visual Studio interprete el tipo como matriz y muestre sus elementos individuales. La visualización de `std::vector` es un buen ejemplo:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` muestra los elementos individuales cuando se expanden en la ventana de variables:

![std::vector que usa la expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector que usa una expansión ArrayItems")

El nodo `ArrayItems` debe tener:

- Expresión `Size` (que debe evaluarse como entero) para que el depurador comprenda la longitud de la matriz.
- Una expresión `ValuePointer` que apunte al primer elemento (que debe ser un puntero de un tipo de elemento que no sea `void*`).

El valor predeterminado del límite inferior de la matriz es 0. Para invalidar el valor, use un elemento `LowerBound`. Los archivos *.natvis* incluidos en Visual Studio contienen ejemplos.

>[!NOTE]
>Puede usar el operador `[]`, por ejemplo `vector[i]`, con cualquier visualización de una matriz unidimensional que use `ArrayItems`, incluso si el mismo tipo no lo admite (por ejemplo, `CATLArray`).

También puede especificar matrices multidimensionales. En ese caso, el depurador necesita un poco más de información para mostrar correctamente los elementos secundarios:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` especifica si la matriz se ordena por fila principal o por columna principal.
- `Rank` especifica el rango de la matriz.
- El elemento `Size` acepta el parámetro `$i` implícito que sustituye al índice de dimensión para buscar la longitud de la matriz en esa dimensión. En el ejemplo anterior, la expresión `_M_extent.M_base[0]` debe proporcionar la longitud de la dimensión 0, `_M_extent._M_base[1]` la de la dimensión 1 y así sucesivamente.

Aquí se muestra cómo un objeto bidimensional `Concurrency::array` busca en la ventana del depurador:

![Matriz bidimensional con expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matriz bidimensional con expansión ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Expansión de IndexListItems

Puede usar la expansión `ArrayItems` solo si los elementos de matriz están dispuestos de forma contigua en la memoria. El depurador obtiene el elemento siguiente simplemente al incrementar el puntero. Si necesita manipular el índice al nodo de valor, use los nodos `IndexListItems`. Aquí tiene una visualización con un nodo `IndexListItems`:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

La única diferencia entre `ArrayItems` y `IndexListItems` es `ValueNode`, que espera la expresión completa para el elemento i<sup>th</sup> con el parámetro implícito `$i`.

>[!NOTE]
>Puede usar el operador `[]`, por ejemplo `vector[i]`, con cualquier visualización de matriz unidimensional que use `IndexListItems`, incluso si el mismo tipo no lo admite (por ejemplo, `CATLArray`).

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Expansión de LinkedListItems

Si el tipo visualizado representa una lista vinculada, el depurador puede mostrar sus elementos secundarios si se usa un nodo `LinkedListItems` . En la visualización siguiente para el tipo `CAtlList`, se utiliza `LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

El elemento `Size` hace referencia a la longitud de la lista. `HeadPointer` apunta al primer elemento, `NextPointer` hace referencia al elemento siguiente y `ValueNode` hace referencia al valor del elemento.

El depurador evalúa las expresiones `NextPointer` y `ValueNode` en el contexto del elemento del nodo `LinkedListItems`, no del tipo de lista primario. En el ejemplo anterior, `CAtlList` tiene una clase `CNode` (que se encuentra en `atlcoll.h`) que es un nodo de la lista vinculada. Los objetos `m_pNext` y `m_element` son campos de la clase `CNode` y no de la clase `CAtlList`.

Puede dejar `ValueNode` en blanco o usar `this` para hacer referencia al nodo `LinkedListItems`.

#### <a name="customlistitems-expansion"></a>Expansión CustomListItems

La expansión `CustomListItems` le permite escribir una lógica personalizada para recorrer una estructura de datos, como una tabla hash. Use `CustomListItems` para visualizar estructuras de datos que puedan usar expresiones de C++ para todo lo que tenga que evaluar, pero que no se ajuste lo suficiente al molde para `ArrayItems`, `IndexListItems` o `LinkedListItems`.

Puede usar `Exec` para ejecutar código dentro de una expansión `CustomListItems` mediante las variables y los objetos definidos en la expansión. Puede utilizar operadores lógicos, operadores aritméticos y operadores de asignación con `Exec`. No se puede usar `Exec` para evaluar funciones, salvo [funciones intrínsecas del depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) admitidas por el evaluador de expresiones de C++.

El visualizador siguiente para `CAtlMap` es un ejemplo excelente de los casos en los que `CustomListItems` es adecuado.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Expansión de TreeItems
 Si el tipo visualizado representa un árbol, el depurador puede recorrer el árbol y mostrar sus elementos secundarios utilizando un nodo `TreeItems` . A continuación se muestra la visualización del tipo `std::map` mediante un nodo `TreeItems`:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

La sintaxis es similar a la del nodo `LinkedListItems`. `LeftPointer`, `RightPointer` y `ValueNode` se evalúan en el contexto de la clase del nodo de árbol. Puede dejar `ValueNode` en blanco o usar `this` para hacer referencia al nodo `TreeItems`.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Expansión de ExpandedItem
 El elemento `ExpandedItem` genera una visualización secundaria agregada que muestra las propiedades de las clases base o los miembros de datos como si fueran elementos secundarios del tipo visualizado. El depurador evalúa la expresión especificada y anexa los nodos secundarios del resultado a la lista secundaria del tipo visualizado.

Por ejemplo, el tipo de puntero inteligente `auto_ptr<vector<int>>` suele mostrarse como:

 ![Expansión predeterminada auto&#95;ptr&#60;vector&#60;int&#62;&#62;](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Expansión predeterminada")

 Para ver los valores del vector, tiene que explorar en profundidad dos niveles en la ventana de variables, pasando por el miembro `_Myptr`. Al agregar un elemento `ExpandedItem`, puede eliminar la variable `_Myptr` de la jerarquía y ver directamente los elementos de vector:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Expansión ExpandedItem auto&#95;ptr&#60;vector&#60;int&#62;&#62;](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expansión de ExpandedItem")

En el ejemplo siguiente, se muestra cómo agregar propiedades a partir de la clase base en una clase derivada. Supongamos que la clase `CPanel` se deriva de `CFrameworkElement`. En lugar de repetir las propiedades procedentes de la clase base `CFrameworkElement`, la visualización del nodo `ExpandedItem` anexa esas propiedades a la lista secundaria de la clase `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Aquí es necesario usar el especificador de formato **nd** que desactiva la coincidencia de visualización para la clase derivada. De lo contrario, la expresión `*(CFrameworkElement*)this` hará que la visualización `CPanel` se vuelva a aplicar, porque las reglas de coincidencia de los tipos de visualización predeterminada la consideran la más adecuada. Use el especificador de formato **nd** para indicar al depurador que utilice la visualización de la clase base o la expansión predeterminada si la clase base no tiene ninguna visualización.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Expansión de elemento Synthetic
 En los casos donde el elemento `ExpandedItem` elimina las jerarquías para proporcionar una vista de datos más plana, el nodo `Synthetic` hace lo contrario. Permite crear un elemento secundario artificial que no sea el resultado de una expresión. El elemento artificial puede tener elementos secundarios propios. En el ejemplo siguiente, la visualización del tipo `Concurrency::array` usa un nodo `Synthetic` para mostrar un mensaje de diagnóstico al usuario:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency::Array con expansión de elementos Sythentic](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array con expansión de elementos Sythentic")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> Elemento HResult
 El elemento `HResult` permite personalizar la información que se muestra para un tipo de datos **HRESULT** en las ventanas del depurador. El elemento `HRValue` debe contener el valor de 32 bits de **HRESULT** que se debe personalizar. El elemento `HRDescription` contiene la información que se va a mostrar en la ventana del depurador.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> Elemento UIVisualizer
Un elemento `UIVisualizer` registra un complemento de visualizador gráfico en el depurador. Un visualizador gráfico crea un cuadro de diálogo u otra interfaz que muestra una variable o un objeto de una forma coherente con su tipo de datos. El complemento del visualizador se debe crear como [VSPackage](../extensibility/internals/vspackages.md) y tiene que exponer un servicio que el depurador pueda consumir. El archivo *.natvis* contiene información de registro del complemento, como su nombre, el GUID del servicio expuesto y los tipos que puede visualizar.

A continuación se muestra un ejemplo de un elemento UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- El par de atributos `ServiceId` - `Id` identifica un elemento `UIVisualizer`. `ServiceId` es el GUID del servicio que expone el paquete del visualizador. `Id` es un identificador único que diferencia los visualizadores cuando un servicio proporciona más de uno. En el ejemplo anterior, el mismo servicio del visualizador proporciona dos visualizadores.

- El atributo `MenuName` define un nombre de visualizador para mostrar en el menú desplegable situado junto al icono de lupa del depurador. Por ejemplo:

  ![Menú contextual de UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menú contextual de UIVisualizer")

Cada tipo definido en el archivo *.natvis* debe mostrar explícitamente los visualizadores de la interfaz de usuario que lo puedan mostrar. El depurador coincide con las referencias del visualizador de las entradas de tipo con los visualizadores registrados. Por ejemplo, la entrada de tipo siguiente para `std::vector` hace referencia al elemento `UIVisualizer` del ejemplo anterior.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Puede ver un ejemplo de `UIVisualizer` en la extensión [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) usada para ver los mapas de bits en memoria.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer` es un punto de extensibilidad que especifica una extensión VSIX que usted escribe para controlar las visualizaciones en el código de Visual Studio. Para más información sobre cómo escribir extensiones VSIX, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Escribir un visualizador personalizado comporta mucho más trabajo que escribir una definición XML de Natvis, pero no conlleva restricciones de compatibilidad con Natvis. Los visualizadores personalizados tienen acceso a todo el conjunto de API de extensibilidad del depurador, que pueden consultar y modificar el proceso de depuración o comunicarse con otras partes de Visual Studio.

 Puede usar los atributos `Condition`, `IncludeView` y `ExcludeView` en elementos `CustomVisualizer`.

## <a name="limitations"></a>Limitaciones

Las personalizaciones de Natvis funcionan con clases y estructuras, pero no con definiciones de tipo.

Natvis no admite visualizadores para tipos primitivos (por ejemplo, `int`, `bool`) ni para punteros a tipos primitivos. En este escenario, una opción es usar el [especificador de formato](../debugger/format-specifiers-in-cpp.md) apropiado para el caso de uso. Por ejemplo, si usa `double* mydoublearray` en el código, puede usar un especificador de formato de matriz en la ventana **Inspección** del depurador, como la expresión `mydoublearray, [100]`, que muestra los primeros 100 elementos.
