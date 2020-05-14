---
title: Depuración de código de usuario con Solo mi código | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535997"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Depuración de código de usuario exclusivamente con Solo mi código

*Solo mi código* es una característica de depuración de Visual Studio que depura paso a paso por procedimientos las llamadas al sistema, el marco y otro código que no es de usuario. En la ventana **Pila de llamadas**, Solo mi código contrae estas llamadas en marcos de **[código externo]** .

Solo mi código funciona de forma diferente en proyectos de .NET, C++ y JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar o deshabilitar Solo mi código

Para la mayoría de los lenguajes de programación, Solo mi código está habilitado de forma predeterminada.

- Para habilitar o deshabilitar Solo mi código en Visual Studio, en **Herramientas** > **Opciones**, o **Depurar** > **Opciones**, > **Depuración** > **General**, seleccione **Habilitar Solo mi código** o anule su selección.

![Habilitar Solo mi código en el cuadro de diálogo Opciones](../debugger/media/dbg_justmycode_options.png "Habilitar Solo mi código")

> [!NOTE]
> La configuración de **Habilitar Solo mi código** es una configuración global que se aplica a todos los proyectos de Visual Studio en todos los lenguajes.

## <a name="just-my-code-debugging"></a>depuración de Sólo mi código

Durante una sesión de depuración, la ventana **Módulos** muestra los módulos de código que el depurador trata como mi código (código de usuario), junto con su estado de carga de símbolos. Para más información, vea [Familiarizarse con el modo en que el depurador se asocia a la aplicación](../debugger/debugger-tips-and-tricks.md#modules_window).

![Código de usuario en la ventana Módulos](../debugger/media/dbg_justmycode_module.png "Código de usuario en la ventana Módulos")

En la ventana **Pila de llamadas** o **Tareas**, Solo mi código contrae el código que no es de usuario en un marco de código anotado atenuado con la etiqueta `[External Code]`.

![Marco Código externo en la ventana Pila de llamadas](../debugger/media/dbg_justmycode_externalcode.png "Marco Código externo")

>[!TIP]
>Para abrir las ventanas **Módulos**, **Pila de llamadas**, **Tareas** o la mayoría de las demás ventanas de depuración, debe estar en una sesión de depuración. Durante la depuración, en **Depurar** > **Windows**, seleccione las ventanas que desea abrir.

<a name="BKMK_Override_call_stack_filtering"></a> Para ver el código en un marco de **[código externo]** contraído, haga clic con el botón derecho en la ventana **Pila de llamadas** o **Tarea** y, después, seleccione **Mostrar código externo** en el menú contextual. Las líneas de código externo expandidas reemplazan el marco de **[código externo**].

![Mostrar código externo en la ventana Pila de llamadas](../debugger/media/dbg_justmycode_showexternalcode.png "Mostrar código externo")

> [!NOTE]
> **Mostrar código externo** es una configuración actual del generador de perfiles de usuario que se aplica a todos los proyectos en todos los lenguajes abiertos por el usuario.

Al hacer doble clic en una línea de código externo expandida en la ventana **Pila de llamadas**, se resalta la línea de código de llamada en verde en el código fuente. En el caso de los archivos DLL u otros módulos no encontrados o cargados, es posible que se abra una página de símbolos o de código fuente no encontrado.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Solo mi código de .NET

En los proyectos de .NET, Solo mi código usa archivos de símbolos ( *.pdb*) y optimizaciones de programas para clasificar código de usuario y que no es de usuario. El depurador de .NET considera los archivos binarios optimizados y archivos *.pdb* no cargados como código que no es de usuario.

Hay tres atributos del compilador que también afectan a lo que el depurador de .NET considera como código de usuario:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al depurador que el código al que se aplica no es código de usuario.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta el código para el depurador, incluso si Solo mi código está desactivado.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra el código al que se aplica en lugar de depurarlo paso a paso por instrucciones.

El depurador de .NET considera que el resto del código es código de usuario.

Durante la depuración de .NET:

- **Depurar** > **Depurar paso a paso por instrucciones**, o **F11**, en el código que no es de usuario salta el código hasta la siguiente línea de código de usuario.
- **Depurar** > **Depurar paso a paso para salir**, o **Mayús**+**F11**, en el código que no es de usuario se ejecuta en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, alcanza otro punto de interrupción o produce un error.

<a name="BKMK_NET_Breakpoint_behavior"></a> Si el depurador interrumpe la ejecución en código que no es de usuario (por ejemplo, usa **Depurar** > **Interrumpir todos** y pausa en código que no es de usuario), se abre la ventana **Sin origen**. Después, puede usar un comando **Depurar** > **Saltar** para ir a la siguiente línea de código de usuario.

Si se produce una excepción no controlada en código que no es de usuario, el depurador interrumpe la ejecución en la línea del código de usuario donde se generó la excepción.

Si se han habilitado excepciones de primera aparición para la excepción, la línea de código de usuario de llamada se resalta en color verde en el código fuente. En la ventana **Pila de llamadas** se muestra un marco anotado con la etiqueta **[Código externo]** .

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Solo mi código de C++

A partir de la versión 15.8 de Visual Studio 2017, también se admite Solo mi código para la ejecución paso a paso del código. Esta característica también requiere el uso del modificador del compilador [/JMC (Depuración de Solo mi código)](/cpp/build/reference/jmc). El modificador está habilitado de forma predeterminada en los proyectos de C++. Para la ventana **Pila de llamadas** y la compatibilidad con la pila de llamadas en Solo mi código, no es necesario el modificador /JMC.

<a name="BKMK_CPP_User_and_non_user_code"></a> Para que se clasifique como código de usuario, el depurador debe cargar el archivo PDB del archivo binario que contiene el código de usuario (use la ventana **Módulos** para comprobarlo).

En el caso del comportamiento de la pila de llamadas, como en la ventana **Pila de llamadas**, Solo mi código en C++ considera que solo estas funciones son *código que no es de usuario*:

- Funciones con información de origen eliminada en su archivo de símbolos.
- Funciones en las que los archivos de símbolos indican que no hay ningún archivo de código fuente correspondiente al marco de pila.
- Funciones especificadas en archivos *\*.natjmc* en la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.

En el caso del comportamiento de la ejecución paso a paso del código, Solo mi código en C++ considera que solo estas funciones son *código que no es de usuario*:

- Funciones para las que el archivo PDB correspondiente no se ha cargado en el depurador.
- Funciones especificadas en archivos *\*.natjmc* en la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.

> [!NOTE]
> Para la compatibilidad con la ejecución paso a paso del código en Solo mi código, el código de C++ debe compilarse con los compiladores de MSVC en Visual Studio 15.8 Preview 3 o posterior, y el modificador del compilador /JMC debe estar habilitado (está habilitado de forma predeterminada). Para más información, vea [Personalizar el comportamiento de la ejecución paso a paso del código y de la pila de llamadas en C++](#BKMK_CPP_Customize_call_stack_behavior) y esta [entrada de blog](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Para el código compilado mediante un compilador anterior, los archivos *.natstepfilter* son la única manera de personalizar la ejecución paso a paso del código, que es independiente de Solo mi código. Vea [Personalizar el comportamiento de ejecución paso a paso en C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a> Durante la depuración en C++:

- **Depurar** > **Depurar paso a paso por instrucciones**, o **F11**, en el código que no es de usuario salta el código hasta la siguiente línea de código de usuario.
- **Depurar** > **Depurar paso a paso para salir**, o **Mayús**+**F11**, en el código que no es de usuario se ejecuta en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, alcanza otro punto de interrupción o produce un error.

Si el depurador interrumpe la ejecución en código que no es de usuario (por ejemplo, se usa **Depurar** > **Interrumpir todos** y se detiene en código que no es de usuario), la ejecución paso a paso continúa en el código que no es de usuario.

Si el depurador produce una excepción, se detiene en la excepción, independientemente de si está en código de usuario o en código que no es de usuario. Las opciones **No controlada por el usuario** del cuadro de diálogo **Configuración de excepciones** se ignoran.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizar el comportamiento de la ejecución paso a paso del código y de la pila de llamadas en C++

Si se trata de proyectos de C++, puede especificar los módulos, los archivos de código fuente y las funciones que la ventana **Pila de llamadas** trata como código que no es de usuario al especificarlos en los archivos *\*.natjmc*. Esta personalización también se aplica a la ejecución paso a paso del código si usa el compilador más reciente (vea [Solo mi código de C++](#BKMK_CPP_User_and_non_user_code)).

- Para especificar código que no es de usuario para todos los usuarios del equipo de Visual Studio, agregue el archivo *.natjmc* a la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Para especificar código que no es de usuario para un usuario individual, agregue el archivo *.natjmc* a la carpeta *%USERPROFILE%\Mis documentos\\<versión de Visual Studio\>\Visualizers*.

Un archivo *.natjmc* es un archivo XML con esta sintaxis:

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
|`Name`|Obligatorio. Ruta de acceso completa al módulo o los módulos. Puede usar los caracteres comodín `?` (cero o un carácter) y `*` (cero o más caracteres) de Windows. Por ejemplo,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> indica al depurador que trate como código externo todos los módulos de *\3rdParty\UtilLibs* en cualquier unidad.|
|`Company`|Opcional. Nombre de la compañía que publica el módulo que está incrustado en el archivo ejecutable. Puede utilizar este atributo para eliminar la ambigüedad de los módulos.|

 **Atributos del elemento File**

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Obligatorio. Ruta de acceso completa del archivo o archivos de código fuente que se van a tratar como código externo. Puede usar los caracteres comodín `?` y `*` de Windows para especificar la ruta de acceso.|

 **Atributos del elemento Function**

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Obligatorio. Nombre completo de la función que se va a tratar como código externo.|
|`Module`|Opcional. Nombre o ruta de acceso completa al módulo que contiene la función. Puede utilizar este atributo para eliminar la ambigüedad de funciones que tienen el mismo nombre.|
|`ExceptionImplementation`|Cuando se establece en `true`, la pila de llamadas muestra la función que produjo la excepción en lugar de esta función.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizar el comportamiento de la ejecución paso a paso de C++ independiente de la configuración de Solo mi código

En proyectos de C++, puede especificar que se salten funciones si las enumera como código que no es de usuario en archivos *\*.natstepfilter*. Las funciones enumeradas en archivos *\*.natstepfilter* no dependen de la configuración de Solo mi código.

- Para especificar código que no es de usuario para todos los usuarios locales de Visual Studio, agregue el archivo *.natstepfilter* a la carpeta *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*.
- Para especificar código que no es de usuario para un usuario individual, agregue el archivo *.natstepfilter* a la carpeta *%USERPROFILE%\Mis documentos\\<versión de Visual Studio\>\Visualizers*.

Un archivo *.natstepfilter* es un archivo XML con esta sintaxis:

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
|`Function`|Obligatorio. Especifica una o más funciones como funciones que no son de usuario.|
|`Name`|Obligatorio. Expresión regular con formato ECMA-262 que especifica el nombre de función completo que debe coincidir. Por ejemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al depurador que todos los métodos de `MyNS::MyClass` deben considerarse código que no es de usuario. La coincidencia distingue mayúsculas de minúsculas.|
|`Module`|Opcional. Expresión regular con formato ECMA-262 que especifica la ruta de acceso completa al módulo que contiene la función. La búsqueda no distingue entre mayúsculas y minúsculas.|
|`Action`|Obligatorio. Uno de estos valores que distingue mayúsculas y minúsculas:<br /><br /> `NoStepInto`: indica al depurador que omita la función.<br /> `StepInto`: indica al depurador que depure paso a paso por instrucciones la función, invalidando cualquier otro `NoStepInto` para la función coincidente.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Solo mi código de JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> Solo mi código de JavaScript controla la ejecución paso a paso y la presentación de la pila de llamadas categorizando el código en una de estas clasificaciones:

|||
|-|-|
|**MyCode**|Código de usuario que posee y controla.|
|**LibraryCode**|Código que no es de usuario de bibliotecas que utiliza con frecuencia y que la aplicación necesita para funcionar correctamente (por ejemplo, WinJS o jQuery).|
|**UnrelatedCode**|Código que no es de usuario en la aplicación que no es de su propiedad y en el que la aplicación no se basa para funcionar correctamente. Por ejemplo, un SDK de publicidad que muestra anuncios podría ser UnrelatedCode. En los proyectos de UWP, cualquier código que se carga en la aplicación desde un URI HTTP o HTTPS también se considera UnrelatedCode.|

El depurador de JavaScript clasifica el código como usuario o no usuario en este orden:

1. Las clasificaciones predeterminadas.
   - El script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host es **MyCode**.
   - El script que se ejecuta pasando una cadena al constructor de `Function` es **LibraryCode**.
   - El script de una referencia de Framework, como WinJS o Azure SDK, es **LibraryCode**.
   - El script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval` es **UnrelatedCode**.

2. Clasificaciones especificadas para todos los proyectos de JavaScript para Visual Studio en el archivo *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json*.

3. Clasificaciones en el archivo *mycode.json* del proyecto actual.

Cada paso de clasificación invalida los pasos anteriores.

Todo el código restante se clasifica como **MyCode**.

Es posible modificar las clasificaciones predeterminadas y clasificar los archivos y las direcciones URL especificados como código de usuario o código que no es de usuario; para ello, es necesario agregar un archivo *.json* llamado *mycode.json* a la carpeta raíz de un proyecto de JavaScript. Vea [Personalizar Solo mi código de JavaScript](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a> Durante la depuración de JavaScript:

- Si una función es código que no es de usuario, **Depurar** > **Depurar paso a paso por instrucciones**, o **F11**, se comporta igual que **Depurar** > **Depurar paso a paso por procedimientos**, o **F10**.
- Si un paso se inicia en código que no es de usuario (**LibraryCode** o **UnrelatedCode**), la ejecución paso a paso se comporta temporalmente como si Solo mi código no estuviera habilitado. Al volver al código de usuario, se vuelve a habilitar la ejecución paso a paso de Solo mi código.
- Cuando un paso de código de usuario hace que se abandone el contexto de ejecución actual, el depurador se detiene en la siguiente línea de código de usuario ejecutada. Por ejemplo, si se ejecuta una devolución de llamada en código **LibraryCode**, el depurador continúa hasta que se ejecuta la línea de código de usuario siguiente.
- **Depurar paso a paso para salir**, o **Mayús**+**F11**, se detiene en la siguiente línea de código de usuario.

Si no hay más código de usuario, la depuración continúa hasta que finaliza, alcanza otro punto de interrupción o produce un error.

Siempre se alcanzan los puntos de interrupción establecidos en el código, pero el código se clasifica.

- Si la palabra clave `debugger` aparece en **LibraryCode**, el depurador siempre se interrumpe.
- Si la palabra clave `debugger` aparece en **UnrelatedCode**, el depurador no se detiene.

<a name="BKMK_JS_Exception_behavior"></a> Si se produce una excepción no controlada en el código **MyCode** o **LibraryCode**, el depurador siempre se interrumpe.

Si se produce una excepción no controlada en **UnrelatedCode**, and **MyCode** o **LibraryCode** en la pila de llamadas, se interrumpe el depurador.

Si se han habilitado excepciones de primera aparición para la excepción y la excepción se produce en **LibraryCode** o **UnrelatedCode**:

- Si se controla la excepción, el depurador no se interrumpe.
- Si la excepción no se controla, se interrumpe el depurador.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizar Solo mi código de JavaScript

Para categorizar el código de usuario y el código que no es de usuario para un único proyecto de JavaScript, puede agregar un archivo *.json* denominado *mycode.json* a la carpeta raíz del proyecto.

Las especificaciones de este archivo invalidan las clasificaciones predeterminadas y el archivo *mycode.default.wwa.json*. No es necesario que el archivo *mycode.json* enumere todos los pares clave-valor. Los valores **MyCode**, **Libraries** y **Unrelated** no pueden ser matrices vacías.

Los archivos *Mycode.json* utilizan esta sintaxis:

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

La dirección URL o la cadena de archivo puede tener uno o varios caracteres `*`, que coinciden con cero o más caracteres. `*` es el mismo que la expresión regular `.*`.
