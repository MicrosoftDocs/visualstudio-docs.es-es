---
title: Ver agentes de escucha de eventos de DOM | Documentos de Microsoft
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693584"
---
# <a name="view-dom-event-listeners"></a>Ver agentes de escucha de eventos DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 El **eventos** pestaña del explorador DOM muestra los eventos que están asociados con un elemento DOM. Cada nodo superior en el **eventos** pestaña representa un evento que tiene suscriptores activos. El nodo superior contiene subnodos que representan a los agentes de escucha registrados para el evento específico. Además de para ver los agentes de escucha de eventos, puedes utilizar esta pestaña para navegar a la ubicación del agente de escucha de eventos en el código de JavaScript. La información de este tema se aplica a las aplicaciones de la Tienda compiladas mediante HTML y JavaScript.

 La lista en el **eventos** ficha es dinámica. Si agrega un agente de escucha de eventos mientras la aplicación se está ejecutando, el nuevo evento aparecerá en ella. Para obtener información sobre cómo agregar y quitar agentes de escucha de eventos, consulte [sugerencias para solucionar problemas relacionados con los agentes de escucha de evento](#Tips) en este tema.

> [!NOTE]
> Los agentes de escucha de eventos para los elementos de código que no son elementos DOM, como `xhr`, no aparecen en la **eventos** ficha.

## <a name="view-event-listeners-for-dom-elements"></a>Ver agentes de escucha de eventos para elementos DOM
 En este ejemplo se muestra una aplicación de la Tienda de Windows Phone. Las características del Explorador DOM descritas aquí también son compatibles con las aplicaciones de la Tienda Windows.

#### <a name="to-view-event-listeners"></a>Para ver los agentes de escucha de eventos

1. En Visual Studio, cree una aplicación de JavaScript que use la plantilla de proyecto Aplicación Pivot de Windows Phone.

2. Con la plantilla abierta en Visual Studio, seleccione **Emulator 8.1 WVGA 4 512MB de en** en la lista desplegable en la barra de herramientas de depuración en el depurador:

     ![Seleccionar un destino de depuración](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Presiona F5 para ejecutar la aplicación en modo de depuración.

4. En la aplicación en ejecución, vaya a la **sección 3** elemento dinámico.

5. Cambia a Visual Studio (Alt+Tab o F12).

6. En el Explorador DOM, elija `Find` en la esquina superior derecha.

7. Tipo `ListView`, y, a continuación, presione ENTRAR.

8. Si es necesario, elija el **siguiente** para buscar el `DIV` elemento que representa el `ListView` control (este elemento tiene un `data-win-control` valor `WinJS.UI.ListView`).

     El elemento `DIV` debería estar ahora seleccionado en el Explorador DOM.

9. Elija la **eventos** ficha en el panel de la derecha del explorador DOM.

     Ahora, puedes ver los eventos que tienen suscriptores activos para el elemento `DIV`, como se muestra aquí.

     ![Ficha de eventos del explorador DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Para localizar los agentes de escucha de estos eventos, elija los vínculos de archivo de JavaScript asociados.

11. Para identificar rápidamente agentes de escucha de eventos para elementos principales de la jerarquía DOM, elija un elemento principal en la lista de jerarquías situada en la parte inferior del Explorador DOM.

     ![Selección de elementos primarios en la jerarquía DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     El **eventos** pestaña muestra los agentes de escucha de eventos para cualquier elemento que desee en la lista de la jerarquía.

### <a name="Tips"></a> Sugerencias para solucionar problemas relacionados con los agentes de escucha de eventos
 En algunos escenarios de aplicación, los agentes de escucha de eventos deben quitarse explícitamente mediante [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Use la **eventos** ficha en el explorador DOM para comprobar si se han quitado los agentes de escucha de eventos de los elementos DOM al ejecutar código. A continuación se ofrecen algunas sugerencias para resolver este tipo de problemas:

- Para las aplicaciones que usan el modelo de navegación de una página que se implementa en Visual Studio [plantillas de proyecto](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx), no es normalmente necesario quitar agentes de escucha de eventos registrados para los objetos, como los elementos DOM, que forman parte de una página. En este escenario, un elemento DOM y sus agentes de escucha de eventos asociados tienen la misma vigencia y se pueden recolectar.

- Si la vigencia del elemento u objeto DOM es diferente a la del agente de escucha de eventos asociado, es posible que deba llamar al método `removeEventListener`. Por ejemplo, si usa el evento `window.onresize`, es posible que deba quitar el agente de escucha de eventos al salir de la página en la que controla el evento.

- Si `removeEventListener` no puede quitar el agente de escucha especificado, es posible que se esté llamando en una instancia distinta del objeto. Puede usar el [bind (método) (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) método para resolver este problema al agregar el agente de escucha.

- Para quitar un agente de escucha de eventos que se agregó mediante el uso [bind (método) (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) o mediante el uso de una función anónima, almacene una instancia de la función cuando se agrega el agente de escucha. A continuación se expone un modo de usar este patrón con seguridad:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Si usa el siguiente código en lugar de almacenar una referencia a la función enlazada, no podrá quitar el agente de escucha de eventos explícitamente:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- No puede quitar un agente de escucha de eventos mediante `removeEventListener` si lo agregó mediante el atributo `obj.on<eventname>` como, por ejemplo, `window.onresize = handlerFunc`.

- Usar el analizador de memoria de JavaScript a [memoria de JavaScript](../profiling/javascript-memory.md) en la aplicación. Es posible que los agentes de escucha de eventos que deban quitarse explícitamente aparezcan como fuga de memoria.

## <a name="see-also"></a>Vea también

- [Inicio rápido: depuración de HTML y CSS](../debugger/quickstart-debug-html-and-css.md)
- [Depurar estilos de CSS mediante el Explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Depurar el diseño mediante el Explorador DOM](../debugger/debug-layout-using-dom-explorer.md)