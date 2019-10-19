---
title: Depurar código de usuario con Solo mi código | Microsoft Docs
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c1d474b388dd8f116eb53febb8a472d4c5b8150
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535997"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Depurar solo código de usuario con Solo mi código

*Solo mi código* es una característica de depuración de Visual Studio que recorre automáticamente las llamadas a System, Framework y otro código que no es de usuario. En la ventana **pila de llamadas** , solo mi código contrae estas llamadas en marcos **[código externo]** .

Solo mi código funciona de forma diferente en C++proyectos de .net, y JavaScript.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar o deshabilitar Solo mi código

Para la mayoría de los lenguajes de programación, Solo mi código está habilitada de forma predeterminada.

- Para habilitar o deshabilitar Solo mi código en Visual Studio, en **herramientas**  > **Opciones** (o **depurar** **Opciones**de  > ) > **depuración**  > **General**, Active o desactive **Habilitar solo mi código**.

![Habilitar Solo mi código en el cuadro de diálogo Opciones](../debugger/media/dbg_justmycode_options.png "Habilitar Solo mi código")

> [!NOTE]
> **Habilitar solo mi código** es una configuración global que se aplica a todos los proyectos de Visual Studio en todos los lenguajes.

## <a name="just-my-code-debugging"></a>depuración de Sólo mi código

Durante una sesión de depuración, la ventana **módulos** muestra los módulos de código que el depurador trata como mi código (código de usuario), junto con su estado de carga de símbolos. Para obtener más información, vea [familiarizarse con el modo en que el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).

![Código de usuario en la ventana módulos](../debugger/media/dbg_justmycode_module.png "Código de usuario en la ventana módulos")

En la ventana **pila de llamadas** o **tareas** , solo mi código contrae el código que no es de usuario en un marco de código anotado en gris con la etiqueta `[External Code]`.

![Marco de código externo en la ventana pila de llamadas](../debugger/media/dbg_justmycode_externalcode.png "Marco de código externo")

>[!TIP]
>Para abrir los **módulos**, **pila de llamadas**, **tareas**o la mayoría de las ventanas de depuración, debe estar en una sesión de depuración. Durante la depuración, en **Depurar**  > **Windows**, seleccione las ventanas que desea abrir.

<a name="BKMK_Override_call_stack_filtering"></a>Para ver el código de un marco contraído **[código externo]** , haga clic con el botón secundario en la ventana **pila de llamadas** o **tarea** y seleccione **Mostrar código externo** en el menú contextual. Las líneas de código externo expandidas reemplazan el marco **[código externo**].

![Mostrar código externo en la ventana pila de llamadas](../debugger/media/dbg_justmycode_showexternalcode.png "Mostrar código externo")

> [!NOTE]
> **Mostrar código externo** es una configuración de generador de perfiles de usuario actual que se aplica a todos los proyectos de todos los idiomas abiertos por el usuario.

Al hacer doble clic en una línea de código externa expandida en la ventana **pila de llamadas** , se resalta la línea de código de llamada en verde en el código fuente. En el caso de los archivos dll u otros módulos no encontrados o cargados, es posible que se abra una página de símbolos o de origen no encontrado.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>Solo mi código .NET

En los proyectos de .NET, Solo mi código usa archivos de símbolos ( *. pdb*) y optimizaciones de programas para clasificar el código de usuario y el código que no es de usuario. El depurador de .NET considera archivos binarios optimizados y archivos *. pdb* no cargados como código que no es de usuario.

Tres atributos de compilador también afectan a lo que el depurador de .NET considera como código de usuario:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al depurador que el código al que se aplica no es código de usuario.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta el código para el depurador, incluso si Solo mi código está desactivado.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra paso a paso el código al que se aplica, en lugar de ir al código.

El depurador de .NET considera que el resto del código es código de usuario.

Durante la depuración de .NET:

- **Depure**  > **paso a paso** por instrucciones (o **F11**) en el código que no es de usuario sobre el código a la siguiente línea de código de usuario.
- **Depurar**  > **paso a paso para salir** (o **MAYÚS** +**F11**) en el código que no es de usuario se ejecuta en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, llega a otro punto de interrupción o produce un error.

<a name="BKMK_NET_Breakpoint_behavior"></a>Si el depurador se interrumpe en el código que no es de usuario (por ejemplo, se usa **Debug**  > **interrumpir todo** y pausar en código que no es de usuario), aparece la ventana **no Source** . Después, puede usar el comando **Depurar**  > **paso** para ir a la siguiente línea de código de usuario.

Si se produce una excepción no controlada en código que no es de usuario, el depurador se interrumpe en la línea de código de usuario donde se generó la excepción.

Si las excepciones de primera oportunidad están habilitadas para la excepción, la línea de código de usuario que realiza la llamada se resalta en verde en el código fuente. La ventana **pila de llamadas** muestra el marco anotado con la etiqueta **[código externo]** .

## <a name="BKMK_C___Just_My_Code"></a> Solo mi código de C++

A partir de la versión 15,8 de Visual Studio 2017, también se admite la Solo mi código para la ejecución paso a paso de código. Esta característica también requiere el uso del modificador de compilador [/JMC (solo mi depuración de código)](/cpp/build/reference/jmc) . El modificador está habilitado de C++ forma predeterminada en los proyectos de. En el caso de la ventana **pila de llamadas** y la compatibilidad con la pila de llamadas en solo mi código, no es necesario el modificador/JMC

<a name="BKMK_CPP_User_and_non_user_code"></a>Para que se clasifique como código de usuario, el archivo PDB para el binario que contiene el código de usuario debe cargarse mediante el depurador (use la ventana **módulos** para comprobarlo).

En el comportamiento de la pila de llamadas, como en la ventana **pila** de C++ llamadas, solo mi código en considera que solo estas funciones *son código que no es de usuario*:

- Funciones con información de origen eliminada en su archivo de símbolos.
- Funciones en las que los archivos de símbolos indican que no hay ningún archivo de código fuente correspondiente al marco de pila.
- Funciones especificadas en los archivos *\*. natjmc* de la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

En el caso del comportamiento de la C++ ejecución de código, solo mi código en considera que solo estas funciones *son código que no es de usuario*:

- Funciones para las que el archivo PDB correspondiente no se ha cargado en el depurador.
- Funciones especificadas en los archivos *\*. natjmc* de la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

> [!NOTE]
> Para la compatibilidad con la ejecución de C++ código en solo mi código, el código debe compilarse con los compiladores MSVC en Visual Studio 15,8 Preview 3 o posterior, y el modificador de compilador/JMC debe estar habilitado (está habilitado de forma predeterminada). Para obtener más información, [vea C++ personalizar el comportamiento de la pila de llamadas y la ejecución de código](#BKMK_CPP_Customize_call_stack_behavior)) y esta entrada de [blog](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Para el código compilado mediante un compilador anterior, los archivos *. natstepfilter* son la única manera de personalizar la ejecución de código, que es independiente de solo mi código. Consulte [personalizar C++ el comportamiento](#BKMK_CPP_Customize_stepping_behavior)de la ejecución de instrucciones.

<a name="BKMK_CPP_Stepping_behavior"></a>Durante C++ la depuración:

- **Depure**  > **paso a paso** por instrucciones (o **F11**) en el código que no es de usuario sobre el código a la siguiente línea de código de usuario.
- **Depurar**  > **paso a paso para salir** (o **MAYÚS** +**F11**) en el código que no es de usuario se ejecuta en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, llega a otro punto de interrupción o produce un error.

Si el depurador se interrumpe en código que no es de usuario (por ejemplo, se usa **Debug**  > **interrumpir todo** y pausar en código que no es de usuario), la ejecución paso a paso continúa en el código que no es de usuario.

Si el depurador llega a una excepción, se detiene en la excepción, independientemente de si está en código de usuario o que no es de usuario. Las opciones **no controladas** por el usuario en el cuadro de diálogo **configuración de excepciones** se omiten.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personalizar C++ el comportamiento de la pila de llamadas y la ejecución de código

En C++ el caso de los proyectos, puede especificar los módulos, archivos de código fuente y funciones que la ventana **pila de llamadas** trata como código que no es de usuario si los especifica en *\* archivos. natjmc* . Esta personalización también se aplica a la ejecución paso a paso de código si usa el compilador más reciente (vea [ C++ solo mi código](#BKMK_CPP_User_and_non_user_code)).

- Para especificar código que no es de usuario para todos los usuarios del equipo de Visual Studio, agregue el archivo *.natjmc* a la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Para especificar el código que no es de usuario para un usuario individual, agregue el archivo *. natjmc* a los *documentos de%userprofile%\My \\ < versión de Visual Studio \> carpeta \visualizers* .

Un archivo *. natjmc* es un archivo XML con esta sintaxis:

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **Atributos del elemento Module**

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Requerido. Ruta de acceso completa al módulo o los módulos. Puede usar los caracteres comodín de Windows `?` (cero o un carácter) y `*` (cero o más caracteres). Por ejemplo,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al depurador que trate como código externo todos los módulos de *\3rdParty\UtilLibs* en cualquier unidad.|
|`Company`|Opcional. Nombre de la compañía que publica el módulo que está incrustado en el archivo ejecutable. Puede utilizar este atributo para eliminar la ambigüedad de los módulos.|

 **Atributos del elemento File**

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Requerido. Ruta de acceso completa del archivo o archivos de código fuente que se van a tratar como código externo. Puede usar los caracteres comodín `?` y `*` de Windows para especificar la ruta de acceso.|

 **Atributos del elemento Function**

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Requerido. Nombre completo de la función que se va a tratar como código externo.|
|`Module`|Opcional. Nombre o ruta de acceso completa al módulo que contiene la función. Puede utilizar este atributo para eliminar la ambigüedad de funciones que tienen el mismo nombre.|
|`ExceptionImplementation`|Cuando se establece en `true`, la pila de llamadas muestra la función que produjo la excepción en lugar de esta función.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a>Personalizar C++ el comportamiento de ejecución independientemente de la configuración de solo mi código

En C++ los proyectos de, puede especificar las funciones que se van a depurar si se enumeran como código que no es de usuario en *\* archivos. natstepfilter* . Las funciones enumeradas en *\* archivos. natstepfilter* no dependen de la configuración de solo mi código.

- Para especificar código que no es de usuario para todos los usuarios locales de Visual Studio, agregue el archivo *. natstepfilter* a la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Para especificar el código que no es de usuario para un usuario individual, agregue el archivo *. natstepfilter* a los *documentos de%userprofile%\My \\ < versión de Visual Studio \> carpeta \visualizers* .

Un archivo *. natstepfilter* es un archivo XML con esta sintaxis:

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|Elemento|Descripción|
|-------------|-----------------|
|`Function`|Requerido. Especifica una o más funciones como funciones que no son de usuario.|
|`Name`|Requerido. Expresión regular con formato ECMA-262 que especifica el nombre de función completo que debe coincidir. Por ejemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al depurador que todos los métodos de `MyNS::MyClass` deben considerarse código que no es de usuario. La coincidencia distingue mayúsculas de minúsculas.|
|`Module`|Opcional. Expresión regular con formato ECMA-262 que especifica la ruta de acceso completa al módulo que contiene la función. La búsqueda no distingue entre mayúsculas y minúsculas.|
|`Action`|Requerido. Uno de estos valores que distingue mayúsculas y minúsculas:<br /><br /> `NoStepInto`: indica al depurador que se desplazará por la función.<br /> `StepInto`: indica al depurador que se depure paso a paso por la función, invalidando cualquier otro `NoStepInto` para la función coincidente.|

## <a name="BKMK_JavaScript_Just_My_Code"></a> Solo mi código de JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> Solo mi código de JavaScript controla la ejecución paso a paso y la presentación de la pila de llamadas categorizando el código en una de estas clasificaciones:

|||
|-|-|
|**MyCode**|Código de usuario que posee y controla.|
|**LibraryCode**|Código que no es de usuario de las bibliotecas que se usan con regularidad y en la que se basa la aplicación para funcionar correctamente (por ejemplo, WinJS o jQuery).|
|**UnrelatedCode**|Código que no es de usuario en la aplicación que no es de su propiedad y cuya aplicación no se basa en funcionar correctamente. Por ejemplo, un SDK de publicidad que muestra anuncios podría ser UnrelatedCode. En los proyectos de UWP, cualquier código que se cargue en la aplicación desde un URI HTTP o HTTPS también se considera UnrelatedCode.|

El depurador de JavaScript clasifica el código como usuario o no usuario en este orden:

1. Las clasificaciones predeterminadas.
   - El script que se ejecuta pasando una cadena a la función de `eval` proporcionada por el host es he **code**.
   - El script que se ejecuta pasando una cadena al constructor `Function` es **LibraryCode**.
   - El script en una referencia de Framework, como WinJS o el SDK de Azure, es **LibraryCode**.
   - El script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval` es **UnrelatedCode**.

2. Clasificaciones especificadas para todos los proyectos de JavaScript de Visual Studio en el archivo *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.WWA.JSON* .

3. Clasificaciones en el archivo de *código de. JSON* del proyecto actual.

Cada paso de clasificación invalida los pasos anteriores.

Todo el código restante se clasifica como **MyCode**.

Puede modificar las clasificaciones predeterminadas y clasificar determinados archivos y direcciones URL como código de usuario o de no usuario; para ello, agregue un archivo *. JSON* denominado mi *código. JSON* a la carpeta raíz de un proyecto de JavaScript. Consulte [Personalización de JavaScript solo mi código](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>Durante la depuración de JavaScript:

- Si una función es código que no es de usuario, **debug**  > **Step into** (o **F11**) se comporta igual que **Debug  >  depurar** **paso a paso por procedimientos** (o **F10**).
- Si un paso comienza en código que no es de usuario (**LibraryCode** o **UnrelatedCode**), la ejecución paso a paso se comporta temporalmente como si solo mi código no estuviera habilitado. Al volver a código de usuario, Solo mi código se vuelve a habilitar la ejecución paso a paso.
- Cuando un paso de código de usuario hace que se abandone el contexto de ejecución actual, el depurador se detiene en la siguiente línea de código de usuario ejecutada. Por ejemplo, si se ejecuta una devolución de llamada en código **LibraryCode**, el depurador continúa hasta que se ejecuta la línea de código de usuario siguiente.
- **Paso a paso para salir** (o **MAYÚS** +**F11**) se detiene en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, llega a otro punto de interrupción o produce un error.

Siempre se alcanzan los puntos de interrupción establecidos en el código, pero se clasifica el código.

- Si la palabra clave `debugger` aparece en **LibraryCode**, el depurador siempre se interrumpe.
- Si la palabra clave `debugger` aparece en **UnrelatedCode**, el depurador no se detiene.

<a name="BKMK_JS_Exception_behavior"></a>Si se produce una excepción no controlada en el código **monocode** o **LibraryCode** , el depurador siempre se interrumpe.

Si se produce una excepción no controlada en **UnrelatedCode** **, y** **LibraryCode** está en la pila de llamadas, se interrumpe el depurador.

Si las excepciones de primera oportunidad están habilitadas para la excepción y la excepción se produce en **LibraryCode** o **UnrelatedCode**:

- Si se controla la excepción, el depurador no se interrumpe.
- Si la excepción no se controla, se interrumpe el depurador.

### <a name="BKMK_JS_Customize_Just_My_Code"></a>Personalización de Solo mi código de JavaScript

Para clasificar el código de usuario y de no usuario para un único proyecto de JavaScript, puede Agregar un archivo *. JSON* denominado mi *código. JSON* a la carpeta raíz del proyecto.

Las especificaciones de este archivo invalidan las clasificaciones predeterminadas y el archivo de *código de WWA. JSON* . No es necesario que el archivo de *código. JSON* Enumere todos los pares clave-valor. Los valores de **codificación**, **bibliotecas**y no **relacionados** pueden ser matrices vacías.

Los archivos de *codifique. JSON* usan esta sintaxis:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function y ScriptBlock**

Los pares clave-valor **Eval**, **Function** y **ScriptBlock** determinan cómo se clasifica el código generado dinámicamente:

|||
|-|-|
|**Eval**|Script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host. De forma predeterminada, el script Eval se clasifica como **MyCode**.|
|**Function**|Script que se ejecuta pasando una cadena al constructor de `Function`. De forma predeterminada, el script Function se clasifica como **LibraryCode**.|
|**ScriptBlock**|Script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval`. De forma predeterminada, el script ScriptBlock se clasifica como **UnrelatedCode**.|

Puede cambiar el valor a una de estas palabras clave:

- `MyCode` clasifica el script como **MyCode**.
- `Library` clasifica el script como **LibraryCode**.
- `Unrelated` clasifica el script como **UnrelatedCode**.

**MyCode, Libraries y Unrelated**

Los pares clave-valor **MyCode**, **Libraries** y **Unrelated** especifican las direcciones URL o los archivos que desea incluir en una clasificación:

|||
|-|-|
|**MyCode**|Matriz de direcciones URL o archivos que se clasifican como **MyCode**.|
|**Bibliotecas**|Matriz de direcciones URL o archivos que se clasifican como **LibraryCode**.|
|**Unrelated**|Matriz de direcciones URL o archivos que se clasifican como **UnrelatedCode**.|

La dirección URL o la cadena de archivo pueden tener uno o más caracteres `*`, que coinciden con cero o más caracteres. `*` es igual que la `.*` de la expresión regular.
