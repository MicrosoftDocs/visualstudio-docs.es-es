---
title: Crear vistas personalizadas de los objetos nativos en el depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 38656b9c5ce4165f2a04b5e6d76411ce7f005855
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-native-objects-in-the-visual-studio-debugger"></a>Crear vistas personalizadas de los objetos nativos en el depurador de Visual Studio
El marco Natvis de Visual Studio permite personalizar la forma en que Visual Studio muestra los tipos nativos en ventanas de variables del depurador (por ejemplo, el **inspección** ventana, **locales** ventana y en  **Información sobre datos**.
  
 Natvis sustituye el archivo **autoexp.dat** usado en versiones anteriores de Visual Studio y proporciona una sintaxis XML, mejores diagnósticos, control de versiones y compatibilidad con varios archivos.  
  
> [!NOTE]
>  No se puede usar el marco Natvis para las visualizaciones en los siguientes casos:  
>   
>  -  Está depurando un proyecto de escritorio de Windows de C++ con el tipo de depurador establecido en **mixto**.  
> -   Está realizando la depuración en modo mixto en una aplicación de escritorio de Windows en modo de compatibilidad administrado (**Herramientas > Opciones > depuración > General > usar el modo de compatibilidad administrado**).  
> -   Está depurando una aplicación de escritorio de Windows en modo de compatibilidad nativa (**Herramientas > Opciones > depuración > General > usar el modo de compatibilidad nativa**).  
  
##  <a name="BKMK_Why_create_visualizations_"></a> ¿Por qué crear visualizaciones de Natvis?  
 Puede usar el marco Natvis para crear reglas de visualización para los tipos creados, de manera que los desarrolladores puedan verlas fácilmente durante la depuración.  
  
 Por ejemplo, la siguiente ilustración muestra una variable de tipo [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) que se muestra en el depurador sin aplicar ninguna visualización personalizada.  
  
 ![Visualización predeterminada de TextBox](../debugger/media/dbg_natvis_textbox_default.png "DBG_NATVIS_TextBox_Default")  
  
 La fila resaltada muestra la propiedad `Text` de la clase `TextBox` . La jerarquía de clases complejas dificulta la búsqueda de este valor; Además, el depurador no sabe cómo interpretar el tipo de cadena personalizado usado por el objeto, por lo que no puede ver la cadena incluida en el cuadro de texto.  
  
 El mismo `TextBox` parece mucho más sencillo en la ventana de variables cuando se aplican reglas de visualización personalizadas. Los miembros importantes de la clase se pueden ver juntos y el depurador muestra el valor de cadena subyacente del tipo cadena personalizado.  
  
 ![Los datos de cuadro de texto que usan visualizador](../debugger/media/dbg_natvis_textbox_visualizer.png "DBG_NATVIS_TextBox_Visualizer")  
  
##  <a name="BKMK_Using_Natvis_files"></a> Usar archivos Natvis  
 Los archivos .natvis son archivos XML con una extensión .natvis. El esquema se define en **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  
  
 La estructura básica de un archivo .natvis consta de uno o más elementos `Type` , donde cada elemento `Type` representa una entrada de visualización para un tipo cuyo nombre completo se especifica en el atributo `Name` .  
  
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
  
 Visual Studio proporciona algunos archivos .natvis en la carpeta **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** . Estos archivos contienen reglas de visualización para muchos tipos comunes y pueden servir como ejemplos al escribir visualizaciones para nuevos tipos.  
  
## <a name="adding-natvis-files-to-your-projects"></a>Agregar archivos .natvis a los proyectos  
 Se pueden agregar archivos .natvis a cualquier proyecto de C++.  
  
 Para agregar un nuevo archivo .natvis, con un proyecto de C++ abierto, seleccione el nodo del proyecto en el **el Explorador de soluciones**y haga clic en **Agregar > nuevo elemento > Visual C++ > utilidad > archivo de visualización del depurador (.natvis)**. El depurador cargará automáticamente los archivos Natvis de los proyectos de C++. De forma predeterminada, los archivos Natvis del proyecto también se insertan en el archivo .pdb generado por el proyecto. Es decir, si depura el código binario generado por este proyecto, el depurador carga el archivo Natvis desde el archivo .pdb aunque no tenga abierto el proyecto. Si no desea que el archivo .natvis se incluya en el archivo .pdb, haga clic con el botón derecho en el archivo .natvis en el **Explorador de soluciones**y, en la ventana **Propiedades de configuración** , establezca **Excluir de la compilación** en **Sí**.  
  
 Se recomienda editar los archivos Natvis con Visual Studio. Los cambios efectuados durante la depuración surten efecto automáticamente al guardar el archivo. También obtendrá una mejor experiencia de edición con IntelliSense.  
  
 Los archivos Natvis que se cargan desde un archivo .pdb solo se aplican a los tipos del módulo al que hace referencia el archivo .pdb. Por ejemplo, si Module1.pdb define una entrada para un tipo denominado `Test`, esta entrada solo se aplica a la clase **Test** de Module1.dll. Si hay otro módulo también define una clase denominada **prueba**, la entrada natvis de Module1.pdb no se aplica a él.  
  
##  <a name="BKMK_natvis_location"></a> Implementar archivos .natvis  
 Si el archivo .natvis solo se aplica a los tipos que se va a crear en un proyecto de Visual Studio, no tienes que hacer nada; el archivo .natvis se incluye en el archivo .pdb. No obstante, puede agregar archivos .natvis al directorio del usuario o a un directorio del sistema si desea aplicarlos a varios proyectos.  
  
 El orden de evaluación de los archivos .natvis es el siguiente:  
  
1.  archivos .natvis insertados en un archivo .pdb que está depurando (a menos que exista un archivo del mismo nombre en un proyecto cargado).  
  
2.  archivos .natvis que forman parte de un proyecto de C++ cargado o un elemento de la solución de nivel superior. Este grupo incluye cargados todos los proyectos de C++, incluidas las bibliotecas de clase, pero no incluye proyectos de otros lenguajes (por ejemplo, no se puede cargar un archivo .natvis desde un proyecto de C#). Para los proyectos ejecutables, debe usar los elementos de la solución para hospedar los archivos .natvis que no estén presentes en un archivo .pdb, ya que no hay ningún proyecto de C++ disponible.  
  
3.  El directorio de natvis específico de usuario (por ejemplo, **%USERPROFILE%\Documents\Visual Studio 2017\Visualizers** o **%USERPROFILE%\My 2015\Visualizers documentos\Visual Studio**).  
  
4.  El directorio de Natvis de todo el sistema (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Este directorio es donde se copian los archivos .natvis que se instalan con Visual Studio. Si tiene permisos de administrador, puede agregar otros archivos a este directorio.  
  
## <a name="modifying-natvis-files-while-debugging"></a>Modificar archivos .natvis durante la depuración  
 Es posible modificar un archivo .natvis en el IDE mientras se depura el proyecto en el que está incluido. Abra el archivo en el IDE (con la misma instancia de Visual Studio con la que está efectuando la depuración), modifíquelo y guárdelo. Cuando haya guardado el archivo, debe actualizar las ventanas **Inspección** y **Locales** para reflejar el cambio. Si modifica el archivo .natvis fuera del IDE, los cambios no surtirán efecto automáticamente. Para actualizar las ventanas, puede evaluar el comando **.natvisreload** en la ventana **Inspección** . Esta acción hace que los cambios surtan efecto sin tener que reiniciar la sesión de depuración.  
  
 También puede agregar o eliminar archivos .natvis a una solución que se está depurando, y Visual Studio agrega o quita las visualizaciones pertinentes.  
  
 Si un archivo .natvis se incrusta en un archivo .pdb, no se puede modificar durante la depuración.  
  
 Use la **.natvisreload** comando cuando se actualiza el archivo natvis a una versión más reciente (por ejemplo, si se ha comprobado en el control de código fuente y desea recoger los cambios recientes que alguien ha hecho en el archivo). Es aconsejable editar los archivos natvis con el editor XML de Visual Studio.  
  
##  <a name="BKMK_Expressions_and_formatting"></a> Expresiones y formato  
 Las visualizaciones de Natvis usan expresiones de C++ para especificar los elementos de datos que se deben mostrar. Además de las mejoras y las limitaciones de expresiones de C++ en el depurador, que se describen en [operador de contexto (C++)](../debugger/context-operator-cpp.md), debe tener en cuenta las siguientes diferencias:  
  
-   Las expresiones Natvis se evalúan en el contexto del objeto que se visualiza, no el marco de pila actual. Por ejemplo, si usa `x` en una expresión Natvis, el identificador hace referencia al campo denominado `x` en el objeto que se visualiza, no a una variable local denominada `x` en la función en ejecución. En las expresiones Natvis no se puede acceder a variables locales, aunque sí a variables globales.  
  
-   Las expresiones Natvis no admiten la evaluación o los efectos secundarios de las funciones. Esto significa que se omiten las llamadas y los operadores de asignación. Puesto que las [funciones intrínsecas del depurador](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) no tienen efectos secundarios, pueden llamarse libremente desde cualquier expresión Natvis aunque no se permitan otras llamadas de función.  
  
 Para controlar cómo se muestra una expresión en una ventana de variables, puede usar cualquiera de los especificadores de formato que se describen en la [especificadores de formato](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) sección de la [especificadores de formato en C++](../debugger/format-specifiers-in-cpp.md) tema. Tenga en cuenta que los especificadores de formato se omiten cuando la entrada de virtualización es Natvis usa internamente, como el `Size` expresión en una [expansión de ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  
  
## <a name="natvis-views"></a>Vistas de Natvis  
 Las vistas de Natvis le permiten ver cualquier tipo de más de una manera. Por ejemplo, puede definir una vista denominada **simple** que le ofrezca una vista simplificada de un tipo. Por ejemplo, aquí se muestra la visualización de `std::vector`:
  
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
  
 Los elementos `DisplayString` y `ArrayItems` se usan en la vista predeterminada y en la vista simple, mientras que los elementos `[size]` y `[capacity]` están excluidos de la vista simple. Puede usar el especificador de formato **,view** para especificar una vista alternativa. En la ventana **Inspección** , especifique la vista simple como **vec,view(simple)**:  
  
 ![Ventana Inspección con la vista simple](../debugger/media/watch-simpleview.png "SimpleView de inspección")  
  
##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnosticar errores de Natvis  
 Puede usar los diagnósticos de Natvis para solucionar problemas de sintaxis y errores de análisis. Cuando el depurador detecta errores en una entrada de visualización, omite los errores y muestra el tipo en formato sin procesar o elige otra visualización adecuada. Para comprender por qué se omite una determinada entrada de visualización y para ver cuáles son los errores subyacentes, puede activar los diagnósticos de Natvis **Herramientas > Opciones > depuración > ventana de salida > mensajes de diagnóstico de Natvis (solo en C++)** opción. Los errores se muestran en la ventana **Salida** .  
  
##  <a name="BKMK_Syntax_reference"></a> Referencia de la sintaxis de Natvis  
  
###  <a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer  
 El elemento `AutoVisualizer`  es el nodo raíz del archivo .natvis y contiene el atributo `xmlns:` del espacio de nombres.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  
  
###  <a name="BKMK_Type"></a> Elemento Type  
 Este es el aspecto de un elemento Type básico:  
  
```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  
  
 Especifica:  
  
1.  Para qué tipo de visualización debería usarse (el atributo `Type Name` ).  
  
2.  Cómo debe ser el valor de un objeto de ese tipo (el elemento `DisplayString` ).  
  
3.  Cómo deben ser los miembros del tipo cuando el usuario los expande en una ventana de variables (el nodo `Expand` ).  
  
 **Clases con plantilla** El atributo `Name` del elemento `Type` acepta un asterisco `*` como carácter comodín que se puede usar para los nombres de clase con plantilla:  
  
```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
  
```  
  
 En este ejemplo, se utiliza la misma visualización si el objeto es un `CAtlArray<int>` o `CAtlArray<float>`. Si hay una entrada específica de visualización para una `CAtlArray<float>`, esta tendrá prioridad sobre la genérica.  
  
 Observe que se puede hacer referencia a los parámetros de plantilla en la entrada de visualización mediante macros $T1, $T2, etc. Para buscar ejemplos de estas macros, vea los archivos .natvis incluidos con Visual Studio.  
  
####  <a name="BKMK_Visualizer_type_matching"></a> Coincidencia de tipos del visualizador  
 Si no se puede validar una entrada de visualización, se usará la siguiente visualización disponible.  
  
#### <a name="inheritable-attribute"></a>Atributo heredable  
 Puede especificar si una visualización se aplica únicamente a un tipo base o a un tipo base y a todos los tipos derivados con el atributo opcional `Inheritable` . En el código siguiente, la visualización solo se aplica al tipo `BaseClass` :  
  
```xml
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  
  
 El valor predeterminado de `Inheritable` es `true`.  
  
#### <a name="priority-attribute"></a>Atributo de prioridad  
 El atributo `Priority` especifica el orden en el que se usan las definiciones alternativas si no se puede analizar una definición. Los valores posibles de `Priority` son: `Low`, `MediumLow`,`Medium`, `MediumHigh`y `High`; el valor predeterminado es `Medium`.  
  
 El atributo de prioridad solo se debe usar para distinguir entre las prioridades dentro del mismo archivo .natvis, no entre distintos archivos.  
  
 En el ejemplo siguiente, primero se analizar la entrada que coincida con la STL de 2015 y, si el análisis falla, se utiliza la entrada alternativa para la versión 2013 de la STL:  
  
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
  
####  <a name="BKMK_Versioning"></a> Elemento Version  
 Utilice el elemento `Version` para delimitar las visualizaciones a módulos concretos y sus versiones de manera que se puedan minimizar los conflictos de nombres y se puedan usar diferentes visualizaciones para distintas versiones de los tipos. Por ejemplo:  
  
```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 En este ejemplo, la visualización solo se aplica al tipo `DirectUI::Border` incluido en el objeto `Windows.UI.Xaml.dll` de las versiones 1.0 a 1.5. Agregar elementos de versión se establece el ámbito de la entrada de visualización a un módulo en particular y la versión y reducirán las divergencias inadvertidas. Sin embargo, si un tipo se define en un archivo de encabezado común usado por módulos diferentes, la visualización con versión no se aplica cuando el tipo no está en el módulo especificado.  
  
#### <a name="optional-attribute"></a>Atributo opcional  
 El atributo `Optional` puede aparecer en cualquier nodo. Si no se puede analizar cualquier subexpresión dentro de un nodo opcional, se omitirá dicho nodo, pero el resto del elemento de tipo sigue siendo válido. En el siguiente tipo, `[State]` no es opcional, pero `[Exception]` sí lo es.  Esto significa que si `MyNamespace::MyClass` contiene un campo denominado _`M_exceptionHolder`, sigue sin ver ambos `[State]` nodo y `[Exception]` nodo, pero si el `_M_exceptionHolder` falta, solo se ve el `[State]` nodo.
  
```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  
  
###  <a name="BKMK_Condition_attribute"></a> Atributo Condition  
 El atributo `Condition` opcional está disponible para muchos elementos de visualización y especifica cuándo se debe usar una regla de visualización. Si la expresión del atributo Condition se resuelve como `false`, no se aplicará la regla de visualización especificada por el elemento. Si se evalúa como True o si no hay ningún atributo `Condition` , la regla de visualización se aplica al tipo. Puede usar este atributo para la lógica `if-else` en las entradas de visualización. Por ejemplo, la siguiente visualización tiene dos `DisplayString` elementos para un tipo de puntero inteligente:  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
  
```  
  
 Cuando el miembro `_Myptr` es `null`, la condición del primer elemento `DisplayString` se resuelve como `true`, de manera que se muestra dicho formulario. Cuando el miembro `_Myptr` no es `null`, la condición se evalúa como `false`y se muestra el segundo elemento `DisplayString` .  
  
### <a name="includeview-and-excludeview-attributes"></a>Atributos IncludeView y ExcludeView  
 Estos atributos especifican los elementos que se deben mostrar u ocultar en distintas vistas. Por ejemplo, dada la especificación de Natvis de `std::vector`:  
  
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
  
 La vista simple no muestra los elementos [size] ni [capacity] en la vista simple. Si se hubiera usado `IncludeView="simple"` en lugar de `ExcludeView`, los elementos `[size]` y `[capacity]` se mostrarían en la vista simple, y no en la vista predeterminada.  
  
 Puede usar los atributos `IncludeView` y `ExcludeView` en los tipos y en los miembros individuales.  
  
###  <a name="BKMK_DisplayString"></a> DisplayString  
 Un elemento `DisplayString` especifica la cadena que se mostrará como valor de la variable. Acepta cadenas arbitrarias mezcladas con expresiones. Todos los datos encerrados entre llaves se interpretan como una expresión. Por ejemplo, un `DisplayString` entrada similar al siguiente:  
  
```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
  
```  
  
 Significa que las variables de tipo `CPoint` se muestran como en esta ilustración:  
  
 ![Usar un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "DBG_NATVIS_CPoint_DisplayString")  
  
 En la expresión `DisplayString` , `x` e `y`, que son miembros de `CPoint`, se encuentran dentro de llaves, por lo que sus valores se evalúan. La expresión también muestra cómo se puede omitir una llave con llaves dobles ( `{{` o `}}` ).  
  
> [!NOTE]
>  El elemento `DisplayString` es el único que acepta cadenas arbitrarias y la sintaxis de llaves. Todos los demás elementos de visualización solo aceptan expresiones que evalúa el depurador.  
  
###  <a name="BKMK_StringView"></a> StringView  
 El elemento `StringView` define la expresión cuyo valor se va a enviar al visualizador de texto integrado. Por ejemplo, suponga que tenemos la visualización siguiente para el tipo `ATL::CStringT` :  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  
  
 La visualización muestra un objeto `CStringT` en una ventana de variable como la siguiente:   
  
 ![Elemento CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "DBG_NATVIS_DisplayString_CStringT")  
  
 Agregar un `StringView` elemento indica al depurador que este valor se puede ver mediante una visualización de texto:  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  
  
 Observe el icono de lupa que aparece junto al valor siguiente. Seleccione el icono de inicia el visualizador de texto que se mostrará la cadena que `m_pszData` apunta a.  
  
 ![Datos CStringT con visualizador StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "DBG_NATVIS_StringView_CStringT")  
  
> [!NOTE]
>  Observe que la expresión `{m_pszData,su}` incluye un especificador de formato de C++, `su` , para mostrar el valor como cadena Unicode. Vea [Format Specifiers in C++](../debugger/format-specifiers-in-cpp.md) para obtener más información.  
  
###  <a name="BKMK_Expand"></a> Expand  
 El nodo `Expand` se utiliza para personalizar los elementos secundarios del tipo visualizado cuando el usuario los expande en las ventanas de variables. Acepta una lista de nodos secundarios que definen los elementos secundarios.  
  
 El nodo `Expand` es opcional.  
  
-   Si un `Expand` nodo no se especifica en una entrada de visualización, se usan las reglas de expansión de Visual Studio de forma predeterminada.  
  
-   Si un `Expand` nodo está especificado sin nodos secundarios, el tipo de no ser expandible en las ventanas del depurador.  
  
####  <a name="BKMK_Item_expansion"></a> Expansión de Item  
 El elemento `Item` es el elemento más básico y más común que se usará en un nodo `Expand` . `Item` define un único elemento secundario. Por ejemplo, suponga que tiene una clase `CRect` con `top`, `left`, `right`y `bottom` como campos y la siguiente entrada de visualización:  
  
```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
  
```  
  
 El tipo `CRect` tendrá este aspecto:  
  
 ![CRect con expansión de elementos Item](../debugger/media/dbg_natvis_expand_item_crect1.png "DBG_NATVIS_Expand_Item_CRect1")  
  
 Las expresiones especificadas en los elementos `Width` y `Height` se evalúan y se muestran en la columna Valor. El depurador crea automáticamente el nodo `[Raw View]` siempre que se use una extensión personalizada. Se expande en la captura de pantalla anterior para mostrar cómo la vista sin formato del objeto es diferente de su visualización. La expansión predeterminada de Visual Studio crea un subárbol para la clase base y muestra todos los miembros de datos de la clase base como elementos secundarios.  
  
> [!NOTE]
>  Si la expresión del elemento Item apunta a un tipo complejo, el propio nodo `Item` se puede expandir.  
  
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
  
 ![std:: vector que usa expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  
  
 Como mínimo, el nodo `ArrayItems` debe tener lo siguiente:  
  
1.  Una expresión `Size` (que debe evaluarse como entero) para que el depurador comprenda la longitud de la matriz  
  
2.  Una expresión `ValuePointer` que debe apuntar al primer elemento (que debe ser un puntero de un tipo de elemento que no sea `void*`).  
  
 El valor predeterminado del límite inferior de la matriz es 0. El valor se puede invalidar mediante un elemento `LowerBound` (se pueden encontrar ejemplos en los archivos .natvis incluidos con Visual Studio).  
  
 Ahora puede usar el operador `[]` con una expansión `ArrayItems` , por ejemplo `vector[i]`. El operador [] se puede usar con cualquier visualización de una matriz unidimensional que use `ArrayItems` o `IndexListItems`, incluso si el propio tipo no lo admite (por ejemplo, `CATLArray`).  
  
 También se pueden especificar matrices multidimensionales. El depurador necesita información ligeramente más para mostrar correctamente los elementos secundarios en ese caso:  
  
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
  
 `Direction` especifica si la matriz se ordena por fila principal o por columna principal. `Rank` especifica el rango de la matriz. El `Size` elemento acepta la parte implícita `$i` parámetro, que sustituye al índice de dimensión para buscar la longitud de la matriz en esa dimensión. Por ejemplo, en el ejemplo anterior, la expresión `_M_extent.M_base[0]` debe proporcionar la longitud de la dimensión 0, `_M_extent._M_base[1]` la de la dimensión 1 y así sucesivamente.  
  
 Aquí se muestra cómo un bidimensional `Concurrency::array` objeto busca en el depurador:  
  
 ![Matriz bidimensional con expansión ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  
  
####  <a name="BKMK_IndexListItems_expansion"></a> Expansión de IndexListItems  
 Puede usar la expansión `ArrayItems` solo si los elementos de matriz están dispuestos de forma contigua en la memoria. El depurador obtiene el elemento siguiente al incrementar simplemente el puntero al elemento actual. Para admitir casos donde es necesario manipular el índice al nodo de valor, se pueden usar nodos `IndexListItems` . Esta es una visualización con `IndexListItems` nodo:  
  
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
  
 Ahora puede usar el operador `[]` con una expansión `IndexListItems` , por ejemplo `vector[i]`. El operador `[]` se puede usar con cualquier visualización de una matriz unidimensional que use `ArrayItems` o `IndexListItems`, incluso si el propio tipo no lo admite (por ejemplo, `CATLArray`).  
  
 La única diferencia entre `ArrayItems` y `IndexListItems` reside en que `ValueNode` espera la expresión completa para el elemento<sup>n</sup> con el parámetro `$i` implícito.  
  
####  <a name="BKMK_LinkedListItems_expansion"></a> Expansión de LinkedListItems  
 Si el tipo visualizado representa una lista vinculada, el depurador puede mostrar sus elementos secundarios si se usa un nodo `LinkedListItems` . Esta es la visualización de la `CAtlList` el tipo con esta característica:  
  
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
  
-   Las expresiones `NextPointer` y `ValueNode` se evalúan en el contexto del elemento del nodo de lista de vínculo, no del tipo de lista primario. En el ejemplo anterior, `CAtlList` tiene un `CNode` clase (se encuentra en `atlcoll.h`) que representa un nodo de la lista vinculada. Los objetos`m_pNext` y `m_element` son campos de la clase `CNode` class y not of `CAtlList` .  
  
-   `ValueNode` puede dejarse vacío o usar `this` para hacer referencia al propio nodo de lista de vínculo.  
  
#### <a name="customlistitems-expansion"></a>Expansión CustomListItems  
 La expansión `CustomListItems` le permite escribir una lógica personalizada para recorrer una estructura de datos, como una tabla hash. Debe usar `CustomListItems` para visualizar datos estructuras en que todo lo que necesita evaluar se pueda expresar mediante expresiones de C++, pero no se ajustan lo suficiente al molde para `ArrayItems`, `TreeItems`, o `LinkedListItems.`  
  
 El visualizador de CAtlMap es un ejemplo excelente de dónde es adecuado `CustomListItems` .  
  
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

Puede usar `Exec` para ejecutar el código dentro de un `CustomListItems` expansión mediante las variables y los objetos definidos en el `CustomListItems` expansión. No se puede utilizar `Exec` para evaluar las funciones.

Puede usar operadores lógicos, operadores aritméticos y operadores de asignación con `Exec`.

Se admiten las siguientes funciones intrínsecas:

- `strlen, wcslen, strnlen, wcsnlen, strcmp, wcscmp, _stricmp, _strcmpi, _wcsicmp, strncmp, wcsncmp, _strnicmp, _wcsnicmp, memcmp, memicmp, wmemcmp, strchr, wcschr, memchr, wmemchr, strstr, wcsstr, __log2, __findNonNull`
- `GetLastError, TlsGetValue, DecodeHString, WindowsGetStringLen, WindowsGetStringRawBuffer, WindowsCompareStringOrdinal, RoInspectCapturedStackBackTrace, CoDecodeProxy, GetEnvBlockLength, DecodeWinRTRestrictedException, DynamicMemberLookup, DecodePointer, DynamicCast`
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
 Si el tipo visualizado representa un árbol, el depurador puede recorrer el árbol y mostrar sus elementos secundarios utilizando un nodo `TreeItems` . Esta es la visualización de la `std::map` el tipo con esta característica:  
  
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
  
 La sintaxis es similar a la `LinkedListItems` nodo. Los objetos`LeftPointer`, `RightPointer`y `ValueNode` are evaluated under the context of the tree node classy `ValueNode` puede dejarse vacío o incluir el objeto `this` para hacer referencia al propio nodo de árbol.  
  
####  <a name="BKMK_ExpandedItem_expansion"></a> Expansión de ExpandedItem  
 El elemento `ExpandedItem` se puede utilizar para generar una vista secundaria agregada que muestre las propiedades de las clases base o los miembros de datos como si fueran elementos secundarios del tipo visualizado. Se evalúa la expresión especificada y se anexan los nodos secundarios del resultado a la lista secundaria del tipo visualizado. Por ejemplo, suponga que tenemos un tipo de puntero inteligente `auto_ptr<vector<int>>`, que normalmente se muestra como:  
  
 ![Auto&#95;ptr&#60;vector&#60;int&#62; &#62; expansión predeterminada](../debugger/media/dbg_natvis_expand_expandeditem_default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  
  
 Para ver los valores del vector, tiene que examinar en la ventana de variables dos niveles que pasan por el miembro _Myptr. Al agregar un elemento `ExpandedItem` , puede eliminar la variable `_Myptr` de la jerarquía y ver directamente los elementos de vector:  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 ![Auto&#95;ptr&#60;vector&#60;int&#62; &#62; expansión de ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  
  
 En el ejemplo siguiente se muestra cómo agregar propiedades de la clase base en una clase derivada. Supongamos que la clase `CPanel` se deriva de `CFrameworkElement`. En lugar de repetir las propiedades procedentes de la clase base `CFrameworkElement` , el nodo `ExpandedItem` permite anexar esas propiedades a la lista secundaria de la clase `CPanel` . El **nd** especificador de formato, que desactiva la visualización de búsqueda de coincidencias para la clase derivada, aquí es necesario. En caso contrario, la expresión `*(CFrameworkElement*)this` hace que el `CPanel` visualización se vuelva a aplicar porque las reglas de coincidencia de tipos de la visualización predeterminada consideran la más adecuada. Mediante el **nd** especificador de formato indica al depurador que use la visualización de la clase base o la expansión predeterminada de la clase base si la clase base no tiene una visualización.  
  
```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Synthetic_Item_expansion"></a> Expansión de elemento Synthetic  
 En los casos donde el elemento `ExpandedItem` elimina las jerarquías para proporcionar una vista de datos más plana, el nodo `Synthetic` hace lo contrario. Permite crear un elemento secundario artificial (es decir, un elemento secundario que no es un resultado de una expresión). Este elemento secundario puede contener elementos secundarios propios. En el ejemplo siguiente, la visualización del tipo `Concurrency::array` usa un nodo `Synthetic` para mostrar un mensaje de diagnóstico al usuario:  
  
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
  
 ![Concurrency:: Array con expansión de elementos sintético](../debugger/media/dbg_natvis_expand_synthetic.png "DBG_NATVIS_Expand_Synthetic")  
  
###  <a name="BKMK_HResult"></a> HResult  
 El elemento `HResult` permite personalizar la información que se muestra para un tipo de datos HRESULT en las ventanas del depurador. El elemento `HRValue` debe contener el valor de 32 bits de HRESULT que se debe personalizar. El elemento `HRDescription` contiene la información que se muestra en el depurador.  
  
```  
  
<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  
  
###  <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 Un elemento `UIVisualizer` registra un complemento de visualizador gráfico en el depurador. Un complemento de visualizador gráfico crea un cuadro de diálogo u otra interfaz para mostrar una variable o un objeto de forma adecuada según su tipo de datos. El complemento del visualizador se debe crear como [VSPackage](../extensibility/internals/vspackages.md) y tiene que exponer un servicio que el depurador pueda consumir. El archivo .natvis contiene información de registro del complemento, como su nombre, el GUID del servicio expuesto y los tipos que puede visualizar.  
  
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
  
 Un elemento `UIVisualizer` se identifica mediante un par de atributos `ServiceId` - `Id` . `ServiceId` es el GUID del servicio expuesto por el paquete del visualizador, `Id` es un identificador único que se puede utilizar para diferenciar los visualizadores si un servicio proporciona más de un visualizador. En el ejemplo anterior, el mismo servicio del visualizador proporciona dos visualizadores.  
  
 El atributo `MenuName` es lo que los usuarios ven como el nombre del visualizador cuando abren el menú desplegable junto al icono de lupa en las ventanas de variables del depurador, por ejemplo:  
  
 ![Menú contextual de UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  
  
 Cada tipo definido en el archivo .natvis debe mostrar explícitamente los visualizadores de la interfaz de usuario que lo pueden mostrar. El depurador coincide con las referencias del visualizador de las entradas de tipo para que los tipos coincidan con los visualizadores registrados. Por ejemplo, la siguiente entrada de tipos para `std::vector` hace referencia el elemento UIVisualizer del ejemplo anterior.  
  
```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  
  
 Puede ver un ejemplo de UIVisualizer en la extensión Image Watch usada para ver los mapas de bits en memoria: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  
  
### <a name="customvisualizer-element"></a>Elemento CustomVisualizer  
 `CustomVisualizer` es un punto de extensibilidad que especifica una extensión VSIX que puede escribir para controlar la visualización en un código que se ejecuta en Visual Studio. Para obtener más información sobre cómo escribir extensiones VSIX, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Escribir un visualizador personalizado es mucho más trabajo que escribir una definición de natvis XML, pero le libera de las restricciones sobre qué natvis admite o no es compatible con. Los visualizadores personalizados tienen acceso a todo el conjunto de API de extensibilidad del depurador, que se pueden usar para consultar y modificar el proceso de depurado o para comunicarse con otras partes de Visual Studio.  
  
 Puede usar los atributos `Condition`, `IncludeView`y `ExcludeView` en los elementos CustomVisualizer.