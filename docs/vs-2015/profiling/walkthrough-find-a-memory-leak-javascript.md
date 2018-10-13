---
title: 'Tutorial: Buscar fugas de memoria (JavaScript) | Microsoft Docs'
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
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7feaa8629078be9e5e7a915fe3c09a9599a8f292
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234200"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Tutorial: Buscar pérdidas de memoria (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Este tutorial te guía por el proceso de identificar y corregir un problema simple de memoria con el analizador de memoria de JavaScript. El analizador de memoria de JavaScript está disponible en Visual Studio para las aplicaciones de la Tienda Windows compiladas para Windows que usan JavaScript. En este escenario, crearás una aplicación que conserva incorrectamente elementos DOM en memoria en lugar de eliminarlos a la misma velocidad a la que se crearon.  
  
 Aunque la causa de la pérdida de memoria es muy específica en esta aplicación, los pasos que se muestran aquí indican un flujo de trabajo que suele ser eficaz para aislar los objetos con pérdida de memoria.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Ejecutar la aplicación de prueba del analizador de memoria de JavaScript  
  
1.  En Visual Studio, elige **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Elija **JavaScript** en el panel izquierdo. A continuación, elija **Windows**, **Windows 8**y luego **Universal** o **Aplicaciones Windows Phone**.  
  
    > [!IMPORTANT]
    >  Los resultados del uso de memoria que se muestran en este tema se prueban con una aplicación de Windows 8.  
  
3.  Elija la plantilla de proyecto **Aplicación vacía** en el panel central.  
  
4.  En el cuadro **Nombre** , especifique un nombre como `JS_Mem_Tester`y elija **Aceptar**.  
  
5.  En el **Explorador de soluciones**, abre default.html y pega el siguiente código entre las etiquetas \<body>:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Si usa una plantilla de la aplicación universal de Windows 8.1, deberá actualizar el código HTML y CSS en los proyectos .Windows y .WindowsPhone.  
  
6.  Abre default.css y agrega el código CSS siguiente:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Abre default.js y reemplaza todo el código con este código:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8.  Elija la tecla F5 para iniciar la depuración. Comprueba que el botón **Leak Memory** aparece en la página.  
  
9. Vuelve a Visual Studio (Alt+Tab) y presiona Mayús+F5 para detener la depuración.  
  
     Ahora que has comprobado que la aplicación funciona, puedes examinar el uso de memoria.  
  
### <a name="analyzing-the-memory-usage"></a>Analizar el uso de memoria  
  
1.  En la barra de herramientas **Depurar** , en la lista **Iniciar depuración** , elige el destino de depuración del proyecto actualizado: los emuladores de Windows Phone o **Simulador**.  
  
    > [!TIP]
    >  Para una aplicación de la Tienda Windows, también puedes elegir **Equipo local** o **Equipo remoto** en esta lista. Sin embargo, la ventaja de utilizar el emulador o simulador es que puede colocarlo junto a Visual Studio y cambiar fácilmente entre la aplicación en ejecución y el analizador de memoria de JavaScript. Para obtener más información, consulte [Ejecutar aplicaciones de Visual Studio](../debugger/run-store-apps-from-visual-studio.md) y [Ejecutar aplicaciones de la Tienta Windows en una máquina remota](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2.  En el menú **Depurar** , elija **Performance Profiler...**(Generador de perfiles de rendimiento...).  
  
3.  En **Herramientas disponibles**, elige **Memoria de JavaScript**e **Iniciar**.  
  
     En este tutorial, asociarás el analizador de memoria al proyecto de inicio. Para obtener información sobre otras opciones, como adjuntar el analizador de memoria a una aplicación instalada, consulta [Memoria de JavaScript](../profiling/javascript-memory.md).  
  
     Al iniciar el analizador de memoria, puede aparecer un Control de cuentas de usuario que solicite tu permiso para ejecutar VsEtwCollector.exe. Elija **Sí**.  
  
4.  Elige el botón **Leak Memory** cuatro veces seguidas.  
  
     Cuando eliges el botón, el código de control de eventos de default.js funciona de tal modo que producirá una pérdida de memoria. Lo usarás con fines de diagnóstico.  
  
    > [!TIP]
    >  Al repetir el escenario que deseas probar para una pérdida de memoria se simplifica el filtrado de información que no interesa, como los objetos que se agregan al montón durante la inicialización de la aplicación o cuando se carga una página.  
  
5.  Desde la aplicación en ejecución, cambia a Visual Studio (Alt+Tab).  
  
     El analizador de memoria de JavaScript muestra información en una nueva pestaña en Visual Studio.  
  
     El gráfico de memoria de esta vista de resumen muestra el uso de memoria de proceso a lo largo del tiempo. La vista también proporciona comandos como **Tomar instantánea de montón**. Una instantánea proporciona información detallada sobre el uso de memoria en un momento determinado. Para obtener más información, consulta [Memoria de JavaScript](../profiling/javascript-memory.md).  
  
6.  Elige **Tomar instantánea de montón**.  
  
7.  Cambia a la aplicación y elige **Leak Memory**.  
  
8.  Cambia a Visual Studio y elige de nuevo **Tomar instantánea de montón** .  
  
     En esta ilustración se muestra la instantánea de referencia (1) y la instantánea 2.  
  
     ![La instantánea de línea base y la instantánea 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
    > [!NOTE]
    >  El emulador de Windows Phone no muestra una captura de pantalla de la aplicación cuando se realizó la instantánea.  
  
9. Cambia a la aplicación y vuelve a elegir el botón **Leak Memory** .  
  
10. Cambia a Visual Studio y elige **Tomar instantánea de montón** por tercera vez.  
  
    > [!TIP]
    >  Al tomar una tercera instantánea en este flujo de trabajo, puedes filtrar los cambios de la instantánea de línea de base a la segunda instantánea que no estén asociados con pérdidas de memoria. Por ejemplo, puede haber cambios esperados, como la actualización de encabezados y pies de página en una página. Esto generará algunos cambios en cuanto al uso de la memoria, pero puede que no estén relacionados con pérdidas de memoria.  
  
     En esta ilustración se muestra la instantánea 2 y la instantánea 3.  
  
     ![Instantánea 2 e instantánea 3](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. En Visual Studio, elige **Detener** para detener la generación de perfiles.  
  
12. En Visual Studio, compara las instantáneas. En la instantánea 2 se muestra lo siguiente:  
  
    -   El tamaño del montón (indicado por la flecha arriba de color rojo a la izquierda) ha aumentado en varios kB en comparación con el de la instantánea 1.  
  
        > [!IMPORTANT]
        >  Los valores de uso de memoria exactos para el tamaño del montón dependen del destino de depuración.  
  
    -   El número de objetos del montón (indicado por la flecha arriba de color rojo a la derecha) ha aumentado con respecto al de la instantánea 1. Se agregó un objeto (+1) y no se quitó ninguno (-0).  
  
     En la instantánea 3 se muestra lo siguiente:  
  
    -   El tamaño del montón ha aumentado de nuevo en varios cientos de bytes en comparación con el de la instantánea 2.  
  
    -   El número de objetos del montón también ha aumentado en comparación con el de la instantánea 2. Se agregó un objeto (+1) y no se quitó ninguno (-0).  
  
13. En la instantánea 3, elija el texto del vínculo de la derecha, que muestra un valor de +1 / -0 junto a la flecha arriba de color rojo.  
  
     ![Vincular a una vista diferente de objetos de montón](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Se abrirá una vista de diferencias de los objetos en el montón, denominada **Instantánea 3 - Instantánea 2**, en la que se muestra la vista Tipos de forma predeterminada. De manera predeterminada, se ve una lista de los objetos agregados al montón entre las instantáneas 2 y 3.  
  
14. En el filtro **Ámbito** , elige **Objetos dejados de la instantánea nº 2**.  
  
15. Abre el objeto HTMLDivElement en la parte superior del árbol de objetos, mostrado aquí.  
  
     ![Vista de diferencias del recuento de objetos del montón](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Esta vista muestra información útil sobre la pérdida de memoria, como la siguiente:  
  
    -   Esta vista muestra un elemento DIV con un id. `item`, y el tamaño retenido del objeto es de varios cientos de bytes (el valor exacto puede variar).  
  
    -   Este es un objeto sobrante de la instantánea 2 y representa una posible pérdida de memoria.  
  
     En este punto puede ser útil conocer algo de la aplicación: al elegir el botón **Leak Memory** , se debería quitar un elemento DIV y agregarse un elemento, por lo que el código parece que no funciona bien, es decir, hay una pérdida de memoria. En la sección siguiente se explica cómo solucionar esto.  
  
    > [!TIP]
    >  A veces, la ubicación de un objeto con respecto al objeto `Global` puede ayudar a identificar ese objeto. Para ello, abre el menú contextual del identificador y elige **Mostrar en vista de raíces**.  
  
##  <a name="FixingMemory"></a> Corregir el problema de memoria  
  
1.  Con los datos que revela el generador de perfiles, se examina el código responsable de quitar los elementos DOM cuyo id. sea "item". Esto se produce en la función `initialize()`.  
  
    ```javascript  
    function initialize() {  
  
        if (wrapper != null) {  
            elem.removeNode(true);  
        }  
    }  
    ```  
  
     `elem.removeNode(true)` quizás no funciona bien. Examinas el modo en que el código almacena en caché el elemento DOM y detectas un problema: la referencia al elemento almacenado en caché no se actualiza.  
  
2.  En default.js, agrega la siguiente línea de código a la función de carga, justo antes de la llamada a `appendChild`:  
  
    ```javascript  
    elem = newDiv;  
    ```  
  
     Este código actualiza la referencia al elemento almacenado en caché para que el elemento se quite bien al elegir el botón **Leak Memory** . El código completo de la función de carga tiene ahora el siguiente aspecto:  
  
    ```javascript  
    function load() {  
  
        wrapper = document.querySelector(".wrapper");  
  
        var newDiv = document.createElement("div");  
  
        newDiv.style.zIndex = "-1";  
        newDiv.id = "item";  
        elem = newDiv;  
  
        wrapper.appendChild(newDiv);  
    }  
    ```  
  
3.  En el menú **Depurar** , elija **Rendimiento y diagnósticos**.  
  
4.  En **Herramientas disponibles**, elige **Memoria de JavaScript**e **Iniciar**.  
  
5.  Sigue el mismo procedimiento anterior para tomar tres instantáneas. Aquí se resumen los pasos:  
  
    1.  En la aplicación, elige el botón **Leak Memory** cuatro veces seguidas.  
  
    2.  Cambia a Visual Studio y elige **Tomar instantánea de montón** para la instantánea de referencia.  
  
    3.  En la aplicación, elige el botón **Leak Memory** .  
  
    4.  Cambia a Visual Studio y elige **Tomar instantánea de montón** para la segunda instantánea.  
  
    5.  En la aplicación, elige el botón **Leak Memory** .  
  
    6.  Cambia a Visual Studio y elige **Tomar instantánea de montón** para la tercera instantánea.  
  
     La instantánea 3 ahora muestra el tamaño del montón como **Sin aumento** con respecto a la instantánea 2, y el recuento de objetos como +1 / -1, lo que indica que se ha agregado un objeto y se ha quitado otro. Este es el comportamiento deseado.  
  
     En la ilustración siguiente se muestra la instantánea 2 y la instantánea 3.  
  
     ![Instantáneas que muestran la fuga de memoria corregida](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Vea también  
 [Memoria de JavaScript](../profiling/javascript-memory.md)



