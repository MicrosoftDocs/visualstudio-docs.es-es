---
title: Pseudovariables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5b0369a30e69fc69782bbc4a0f5b0c4518cac07
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776084"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariables en el depurador de Visual Studio
Las pseudovariables son términos que se utilizan para mostrar determinada información en una ventana de variables o el cuadro de diálogo **Inspección rápida**. Las pseudovariables se pueden especificar de la misma manera que las variables normales. No obstante, las pseudovariables no son variables ni corresponden a nombres de variable del programa.

## <a name="example"></a>Ejemplo
 Suponga que está escribiendo una aplicación de código nativo y desea ver el número de identificadores asignados en la aplicación. En la ventana **Inspección**, puede escribir la siguiente pseudovariable en la columna **Nombre** y, a continuación, presionar Entrar para evaluarla:

`$handles`

 En código nativo, puede utilizar el pseudovariables que se muestra en la tabla siguiente:

|Pseudovariable|Función|
|--------------------|--------------|
|`$err`|Muestra el último valor de error establecido con la función SetLastError. El valor que se muestra representa lo que devolvería la función GetLastError.<br /><br /> Use `$err,hr` para ver el formato descodificado de este valor. Por ejemplo, si el último error fue 3, `$err,hr` mostraría `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|
|`$handles`|Muestra el número de identificadores asignados en la aplicación.|
|`$vframe`|Muestra la dirección del marco de pila actual.|
|`$tid`|Muestra el identificador del subproceso actual.|
|`$env`|Muestra el bloque de entorno en el visor de cadenas.|
|`$cmdline`|Muestra la cadena de la línea de comandos que inició el programa.|
|`$pid`|Muestra el identificador del proceso.|
|`$` *RegisterName*<br /><br /> o<br /><br /> `@` *RegisterName*|Muestra el contenido del registro *registername*.<br /><br /> Normalmente, puede mostrar el contenido del registro con solo escribir su nombre. La única vez que necesita utilizar esta sintaxis es cuando el nombre del registro sobrecarga un nombre de variable. Si el nombre del registro es igual que un nombre de variable en el ámbito actual, el depurador lo interpreta como un nombre de variable. En ese caso `$`*registername* o `@`*registername* es muy práctico.|
|`$clk`|Muestra la hora en ciclos de reloj.|
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación. Por razones de seguridad, no se muestra la información de contraseña.|
|`$exceptionstack`|Muestra el seguimiento de pila de excepción actual de Windows Runtime. `$ exceptionstack` solo funciona en aplicaciones de UWP. `$ exceptionstack` no se admite para C++ las excepciones SEH|
|`$returnvalue`|Muestra el valor devuelto de un método.|

 En C# puede usar el pseudovariables que se muestra en la tabla siguiente:

|Pseudovariable|Función|
|--------------------|--------------|
|`$exception`|Muestra información sobre la última excepción. Si no se ha producido ninguna excepción, al evaluar `$exception` se muestra un mensaje de error.<br /><br /> Cuando el Asistente de excepciones está deshabilitado, `$exception` se agrega automáticamente a la ventana **variables locales** cuando se produce una excepción.|
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación. Por razones de seguridad, no se muestra la información de contraseña.|
|`$returnvalue`|Muestra el valor devuelto de un método de .NET.|

 En Visual Basic, puede utilizar las pseudovariables que se muestran en la tabla siguiente:

|Pseudovariable|Función|
|--------------------|--------------|
|`$exception`|Muestra información sobre la última excepción. Si no se ha producido ninguna excepción, al evaluar `$exception` se muestra un mensaje de error.|
|`$delete` o `$$delete`|Elimina una variable implícita que se creó en la ventana **Inmediato**. La sintaxis es `$delete,` *variable* o`$delete,` *variable*`.`|
|`$objectids` o `$listobjectids`|Muestra todos los identificadores de objetos activos como elementos secundarios de la expresión especificada. La sintaxis es `$objectid,` *expresión* o *expresión* de`$listobjectids,``.`|
|`$` *N* `#`|Muestra el objeto cuyo identificador es igual a *N*.|
|`$dynamic`|Muestra el nodo **Vista dinámica** especial para un objeto que implementa la interfaz `IDynamicMetaObjectProvider`. . La sintaxis es `$dynamic,` *objeto*. Esta característica solo se aplica al código que usa .NET Framework versión 4 o posterior.|

## <a name="see-also"></a>Vea también
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Ventanas de variables](../debugger/debugger-windows.md)
