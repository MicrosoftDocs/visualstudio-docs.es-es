---
title: "Pseudovariables | Microsoft Docs"
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
helpviewer_keywords: 
  - "depurar [Visual Studio], pseudovariables"
  - "pseudovariables"
  - "Inspección (ventana), pseudovariables"
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pseudovariables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las pseudovariables son términos que se utilizan para mostrar determinada información en una ventana de variables o el cuadro de diálogo **Inspección rápida**.  Las pseudovariables se pueden especificar de la misma manera que las variables normales.  No obstante, las pseudovariables no son variables ni corresponden a nombres de variable del programa.  
  
## Ejemplo  
 Suponga que está escribiendo una aplicación de código nativo y desea ver el número de identificadores asignados en la aplicación.  En la ventana **Inspección**, puede escribir la siguiente pseudovariable en la columna **Nombre** y, a continuación, presionar Entrar para evaluarla:  
  
```  
$handles  
```  
  
 En código nativo, puede utilizar las pseudovariables que se muestran en esta tabla:  
  
|Pseudovariable|Función|  
|--------------------|-------------|  
|`$err`|Muestra el último valor de error establecido con la función SetLastError.  El valor que se muestra representa lo que devolvería la función GetLastError.<br /><br /> Use `$err,hr` para ver el formato descodificado de este valor.  Por ejemplo, si el último error fue 3, `$err,hr` mostraría `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Muestra el número de identificadores asignados en la aplicación.|  
|`$vframe`|Muestra la dirección del marco de pila actual.|  
|`$tid`|Muestra el identificador del subproceso actual.|  
|`$env`|Muestra el bloque de entorno en el visor de cadenas.|  
|`$cmdline`|Muestra la cadena de la línea de comandos que inició el programa.|  
|`$pid`|Muestra el identificador del proceso.|  
|`$` *registername*<br /><br /> o<br /><br /> `@` *registername*|Muestra el contenido del registro *registername*.<br /><br /> Normalmente, puede mostrar el contenido del registro con solo escribir su nombre.  La única vez que necesita utilizar esta sintaxis es cuando el nombre del registro sobrecarga un nombre de variable.  Si el nombre del registro es igual que un nombre de variable en el ámbito actual, el depurador lo interpreta como un nombre de variable.  En ese caso `$`*registername* o `@`*registername* es muy práctico.|  
|`$clk`|Muestra la hora en ciclos de reloj.|  
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación.  Por razones de seguridad, no se muestra la información de contraseña.|  
|`$exceptionstack`|Muestra el seguimiento de pila de excepción actual de Windows en tiempo de ejecución.  `$ exceptionstack` solo funciona en aplicaciones de la Tienda que se ejecutan en Windows 8.1 o versiones posteriores.  No se admite `$ exceptionstack` para excepciones de C\+\+ y SHE.|  
|`$ReturnValue`|Muestra el valor devuelto de un método de .NET Framework.  Vea [Examinar los valores devueltos por las llamadas a métodos](../Topic/Examine%20return%20values%20of%20method%20calls.md).|  
  
 En C\# y Visual Basic, puede utilizar las pseudovariables que se muestran en esta tabla:  
  
|Pseudovariable|Función|  
|--------------------|-------------|  
|`$exception`|Muestra información sobre la última excepción.  Si no se ha producido ninguna excepción, al evaluar `$exception` se muestra un mensaje de error.<br /><br /> Solo en Visual C\#, cuando el Asistente de excepciones está deshabilitado, `$exception` se agrega automáticamente a la ventana **Variables locales** cuando se produce una excepción.|  
|`$user`|Muestra una estructura con información de la cuenta que ejecuta la aplicación.  Por razones de seguridad, no se muestra la información de contraseña.|  
  
 En Visual Basic, puede utilizar las pseudovariables que se muestran en la tabla siguiente:  
  
|Pseudovariable|Función|  
|--------------------|-------------|  
|`$delete` o `$$delete`|Elimina una variable implícita que se creó en la ventana **Inmediato**.  La sintaxis es `$delete,` *variable* o `$delete,` *variable*`.`|  
|`$objectids` o `$listobjectids`|Muestra todos los identificadores de objetos activos como elementos secundarios de la expresión especificada.  La sintaxis es `$objectid,` *expression* o `$listobjectids,` *expression*`.`|  
|`$` *N* `#`|Muestra el objeto cuyo identificador es igual a *N*.|  
|`$dynamic`|Muestra el nodo **Vista dinámica** especial para un objeto que implementa la interfaz `IDynamicMetaObjectProvider`.  .  La sintaxis es `$dynamic,` *object*.  Esta característica solo se aplica a código que utiliza .NET Framework versión 4.  Vea [Vista dinámica](../Topic/Dynamic%20View.md).|  
  
## Vea también  
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Ventanas de variables](../Topic/Variable%20Windows.md)