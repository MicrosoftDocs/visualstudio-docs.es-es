---
title: 'Inicio rápido: Depurar HTML y CSS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 710bafe2383d95358ba06a287a300d9aea7baf66
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729973"
---
# <a name="quickstart-debug-html-and-css"></a>Inicio rápido: Depurar HTML y CSS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Para las aplicaciones de JavaScript, Visual Studio ofrece una experiencia de depuración completa que incluye características que los desarrolladores de Internet Explorer y Visual Studio ya conocen. Estas características son compatibles con las aplicaciones [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], las aplicaciones de la Tienda de Windows Phone y las aplicaciones creadas con Visual Studio Tools para Apache Cordova.  
  
 Con el modelo de depuración interactivo ofrecido por las herramientas de inspección de DOM, puede ver y modificar el código HTML y CSS presentado, y todo ello sin detener y reiniciar el depurador.  
  
 En este tema:  
  
- [Inspeccionar el DOM activo](#InspectingDOM)  
  
- [Selecting elements](#SelectingElements)  
  
  Para obtener más información sobre el empleo del Explorador DOM, consulte los siguientes temas:  
  
- [Depurar estilos de CSS mediante el Explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [Depurar el diseño mediante el Explorador DOM](../debugger/debug-layout-using-dom-explorer.md)  
  
- [Ver agentes de escucha de eventos DOM](../debugger/view-dom-event-listeners.md)  
  
- [Actualizar una aplicación (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [Depurar un control WebView](../debugger/debug-a-webview-control.md)  
  
  Para obtener información sobre otras características, como el uso de la ventana Consola JavaScript y establecer puntos de interrupción, la depuración de JavaScript consulte [inicio rápido: depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) y [depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InspectingDOM"></a> Inspeccionar el DOM activo  
 El Explorador DOM muestra una vista de la página presentada. Puedes utilizarlo para cambiar valores y ver inmediatamente los resultados. Eso permite probar los cambios sin necesidad de detener y reiniciar el depurador. El código fuente del proyecto no cambia cuando se interactúa con la página mediante este método. Así pues, cuando encuentre las correcciones de código deseadas, realice los cambios en el código fuente.  
  
> [!TIP]
>  Para evitar detener y reiniciar el depurador al realizar cambios en el código fuente, puede actualizar la aplicación mediante el botón **Actualizar aplicación de Windows** de la barra de herramientas Depurar (o al presionar F4). Para obtener más información, consulte [actualizar una aplicación (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 Puedes utilizar el Explorador DOM para:  
  
- Navegar por el subárbol de elementos DOM e inspeccionar el código HTML, CSS y JavaScript presentado.  
  
- Editar de forma dinámica atributos y estilos CSS de los elementos presentados y ver los resultados de inmediato.  
  
- Inspeccionar la aplicación de los estilos CSS a los elementos de la página y realizar el seguimiento de las reglas que se han aplicado.  
  
  Al depurar aplicaciones, con frecuencia tienes que seleccionar elementos en el Explorador DOM. Cuando se selecciona un elemento, los valores que aparecen en las pestañas del lado derecho del Explorador DOM se actualizan automáticamente para reflejar el elemento seleccionado en este. Estas son las pestañas: **Estilos**, **Calculado**y **Diseño**. Las aplicaciones de la Tienda Windows también admiten las pestañas **Eventos** y **Cambios** . Para obtener más información sobre la selección de elementos, consulte [Selecting elements](#SelectingElements).  
  
> [!TIP]
>  Si la ventana del Explorador DOM está cerrada, elija **Depurar**>**Ventanas** > **Explorador DOM** para abrirla de nuevo. La ventana únicamente aparece durante las sesiones de depuración de script.  
  
 En el procedimiento siguiente, analizaremos el proceso de depurar de forma interactiva una aplicación utilizando el Explorador DOM. Crearemos una aplicación que usa un control `FlipView` y la depuraremos. La aplicación contiene varios errores.  
  
> [!WARNING]
>  La siguiente aplicación de muestra es una aplicación de la Tienda Windows. Se admiten las mismas características para Cordova, pero la aplicación sería diferente.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Para depurar inspeccionando el DOM activo  
  
1. Cree una nueva solución en Visual Studio eligiendo **Archivo** > **Nuevo proyecto**.  
  
2. Elija **JavaScript** > **Tienda**, elija **Aplicaciones Windows** o **Aplicaciones Windows Phone**y, a continuación, **Aplicación vacía**.  
  
3. Escriba un nombre para el proyecto, como `FlipViewApp`, y elija **Aceptar** para crear la aplicación.  
  
4. En el elemento BODY de default.html, agrega este código:  
  
   ```html  
   <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
            style="display:none">  
       <div class="fixedItem" >  
           <img src="#" data-win-bind="src: flipImg" />  
       </div>  
   </div>  
   <div id="fView" style="width:100px;height:100px"  
       data-win-control="WinJS.UI.FlipView" data-win-options="{  
       itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
   </div>  
   ```  
  
5. Abre default.css y agrega el código CSS siguiente:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Reemplaza el código de default.js con este otro:  
  
   ```javascript  
   (function () {  
       "use strict";  
  
       var app = WinJS.Application;  
       var activation = Windows.ApplicationModel.Activation;  
  
       var myData = [];  
       for (var x = 0; x < 4; x++) {  
           myData[x] = { flipImg: "/images/logo.png" }  
       };  
  
       var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
       app.onactivated = function (args) {  
           if (args.detail.kind === activation.ActivationKind.launch) {  
               if (args.detail.previousExecutionState !==  
               activation.ApplicationExecutionState.terminated) {  
                   // TODO: . . .  
               } else {  
                   // TODO: . . .  
               }  
               args.setPromise(WinJS.UI.processAll());  
  
               updateImages();  
           }  
       };  
  
       function updateImages() {  
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
       };  
  
       app.oncheckpoint = function (args) {  
       };  
  
       app.start();  
  
       var publicMembers = {  
           items: pages  
       };  
  
       WinJS.Namespace.define("Data", publicMembers);  
  
   })();  
   ```  
  
    En la siguiente ilustración se muestra lo que queremos ver al ejecutar esta aplicación en el emulador de Windows Phone (es parecido en el simulador). En cambio, para que la aplicación tenga este estado, primero tenemos que corregir algunos errores.  
  
    ![Aplicación FlipView que muestra los resultados esperados](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Elige **Simulador** o **Emulator 8.1 WVGA 512MB(ES)** en la lista desplegable situada junto al botón **Iniciar depuración** de la barra de herramientas **Depurar** :  
  
    ![Lista de destinos de depuración seleccione](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Elija **Depurar** > **Iniciar depuración**o bien presione F5 para ejecutar la aplicación en modo de depuración.  
  
    La aplicación se ejecuta en el simulador o en el emulador de Windows Phone, pero lo que verás sobre todo será una pantalla en blanco, porque el estilo tiene algunos errores. La primera imagen `FlipView` aparece en un cuadrado pequeño cerca del centro de la pantalla.  
  
9. Si ejecuta la aplicación en el simulador, elija el comando de barra de herramientas **Cambiar resolución** en la parte derecha del simulador para configurar una resolución de pantalla de 1280 x 800. De este modo nos aseguraremos de que los valores que se muestran en los pasos siguientes coincidan con los que ves en el simulador.  
  
10. Cambia a Visual Studio y elige la pestaña **Explorador DOM** .  
  
    > [!TIP]
    >  Puedes presionar Alt+Tab o F12 para cambiar entre Visual Studio y la aplicación en ejecución.  
  
11. En la ventana del Explorador DOM, selecciona el elemento DIV de la sección cuyo identificador es `"fView"`. Utiliza las teclas de dirección para ver y seleccionar el elemento DIV correcto. (La tecla de flecha derecha te permite ver los elementos secundarios de un elemento).  
  
     ![DOM Explorer](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  También puede seleccionar el elemento DIV en la esquina inferior izquierda de la ventana Consola JavaScript; para ello, escriba `select(fView)` en el indicador de entrada >> y presione Entrar.  
  
     Los valores que aparecen en las pestañas del lado derecho de la ventana del Explorador DOM se actualizan automáticamente para reflejar el elemento actual en el Explorador DOM.  
  
12. Elige la pestaña **Calculado** a la derecha.  
  
     Esta pestaña muestra el valor calculado, o final, para cada propiedad del elemento DOM seleccionado.  
  
13. Abre la regla CSS para el alto. Observa que hay un estilo en línea establecido en 100px que no parece coherente con el valor del alto de 100 % establecido para el selector de CSS `#fView` . El texto tachado para el selector `#fView` indica que el estilo en línea tiene prioridad sobre este estilo.  
  
     En la siguiente ilustración se muestra la pestaña **Calculado** .  
  
     ![Pestaña calculado del explorador DOM](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. En la ventana principal del Explorador DOM, haz doble clic en el estilo en línea para el alto y el ancho del elemento DIV `fView` . Puedes editar aquí los valores. En este escenario, deseamos quitarlos por completo.  
  
15. Seleccione `width: 100px;height: 100px;`y presione la tecla Supr y luego Entrar. Después de presionar Entrar, los nuevos valores se reflejan de inmediato en el simulador o en el emulador de Windows Phone, aunque no haya detenido la sesión de depuración.  
  
    > [!IMPORTANT]
    >  Al igual que puedes actualizar atributos en la ventana del Explorador DOM, también puede actualizar los valores que aparecen en las pestañas **Estilos**, **Calculado**y **Diseño** . Para obtener más información, consulte [estilos CSS depurar mediante el explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md) y [diseño de depuración mediante el explorador DOM](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Cambia a la aplicación seleccionando el simulador o el emulador de Windows Phone, o utilizando Alt + Tab.  
  
     Ahora, el control `FlipView` parece mayor que la pantalla del simulador o el emulador de Windows Phone. Este no es el resultado deseado. Para averiguar más, vuelve a Visual Studio.  
  
17. En el Explorador DOM, selecciona de nuevo la pestaña **Calculado** y abre la regla del alto. El elemento fView sigue mostrando un valor de 100 %, tal como se espera de la CSS, pero el valor calculado es igual al alto de pantalla del simulador (por ejemplo, 800 px o 667,67 px), y no es lo que queremos para esta aplicación. Para investigar, puede quitar el alto y el ancho del elemento DIV `fView` .  
  
18. En la pestaña **Estilos** , desactive las propiedades de ancho y alto del selector de CSS `#fView` .  
  
     La pestaña **Calculado** muestra ahora un alto de 400px. La información indica que este valor se obtiene del selector .win-flipview especificado en ui-dark.css, que es un archivo CSS de plataforma.  
  
19. Cambia de nuevo a la aplicación.  
  
     Las cosas han mejorado. Pero hay un problema más por resolver: los márgenes son demasiado grandes.  
  
20. Para investigar, vaya a Visual Studio y elija la pestaña **Diseño** para ver el modelo de cuadros del elemento.  
  
     En la pestaña **Diseño** , verá los valores siguientes:  
  
    - Para el simulador: 320 píxeles (desplazamiento) y 320 píxeles (margen).  
  
    - Para el emulador de Windows Phone: 100 píxeles (desplazamiento) y 100 píxeles (margen).  
  
      En la siguiente ilustración se muestra el aspecto de la pestaña **Diseño** si se usa el emulador de Windows Phone (100 píxeles de desplazamiento y margen).  
  
      ![Pestaña diseño del explorador DOM](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      Esto no parece correcto. La pestaña **Calculado** también muestra los mismos valores de margen.  
  
21. Elige la pestaña **Estilos** y busca el selector de CSS `#fView` . Aquí, se ve el valor del 25 % para la propiedad **margen** .  
  
22. Selecciona el 25 %, cámbialo a 25px y presiona Intro.  
  
23. También en la pestaña **Estilos** , elija la regla del alto para el selector .win-flipview, cambie 400 píxeles por 500 y presione Entrar.  
  
24. Cambia de nuevo a la aplicación. Comprobarás que la posición de los elementos es correcta. Para realizar correcciones en el código fuente y actualizar la aplicación sin detener y reiniciar el depurador, consulta el procedimiento siguiente.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Para actualizar la aplicación durante la depuración  
  
1.  Mientras la aplicación se está ejecutando, cambia a Visual Studio.  
  
2.  Abre default.html y modifica tu código fuente cambiando el alto y ancho del elemento DIV `"fView"` al 100 %.  
  
3.  Elige el botón **Actualizar aplicación de Windows** situado en la barra de herramientas Depurar (o presiona F4). El botón tiene este aspecto: ![botón de actualización de Windows app](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Se recargan las páginas de la aplicación y el simulador o el emulador de Windows Phone vuelven al primer plano.  
  
     Para obtener más información acerca de la característica de actualización, vea [actualizar una aplicación (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
##  <a name="SelectingElements"></a> Selecting elements  
 Puedes seleccionar elementos DOM de tres maneras al depurar una aplicación:  
  
- Haciendo clic en los elementos directamente en la ventana del Explorador DOM (o utilizando las teclas de dirección).  
  
- Utilizando el botón **Seleccionar elemento** (Ctrl + B).  
  
- Utilizando el botón `select` , que es uno de los [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
  Cuando utilices la ventana del Explorador DOM para seleccionar elementos y sitúes el puntero del mouse sobre un elemento, el elemento correspondiente se resaltará en la aplicación que se ejecuta. Haz clic en el elemento en DOM Explorer para seleccionarlo, o puedes utilizar las teclas de dirección para resaltar y seleccionar elementos. También puedes seleccionar elementos del Explorador DOM mediante el botón **Seleccionar elemento** . En la ilustración siguiente se muestra el botón **Seleccionar elemento** .  
  
  ![Botón Seleccionar elemento en el explorador DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Al hacer clic en **Seleccionar elemento** (o presionar Ctrl + B), el modo de selección cambia para que puedas seleccionar un elemento del Explorador DOM haciendo clic en él desde la aplicación que se ejecuta. El modo vuelve a cambiar al modo de selección normal después de un solo clic. Al hacer clic en **Seleccionar elemento**, la aplicación se pone en primer plano. El cursor cambia para reflejar el nuevo modo de selección. Al hacer clic en el elemento con contorno, el Explorador DOM vuelve al primer plano con ese elemento seleccionado.  
  
  Antes de elegir **Seleccionar elemento**, puede especificar si desea resaltar los elementos de la aplicación en ejecución mediante la alternancia del botón **Mostrar cuadros de resaltado de página web para el elemento seleccionado en el árbol DOM** . En la siguiente ilustración se muestra este botón. Los elementos resaltados se muestran de forma predeterminada.  
  
  ![Página de presentación web destaca botón](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Al elegir que se resalten los elementos, se resaltan aquellos sobre los que se mantiene el mouse en el simulador. Los colores de los elementos resaltados coinciden con el modelo de cuadro que aparece en la pestaña **Diseño** del Explorador DOM.  
  
> [!NOTE]
>  El resaltado de elementos al pasar sobre ellos solo se admite en parte en el emulador de Windows Phone.  
  
 Para obtener un ejemplo que muestra cómo seleccionar elementos mediante el **elemento Select** botón, consulte [estilos CSS depurar mediante el explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
##  <a name="BrowserSupport"></a> Compatibilidad con explorador y plataforma  
 Las herramientas de Visual Studio para JavaScript, el Explorador DOM y la ventana Consola JavaScript se admiten en las plataformas siguientes:  
  
- Aplicaciones de la[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] y la Tienda de Windows Phone con JavaScript y HTML  
  
- Internet Explorer 11 que se ejecute en [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Internet Explorer 10 que se ejecute en [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Entre [aquí](http://go.microsoft.com/fwlink/?LinkID=232448) para descargar [!INCLUDE[win8](../includes/win8-md.md)] y Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Depurar estilos de CSS mediante el explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Depurar el diseño mediante el explorador DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Ver agentes de escucha de eventos de DOM](../debugger/view-dom-event-listeners.md)   
 [Actualizar una aplicación (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Depurar un control WebView](../debugger/debug-a-webview-control.md)   
 [Métodos abreviados de teclado](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [JavaScript Console commands](../debugger/javascript-console-commands.md)   
 [Depurar código de ejemplo HTML, CSS y JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Compatibilidad de productos y accesibilidad](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)



