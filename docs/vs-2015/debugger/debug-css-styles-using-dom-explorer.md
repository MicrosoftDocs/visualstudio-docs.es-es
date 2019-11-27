---
title: Depurar estilos CSS mediante el explorador DOM | Microsoft Docs
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
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9f07fc064a87910f59f5734d4d635aa3b5d6b77
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299507"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Depurar estilos de CSS mediante el Explorador DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content. png "windows_and_phone_content")  
  
 Al depurar aplicaciones de la Tienda Windows, aplicaciones de la Tienda de Windows Phone y aplicaciones creadas con Visual Studio Tools para Apache Cordova, puede ver y cambiar las reglas de CSS de los elementos DOM seleccionados y sus elementos secundarios.  
  
 Las pestañas **Estilos** y **Calculado** del Explorador DOM muestran las reglas de CSS que se aplican a un elemento seleccionado. Las reglas se muestran en orden de especificidad de acuerdo con las reglas de prioridad de CSS. Las que aparecen al principio de un selector o estilo en una pestaña (las más específicas) son las últimas que se aplican al elemento seleccionado y las de la parte inferior se aplican en primer lugar. Cuando las reglas se aplican, invalidan las aplicadas anteriormente.  
  
 Las pestañas **Estilos**, **Calculado**y **Cambios** proporcionan vistas diferentes de la información de estilo.  
  
- Use la pestaña **Estilos** para ver las reglas organizadas por nombre de selector de CSS, como `html, body`. También puede usar esta pestaña para habilitar o deshabilitar estilos específicos, editar manualmente los valores y ver los resultados inmediatos de estos cambios.  
  
- Use la pestaña **Calculado** para ver los valores calculados de un estilo. Por ejemplo, si establece el tamaño en 1em, el valor calculado por Internet Explorer puede ser 16px. Los estilos de esta pestaña se organizan por nombre de estilo, como `height`. También puede usar esta pestaña para habilitar o deshabilitar estilos específicos, editar manualmente los valores y ver los resultados inmediatos de estos cambios.  
  
    > [!NOTE]
    > En Visual Studio 2013 Update 2, la información proporcionada en la pestaña **Seguimiento** se ha combinado con la pestaña **Calculado** y la pestaña **Seguimiento** se ha quitado.  
  
- Use la pestaña **Cambios** (solo aplicaciones de la Tienda Windows y aplicaciones de la Tienda de Windows Phone) para identificar y realizar un seguimiento de los estilos CSS que ha cambiado durante una sesión de depuración.  
  
> [!TIP]
> Los cambios realizados en los estilos de las pestañas **Estilos** y **Calculado** no son permanentes. Se pierden cuando se detiene la depuración. Para cambiar el código fuente y recargar las páginas sin detener y reiniciar el depurador, actualice la aplicación mediante el botón de ![botón actualizar aplicación de Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Actualizar aplicación de Windows**) en la barra de herramientas **depurar** (solo aplicaciones de la tienda windows y de la tienda de Windows Phone). Para obtener más información, vea [actualizar una aplicación (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Ejemplo de corrección de una regla de CSS  
 En este ejemplo se muestra cómo inspeccionar las reglas CSS y depurar un problema de estilo. En este ejemplo, digamos que quiere cambiar el color de una fuente utilizada para mostrar títulos de grupo en la plantilla Aplicación dividida de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
> [!NOTE]
> En este ejemplo se muestra una aplicación de la Tienda Windows, pero todas las características del explorador DOM mostradas también se aplican a una aplicación de la Tienda de Windows Phone y, excepto la pestaña Cambios, a una aplicación creada con Visual Studio Tools para Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Para ver y cambiar las reglas CSS  
  
1. En Visual Studio, cree una aplicación de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] con JavaScript y HTML en la plantilla de proyecto Aplicación dividida.  
  
2. En el **Explorador de soluciones**, abra items.css. (Puede buscar items.css en la carpeta de páginas).  
  
3. Reemplace el código de CSS siguiente:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
    }  
    ```  
  
     por este:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
        color: #ff6a00;  
    }  
    ```  
  
     De este modo se agrega un estilo que especifica el color #ff6a00 (naranja) para cada elemento de la lista. El selector de CSS, `.itemspage .itemslist .item`, indica un conjunto de nombres de clase para elementos DIV en items.html, que aparecen como elementos anidados en el DOM activo. El elemento DIV `item` especifica los elementos de lista.  
  
4. Selecciona **Simulador** en la lista desplegable de la barra de herramientas **Depurar** (**Equipo local** es el valor predeterminado).  
  
     ![Seleccionar lista de destinos de depuración](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Presiona F5 para ejecutar la aplicación en modo de depuración.  
  
     Cuando la aplicación finalice la carga, mire los encabezados de los elementos de lista, como **Título de grupo: 1**. El color no ha cambiado, por lo que el intento de aplicar un color naranja a los títulos no ha funcionado. Averiguaremos qué ha salido mal y lo corregiremos usando las pestañas CSS en el Explorador DOM.  
  
    > [!TIP]
    > Cuando la aplicación aparezca en el simulador, colóquelo junto a la ventana de Visual Studio para que pueda ver inmediatamente los resultados de sus selecciones y los cambios realizados en los estilos CSS.  
  
6. Cambie a Visual Studio y haga clic en **Seleccionar elemento** en el Explorador DOM (o presione Ctrl+B). El modo de selección se modifica para que pueda seleccionar un elemento haciendo clic en él. Además, la aplicación se sitúa en primer plano. El modo se revierte al original al hacer clic. Aquí está el botón **Seleccionar elemento** . ![Botón Seleccionar elemento en el explorador DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button ")  
  
    > [!TIP]
    > También puede seleccionar elementos HTML directamente en el Explorador DOM. Para obtener más información sobre la selección de elementos, consulte [Inicio rápido: depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. En el simulador, mantén el mouse sobre el título del primer elemento de la lista, **Título de grupo: 1**, en el panel izquierdo de la página principal. Se resalta el título, como se muestra aquí:  
  
     ![Usar el botón Seleccionar elemento](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > El emulador de Windows Phone solo admite en parte resaltar elementos al colocarse sobre ellos.  
  
8. Haga clic en el título con contorno. El Explorador DOM selecciona automáticamente el elemento HTML correspondiente, que es parecido a este.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Cuando seleccione el elemento H4 en el Explorador DOM, las pestañas del Explorador DOM mostrarán ahora las reglas asociadas al elemento H4. La pestaña **Calculado** se muestra aquí, con la propiedad `color` abierta:  
  
     ![Pestaña estilos de seguimiento del explorador DOM](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Esta vista proporciona información útil sobre las reglas asociadas al estilo de `color` , como la siguiente:  
  
    - El selector de CSS que hemos modificado en items.css, `.itemspage .itemslist .item`, no se usa en el cálculo final del estilo (está tachado). Tampoco se usan otras apariciones del estilo de `color` .  
  
        > [!TIP]
        > En el caso de nombres de selector más largos, el nombre completo aparece como información sobre herramientas.  
  
    - El valor calculado final de CSS, `rgba(255, 255, 255, 0.87)`, se establece específicamente para el selector de CSS siguiente: `.itemspage .itemslist .item .item-overlay .item-title`, que también está definido en items.css.  
  
        > [!TIP]
        > Ahora que sabemos dónde se establece el color del título, también sabemos dónde podemos cambiarlo. Sin embargo, también podemos probar los cambios en el Explorador DOM sin actualizar la aplicación, como se muestra en los pasos restantes.  
  
9. Desactive la casilla de la primera aparición de estilo de `color` , que es la que corresponde al selector `.itemspage .itemslist .item .item-overlay .item-title` . Ahora, en el simulador, verá que el color de los títulos de elemento cambia a naranja, tal como queríamos, y que el selector que modificamos en CSS, `.itemspage .itemslist .item`, ya no se reemplaza (es decir, ya no tiene el tachado de texto aplicado). A continuación se muestra la pestaña **Calculado** después de desactivar la casilla.  
  
     ![La pestaña calculado después de actualizar el estilo CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Seleccione la pestaña **Cambios** .  
  
     Use la pestaña **Cambios** para identificar y realizar un seguimiento de los cambios de estilo que aplique durante una sesión de depuración. En la siguiente ilustración se muestra el selector `.itemspage .itemslist .item .item-overlay .item-title` en la pestaña **Cambios** , que ha sido reemplazado.  
  
     ![Pestaña cambios del explorador DOM](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. También puedes editar manualmente los valores de estilo de CSS y ver el resultado inmediato mediante la pestaña **Estilos** .  
  
12. Selecciona la pestaña **Estilos** .  
  
13. Abra el selector de estilo `.itemspage .itemslist .item .item-overlay .item-title` .  
  
14. Seleccione la primera aparición del estilo de `color` y, a continuación, haga doble clic en el valor de propiedad `rgb(255, 255, 255, 0.87)`.  
  
15. Use el teclado para modificar este valor. Cámbielo a `rgb(255, 255, 0, 0.87)`y, a continuación, presione Intro. Los colores de todos los títulos de elemento del simulador cambiarán a amarillo.  
  
16. Para realizar cambios en el archivo CSS de origen, haga clic en el vínculo **Items. CSS** de la pestaña **estilos** . Se abrirá items. CSS, donde puede cambiar el valor del estilo `color` en el código de la aplicación. Para actualizar la aplicación sin detener y reiniciar el depurador, haga clic en el botón ![Actualizar aplicación de Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Actualizar aplicación de Windows**) en la barra de herramientas **depurar** .  
  
## <a name="see-also"></a>Vea también  
 [Inicio rápido: depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Depurar el diseño mediante el explorador DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Ver agentes de escucha de eventos DOM](../debugger/view-dom-event-listeners.md)   
 [Compatibilidad de productos y accesibilidad](https://go.microsoft.com/fwlink/?LinkId=253502)
