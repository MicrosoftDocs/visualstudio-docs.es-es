---
title: Comandos de la consola de JavaScript | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console commands [Windows Store apps]
- JavaScript debugging, console [Windows Store apps]
- debugging JavaScript, console [Windows Store apps]
ms.assetid: 359e2b24-6bb7-48e7-8b55-b570df0cb774
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aeaba355e101bd8e48126bfa01f95668a37abe3e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081429"
---
# <a name="javascript-console-commands"></a>JavaScript Console commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 La ventana Consola JavaScript de Visual Studio te permite usar comandos para enviar mensajes y realizar otras tareas. Para obtener ejemplos que muestran cómo usar esa ventana, consulte [inicio rápido: Depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). La información de este tema se aplica a las aplicaciones de la Tienda Windows, las aplicaciones de la Tienda de Windows Phone y las aplicaciones creadas con Visual Studio Tools para Apache Cordova. Para obtener información acerca sobre los comandos de consola compatibles en las aplicaciones de Cordova, vea [Debug Your App](http://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1). Para obtener información sobre el uso de la consola con herramientas de F12 de Internet Explorer, consulte [este tema](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Si la ventana Consola JavaScript está cerrada, puedes abrirla durante la depuración en Visual Studio si eliges **Depurar** > **Ventanas** > **Consola JavaScript**.  
  
> [!NOTE]
>  Si la ventana no está disponible durante una sesión de depuración, asegúrese de que el tipo de depurador está establecido en **Script** en las propiedades de depuración del proyecto.  
  
## <a name="console-object-commands"></a>Comandos del objeto console  
 En esta tabla se muestra la sintaxis de los comandos del objeto `console` que puedes usar en la ventana Consola JavaScript o para enviar mensajes a la consola desde el código. Este objeto tiene varias formas que te permiten diferenciar, si quieres, los mensajes informativos de los mensajes de error.  
  
 Puedes usar la forma larga del comando `window.console.[command]` si tienes que evitar confusiones posibles con objetos locales cuyo nombre también sea console.  
  
> [!TIP]
>  Las versiones anteriores de Visual Studio no admiten el conjunto completo de comandos. Use IntelliSense en el objeto de la consola para obtener información rápida sobre los comandos admitidos.  
  
|Comando|Descripción|Ejemplo|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Envía un mensaje si `expression` se evalúa como **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Borra mensajes de la ventana de consola, incluidos los mensajes de error de script, y también borra el script que aparece en la ventana de consola. No borra el script especificado en el indicador de entrada de la consola.|`console.clear();`|  
|`count(title)`|Envía el número de veces que se llamó el comando count en la ventana de consola. Cada llamada a este comando se identifica de forma única mediante el parámetro `title`opcional.<br /><br /> La entrada existente en la ventana de consola se identifica mediante el parámetro `title` (si existe) y se actualiza mediante el comando count. No se crea una nueva entrada.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Envía `message` a la ventana de consola.<br /><br /> Este comando es idéntico a console.log.<br /><br /> Los objetos que se pasan mediante el comando se convierten en un valor de cadena.|`console.debug("logging message");`|  
|`dir(object)`|Envía el objeto especificado a la ventana de consola y lo muestra en un visualizador de objeto. Puedes usar el visualizador para inspeccionar las propiedades en la ventana de consola.|`console.dir(obj);`|  
|`dirxml(object)`|Envía el nodo XML `object` especificado a la ventana de consola y lo muestra como un árbol de nodos XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Envía `message` a la ventana de consola. El texto del mensaje es de color rojo y va precedido de un símbolo de error.<br /><br /> Los objetos que se pasan mediante el comando se convierten en un valor de cadena.|`console.error("error message");`|  
|`group(title)`|Inicia una agrupación para los mensajes que se envían a la ventana de consola, y envía el parámetro `title` opcional como etiqueta de grupo. Es posible anidar los grupos y mostrarlos en una vista de árbol en la ventana de consola.<br /><br /> Los comandos group* facilitan la visualización de la salida de la ventana de consola en algunos escenarios, como cuando se utiliza un modelo de componentes.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Inicia una agrupación para los mensajes que se envían a la ventana de consola, y envía el parámetro `title` opcional como etiqueta de grupo. De forma predeterminada, los grupos que se envían mediante `groupCollapsed` aparecen en una vista contraída. Es posible anidar los grupos y mostrarlos en una vista de árbol en la ventana de consola.|Su uso es igual que el del comando `group` .<br /><br /> Consulta el ejemplo para el comando `group` .|  
|`groupEnd()`|Finaliza el grupo actual.<br /><br /> Requisitos:<br /><br /> Visual Studio 2013|Consulta el ejemplo para el comando `group` .|  
|`info(message)`|Envía `message` a la ventana de consola. El mensaje va precedido de un símbolo de información.|`console.info("info message");`<br /><br /> Para ver más ejemplos, consulte [Formatting console.log output](#ConsoleLog) más adelante en este tema.|  
|`log(message)`|Envía `message` a la ventana de consola.<br /><br /> Si pasas un objeto, este comando lo envía a la ventana de la consola y lo muestra en un visualizador de objeto. Puedes usar el visualizador para inspeccionar las propiedades en la ventana de consola.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Se utiliza en aplicaciones web. No se admite en aplicaciones de la Tienda con JavaScript.|No se admite.|  
|`profile(reportName)`|Se utiliza en aplicaciones web. No se admite en aplicaciones de la Tienda con JavaScript.|No se admite.|  
|`profileEnd()`|Se utiliza en aplicaciones web. No se admite en aplicaciones de la Tienda con JavaScript.|No se admite.|  
|`select(element)`|Selecciona el parámetro HTML `element` especificado en el [Explorador DOM](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Inicia un temporizador identificado por el parámetro `name` opcional. Cuando se utiliza con `console.timeEnd`, calcula el tiempo transcurrido entre `time` y `timeEnd`, y envía el resultado (medido en ms) a la consola utilizando la cadena `name` como prefijo. Se utiliza para habilitar la instrumentación del código de la aplicación para medir el rendimiento.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Detiene un temporizador identificado por el parámetro `name` opcional. Consulta el comando de la consola `time` .|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Envía un seguimiento de la pila a la ventana de consola. Los datos de seguimiento incluyen la pila de llamadas completa e información como el nombre de archivo, el número de línea y el número de columna.|`console.trace();`|  
|`warn(message)`|Envía `message` a la ventana de consola, precedido de un símbolo de advertencia.<br /><br /> Los objetos que se pasan mediante el comando se convierten en un valor de cadena.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Comandos varios  
 Estos comandos también están disponibles en la ventana Consola JavaScript (no están disponibles desde el código).  
  
|Comando|Descripción|Ejemplo|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Devuelve el elemento especificado a la ventana de consola. `$0` devuelve el elemento que está seleccionado en el Explorador DOM, `$1` devuelve el elemento seleccionado anteriormente en el Explorador DOM y así sucesivamente, hasta el cuarto elemento anterior seleccionado.|$3|  
|`$(id)`|Devuelve un elemento por su identificador. Se trata de un comando de acceso directo para `document.getElementById(id)`, donde `id` es una cadena que representa el identificador del elemento.|`$("contenthost")`|  
|`$$(selector)`|Devuelve una matriz de elementos que coinciden con el selector especificado mediante la sintaxis del selector de CSS. Es un comando de acceso directo para `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Permite cambiar el contexto para la evaluación de la expresión desde la ventana predeterminada de nivel superior de la página hasta la ventana del marco especificado. Si se llama a `cd()` sin parámetros, se devuelve el contexto a la ventana de nivel superior.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Selecciona el elemento especificado en el [Explorador DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Devuelve un visualizador para el objeto especificado. Puedes usar el visualizador para inspeccionar las propiedades en la ventana de consola.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Comprobar si existe un comando de consola  
 Puedes comprobar si existe un comando determinado antes de intentar utilizarlo. En este ejemplo se comprueba la existencia del comando `console.log` . Si `console.log` existe, el código lo llama.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Examinar objetos en la ventana Consola JavaScript  
 Puedes interactuar con cualquier objeto que esté dentro del ámbito cuando utilices la ventana Consola JavaScript. Para inspeccionar un objeto que esté fuera del ámbito en la ventana de la consola, utiliza `console.log` , `console.dir`u otros comandos del código. También puede interactuar con el objeto desde la ventana de la consola mientras esté dentro del ámbito si establece un punto de interrupción en el código (**Punto de interrupción** > **Insert Punto de interrupción**).  
  
## <a name="ConsoleLog"></a> Aplicación de formato a la salida de console.log  
 Si pasas varios argumentos a `console.log`, la consola los tratará como una matriz y concatenará el resultado.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` también admite patrones de sustitución "printf" para aplicar formato al resultado. Si usas patrones de sustitución en el primer argumento, los demás argumentos se emplearán para sustituir los patrones especificados en el orden en que se utilicen.  
  
 Se admiten los siguientes patrones de sustitución:  
  
- %s - cadena  
   %i - entero  
   %d - entero  
   %f - flotante  
   %o - objeto  
   %b - binario  
   %x - hexadecimal  
   %e - exponente  
  
  Aquí se proporcionan algunos ejemplos del empleo de patrones de sustitución en `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Vea también  
 [Inicio rápido: Depuración de JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Inicio rápido: depuración de HTML y CSS](../debugger/quickstart-debug-html-and-css.md)
