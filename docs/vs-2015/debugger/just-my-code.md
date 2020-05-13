---
title: Sólo mi código ? Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301396"
---
# <a name="just-my-code"></a>Solo mi código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los desarrolladores que utilizan lenguajes de .NET Framework están familiarizados con la característica del depurador Solo mi código que salta las llamadas del sistema, del marco de trabajo y otras llamadas que no son de usuario, y las contrae en las ventanas Pila de llamadas. Solo mi código se amplió a los lenguajes C++ y JavaScript. En este tema se describen los detalles del uso de Solo mi código en proyectos de .NET Framework, C++ nativo y JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Habilitar o deshabilitar Solo mi código  
 Para habilitar o deshabilitar Solo mi código, elija **Opciones y configuración** en el menú **Depurar.** En el nodo**General** **de depuración,** / elija o desactive Habilitar solo **mi código**.  
  
 ![Habilitar Solo mi código en el cuadro de diálogo Opciones](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> La configuración **Habilitar solo mi código** es una configuración global que se aplica a todos los proyectos de Visual Studio en todos los idiomas.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Reemplazar el filtrado de pila de llamadas  
 En las presentaciones de pilas de llamada, como las ventanas Pila de llamadas y Tareas, Solo mi código contrae el código que no es de usuario en un marco anotado con la etiqueta `[External Code]`. Para ver los fotogramas contraídos, elija **Mostrar código externo** en el menú contextual de la visualización de la pila de llamadas.  
  
> [!NOTE]
> La configuración **Mostrar código externo** se guarda en el generador de perfiles del usuario actual. Se aplica a todos los proyectos en todos los lenguajes abiertos por el usuario.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Just My Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Código de usuario y no usuario  
 Para distinguir el código de usuario del código que no es de usuario, Just My Code examina los archivos de símbolo (.pdb) y las optimizaciones del programa. El depurador considera el código como código que no es de usuario cuando se optimiza el archivo binario o cuando el archivo .pdb no está disponible.  
  
 Hay tres atributos que también afectan a lo que el depurador considera ser Mi código:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> indica al depurador que el código al que se aplica no es Mi código.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta el código para el depurador, incluso si Solo mi código está desactivado.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al depurador que recorra el código al que se aplica en lugar de ejecutarlo paso a paso por instrucciones.  
  
  El código restante se considera código de usuario.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Comportamiento de paso  
 Al **entrar en** el código de usuario (método abreviado de teclado: F11), el depurador pasa sobre el código a la siguiente instrucción de usuario. Al **salir** (teclado: Mayús + F11), el depurador se ejecuta en la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Comportamiento del punto de interrupción  
 Cuando Just My Code está habilitado, puede elegir **Break All** (Teclado: Ctrl + Alt + Break) y detener la ejecución en una ubicación donde no hay código de usuario para mostrar. Cuando esto sucede, se muestra la ventana No hay código fuente. Si se elige un comando Paso, el depurador le lleva a la línea siguiente de código de usuario.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Comportamiento de excepción  
 Si se produce una excepción no controlada en código que no es de usuario, el depurador interrumpe la ejecución en la línea del código de usuario donde se generó la excepción.  
  
 Si se han habilitado excepciones de primera aparición para la excepción, la línea de código de usuario se resalta en color verde. La pila de llamadas muestra un marco anotado con la etiqueta **[Código externo]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Solo mi código de C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Código de usuario y no usuario  
 Solo mi código de C++ es diferente de Solo mi código de .NET Framework y JavaScript porque el comportamiento de ejecución paso a paso es independiente del comportamiento de la pila de llamadas.  
  
 **Pilas de llamadas**  
  
 De forma predeterminada, el depurador considera que estas funciones son código que no es de usuario las en ventanas Pila de llamadas:  
  
- Funciones con información de origen eliminada en su archivo de símbolos.  
  
- Funciones en las que los archivos de símbolos indican que no hay ningún archivo de código fuente correspondiente al marco de pila.  
  
- Funciones especificadas en archivos `*.natjmc` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`.  
  
  **Recorrido paso a paso**  
  
  De forma predeterminada, solo las funciones especificadas en archivos `*.natstepfilter` en la carpeta `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` se consideran código que no es de usuario.  
  
  Puede crear sus propios archivos `.natstepfilter` y `.natjmc` para personalizar el comportamiento de ejecución paso a paso y de la ventana Pila de llamadas en `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Comportamiento de paso  
 Al **entrar en** el código de usuario (método abreviado de teclado: F11) del código de usuario, el depurador pasa sobre el código a la siguiente línea de código de usuario. Al **salir** (teclado: Mayús + F11), el depurador se ejecuta en la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
 Si el depurador interrumpe la ejecución en código que no es de usuario (por ejemplo, si un comando Interrumpir todos se detiene en código que no es de usuario), la ejecución paso a paso continúa en el código que no es de usuario.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Comportamiento de excepción  
 Cuando el depurador visita una excepción, se detiene en la excepción independientemente de si está en código de usuario o en código que no es de usuario. Las opciones no **controladas por** el usuario en el cuadro de diálogo **Excepciones** se omiten.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Personalizar el comportamiento de los pasos  
 Puede especificar que se salten funciones si las enumera como código que no es de usuario en archivos `*.natstepfilter`.  
  
- Para especificar código que no sea de usuario para todos los usuarios `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` del equipo de Visual Studio, agregue el archivo .natstepfilter a la carpeta.  
  
- Para especificar código que no sea de usuario para un usuario `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` individual, agregue el archivo .natstepfilter a la carpeta.  
  
  Los archivos .natstepfilter son archivos XML con esta sintaxis:  
  
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
|Función|Necesario. Especifica una o más funciones como funciones que no son de usuario.|  
|`Name`|Necesario. Expresión regular con formato ECMA-262 que especifica el nombre de función completo que debe coincidir. Por ejemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> indica al depurador que todos los métodos de `MyNS::MyClass` deben considerarse código que no es de usuario. La coincidencia distingue mayúsculas de minúsculas.|  
|`Module`|Opcional. Expresión regular con formato ECMA-262 que especifica la ruta de acceso completa al módulo que contiene la función. La búsqueda no distingue entre mayúsculas y minúsculas.|  
|`Action`|Necesario. Uno de estos valores que distingue mayúsculas y minúsculas:<br /><br /> -   `NoStepInto`– indica al depurador que pase por encima de la función coincidente.<br />-   `StepInto`– indica al depurador que entre en las funciones coincidentes, reemplazando cualquier otra `NoStepInto` para las funciones coincidentes.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Personalizar el comportamiento de la pila de llamadas  
 Se puede especificar que se trate como código que no es de usuario módulos, archivos de código fuente y funciones en las pilas de llamadas; para ello, hay que especificarlos en archivos `*.natjmc`.  
  
- Para especificar código que no sea de usuario para todos los usuarios `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` del equipo de Visual Studio, agregue el archivo .natjmc a la carpeta.  
  
- Para especificar código que no sea de usuario para un usuario `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` individual, agregue el archivo .natjmc a la carpeta.  
  
  Los archivos .natjmc son archivos XML con esta sintaxis:  
  
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
|`Name`|Necesario. Ruta de acceso completa al módulo o los módulos. Puede usar los caracteres comodín `?` (cero o un carácter) y `*` (cero o más caracteres) de Windows. Por ejemplo,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> indica al depurador que trate como código externo todos los módulos de `\3rdParty\UtilLibs` en cualquier unidad.|  
|`Company`|Opcional. Nombre de la compañía que publica el módulo que está incrustado en el archivo ejecutable. Puede utilizar este atributo para eliminar la ambigüedad de los módulos.|  
  
 **Atributos del elemento File**  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Necesario. Ruta de acceso completa del archivo o archivos de código fuente que se van a tratar como código externo. Puede usar los caracteres comodín `?` y `*` de Windows para especificar la ruta de acceso.|  
  
 **Atributos del elemento Function**  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Necesario. Nombre completo de la función que se va a tratar como código externo.|  
|`Module`|Opcional. Nombre o ruta de acceso completa al módulo que contiene la función. Puede utilizar este atributo para eliminar la ambigüedad de funciones que tienen el mismo nombre.|  
|`ExceptionImplementation`|Cuando se establece en `true`, la pila de llamadas muestra la función que produjo la excepción en lugar de esta función.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Solo mi código de JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Código de usuario y no usuario  
 **Clasificaciones de código**  
  
 Solo mi código de JavaScript controla la ejecución paso a paso y la presentación de la pila de llamadas categorizando el código en una de estas clasificaciones:  
  
|||  
|-|-|  
|**MyCode**|Código de usuario que posee y controla.|  
|**LibraryCode**|Código que no es de usuario de bibliotecas que utiliza con frecuencia y que la aplicación necesita para funcionar correctamente (por ejemplo, WinJS o jQuery).|  
|**UnrelatedCode**|Código que no sea de usuario que podría estar ejecutándose en la aplicación, pero que no es propietario y la aplicación no confía directamente en él para funcionar correctamente (por ejemplo, un SDK de publicidad que muestra anuncios). En los proyectos de la Tienda Windows, cualquier código que se carga en la aplicación desde un URI HTTP o HTTPS también se considera UnrelatedCode.|  
  
 El depurador de JavaScript clasifica automáticamente estos tipos de código:  
  
- El script que se ejecuta pasando una `eval` cadena a la función proporcionada por el host se clasifica como **MyCode**.  
  
- Script que se ejecuta pasando `Function` una cadena al constructor se clasifica como **LibraryCode**.  
  
- El script que se encuentra en una referencia de marco de trabajo, como WinJS o el SDK de Azure, se clasifica como **LibraryCode**.  
  
- El script que se ejecuta `setTimeout`pasando `setImmediate`una `setInterval` cadena a las funciones , , o se clasifica como **Código no relacionado**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` especifica otro usuario y código que no es de usuario para todos los proyectos de JavaScript de Visual Studio.  
  
  Es posible modificar las clasificaciones predeterminadas y clasificar determinados archivos y direcciones URL si se agrega un archivo .json denominado `mycode.json` a la carpeta raíz de un proyecto.  
  
  Todo el código restante se clasifica como **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Comportamiento de paso  
  
- Si una función no es código de usuario (**MyCode**), **Step Into** (método abreviado de teclado: F11) se comporta como **Step Over** (Teclado: F10).  
  
- Si un paso comienza en código que no es de usuario (**LibraryCode** o **UnrelatedCode**), el paso se comporta temporalmente como si Just My Code no estuviera habilitado. En cuanto se vuelve al código de usuario, se vuelve a habilitar el paso a paso por instrucciones de Solo mi código.  
  
- Cuando un paso en código de usuario hace que se salga del contexto de ejecución actual (como un paso en la última línea de un controlador de eventos), el depurador se detiene en la siguiente línea de código de usuario ejecutada. Por ejemplo, si una devolución de llamada se ejecuta en el código **LibraryCode,** el depurador continúa hasta que se ejecuta la siguiente línea de código de usuario.  
  
- **Step Out** (Teclado: Mayús + F11) se detiene en la siguiente línea de código de usuario. Si no se encuentra ningún código de usuario, la ejecución continúa hasta que se cierra la aplicación, se visita un punto de interrupción o se produce una excepción.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Comportamiento del punto de interrupción  
  
- Siempre se visitan los puntos de interrupción que se han establecido en cualquier código independientemente de la clasificación de ese código  
  
- Si se encuentra la palabra clave `debugger` en:  
  
  - **Código LibraryCode,** el depurador siempre se interrumpe.  

  - **Código UnrelatedCode,** el depurador no se detiene.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Comportamiento de excepción  
 Si se produce una excepción no controlada en:  
  
- **MyCode** o **LibraryCode** código, el depurador siempre se interrumpe.  
  
- **Código unrelatedCode** y código **MyCode** o **LibraryCode** en la pila de llamadas, el depurador se interrumpe.  
  
  Si se habilitan excepciones de primera oportunidad para la excepción en el cuadro de diálogo Excepciones y la excepción se produce en el código **LibraryCode** o **UnrelatedCode:**  
  
- Si se controla la excepción, el depurador no se interrumpe.  
  
- Si la excepción no se controla, se interrumpe el depurador.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Personalizar solo mi código  
 Para categorizar el código de usuario y el código que no es de usuario para un único proyecto de Visual Studio, agregue un archivo .json denominado `mycode.json` a la carpeta raíz del proyecto.  
  
 Las clasificaciones se realizan en este orden:  
  
1. Clasificaciones predeterminadas  
  
2. Clasificaciones en el archivo `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`  
  
3. Clasificaciones en el archivo `mycode. json` del proyecto actual.  
  
   Cada paso de clasificación invalida los pasos anteriores. Un archivo .json no necesita enumerar todos los pares de valores de clave y los valores **MyCode**, **Libraries**y **Unrelated** pueden ser matrices vacías.  
  
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
  
 Los pares de valores de clave **Eval**, **Function**y **ScriptBlock** determinan cómo se clasifica el código generado dinámicamente.  
  
|||  
|-|-|  
|**Eval**|Script que se ejecuta pasando una cadena a la función `eval` proporcionada por el host. De forma predeterminada, el script Eval se clasifica como **MyCode**.|  
|**Función**|Script que se ejecuta pasando una cadena al constructor de `Function`. De forma predeterminada, el script Function se clasifica como **LibraryCode**.|  
|**ScriptBlock**|Script que se ejecuta pasando una cadena a las funciones `setTimeout`, `setImmediate` o `setInterval`. De forma predeterminada, el script ScriptBlock se clasifica como **UnrelatedCode**.|  
  
 Puede cambiar el valor a una de estas palabras clave:  
  
- `MyCode`clasifica el script como **MyCode**.  
  
- `Library`clasifica el script como **LibraryCode**.  
  
- `Unrelated`clasifica el script como **UnrelatedCode**.  
  
  **MyCode, Libraries y Unrelated**  
  
  Los pares de valores de clave **MyCode**, **Libraries**y **Unrelated** especifican las URL o los archivos que desea incluir en una clasificación:  
  
|||  
|-|-|  
|**MyCode**|Una matriz de urls o archivos que se clasifican como **MyCode**.|  
|**Bibliotecas**|Matriz de urls o archivos clasificados como **LibraryCode**.|  
|**Unrelated**|Matriz de URL o archivos clasificados como **UnrelatedCode**.|  
  
 La dirección URL o la cadena de archivo puede contener uno o más caracteres `*`, que coinciden con cero o más caracteres. `*` es el equivalente de la expresión regular `.*`.
