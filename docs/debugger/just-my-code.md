---
title: "Solo mi c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Solo mi c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los desarrolladores que utilizan lenguajes de .NET Framework están familiarizados con la característica del depurador Solo mi código que salta las llamadas del sistema, del marco de trabajo y otras llamadas que no son de usuario, y las contrae en las ventanas Pila de llamadas.  Solo mi código se amplió a los lenguajes C\+\+ y JavaScript.  En este tema se describen los detalles del uso de Solo mi código en proyectos de .NET Framework, C\+\+ nativo y JavaScript.  
  
##  <a name="BKMK_Contents"></a> Contenido  
 [Habilitar o deshabilitar Solo mi código](#BKMK_Enable_or_disable_Just_My_Code)  
  
 [Solo mi código de .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
 [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
 [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar o deshabilitar Solo mi código  
 Para habilitar o deshabilitar Solo mi código, elija **Opciones y configuración** en el menú **Depurar**.  En el nodo **Depuración** \/ **General**, elija o desactive **Habilitar Solo mi código**.  
  
 ![Habilitar Solo mi código en el cuadro de diálogo Opciones](../debugger/media/dbg_justmycode_options.png "DBG\_JustMyCode\_Options")  
  
> [!NOTE]
>  La configuración de **Habilitar Solo mi código** es una configuración global que se aplica a todos los proyectos de Visual Studio en todos los lenguajes.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Invalidar el filtrado de la pila de llamadas  
 En las presentaciones de pilas de llamada, como las ventanas Pila de llamadas y Tareas, Solo mi código contrae el código que no es de usuario en un marco anotado con la etiqueta `[External Code]`.  Para ver los marcos contraídos, elija **Mostrar código externo** en el menú contextual de la presentación de la pila de llamadas.  
  
> [!NOTE]
>  La configuración de **Mostrar código externo** se guarda en el generador de perfiles del usuario actual.  Se aplica a todos los proyectos en todos los lenguajes abiertos por el usuario.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents)  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Solo mi código de .NET Framework  
 [Código de usuario y que no es de usuario](#BKMK_NET_User_and_non_user_code) **&#124;** [Comportamiento de ejecución paso a paso](#BKMK_NET_Stepping_behavior) **&#124;** [Comportamiento de puntos de interrupción](#BKMK_NET_Breakpoint_behavior) **&#124;** [Comportamiento de excepciones](#BKMK_NET_Exception_behavior)  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Código de usuario y que no es de usuario  
 Para distinguir entre el código de usuario del código que no es de usuario, Solo mi código examina los proyectos abiertos, los archivos de símbolos \(.pdb\) y las optimizaciones de programa.  
  
1.  Si un archivo binario se compila desde un proyecto abierto de Visual Studio, siempre se considera código de usuario.  
  
2.  El depurador considera el código como código que no es de usuario cuando se optimiza el archivo binario o cuando el archivo .pdb no está disponible.  
  
 Hay tres atributos que también afectan a lo que el depurador considera ser Mi código:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al depurador que el código al que se aplica no es Mi código.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta el código para el depurador, incluso si Solo mi código está desactivado.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra el código al que se aplica en lugar de ejecutarlo paso a paso por instrucciones.  
  
 El código restante se considera código de usuario.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
 Cuando se usa **Paso a paso por instrucciones** \(método abreviado de teclado: F11\) en código que no es de usuario, el depurador salta el código hasta la siguiente instrucción del usuario.  Cuando se usa **Paso a paso para salir** \(teclado: Mayús \+ F11\), el depurador ejecuta hasta la siguiente línea de código de usuario.  Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Comportamiento de puntos de interrupción  
 Cuando está habilitado Solo mi código, puede elegir **Interrumpir todos** \(teclado: Ctrl \+ Alt \+ Inter\) y detener la ejecución en una ubicación donde no haya código de usuario para mostrar.  Cuando esto sucede, se muestra la ventana No hay código fuente.  Si se elige un comando Paso, el depurador le lleva a la línea siguiente de código de usuario.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Comportamiento de excepciones  
 Si se produce una excepción no controlada en código que no es de usuario, el depurador interrumpe la ejecución en la línea del código de usuario donde se generó la excepción.  
  
 Si se han habilitado excepciones de primera aparición para la excepción, la línea de código de usuario se resalta en color verde.  La pila de llamadas muestra un marco anotado con la etiqueta **\[Código externo\]**.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
##  <a name="BKMK_C___Just_My_Code"></a> Solo mi código de C\+\+  
 [Código de usuario y que no es de usuario](#BKMK_CPP_User_and_non_user_code) **&#124;** [Comportamiento de ejecución paso a paso](#BKMK_CPP_Stepping_behavior) **&#124;** [Comportamiento de excepciones](#BKMK_CPP_Exception_behavior) **&#124;** [Personalizar el comportamiento de ejecución paso a paso](#BKMK_CPP_Customize_stepping_behavior) **&#124;** [Personalizar el comportamiento de la pila de llamadas](#BKMK_CPP_Customize_call_stack_behavior)  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Código de usuario y que no es de usuario  
 Solo mi código de C\+\+ es diferente de Solo mi código de .NET Framework y JavaScript porque el comportamiento de ejecución paso a paso es independiente del comportamiento de la pila de llamadas.  
  
 **Pilas de llamadas**  
  
 De forma predeterminada, el depurador considera que estas funciones son código que no es de usuario en las ventanas Pila de llamadas:  
  
-   Funciones con información de origen eliminada en su archivo de símbolos.  
  
-   Funciones en las que los archivos de símbolos indican que no hay ningún archivo de código fuente correspondiente al marco de pila.  
  
-   Funciones especificadas en archivos `*.natjmc` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
 **Recorrido paso a paso**  
  
 De forma predeterminada, solo las funciones especificadas en archivos `*.natstepfilter` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` se consideran código que no es de usuario.  
  
 Puede crear sus propios archivos `.natstepfilter` y `.natjmc` para personalizar el comportamiento de ejecución paso a paso y de la ventana Pila de llamadas en `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
 Cuando se usa **Paso a paso por instrucciones** \(método abreviado de teclado: F11\) para recorrer paso a paso código que no es de usuario desde código de usuario, el depurador salta el código hasta la siguiente línea de código de usuario.  Cuando se usa **Paso a paso para salir** \(teclado: Mayús \+ F11\), el depurador ejecuta hasta la siguiente línea de código de usuario.  Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
 Si el depurador interrumpe la ejecución en código que no es de usuario \(por ejemplo, si un comando Interrumpir todos se detiene en código que no es de usuario\), la ejecución paso a paso continúa en el código que no es de usuario.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Comportamiento de excepciones  
 Cuando el depurador visita una excepción, se detiene en la excepción independientemente de si está en código de usuario o en código que no es de usuario.  Las opciones de **No controlada por el usuario** del cuadro de diálogo **Excepciones** se pasan por alto.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizar el comportamiento de ejecución paso a paso  
 Puede especificar que se salten funciones si las enumera como código que no es de usuario en archivos `*.natstepfilter`.  
  
-   Para especificar el código que no es de usuario para todos los usuarios del equipo de Visual Studio, agregue  el archivo .natstepfilter a la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
-   Para especificar el código que no es de usuario para un usuario individual, agregue  el archivo .natstepfilter a la carpeta `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
 .  Los archivos .natstepfilter son archivos XML con esta sintaxis:  
  
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
  
|Element|Descripción|  
|-------------|-----------------|  
|Función|Requerido.  Especifica una o más funciones como funciones que no son de usuario.|  
|`Name`|Requerido.  Expresión regular con formato ECMA\-262 que especifica el nombre de función completo que debe coincidir.  Por ejemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al depurador que todos los métodos de `MyNS::MyClass` deben considerarse código que no es de usuario.  La coincidencia distingue mayúsculas de minúsculas.|  
|`Module`|Opcional.  Expresión regular con formato ECMA\-262 que especifica la ruta de acceso completa al módulo que contiene la función.  La búsqueda no distingue entre mayúsculas y minúsculas.|  
|`Action`|Requerido.  Uno de estos valores que distingue mayúsculas y minúsculas:<br /><br /> -   `NoStepInto` : indica al depurador que omita la función coincidente.<br />-   `StepInto` : indica al depurador que recorra paso a paso las funciones coincidentes, invalidando cualquier otro `NoStepInto` para las funciones coincidentes.|  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizar el comportamiento de la pila de llamadas  
 Se puede especificar que se trate como código que no es de usuario módulos, archivos de código fuente y funciones en las pilas de llamadas; para ello, hay que especificarlos en archivos `*.natjmc`.  
  
-   Para especificar el código que no es de usuario para todos los usuarios del equipo de Visual Studio, agregue .  archivo natjmc a la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
-   Para especificar el código que no es de usuario para un usuario individual, agregue .  archivo natjmc a la carpeta `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
 .  Los archivos .natjmc son archivos XML con esta sintaxis:  
  
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
|--------------|-----------------|  
|`Name`|Requerido.  Ruta de acceso completa al módulo o los módulos.  Puede usar los caracteres comodín `?` \(cero o un carácter\) y `*` \(cero o más caracteres\) de Windows.  Por ejemplo,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> indica al depurador que trate como código externo todos los módulos de `\3rdParty\UtilLibs` en cualquier unidad.|  
|`Company`|Opcional.  Nombre de la compañía que publica el módulo que está incrustado en el archivo ejecutable.  Puede utilizar este atributo para eliminar la ambigüedad de los módulos.|  
  
 **Atributos del elemento File**  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Requerido.  Ruta de acceso completa del archivo o archivos de código fuente que se van a tratar como código externo.  Puede usar los caracteres comodín `?` y `*` de Windows para especificar la ruta de acceso.|  
  
 **Atributos del elemento Function**  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Requerido.  Nombre completo de la función que se va a tratar como código externo.|  
|`Module`|Opcional.  Nombre o ruta de acceso completa al módulo que contiene la función.  Puede utilizar este atributo para eliminar la ambigüedad de funciones que tienen el mismo nombre.|  
|`ExceptionImplementation`|Cuando se establece en `true`, la pila de llamadas muestra la función que produjo la excepción en lugar de esta función.|  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de C++](#BKMK_C___Just_My_Code)  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Solo mi código de JavaScript  
 [Código de usuario y que no es de usuario](#BKMK_JS_User_and_non_user_code) **&#124;** [Comportamiento de ejecución paso a paso](#BKMK_JS_Stepping_behavior) **&#124;** [Comportamiento de puntos de interrupción](#BKMK_JS_Breakpoint_behavior) **&#124;** [Comportamiento de excepciones](#BKMK_JS_Exception_behavior) **&#124;** [Personalizar Solo mi código](#BKMK_JS_Customize_Just_My_Code)  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Código de usuario y que no es de usuario  
 **Clasificaciones de código**  
  
 Solo mi código de JavaScript controla la ejecución paso a paso y la presentación de la pila de llamadas categorizando el código en una de estas clasificaciones:  
  
|||  
|-|-|  
|**MyCode**|Código de usuario que posee y controla.|  
|**LibraryCode**|Código que no es de usuario de bibliotecas que utiliza con frecuencia y que la aplicación necesita para funcionar correctamente \(por ejemplo, WinJS o jQuery\).|  
|**UnrelatedCode**|Código que no es de usuario que podría ejecutarse en la aplicación, pero que no posee y del que la aplicación no depende directamente para funcionar correctamente \(por ejemplo, un SDK publicitario que muestra anuncios\).  En los proyectos de la Tienda Windows, cualquier código que se carga en la aplicación desde un URI HTTP o HTTPS también se considera UnrelatedCode.|  
  
 El depurador de JavaScript clasifica automáticamente estos tipos de código:  
  
-   Un script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host se clasifica como **MyCode**.  
  
-   Un script que se ejecuta pasando una cadena al constructor de `Function` se clasifica como **LibraryCode**.  
  
-   Un script contenido en una referencia de .NET Framework, como WinJS o Azure SDK, se clasifica como **LibraryCode**.  
  
-   Un script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval` se clasifica como **UnrelatedCode**.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` especifica otro usuario y código que no es de usuario para todos los proyectos de JavaScript de Visual Studio.  
  
 Es posible modificar las clasificaciones predeterminadas y clasificar determinados archivos y direcciones URL si se agrega un archivo .json denominado `mycode.json` a la carpeta raíz de un proyecto.  
  
 Todo el código restante se clasifica como **MyCode**.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Comportamiento de ejecución paso a paso  
  
-   Si una función no es código de usuario \(**MyCode**\), **Paso a paso por instrucciones** \(método abreviado de teclado: F11\) se comporta como **Paso a paso por procedimientos** \(teclado: F10\).  
  
-   Si un paso se inicia en código que no es de usuario \(**LibraryCode** o **UnrelatedCode**\), el paso a paso por instrucciones se comporta temporalmente como si no estuviera habilitado Solo mi código.  En cuanto se vuelve al código de usuario, se vuelve a habilitar el paso a paso por instrucciones de Solo mi código.  
  
-   Cuando un paso en código de usuario hace que se salga del contexto de ejecución actual \(como un paso en la última línea de un controlador de eventos\), el depurador se detiene en la siguiente línea de código de usuario ejecutada.  Por ejemplo, si se ejecuta una devolución de llamada en código **LibraryCode**, el depurador continúa hasta que se ejecuta la línea de código de usuario siguiente.  
  
-   **Paso a paso para salir** \(teclado: Mayús \+ F11\) se detiene en la siguiente línea de código de usuario.  Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Comportamiento de puntos de interrupción  
  
-   Siempre se visitan los puntos de interrupción que se han establecido en cualquier código independientemente de la clasificación de ese código  
  
-   Si se encuentra la palabra clave `debugger` en:  
  
    -   Código **LibraryCode**, el depurador siempre se interrumpe.  
  
    -   Código **UnrelatedCode**, el depurador no se detiene.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Comportamiento de excepciones  
 Si se produce una excepción no controlada en:  
  
-   Código **MyCode** o **LibraryCode**, el depurador siempre se interrumpe.  
  
-   Código **UnrelatedCode**, y si hay código **MyCode** o **LibraryCode** en la pila de llamadas, se interrumpe el depurador.  
  
 Si se han habilitado excepciones de primera aparición para la excepción en el cuadro de diálogo Excepciones y la excepción se produce en código **LibraryCode** o **UnrelatedCode**:  
  
-   Si se controla la excepción, el depurador no se interrumpe.  
  
-   Si la excepción no se controla, se interrumpe el depurador.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizar Solo mi código  
 Para categorizar el código de usuario y el código que no es de usuario para un único proyecto de Visual Studio, agregue un archivo .json denominado `mycode.json` a la carpeta raíz del proyecto.  
  
 Las clasificaciones se realizan en este orden:  
  
1.  Clasificaciones predeterminadas  
  
2.  Clasificaciones en el archivo `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3.  Clasificaciones en el archivo `mycode. json` del proyecto actual.  
  
 Cada paso de clasificación invalida los pasos anteriores.  No es necesario que un archivo .json enumere todos los pares clave\-valor, y los valores **MyCode**, **Libraries** y **Unrelated** pueden ser matrices vacías.  
  
 Los archivos .json de Mi código utilizan esta sintaxis:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function y ScriptBlock**  
  
 Los pares clave\-valor **Eval**, **Function** y **ScriptBlock** determinan cómo se clasifica el código generado dinámicamente.  
  
|||  
|-|-|  
|**Eval**|Script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host.  De forma predeterminada, el script Eval se clasifica como **MyCode**.|  
|**Función**|Script que se ejecuta pasando una cadena al constructor de `Function`.  De forma predeterminada, el script Function se clasifica como **LibraryCode**.|  
|**ScriptBlock**|Script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval`.  De forma predeterminada, el script ScriptBlock se clasifica como **UnrelatedCode**.|  
  
 Puede cambiar el valor a una de estas palabras clave:  
  
-   `MyCode`  clasifica el script como **MyCode**.  
  
-   `Library`  clasifica el script como **LibraryCode**.  
  
-   `Unrelated`  clasifica el script como **UnrelatedCode**.  
  
 **MyCode, Libraries y Unrelated**  
  
 Los pares clave\-valor **MyCode**, **Libraries** y **Unrelated** especifican las direcciones URL o los archivos que desea incluir en una clasificación:  
  
|||  
|-|-|  
|**MyCode**|Matriz de direcciones URL o archivos que se clasifican como **MyCode**.|  
|**Bibliotecas**|Matriz de direcciones URL o archivos que se clasifican como **LibraryCode**.|  
|**Unrelated**|Matriz de direcciones URL o archivos que se clasifican como **UnrelatedCode**.|  
  
 La dirección URL o la cadena de archivo puede contener uno o más caracteres `*`, que coinciden con cero o más caracteres.  `*` es el equivalente de la expresión regular `.*`.  
  
 ![Volver al principio](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Contenido](#BKMK_Contents) **&#124;** [Solo mi código de JavaScript](#BKMK_JavaScript_Just_My_Code)