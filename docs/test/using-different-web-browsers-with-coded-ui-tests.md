---
title: Uso de diferentes exploradores web con las pruebas automatizadas de IU en Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 69f2f186b8462b5630970bdc93e358ffc61ad0f5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Usar diferentes exploradores web con las pruebas automatizadas de IU

Las pruebas de IU codificadas pueden automatizar las pruebas para las aplicaciones web grabando las pruebas con Internet Explorer. Después, puede personalizar la prueba y reproducirla de nuevo en Internet Explorer u otros tipos de exploradores para estas aplicaciones web.

En primer lugar, instale los [componentes Selenium para pruebas automatizadas de IU en distintos exploradores](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>¿Qué se admite en todos los exploradores web?

-   [Agregar código personalizado para controlar características](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) como propiedades, búsqueda y objetos Waiter de reproducción

-   Elementos emergentes y cuadros de diálogo

-   [Ejecutar JavaScript básico sin tipo de valor devuelto](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)

-   Resistencia de búsqueda (mediante coincidencia inteligente) y [mejoras de rendimiento](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>¿Por qué se deben usar pruebas de IU codificadas en varios tipos de explorador web?

Al probar la aplicación web en varios tipos de explorador web, se emula mejor la experiencia de los usuarios que pueden trabajar con exploradores diferentes. Por ejemplo, la aplicación puede incluir un control o código en Internet Explorer que no sean compatibles con otros exploradores web. Al ejecutar las pruebas codificadas de la interfaz de usuario en otros exploradores, puede detectar y corregir cualquier problema antes de que afecte a los clientes.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>¿Cómo grabar y reproducir pruebas de IU codificadas en aplicaciones web mediante los exploradores web admitidos?

**Grabación**: debe usar el generador de pruebas automatizadas de IU para grabar la prueba de la aplicación web mediante Internet Explorer. Puede agregar opcionalmente validación y código personalizado para los controles probados utilizando un conjunto predefinido de propiedades, como lo haría normalmente para las pruebas de IU codificadas. Para más información, vea [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> No puede grabar pruebas de IU codificadas con los exploradores Google Chrome o Mozilla Firefox.

 **Reproducción con Internet Explorer:** cuando no se especifica ningún explorador explícitamente, las pruebas se ejecutarán en Internet Explorer de forma predeterminada. Puede indicar explícitamente el explorador que se usará mediante el establecimiento de la propiedad **BrowserWindow.CurrentBrowser** en el código de prueba. Con Internet Explorer, esta propiedad se debe establecer en **IE** o **Internet Explorer**.

 **Reproducción con exploradores web que no son Internet Explorer:** para reproducir en exploradores web que no son Internet Explorer, cambie la propiedad BrowserWindow.CurrentBrowser del código de prueba a **Firefox** o **Chrome**.

 Para reproducir pruebas en exploradores web que no son IE, debe instalar los **componentes Selenium para pruebas automatizadas de interfaz de usuario en distintos exploradores**.

### <a name="install-selenium-components"></a>Instalar componentes Selenium

1.  En el menú **Herramientas** , elija **Extensiones y actualizaciones**.

2.  En el cuadro de diálogo Extensiones y actualizaciones, busque `Selenium components for Cross Browser Testing`.

3.  Resalte la extensión y seleccione **Descargar**.

    > [!TIP]
    > También puede descargar los componentes Selenium para pruebas automatizadas de IU en distintos exploradores [aquí](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Para más información sobre cómo crear y usar pruebas automatizadas de IU, vea la sección relativa a la [creación de pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Habilitar depuración

Para habilitar la depuración de la aplicación web, debe completar las opciones de configuración siguientes:

1.  Habilitar Solo mi código:

    1.  En el menú **Herramientas**, seleccione **Opciones** y, después, **Depuración**.

    2.  Seleccione **Habilitar Solo mi código**.

2.  Deshabilitar excepciones de CLR:

    1.  En el menú **Depurar**, seleccione **Excepciones**.

    2.  Para **Common Language Runtime Exceptions** (Excepciones de Common Language Runtime), desactive **No controlada por el usuario**.

Si no ve la opción para cambiar `BrowserWindow.CurrentBrowser` en la prueba automatizada de IU, puede que esté usando una versión de Visual Studio que no admite las pruebas automatizadas de IU con varios exploradores web. Para usar estas pruebas automatizadas de IU, debe utilizar la edición Visual Studio Enterprise.

Otra información que debe saber:

- El explorador web Apple Safari no se admite.

- La acción de iniciar el explorador web debe formar parte de la prueba de IU codificada.

   Si tiene un explorador web abierto y desea ejecutar pasos en él, la reproducción producirá un error a menos que se utilice Internet Explorer. Por consiguiente, se recomienda incluir el inicio del explorador web como parte de las pruebas de IU codificadas.

- No se admite la automatización de acciones de IU específicas del explorador como maximizar, minimizar y restaurar.

## <a name="tips"></a>Sugerencias

Puede configurar la salida para incluir capturas de pantalla en los registros de IU codificados. Para ello, debe establecer algunas opciones de configuración en el archivo *QTAgent32.exe.config*. De forma predeterminada, este archivo se instala en la siguiente ubicación:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Establezca los siguientes valores:

- `EqtTraceLevel` en la sección `system.diagnostics`.

- `<add name="EqtTraceLevel" value="4" />`

   Al establecer el valor en 3 o más, se toman capturas de pantalla para cada acción. Cuando el valor se establece en 1 o 2, las capturas de pantalla se toman solo para acciones de error.

Para obtener más información, consulte [Analizar pruebas de IU codificadas usando los registros de pruebas de IU codificadas](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Recursos de vídeo

 [Grabación en IE y reproducción en cualquier lugar](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Crear pruebas en distintos exploradores con el generador de pruebas automatizadas de IU](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Crear pruebas en distintos exploradores con codificación manual normal sin asignación de IU](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Ejecutar pruebas en varios exploradores secuencialmente](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Solucionar problemas debidos a errores de pruebas en varios exploradores](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Vea también

- [Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizar pruebas de IU codificadas mediante los registros de pruebas de IU codificadas](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
