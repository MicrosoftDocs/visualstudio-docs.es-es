---
title: Creación de vistas personalizadas de objetos de C++
description: Usar el marco Natvis para personalizar la forma en que Visual Studio muestra los tipos nativos en el depurador
ms.date: 10/31/2018
ms.topic: conceptual
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
ms.openlocfilehash: 2dba61d53bdb0007eb2a4f0acff734613e320ab9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649646"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger"></a>Crear vistas personalizadas de C++ objetos en el depurador

Visual Studio *Natvis* framework personaliza la forma en que los tipos nativos aparecen en ventanas de variables del depurador, como la **variables locales** y **inspección** windows y en **DataTips**. Las visualizaciones de Natvis pueden ayudar a los tipos creados más visible durante la depuración.

Natvis sustituye el *autoexp.dat* archivo en versiones anteriores de Visual Studio con sintaxis XML, mejores diagnósticos, control de versiones y varios archivos de soporte técnico.

## <a name="BKMK_Why_create_visualizations_"></a>Visualizaciones de Natvis

Usar el marco Natvis para crear reglas de visualización para los tipos de que crear, de modo que los desarrolladores puedan verlas más fácilmente durante la depuración.

Por ejemplo, la siguiente ilustración muestra una variable de tipo [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) en una ventana del depurador sin aplicar ninguna visualización personalizada.

![Visualización predeterminada de TextBox](../debugger/media/dbg_natvis_textbox_default.png "visualización predeterminada de TextBox")

La fila resaltada muestra la propiedad `Text` de la clase `TextBox` . La jerarquía de clases complejas dificulta encontrar esta propiedad. El depurador no sabe cómo interpretar el tipo de cadena personalizado, por lo que no puede ver la cadena incluida en el cuadro de texto.

El mismo `TextBox` parece mucho más sencillo en la ventana de variables cuando se aplican las reglas de Natvis visualizador personalizado. Los miembros importantes de la clase aparecen juntos, y el depurador muestra el valor de cadena subyacente del tipo cadena personalizada.

![Datos de cuadro de texto mediante el visualizador](../debugger/media/dbg_natvis_textbox_visualizer.png "mediante el visualizador de datos de cuadro de texto")

##  <a name="BKMK_Using_Natvis_files"></a>Usar archivos .natvis en proyectos de C++

Natvis usa *.natvis* archivos para especificar las reglas de visualización. Un *.natvis* archivo es un archivo XML con un *.natvis* extensión. Se define el esquema de Natvis en *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

La estructura básica de un *.natvis* archivo consta de uno o más `Type` elementos que representan entradas de visualización. El nombre completo de cada `Type` elemento se especifica en su `Name` atributo.

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

Visual Studio proporciona algunos *.natvis* archivos en el *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* carpeta. Estos archivos tienen reglas de visualización para muchos tipos comunes y pueden servir como ejemplos para escribir visualizaciones para nuevos tipos.

### <a name="add-a-natvis-file-to-a-c-project"></a>Agregar un archivo .natvis a un proyecto de C++

Puede agregar un *.natvis* archivo a cualquier proyecto de C++.

**Para agregar un nuevo *.natvis* archivo:**

1. Seleccione el nodo de proyecto de C++ en **el Explorador de soluciones**y seleccione **proyecto** > **Agregar nuevo elemento**, o haga clic en el proyecto y seleccione **agregar**   >  **Nuevo elemento**.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Visual C++** > **utilidad** > **archivo de visualización del depurador (.natvis)**.

1. Nombre del archivo y seleccione **agregar**.

   El nuevo archivo se agrega a **el Explorador de soluciones**y se abre en el panel de documento de Visual Studio.

El depurador de Visual Studio carga *.natvis* archivos en proyectos de C++ automáticamente y de forma predeterminada, también incluye en el *.pdb* cuando se compila el proyecto de archivos. Si depura la aplicación integrada, el depurador carga el *.natvis* de archivos desde el *.pdb* archivo, incluso si no tiene abierto el proyecto. Si no desea la *.natvis* archivo incluido en el *.pdb*, puede excluirla de la compilación *.pdb* archivo.

**Para excluir un *.natvis* de archivos desde un *.pdb*:**

1. Seleccione el *.natvis* archivo **el Explorador de soluciones**y seleccione el **propiedades** icono, o haga clic en el archivo y seleccione **propiedades**.

1. La flecha desplegable junto a **excluir de la generación** y seleccione **Sí**y, a continuación, seleccione **Aceptar**.

>[!NOTE]
>Para depurar los proyectos ejecutables, utilice los elementos de la solución para agregar cualquier *.natvis* archivos que no están en el *.pdb*, ya que no hay ningún proyecto de C++.

>[!NOTE]
>Reglas de Natvis cargadas desde un *.pdb* solo se aplican a los tipos en los módulos que el *.pdb* hace referencia a. Por ejemplo, si *Module1.pdb* tiene una entrada Natvis para un tipo denominado `Test`, solo se aplica a la `Test` clase *Module1.dll*. Si hay otro módulo también define una clase denominada `Test`, *Module1.pdb* entrada Natvis no se aplica a él.

### <a name="BKMK_natvis_location"></a> Ubicaciones de los archivos Natvis

Puede agregar *.natvis* archivos al directorio del usuario o a un directorio del sistema, si desea aplicarlos a varios proyectos.

El *.natvis* archivos se evalúan en el orden siguiente:

1. Cualquier *.natvis* archivos que están incrustados en un *.pdb* depurar, a menos que exista un archivo del mismo nombre en el proyecto cargado.

2. Cualquier *.natvis* archivos que están en un proyecto de C++ cargado o una solución de nivel superior. Este grupo incluye cargados todos los proyectos de C++, incluidas las bibliotecas de clases, pero no los proyectos en otros idiomas.

::: moniker range="vs-2017"

3.  El directorio de Natvis específico del usuario (por ejemplo, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

3.  El directorio de Natvis específico del usuario (por ejemplo, *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

4.  El directorio de Natvis de todo el sistema (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Este directorio tiene el *.natvis* archivos que se instalan con Visual Studio. Si tiene permisos de administrador, puede agregar archivos a este directorio.

## <a name="modify-natvis-files-while-debugging"></a>Modificar archivos .natvis durante la depuración

Puede modificar un *.natvis* archivo en el IDE mientras se depura su proyecto. Abra el archivo en la misma instancia de Visual Studio está depurando con, modificarlo y guardarlo. Tan pronto como se guarda el archivo, el **inspección** y **variables locales** windows se actualizan para reflejar el cambio.

También puede agregar o eliminar *.natvis* archivos en una solución que se está depurando, y Visual Studio agrega o quita las visualizaciones pertinentes.

No puede actualizar *.natvis* archivos que se incrustan en *.pdb* archivos durante la depuración.

Si modifica el *.natvis* archivo fuera de Visual Studio, los cambios no surtirán efecto automáticamente. Para actualizar las ventanas del depurador, puede volver a evaluar el **.natvisreload** comando en el **inspección** ventana. A continuación, los cambios surten efecto sin tener que reiniciar la sesión de depuración.

Use también el **.natvisreload** comando para actualizar el *.natvis* archivo a una versión más reciente. Por ejemplo, el *.natvis* se puede comprobar el archivo de control de código fuente, y desea recoger los cambios recientes que alguien ha hecho.

##  <a name="BKMK_Expressions_and_formatting"></a> Expresiones y formato
Las visualizaciones de Natvis usan expresiones de C++ para especificar los elementos de datos que se deben mostrar. Además de las mejoras y las limitaciones de las expresiones de C++ en el depurador, que se describen en [operador de contexto (C++)](../debugger/context-operator-cpp.md), tenga en cuenta lo siguiente:

- Las expresiones Natvis se evalúan en el contexto del objeto que se visualiza, no el marco de pila actual. Por ejemplo, `x` en un Natvis expresión hace referencia al campo denominado **x** en el objeto visualizado, no a una variable local denominada **x** en la función actual. No se puede tener acceso a las variables locales en las expresiones Natvis, aunque puede tener acceso a las variables globales.

- Las expresiones Natvis no permiten la evaluación de funciones o los efectos. Se omiten las llamadas a funciones y operadores de asignación. Puesto que las [funciones intrínsecas del depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) no tienen efectos secundarios, pueden llamarse libremente desde cualquier expresión Natvis aunque no se permitan otras llamadas de función.

- Para controlar cómo se muestra una expresión, puede usar cualquiera de los especificadores de formato se describe en [especificadores en C++ de formato](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Especificadores de formato se omiten cuando la entrada es Natvis usa internamente, tales como la `Size` expresión en un [expansión de ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Vistas de Natvis

Puede definir diferentes vistas de Natvis para mostrar los tipos de maneras diferentes. Por ejemplo, esta es una visualización de `std::vector` que define una vista simplificada denominada `simple`. El `DisplayString` y `ArrayItems` elementos se muestran en la vista predeterminada y el `simple` vista, mientras el `[size]` y `[capacity]` elementos no se muestran en la `simple` vista.

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

En el **inspección** ventana, utilice el **, vista** especificador para especificar una vista alternativa de formato. Aparece la vista simple como **vec**:

![Ventana Inspección con vista sencilla](../debugger/media/watch-simpleview.png "ventana Inspección con vista simple")

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Errores de Natvis

Cuando el depurador detecta errores en una entrada de visualización, omite. Muestra el tipo en formato sin procesar o elige otra visualización adecuada. Puede usar los diagnósticos de Natvis para comprender por qué el depurador omite una entrada de visualización y para ver la sintaxis subyacente y errores de análisis.

**Para activar los diagnósticos de Natvis:**

- En **herramientas** > **opciones** (o **depurar** > **opciones**) > **depuración**  >  **Ventana de salida**, establezca **mensajes de diagnóstico de Natvis (C++ sólo)** a **Error**, **advertencia** , o **detallado**y, a continuación, seleccione **Aceptar**.

Los errores aparecen en la **salida** ventana.

##  <a name="BKMK_Syntax_reference"></a> Referencia de la sintaxis de Natvis

###  <a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
El elemento `AutoVisualizer` es el nodo raíz del archivo *.natvis* y contiene el atributo `xmlns:` del espacio de nombres.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

El `AutoVisualizer` elemento puede tener [tipo](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), y [CustomVisualizer](#BKMK_CustomVisualizer) elementos secundarios.

###  <a name="BKMK_Type"></a> Elemento Type

Básico `Type` similar a este ejemplo:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 El `Type` especifica el elemento:

1. El tipo de la visualización que debe utilizarse para (el `Name` atributo).

2. Cómo debe ser el valor de un objeto de ese tipo (el elemento `DisplayString` ).

3. Los miembros del tipo de aspecto cuando el usuario expande el tipo en una ventana de variables (el `Expand` nodo).

#### <a name="templated-classes"></a>Clases con plantilla
El `Name` atributo de la `Type` elemento acepta un asterisco `*` como un carácter comodín que se puede usar para los nombres de clase con plantilla.

En el ejemplo siguiente, se utiliza la misma visualización si el objeto es un `CAtlArray<int>` o `CAtlArray<float>`. Si hay una entrada de visualización específica para un `CAtlArray<float>`, a continuación, tiene prioridad sobre la genérica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Puede hacer referencia a parámetros de plantilla en la entrada de visualización mediante macros $t1, $t2 y así sucesivamente. Para buscar ejemplos de estas macros, vea los archivos *.natvis* incluidos con Visual Studio.

####  <a name="BKMK_Visualizer_type_matching"></a> Coincidencia de tipos del visualizador
Si no se puede validar una entrada de visualización, se usa la siguiente visualización disponible.

#### <a name="inheritable-attribute"></a>Atributo heredable
El elemento opcional `Inheritable` atributo especifica si una visualización solo se aplica a un tipo base o a un tipo base y todos los tipos derivados. El valor predeterminado de `Inheritable` es `true`.

En el ejemplo siguiente, la visualización solo se aplica a la `BaseClass` tipo:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atributo de prioridad

El elemento opcional `Priority` atributo especifica el orden en que se va a usar las definiciones alternativas, si no se puede analizar una definición. Los valores posibles de `Priority` son: `Low`, `MediumLow`,`Medium`, `MediumHigh`, y `High`. El valor predeterminado es `Medium`. El `Priority` atributo distingue solo entre las prioridades dentro del mismo *.natvis* archivo.

En primer lugar, en el ejemplo siguiente se analiza la entrada que coincide con la STL de 2015. Si se produce un error al analizar, usa la entrada alternativa para la versión 2013 de la STL:

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
Puede colocar un `Optional` atributo en cualquier nodo. Si no se puede analizar una subexpresión dentro de un nodo opcional, el depurador omite ese nodo, pero se aplica el resto de la `Type` reglas. En el siguiente tipo, `[State]` no es opcional, pero `[Exception]` sí lo es.  Si `MyNamespace::MyClass` tiene un campo denominado _`M_exceptionHolder`, tanto el `[State]` nodo y el `[Exception]` nodo aparece, pero si no hay ningún `_M_exceptionHolder` campo, sólo el `[State]` nodo aparece.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

###  <a name="BKMK_Condition_attribute"></a> Atributo Condition

El elemento opcional `Condition` atributo está disponible para muchos elementos de visualización y especifica cuándo se debe usar una regla de visualización. Si la expresión del atributo condition se resuelve en `false`, no se aplica la regla de visualización. Si se evalúa como `true`, o no hay ningún `Condition` atributo, la visualización se aplica. Puede usar este atributo para la lógica de if-else en las entradas de visualización.

Por ejemplo, la visualización siguiente tiene dos `DisplayString` elementos para un tipo de puntero inteligente. Cuando el `_Myptr` miembro está vacío, la condición del primer `DisplayString` se resuelve como elemento `true`, por lo que muestra dicho formulario. Cuando el `_Myptr` miembro no está vacío, la condición se evalúa como `false`y el segundo `DisplayString` muestra el elemento.

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

El `IncludeView` y `ExcludeView` atributos especifican los elementos para mostrar o no mostrar en vistas específicas. Por ejemplo, en la siguiente especificación de Natvis de `std::vector`, `simple` vista no muestra el `[size]` y `[capacity]` elementos.

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

Puede usar el `IncludeView` y `ExcludeView` atributos de tipos y de miembros individuales.

###  <a name="BKMK_Versioning"></a> Elemento Version
El `Version` elemento establece el ámbito de una entrada de visualización a un módulo específico y una versión. El `Version` elemento ayuda a evitar conflictos de nombres, las divergencias inadvertidas y permite diferentes visualizaciones para las versiones de un tipo diferente.

Si un archivo de encabezado común usado por módulos diferentes, define un tipo, la visualización con versión solo aparece cuando el tipo está en la versión del módulo especificado.

En el ejemplo siguiente, la visualización solo es aplicable la `DirectUI::Border` tipo se encuentra en la `Windows.UI.Xaml.dll` de las versiones 1.0 a 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

###  <a name="BKMK_DisplayString"></a> Elemento DisplayString
El `DisplayString` elemento especifica una cadena para mostrar como el valor de una variable. Acepta cadenas arbitrarias mezcladas con expresiones. Todos los datos encerrados entre llaves se interpretan como una expresión. Por ejemplo, la siguiente `DisplayString` entrada:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa que las variables de tipo `CPoint` mostrar como se muestra en esta ilustración:

 ![Usar un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "usar un elemento DisplayString")

En el `DisplayString` expresión, `x` y `y`, que son miembros de `CPoint`, son dentro de llaves, por lo que se evalúan sus valores. El ejemplo también muestra cómo se puede omitir una llave de cierre mediante el uso de llaves dobles ( `{{` o `}}` ).

> [!NOTE]
> El elemento `DisplayString` es el único que acepta cadenas arbitrarias y la sintaxis de llaves. Todos los demás elementos de visualización solo aceptan expresiones que el depurador puede evaluar.

###  <a name="BKMK_StringView"></a> Elemento StringView

El `StringView` elemento define un valor que se puede enviar el depurador al visualizador de texto integrado. Por ejemplo, dada la visualización siguiente para el `ATL::CStringT` tipo:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

La `CStringT` muestra el objeto en una ventana de variables como en este ejemplo:

![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "elemento CStringT DisplayString")

Agregar un `StringView` elemento indica que el depurador puede mostrar el valor como una visualización de texto.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante la depuración, puede seleccionar el icono de lupa junto a la variable y, a continuación, seleccione **visualizador de texto** para mostrar la cadena que **m_pszData** apunta a.

 ![Datos CStringT con visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "datos CStringT con visualizador StringView")

La expresión `{m_pszData,su}` incluye un especificador de formato de C++ **su**, para mostrar el valor como una cadena Unicode. Para obtener más información, consulte [especificadores en C++ de formato](../debugger/format-specifiers-in-cpp.md).

###  <a name="BKMK_Expand"></a> Expanda el elemento

El elemento opcional `Expand` nodo personaliza los elementos secundarios de un tipo visualizado cuando se expande el tipo en una ventana de variables. El `Expand` nodo acepta una lista de nodos secundarios que definen los elementos secundarios.

- Si un `Expand` nodo no se especifica en una entrada de visualización, los elementos secundarios usa las reglas predeterminadas de expansión.

- Si un `Expand` se especifica al nodo sin nodos secundarios debajo de él, el tipo no es expansible en las ventanas del depurador.

####  <a name="BKMK_Item_expansion"></a> Expansión de Item

 El `Item` es un elemento más básico y comunes en un `Expand` nodo. `Item` define un único elemento secundario. Por ejemplo, un `CRect` clase con campos `top`, `left`, `right`, y `bottom` tiene la siguiente entrada de visualización:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

En la ventana del depurador, el `CRect` tipo es similar a este ejemplo:

![CRect con expansión de elementos Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con expansión de elemento de elemento")

El depurador evalúa las expresiones especificadas en el `Width` y `Height` elementos y se muestran los valores en el **valor** columna de la ventana de variables.

El depurador crea automáticamente el **[vista sin formato]** nodo para cada extensión personalizada. La captura de pantalla anterior muestra la **[vista sin formato]** nodo expandido, para mostrar cómo la vista sin formato del valor predeterminado del objeto difiere de su visualización Natvis. La expansión predeterminada crea un subárbol de la clase base y enumera a todos los miembros de datos de la clase base como elementos secundarios.

> [!NOTE]
> Si la expresión del elemento item apunta a un tipo complejo, el **elemento** propio nodo es expansible.

####  <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
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

![std:: vector usa expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: vector usa expansión ArrayItems")

El `ArrayItems` nodo debe tener:

- Expresión `Size` (que debe evaluarse como entero) para que el depurador comprenda la longitud de la matriz.
- Un `ValuePointer` expresión que apunta al primer elemento (que debe ser un puntero de un tipo de elemento que no es `void*`).

El valor predeterminado del límite inferior de la matriz es 0. Para invalidar el valor, use un `LowerBound` elemento. El *.natvis* archivos incluidos con Visual Studio tienen algunos ejemplos.

>[!NOTE]
>Puede usar el `[]` operador, por ejemplo `vector[i]`, con cualquier visualización de matriz unidimensional que usa `ArrayItems`, incluso si el propio tipo (por ejemplo `CATLArray`) no admite este operador.

También puede especificar matrices multidimensionales. En ese caso, el depurador necesita un poco más información para mostrar correctamente los elementos secundarios:

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

- `Direction` Especifica si la matriz está en orden fila principal o por columna principal.
- `Rank` especifica el rango de la matriz.
- El elemento `Size` acepta el parámetro `$i` implícito que sustituye al índice de dimensión para buscar la longitud de la matriz en esa dimensión. En el ejemplo anterior, la expresión `_M_extent.M_base[0]` debe proporcionar la longitud de la dimensión 0, `_M_extent._M_base[1]` el día 1 y así sucesivamente.

Le mostramos cómo un bidimensional `Concurrency::array` objeto busca en la ventana del depurador:

![Matriz bidimensional con expansión de ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "matriz bidimensional con expansión ArrayItems")

####  <a name="BKMK_IndexListItems_expansion"></a> Expansión de IndexListItems

Puede usar `ArrayItems` expansión solo si los elementos de matriz están dispuestos de forma contigua en la memoria. Obtiene el depurador hasta el siguiente elemento al incrementar simplemente el puntero. Si necesita manipular el índice para el nodo de valor, use `IndexListItems` nodos. Esta es una visualización con una `IndexListItems` nodo:

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

La única diferencia entre `ArrayItems` y `IndexListItems` es el `ValueNode`, que espera la expresión completa para el<sup>th</sup> elemento con implícito `$i` parámetro.

>[!NOTE]
>Puede usar el `[]` operador, por ejemplo `vector[i]`, con cualquier visualización de matriz unidimensional que usa `IndexListItems`, incluso si el propio tipo (por ejemplo `CATLArray`) no admite este operador.

####  <a name="BKMK_LinkedListItems_expansion"></a> Expansión de LinkedListItems

Si el tipo visualizado representa una lista vinculada, el depurador puede mostrar sus elementos secundarios si se usa un nodo `LinkedListItems` . La visualización siguiente para el `CAtlList` tipo utiliza `LinkedListItems`:

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

El depurador evalúa la `NextPointer` y `ValueNode` expresiones en el contexto de la `LinkedListItems` elemento node, no el tipo de lista primario. En el ejemplo anterior, `CAtlList` tiene un `CNode` clase (se encuentra en `atlcoll.h`) que es un nodo de la lista vinculada. `m_pNext` y `m_element` son campos de `CNode` (clase), no de la `CAtlList` clase.

`ValueNode` puede dejarse vacío o usar `this` para hacer referencia a la `LinkedListItems` nodo en Sí.

#### <a name="customlistitems-expansion"></a>Expansión CustomListItems
La expansión `CustomListItems` le permite escribir una lógica personalizada para recorrer una estructura de datos, como una tabla hash. Usar `CustomListItems` visualizar estructuras de datos que pueden usar expresiones de C++ para todo lo que necesita para evaluar, pero no muy ajustarse lo suficiente al molde para `ArrayItems`, `IndexListItems`, o `LinkedListItems`.

El visualizador siguiente para `CAtlMap` es un excelente ejemplo donde `CustomListItems` es adecuado.

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

Puede usar `Exec` para ejecutar código dentro de un `CustomListItems` expansión, mediante las variables y objetos definidos en la expansión. Puede usar operadores lógicos, operadores aritméticos y los operadores de asignación con `Exec`. No puede usar `Exec` para evaluar las funciones.

`CustomListItems` admite las siguientes funciones intrínsecas:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> Expansión de TreeItems
 Si el tipo visualizado representa un árbol, el depurador puede recorrer el árbol y mostrar sus elementos secundarios utilizando un nodo `TreeItems` . Esta es la visualización de la `std::map` escriba mediante un `TreeItems` nodo:

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

La sintaxis es similar a la `LinkedListItems` nodo. `LeftPointer`, `RightPointer`, y `ValueNode` se evalúan en el contexto de la clase de nodo de árbol. `ValueNode` puede dejarse vacío o usar `this` para hacer referencia a la `TreeItems` nodo en Sí.

####  <a name="BKMK_ExpandedItem_expansion"></a> Expansión de ExpandedItem
 El `ExpandedItem` elemento genera una vista secundaria agregada que muestre las propiedades de los miembros de datos o clases base como si fueran elementos secundarios del tipo visualizado. El depurador evalúa la expresión especificada y anexa los nodos secundarios del resultado a la lista secundaria del tipo visualizado.

Por ejemplo, el tipo de puntero inteligente `auto_ptr<vector<int>>` normalmente se muestra como:

 ![Auto&#95;ptr&#60;vector&#60;int&#62; &#62; expansión predeterminada](../debugger/media/dbg_natvis_expand_expandeditem_default.png "expansión predeterminada")

 Para ver los valores del vector, tiene que explorar en profundidad de dos niveles en la ventana de variables, pasar a través de la `_Myptr` miembro. Al agregar un elemento `ExpandedItem`, puede eliminar la variable `_Myptr` de la jerarquía y ver directamente los elementos de vector:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Auto&#95;ptr&#60;vector&#60;int&#62; &#62; expansión de ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "expansión de ExpandedItem")

El ejemplo siguiente muestra cómo agregar propiedades de la clase base en una clase derivada. Supongamos que la clase `CPanel` se deriva de `CFrameworkElement`. En lugar de repetir las propiedades que proceden de la base de `CFrameworkElement` (clase), el `ExpandedItem` visualización nodo anexa esas propiedades a la lista secundaria de la `CPanel` clase.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Aquí es necesario usar el especificador de formato **nd** que desactiva la coincidencia de visualización para la clase derivada. En caso contrario, la expresión `*(CFrameworkElement*)this` provocaría el `CPanel` visualización se vuelva a aplicar, porque las reglas de coincidencia de tipos de la visualización predeterminada se considere lo más adecuado. Utilice la **nd** especificador para indicar al depurador que use la visualización de la clase base, o la expansión predeterminada si la clase base no tiene ninguna visualización de formato.

####  <a name="BKMK_Synthetic_Item_expansion"></a> Expansión de elemento Synthetic
 En los casos donde el elemento `ExpandedItem` elimina las jerarquías para proporcionar una vista de datos más plana, el nodo `Synthetic` hace lo contrario. Permite crear un elemento secundario artificial que no es un resultado de una expresión. El elemento artificial puede tener elementos secundarios propios. En el ejemplo siguiente, la visualización del tipo `Concurrency::array` usa un nodo `Synthetic` para mostrar un mensaje de diagnóstico al usuario:

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

 ![Concurrency:: Array con expansión de elemento sintéticas](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: Array con expansión de elemento sintético")

###  <a name="BKMK_HResult"></a> Elemento HResult
 El `HResult` elemento le permite personalizar la información que se muestra para un **HRESULT** en ventanas del depurador. El elemento `HRValue` debe contener el valor de 32 bits de **HRESULT** que se debe personalizar. El `HRDescription` elemento contiene la información que se muestra en la ventana del depurador.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

###  <a name="BKMK_UIVisualizer"></a> Elemento UIVisualizer
Un elemento `UIVisualizer` registra un complemento de visualizador gráfico en el depurador. Un visualizador gráfico crea un cuadro de diálogo u otra interfaz que muestra una variable o un objeto de una manera coherente con su tipo de datos. El complemento del visualizador se debe crear como un [VSPackage](../extensibility/internals/vspackages.md)y debe exponer un servicio que puede consumir el depurador. El *.natvis* archivo contiene información de registro para el complemento, como su nombre, el GUID del servicio expuesto y los tipos que puede visualizar.

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

- Un `ServiceId`  -  `Id` par atributo identifica un `UIVisualizer`. El `ServiceId` es el GUID del servicio el visualizador de paquete expone. `Id` es un identificador único que diferencia los visualizadores, si un servicio proporciona más de uno. En el ejemplo anterior, el mismo servicio del visualizador proporciona dos visualizadores.

- El `MenuName` atributo define un nombre de visualizador para mostrar en la lista desplegable situada junto al icono de lupa en el depurador. Por ejemplo:

  ![Menú contextual de UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "menú contextual de UIVisualizer")

Cada tipo definido en el *.natvis* archivo debe mostrar explícitamente los visualizadores de la interfaz de usuario que pueden mostrarla. El depurador coincide con las referencias del visualizador en las entradas de tipo con los visualizadores registrados. Por ejemplo, el siguiente tipo entrada para `std::vector` referencias el `UIVisualizer` en el ejemplo anterior.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Puede ver un ejemplo de un `UIVisualizer` en el [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) extensión usada para ver los mapas de bits en memoria.

### <a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer` es un punto de extensibilidad que especifica una extensión VSIX que escribir para controlar las visualizaciones en el código de Visual Studio. Para obtener más información sobre cómo escribir extensiones VSIX, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

Es mucho más trabajo para escribir un visualizador personalizado a una definición de Natvis XML, pero tiene la libertad de restricciones sobre lo que hace o no es compatible con Natvis. Los visualizadores personalizados tienen acceso al conjunto completo de extensibilidad del depurador de API, lo que pueden consultar y modificar el proceso depurado o comunicarse con otras partes de Visual Studio.

 Puede usar el `Condition`, `IncludeView`, y `ExcludeView` atributos en `CustomVisualizer` elementos.