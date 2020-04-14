---
title: Creación de vistas personalizadas de objetos de C++
description: Use el marco de trabajo de Natvis para personalizar la forma en que Visual Studio muestra los tipos nativos en el depurador
ms.date: 03/02/2020
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
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224516"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Crear vistas personalizadas de objetos C++ en el depurador mediante el marco Natvis

El marco de trabajo de Visual Studio *Natvis* personaliza la forma en que aparecen los tipos nativos en las ventanas de variables del depurador, como las **ventanas Locales** y **Inspección,** y en **Información sobre datos**. Las visualizaciones de Natvis pueden ayudar a que los tipos que cree sean más visibles durante la depuración.

Natvis reemplaza el archivo *autoexp.dat* en versiones anteriores de Visual Studio con sintaxis XML, diagnóstico mejor, control de versiones y compatibilidad con varios archivos.

> [!NOTE]
> Las personalizaciones de Natvis funcionan con clases y estructuras, pero no con typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualizaciones de Natvis

Utilice el marco natvis para crear reglas de visualización para los tipos que cree, de modo que los desarrolladores puedan verlas más fácilmente durante la depuración.

Por ejemplo, la siguiente ilustración muestra una variable de tipo [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) en una ventana del depurador sin ninguna visualización personalizada aplicada.

![Visualización predeterminada de TextBox](../debugger/media/dbg_natvis_textbox_default.png "Visualización predeterminada de TextBox")

La fila resaltada muestra la propiedad `Text` de la clase `TextBox` . La jerarquía de clases compleja hace que sea difícil encontrar esta propiedad. El depurador no sabe cómo interpretar el tipo de cadena personalizada, por lo que no puede ver la cadena que se mantiene dentro del cuadro de texto.

Lo `TextBox` mismo se ve mucho más simple en la ventana de variables cuando se aplican las reglas del visualizador personalizado Natvis. Los miembros importantes de la clase aparecen juntos y el depurador muestra el valor de cadena subyacente del tipo de cadena personalizado.

![Datos de TextBox que usan visualizador](../debugger/media/dbg_natvis_textbox_visualizer.png "Datos de TextBox que usan visualizador")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Utilice archivos .natvis en proyectos C++

Natvis utiliza archivos *.natvis* para especificar reglas de visualización. Un archivo *.natvis* es un archivo XML con extensión *.natvis.* El esquema natvis se define en *%VSINSTALLDIR%-Xml-Schemas-natvis.xsd*.

La estructura básica de un archivo *.natvis* es uno o varios `Type` elementos que representan entradas de visualización. El nombre completo `Type` de cada elemento `Name` se especifica en su atributo.

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

Visual Studio proporciona algunos archivos *.natvis* en la carpeta *%VSINSTALLDIR%-Common7-Packages-Debugger-Visualizers.* Estos archivos tienen reglas de visualización para muchos tipos comunes y pueden servir como ejemplos para escribir visualizaciones para nuevos tipos.

### <a name="add-a-natvis-file-to-a-c-project"></a>Agregue un archivo .natvis a un proyecto C++

Puede agregar un archivo *.natvis* a cualquier proyecto C++.

**Para agregar un nuevo archivo *.natvis:***

1. Seleccione el nodo de proyecto C++ en el **Explorador**de soluciones y **seleccione** > **Agregar nuevo elemento**de proyecto o haga clic con el botón derecho en el proyecto y seleccione **Agregar** > **nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento,** seleccione Archivo de visualización del**Utility** > depurador de utilidades de Visual C++(.natvis) **Visual C++** > .**Debugger visualization file (.natvis)**

1. Asigne un nombre al archivo y seleccione **Agregar**.

   El nuevo archivo se agrega al Explorador de **soluciones**y se abre en el panel de documentos de Visual Studio.

El depurador de Visual Studio carga automáticamente archivos *.natvis* en proyectos De+ y, de forma predeterminada, también los incluye en el archivo *.pdb* cuando se compila el proyecto. Si depura la aplicación compilada, el depurador carga el archivo *.natvis* desde el archivo *.pdb,* incluso si no tiene el proyecto abierto. Si no desea que el archivo *.natvis* se incluya en el *archivo .pdb*, puede excluirlo del archivo *.pdb* compilado.

**Para excluir un archivo *.natvis* de un *archivo .pdb:***

1. Seleccione el archivo *.natvis* en el **Explorador**de soluciones y seleccione el icono **Propiedades** o haga clic con el botón derecho en el archivo y seleccione **Propiedades**.

1. Desmenúla flecha situada junto a **Excluido de compilación** y seleccione **Sí**y, a continuación, seleccione **Aceptar**.

>[!NOTE]
>Para depurar proyectos ejecutables, use los elementos de solución para agregar archivos *.natvis* que no estén en *el archivo .pdb*, ya que no hay ningún proyecto De++ disponible.

>[!NOTE]
>Las reglas Natvis cargadas desde *un archivo .pdb* solo se aplican a los tipos de los módulos a los que hace *referencia el archivo .pdb.* Por ejemplo, si *Module1.pdb* tiene una entrada Natvis para un tipo denominado `Test`, solo se aplica a la `Test` clase de *Module1.dll*. Si otro módulo también `Test`define una clase denominada , la entrada *Module1.pdb* Natvis no se aplica a ella.

**Para instalar y registrar un archivo *.natvis* a través de un paquete VSIX:**

Un paquete VSIX puede instalar y registrar archivos *.natvis.* No importa dónde se instalen, todos los archivos *.natvis* registrados se recogen automáticamente durante la depuración.

1. Incluya el archivo *.natvis* en el paquete VSIX. Por ejemplo, para el siguiente archivo de proyecto:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registre el archivo *.natvis* en el archivo *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Ubicaciones de archivos Natvis

Puede agregar archivos *.natvis* al directorio de usuario o a un directorio del sistema, si desea que se apliquen a varios proyectos.

Los archivos *.natvis* se evalúan en el siguiente orden:

1. Cualquier archivo *.natvis* que esté incrustado en un *.pdb* que esté depurando, a menos que exista un archivo con el mismo nombre en el proyecto cargado.

2. Cualquier archivo *.natvis* que se encuentra en un proyecto C++ cargado o solución de nivel superior. Este grupo incluye todos los proyectos C++ cargados, incluidas las bibliotecas de clases, pero no los proyectos en otros idiomas.

3. Cualquier archivo *.natvis* instalado y registrado a través de un paquete VSIX.

::: moniker range="vs-2017"

4. El directorio Natvis específico del usuario (por ejemplo, *%USERPROFILE%-Documents-Visual Studio 2017-Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. El directorio Natvis específico del usuario (por ejemplo, *%USERPROFILE%-Documents-Visual Studio 2019-Visualizers*).

::: moniker-end

5. El directorio de Natvis de todo el sistema (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Este directorio tiene los archivos *.natvis* que se instalan con Visual Studio. Si tiene permisos de administrador, puede agregar archivos a este directorio.

## <a name="modify-natvis-files-while-debugging"></a>Modificar archivos .natvis durante la depuración

Puede modificar un archivo *.natvis* en el IDE al depurar su proyecto. Abra el archivo en la misma instancia de Visual Studio con la que está depurando, modifíquelo y guárdelo. Tan pronto como se guarda el archivo, las ventanas **Inspección** y **Locales** se actualizan para reflejar el cambio.

También puede agregar o eliminar archivos *.natvis* en una solución que esté depurando y Visual Studio agrega o quita las visualizaciones relevantes.

No puede actualizar archivos *.natvis* incrustados en archivos *.pdb* mientras está depurando.

Si modifica el archivo *.natvis* fuera de Visual Studio, los cambios no surten efecto automáticamente. Para actualizar las ventanas del depurador, puede volver a evaluar el comando **.natvisreload** en la ventana **Inmediato.** A continuación, los cambios surten efecto sin reiniciar la sesión de depuración.

Utilice también el comando **.natvisreload** para actualizar el archivo *.natvis* a una versión más reciente. Por ejemplo, el archivo *.natvis* se puede registrar en el control de código fuente y desea recoger los cambios recientes que otra persona realizó.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Expresiones y formato
Las visualizaciones de Natvis usan expresiones de C++ para especificar los elementos de datos que se deben mostrar. Además de las mejoras y limitaciones de las expresiones C++ en el depurador, que se describen en [el operador de contexto (C++),](../debugger/context-operator-cpp.md)tenga en cuenta lo siguiente:

- Las expresiones Natvis se evalúan en el contexto del objeto que se visualiza, no el marco de pila actual. Por ejemplo, `x` en una expresión Natvis hace referencia al campo denominado **x** en el objeto que se está visualizando, no a una variable local denominada **x** en la función actual. No se puede acceder a variables locales en expresiones Natvis, aunque puede tener acceso a variables globales.

- Las expresiones Natvis no permiten la evaluación de funciones ni los efectos secundarios. Las llamadas a funciones y los operadores de asignación se omiten. Puesto que las [funciones intrínsecas del depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) no tienen efectos secundarios, pueden llamarse libremente desde cualquier expresión Natvis aunque no se permitan otras llamadas de función.

- Para controlar cómo se muestra una expresión, puede utilizar cualquiera de los especificadores de formato descritos en Especificadores de formato [en C++.](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) Los especificadores de formato se omiten cuando Natvis `Size` utiliza internamente la entrada, como la expresión en una [expansión ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Vistas de Natvis

Puede definir diferentes vistas Detvis para mostrar tipos de diferentes maneras. Por ejemplo, aquí hay `std::vector` una visualización `simple`que define una vista simplificada denominada . Los `DisplayString` elementos `ArrayItems` y los se `simple` muestran en `[size]` `[capacity]` la vista predeterminada y `simple` en la vista, mientras que los elementos y no se muestran en la vista.

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

En la ventana **Inspección,** utilice el especificador de formato **,view** para especificar una vista alternativa. La vista simple aparece como **vec,view(simple)**:

![Ventana Inspección con vista sencilla](../debugger/media/watch-simpleview.png "Ventana Inspección con vista sencilla")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Errores de Natvis

Cuando el depurador encuentra errores en una entrada de visualización, los omite. Muestra el tipo en su forma sin formato o elige otra visualización adecuada. Puede usar los diagnósticos de Natvis para comprender por qué el depurador omitió una entrada de visualización y para ver los errores de sintaxis y análisis subyacentes.

**Para activar el diagnóstico de Natvis:**

- En **Tools** > **Opciones** de herramientas (o**Opciones**de **depuración** > ) >**ventana**de salida **de depuración** > , establezca los mensajes de diagnóstico de **Natvis (solo C+)** en **Error**, **Advertencia**o **Detallado**y, a continuación, seleccione **Aceptar**.

Los errores aparecen en la ventana **Salida.**

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

El `AutoVisualizer` elemento puede tener elementos secundarios [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)y [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="type-element"></a><a name="BKMK_Type"></a>Elemento de tipo

Un `Type` aspecto básico se parece a este ejemplo:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 El `Type` elemento especifica:

1. Para qué tipo se debe `Name` utilizar la visualización (el atributo).

2. Cómo debe ser el valor de un objeto de ese tipo (el elemento `DisplayString` ).

3. Cómo deben ser los miembros del tipo cuando el usuario expande el tipo en una ventana de variable (el `Expand` nodo).

#### <a name="templated-classes"></a>Clases con plantillas
El `Name` atributo `Type` del elemento acepta `*` un asterisco como carácter comodín que se puede utilizar para los nombres de clase con plantilla.

En el ejemplo siguiente, se utiliza la `CAtlArray<int>` misma `CAtlArray<float>`visualización si el objeto es a o un archivo . Si hay una entrada de `CAtlArray<float>`visualización específica para un , entonces tiene prioridad sobre la genérica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Puede hacer referencia a parámetros de plantilla en la entrada de visualización mediante macros $T1, $T2, etc. Para buscar ejemplos de estas macros, vea los archivos *.natvis* incluidos con Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Coincidencia de tipos del visualizador
Si una entrada de visualización no se valida, se utiliza la siguiente visualización disponible.

#### <a name="inheritable-attribute"></a>Atributo heredable
El `Inheritable` atributo opcional especifica si una visualización solo se aplica a un tipo base o a un tipo base y a todos los tipos derivados. El valor predeterminado de `Inheritable` es `true`.

En el ejemplo siguiente, la `BaseClass` visualización solo se aplica al tipo:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atributo de prioridad

El `Priority` atributo opcional especifica el orden en el que se deben utilizar definiciones alternativas, si una definición no se puede analizar. Los valores `Priority` posibles `Low`de:`Medium` `MediumHigh`, `MediumLow` `High`, , , y . El valor predeterminado es `Medium`. El `Priority` atributo distingue solo entre las prioridades dentro del mismo archivo *.natvis.*

En el ejemplo siguiente se analiza primero la entrada que coincide con el STL de 2015. Si eso no puede analizar, utiliza la entrada alternativa para la versión 2013 del STL:

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
Puede colocar `Optional` un atributo en cualquier nodo. Si una subexpresión dentro de un nodo opcional no se puede analizar, el `Type` depurador omite ese nodo, pero aplica el resto de las reglas. En el siguiente tipo, `[State]` no es opcional, pero `[Exception]` sí lo es.  Si `MyNamespace::MyClass` tiene un`M_exceptionHolder`campo denominado `[State]` _ , `[Exception]` aparecen tanto el nodo `_M_exceptionHolder` como el `[State]` nodo, pero si no hay ningún campo, solo aparece el nodo.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atributo Condition

El `Condition` atributo opcional está disponible para muchos elementos de visualización y especifica cuándo se debe utilizar una regla de visualización. Si la expresión dentro del `false`atributo condition se resuelve en , la regla de visualización no se aplica. Si se evalúa `true`como , `Condition` o no hay ningún atributo, se aplica la visualización. Puede utilizar este atributo para la lógica if-else en las entradas de visualización.

Por ejemplo, la siguiente `DisplayString` visualización tiene dos elementos para un tipo de puntero inteligente. Cuando `_Myptr` el miembro está vacío, `DisplayString` se resuelve `true`la condición del primer elemento en , para que se muestre el formulario. Cuando `_Myptr` el miembro no está vacío, `false`la condición se evalúa como , y se muestra el segundo `DisplayString` elemento.

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

Los `IncludeView` `ExcludeView` atributos y especifican los elementos que se mostrarán o no se mostrarán en vistas específicas. Por ejemplo, en la siguiente especificación Natvis de `std::vector`, la `simple` vista no muestra los `[size]` elementos y. `[capacity]`

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

Puede usar `IncludeView` los `ExcludeView` atributos y en los tipos y en los miembros individuales.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Elemento de versión
El `Version` elemento limita una entrada de visualización a un módulo y una versión específicos. El `Version` elemento ayuda a evitar colisiones de nombres, reduce las discrepancias involuntarias y permite diferentes visualizaciones para diferentes versiones de tipo.

Si un archivo de encabezado común que utilizan diferentes módulos define un tipo, la visualización versionada solo aparece cuando el tipo está en la versión de módulo especificada.

En el ejemplo siguiente, la visualización solo es aplicable para el `DirectUI::Border` tipo que se encuentra en la `Windows.UI.Xaml.dll` versión 1.0 a la 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Usted no necesita `Min` ambos `Max`y . Son atributos opcionales. No se admiten caracteres comodín.

El `Name` atributo tiene el formato *filename.ext*, como *hello.exe* o *some.dll*. No se permiten nombres de ruta de acceso.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Elemento DisplayString
El `DisplayString` elemento especifica una cadena para mostrar como el valor de una variable. Acepta cadenas arbitrarias mezcladas con expresiones. Todos los datos encerrados entre llaves se interpretan como una expresión. Por ejemplo, `DisplayString` la entrada siguiente:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa que las `CPoint` variables de tipo se muestran como en esta ilustración:

 ![Utilice un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Utilice un elemento DisplayString")

En `DisplayString` la `x` expresión `y`y , `CPoint`que son miembros de , están dentro de llaves, por lo que se evalúan sus valores. El ejemplo también muestra cómo se puede escapar de una `{{` llave `}}` mediante el uso de llaves dobles ( o ).

> [!NOTE]
> El elemento `DisplayString` es el único que acepta cadenas arbitrarias y la sintaxis de llaves. Todos los demás elementos de visualización solo aceptan expresiones que el depurador puede evaluar.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Elemento StringView

El `StringView` elemento define un valor que el depurador puede enviar al visualizador de texto integrado. Por ejemplo, dada la `ATL::CStringT` siguiente visualización para el tipo:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

El `CStringT` objeto se muestra en una ventana de variable como este ejemplo:

![CStringT (elemento DisplayString)](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT (elemento DisplayString)")

Agregar `StringView` un elemento indica al depurador que puede mostrar el valor como una visualización de texto.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante la depuración, puede seleccionar el icono de lupa junto a la variable y, a continuación, seleccionar **Visualizador** de texto para mostrar la cadena a la que **m_pszData** apunta.

 ![Datos CStringT con visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Datos CStringT con visualizador StringView")

La `{m_pszData,su}` expresión incluye un especificador de formato C++ **su**, para mostrar el valor como una cadena Unicode. Para obtener más información, consulte Especificadores de formato [en C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Expandir elemento

El `Expand` nodo opcional personaliza los elementos secundarios de un tipo visualizado al expandir el tipo en una ventana de variable. El `Expand` nodo acepta una lista de nodos secundarios que definen los elementos secundarios.

- Si `Expand` no se especifica un nodo en una entrada de visualización, los elementos secundarios usan las reglas de expansión predeterminadas.

- Si `Expand` se especifica un nodo sin nodos secundarios debajo, el tipo no se puede expandir en las ventanas del depurador.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Expansión de Item

 El `Item` elemento es el elemento más `Expand` básico y común de un nodo. `Item` define un único elemento secundario. Por ejemplo, `CRect` una `top`clase `left` `right`con `bottom` campos , , , y tiene la siguiente entrada de visualización:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

En la ventana `CRect` del depurador, el tipo se parece a este ejemplo:

![CRect con expansión de elementos Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con expansión de elementos Item")

El depurador evalúa las expresiones `Width` `Height` especificadas en los elementos y muestra los valores de la columna **Valor** de la ventana de variables.

El depurador crea automáticamente el nodo **[Raw View]** para cada expansión personalizada. La captura de pantalla anterior muestra el nodo **[Raw View]** expandido, para mostrar cómo la vista sin procesar predeterminada del objeto difiere de su visualización Natvis. La expansión predeterminada crea un subárbol para la clase base y enumera todos los miembros de datos de la clase base como elementos secundarios.

> [!NOTE]
> Si la expresión del elemento de elemento apunta a un tipo complejo, el **elemento** propio nodo es expandible.

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

![std::vector que usa expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector que usa expansión ArrayItems")

El `ArrayItems` nodo debe tener:

- Expresión `Size` (que debe evaluarse como entero) para que el depurador comprenda la longitud de la matriz.
- Expresión `ValuePointer` que apunta al primer elemento (que debe ser un `void*`puntero de un tipo de elemento que no lo es).

El valor predeterminado del límite inferior de la matriz es 0. Para invalidar el valor, utilice un `LowerBound` elemento. Los archivos *.natvis* incluidos con Visual Studio tienen ejemplos.

>[!NOTE]
>Puede utilizar `[]` el operador, `vector[i]`por ejemplo, con cualquier `ArrayItems`visualización de matriz unidimensional que utilice , incluso si el propio tipo (por ejemplo) `CATLArray`no permite este operador.

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

- `Direction`especifica si la matriz está en orden de fila mayor o de columna principal.
- `Rank` especifica el rango de la matriz.
- El elemento `Size` acepta el parámetro `$i` implícito que sustituye al índice de dimensión para buscar la longitud de la matriz en esa dimensión. En el ejemplo anterior, la expresión `_M_extent.M_base[0]` debe dar `_M_extent._M_base[1]` la longitud de la dimensión 0, la 1a, etc.

Así es como se `Concurrency::array` ve un objeto bidimensional en la ventana del depurador:

![Matriz bidimensional con expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matriz bidimensional con expansión ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Expansión de IndexListItems

Solo se `ArrayItems` puede utilizar la expansión si los elementos de la matriz se distribuyen de forma contigua en la memoria. El depurador llega al siguiente elemento simplemente incrementando su puntero. Si necesita manipular el índice en el `IndexListItems` nodo de valor, utilice nodos. Esta es una visualización con un `IndexListItems` nodo:

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

La única `ArrayItems` diferencia `IndexListItems` entre `ValueNode`y es el , que espera la `$i` expresión completa al elemento i<sup>th</sup> con el parámetro implícito.

>[!NOTE]
>Puede utilizar `[]` el operador, `vector[i]`por ejemplo, con cualquier `IndexListItems`visualización de matriz unidimensional que utilice , incluso si el propio tipo (por ejemplo) `CATLArray`no permite este operador.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Expansión de LinkedListItems

Si el tipo visualizado representa una lista vinculada, el depurador puede mostrar sus elementos secundarios si se usa un nodo `LinkedListItems` . La siguiente visualización para el `CAtlList` tipo utiliza: `LinkedListItems`

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

El depurador evalúa `NextPointer` `ValueNode` las expresiones y `LinkedListItems` en el contexto del elemento de nodo, no en el tipo de lista primaria. En el ejemplo `CAtlList` anterior, `CNode` tiene una `atlcoll.h`clase (que se encuentra en ) que es un nodo de la lista vinculada. `m_pNext`y `m_element` son campos `CNode` de esa `CAtlList` clase, no de la clase.

`ValueNode`se puede dejar vacío, o `this` `LinkedListItems` utilizar para hacer referencia al propio nodo.

#### <a name="customlistitems-expansion"></a>Expansión CustomListItems

La expansión `CustomListItems` le permite escribir una lógica personalizada para recorrer una estructura de datos, como una tabla hash. Se `CustomListItems` utiliza para visualizar estructuras de datos que pueden utilizar expresiones C++ para `ArrayItems` `IndexListItems`todo `LinkedListItems`lo que necesita evaluar, pero no se ajustan del todo al molde para , , o .

Puede utilizar `Exec` para ejecutar código `CustomListItems` dentro de una expansión, utilizando las variables y objetos definidos en la expansión. Puede utilizar operadores lógicos, operadores `Exec`aritméticos y operadores de asignación con . No se puede `Exec` usar para evaluar funciones, excepto para las [funciones intrínsecas](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) del depurador admitidas por el evaluador de expresiones C++.

El siguiente visualizador para `CAtlMap` es `CustomListItems` un excelente ejemplo cuando es apropiado.

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
 Si el tipo visualizado representa un árbol, el depurador puede recorrer el árbol y mostrar sus elementos secundarios utilizando un nodo `TreeItems` . Aquí está la visualización `std::map` del `TreeItems` tipo mediante un nodo:

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

La sintaxis es `LinkedListItems` similar al nodo. `LeftPointer`, `RightPointer`, `ValueNode` y se evalúan en el contexto de la clase de nodo de árbol. `ValueNode`se puede dejar `this` vacío o `TreeItems` utilizar para hacer referencia al propio nodo.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Expansión de ExpandedItem
 El `ExpandedItem` elemento genera una vista secundaria agregada mostrando las propiedades de las clases base o los miembros de datos como si fueran elementos secundarios del tipo visualizado. El depurador evalúa la expresión especificada y anexa los nodos secundarios del resultado a la lista secundaria del tipo visualizado.

Por ejemplo, el `auto_ptr<vector<int>>` tipo de puntero inteligente normalmente se muestra como:

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; expansión predeterminada](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Expansión predeterminada")

 Para ver los valores del vector, debe explorar dos niveles en `_Myptr` la ventana de variables, pasando por el miembro. Al agregar un elemento `ExpandedItem`, puede eliminar la variable `_Myptr` de la jerarquía y ver directamente los elementos de vector:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; expansión ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expansión de ExpandedItem")

En el ejemplo siguiente se muestra cómo agregar propiedades de la clase base en una clase derivada. Supongamos que la clase `CPanel` se deriva de `CFrameworkElement`. En lugar de repetir las propiedades `CFrameworkElement` que `ExpandedItem` proceden de la clase base, la `CPanel` visualización del nodo anexa esas propiedades a la lista secundaria de la clase.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Aquí es necesario usar el especificador de formato **nd** que desactiva la coincidencia de visualización para la clase derivada. De lo `*(CFrameworkElement*)this` contrario, `CPanel` la expresión haría que la visualización se aplicara de nuevo, porque las reglas de coincidencia de tipo de visualización predeterminadas la consideran la más adecuada. Utilice el especificador de formato **nd** para indicar al depurador que utilice la visualización de la clase base o la expansión predeterminada si la clase base no tiene visualización.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Expansión de artículos sintéticos
 En los casos donde el elemento `ExpandedItem` elimina las jerarquías para proporcionar una vista de datos más plana, el nodo `Synthetic` hace lo contrario. Le permite crear un elemento secundario artificial que no es el resultado de una expresión. El elemento artificial puede tener elementos secundarios propios. En el ejemplo siguiente, la visualización del tipo `Concurrency::array` usa un nodo `Synthetic` para mostrar un mensaje de diagnóstico al usuario:

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

 ![Simultaneidad::Array con expansión de elementos sintéticos](../debugger/media/dbg_natvis_expand_synthetic.png "Simultaneidad::Array con expansión de elementos sintéticos")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Elemento HResult
 El `HResult` elemento permite personalizar la información que se muestra para un **HRESULT** en las ventanas del depurador. El elemento `HRValue` debe contener el valor de 32 bits de **HRESULT** que se debe personalizar. El `HRDescription` elemento contiene la información que se mostrará en la ventana del depurador.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Elemento UIVisualizer
Un elemento `UIVisualizer` registra un complemento de visualizador gráfico en el depurador. Un visualizador gráfico crea un cuadro de diálogo u otra interfaz que muestra una variable u objeto de una manera coherente con su tipo de datos. El complemento del visualizador debe crearse como un [VSPackage](../extensibility/internals/vspackages.md)y debe exponer un servicio que el depurador puede consumir. El archivo *.natvis* contiene información de registro para el complemento, como su nombre, el GUID del servicio expuesto y los tipos que puede visualizar.

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

- `ServiceId`  -  Un `Id` par de `UIVisualizer`atributos identifica un archivo . Es `ServiceId` el GUID del servicio que expone el paquete del visualizador. `Id`es un identificador único que diferencia a los visualizadores, si un servicio proporciona más de uno. En el ejemplo anterior, el mismo servicio de visualizador proporciona dos visualizadores.

- El `MenuName` atributo define un nombre de visualizador que se mostrará en la lista desplegable junto al icono de lupa en el depurador. Por ejemplo:

  ![Menú contextual de UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menú contextual de UIVisualizer")

Cada tipo definido en el archivo *.natvis* debe enumerar explícitamente los visualizadores de interfaz de usuario que puedan mostrarlo. El depurador hace coincidir las referencias del visualizador en las entradas de tipo con los visualizadores registrados. Por ejemplo, la siguiente `std::vector` entrada `UIVisualizer` de tipo para hace referencia al ejemplo anterior.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Puede ver un ejemplo `UIVisualizer` de una en la extensión [Image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) utilizada para ver mapas de bits en memoria.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer`es un punto de extensibilidad que especifica una extensión VSIX que se escribe para controlar las visualizaciones en código de Visual Studio. Para obtener más información acerca de cómo escribir extensiones VSIX, vea el SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

Es mucho más trabajo escribir un visualizador personalizado que una definición de XML Natvis, pero está libre de restricciones sobre lo que Natvis hace o no admite. Los visualizadores personalizados tienen acceso al conjunto completo de API de extensibilidad del depurador, que pueden consultar y modificar el proceso de depuración o comunicarse con otras partes de Visual Studio.

 Puede utilizar `Condition`los `IncludeView`atributos , , y `ExcludeView` en `CustomVisualizer` los elementos.

 ## <a name="limitations"></a>Limitaciones

Las personalizaciones de Natvis funcionan con clases y estructuras, pero no con typedefs.

Natvis no admite visualizadores para tipos primitivos (por ejemplo, `int`, `bool`) o para punteros a tipos primitivos. En este escenario, una opción es usar el [especificador](../debugger/format-specifiers-in-cpp.md) de formato adecuado para su caso de uso. Por ejemplo, si `double* mydoublearray` usa en el código, puede usar un especificador de formato de `mydoublearray, [100]`matriz en la ventana **Inspección** del depurador, como la expresión , que muestra los primeros 100 elementos.
