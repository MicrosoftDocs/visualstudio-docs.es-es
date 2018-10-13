---
title: Pseudovariables | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 028ca4630ca2e07b8f522d3cb630305d0e3ae5d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281794"
---
# <a name="pseudovariables"></a>Pseudovariables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudovariables son términos que se usan para mostrar determinada información en una ventana de variables o **Inspección rápida** cuadro de diálogo. Las pseudovariables se pueden especificar de la misma manera que las variables normales. No obstante, las pseudovariables no son variables ni corresponden a nombres de variable del programa.  
  
## <a name="example"></a>Ejemplo  
 Suponga que está escribiendo una aplicación de código nativo y desea ver el número de identificadores asignados en la aplicación. En el **inspección** ventana, puede escribir la siguiente pseudovariable en la **nombre** columna y, a continuación, presione ENTRAR para evaluarla:  
  
```  
$handles  
```  
  
 En código nativo, puede utilizar las pseudovariables que se muestran en esta tabla:  
  
|Pseudovariable|Función|  
|--------------------|--------------|  
|`$err`|Muestra el último valor de error establecido con la función SetLastError. El valor que se muestra representa lo que devolvería la función GetLastError.<br /><br /> Use `$err,hr` para ver el formato descodificado de este valor. Por ejemplo, si el último error fue 3, `$err,hr` mostraría `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Muestra el número de identificadores asignados en la aplicación.|  
|`$vframe`|Muestra la dirección del marco de pila actual.|  
|`$tid`|Muestra el identificador del subproceso actual.|  
|`$env`|Muestra el bloque de entorno en el visor de cadenas.|  
|`$cmdline`|Muestra la cadena de la línea de comandos que inició el programa.|  
|`$pid`|Muestra el identificador del proceso.|  
|`$` *nombre de registro*<br /><br /> o<br /><br /> `@` *nombre de registro*|Muestra el contenido del registro *registername*.<br /><br /> Normalmente, puede mostrar el contenido del registro con solo escribir su nombre. La única vez que necesita utilizar esta sintaxis es cuando el nombre del registro sobrecarga un nombre de variable. Si el nombre del registro es igual que un nombre de variable en el ámbito actual, el depurador lo interpreta como un nombre de variable. Es decir, cuando `$` *registername* o `@` *registername* resulta útil.|  
|`$clk`|Muestra la hora en ciclos de reloj.|  
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación. Por razones de seguridad, no se muestra la información de contraseña.|  
|`$exceptionstack`|Muestra el seguimiento de pila de excepción actual de Windows en tiempo de ejecución. `$ exceptionstack` solo funciona en aplicaciones de la Tienda que se ejecutan en Windows 8.1 o versiones posteriores. No se admite `$ exceptionstack` para excepciones de C++ y SHE.|  
|`$ReturnValue`|Muestra el valor devuelto de un método de .NET Framework. Consulte [examinar los valores devueltos de llamadas de método](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 En C# y Visual Basic, puede utilizar las pseudovariables que se muestran en esta tabla:  
  
|Pseudovariable|Función|  
|--------------------|--------------|  
|`$exception`|Muestra información sobre la última excepción. Si no se ha producido ninguna excepción, al evaluar `$exception` se muestra un mensaje de error.<br /><br /> En Visual C#, cuando se deshabilita el Asistente de excepciones, `$exception` se agrega automáticamente a la **variables locales** ventana cuando se produce una excepción.|  
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación. Por razones de seguridad, no se muestra la información de contraseña.|  
  
 En Visual Basic, puede utilizar las pseudovariables que se muestran en la tabla siguiente:  
  
|Pseudovariable|Función|  
|--------------------|--------------|  
|`$delete` o `$$delete`|Elimina una variable implícita que se creó en el **inmediato** ventana. La sintaxis es `$delete,` *variable* o`$delete,` *variable*`.`|  
|`$objectids` o `$listobjectids`|Muestra todos los identificadores de objetos activos como elementos secundarios de la expresión especificada. La sintaxis es `$objectid,` *expresión* o`$listobjectids,` *expresión*`.`|  
|`$` *N* `#`|Muestra el objeto cuyo identificador es igual a *N*.|  
|`$dynamic`|Muestra especial **vista dinámica** nodo para un objeto que implementa el `IDynamicMetaObjectProvider`. . La sintaxis es `$dynamic,` *objeto*. Esta característica solo se aplica a código que utiliza .NET Framework versión 4. Consulte [vista dinámica](http://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Vea también  
 [Inspección e inspección rápida Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Windows variable](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





