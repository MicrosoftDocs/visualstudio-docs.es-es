---
title: "Usar diferentes exploradores web con las pruebas de IU codificadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "mlearned"
manager: "douge"
---
# Usar diferentes exploradores web con las pruebas de IU codificadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las pruebas de IU codificadas pueden automatizar las pruebas para las aplicaciones web grabando las pruebas con Internet Explorer.  Después, puede personalizar la prueba y reproducirla de nuevo en Internet Explorer u otros tipos de exploradores para estas aplicaciones web.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
-   Sistemas operativos:  
  
    -   Microsoft Windows 7  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Versiones de explorador web:  
  
    -   Windows Internet Explorer 9  
  
    -   Windows Internet Explorer 10  
  
    -   Si desea conocer las versiones de Mozilla Firefox y Google Chrome compatibles, vaya [aquí](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
-   Instale los [componentes Selenium para pruebas de interfaz de usuario codificadas en distintos exploradores](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **¿Qué se admite en todos los exploradores web?**  
  
-   [Agregar código personalizado para controlar características](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) como propiedades, búsqueda y objetos Waiter de reproducción.  
  
-   Elementos emergentes y cuadros de diálogo  
  
-   [Ejecutar JavaScript básico sin tipo de valor devuelto](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Resistencia de búsqueda \(mediante coincidencia inteligente\) y [mejoras de rendimiento](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## ¿Por qué se deben usar pruebas de IU codificadas en varios tipos de explorador web?  
 Al probar la aplicación web en varios tipos de explorador web, se emula mejor la experiencia de los usuarios que pueden trabajar con exploradores diferentes.  Por ejemplo, la aplicación puede incluir un control o código en Internet Explorer que no sean compatibles con otros exploradores web.  Al ejecutar las pruebas codificadas de la interfaz de usuario en otros exploradores, puede detectar y corregir cualquier problema antes de que afecte a los clientes.  
  
## ¿Cómo grabar y reproducir pruebas de IU codificadas en aplicaciones web mediante los exploradores web admitidos?  
 **Grabación:** debe utilizar el generador de pruebas de IU codificadas para grabar la prueba de la aplicación web mediante Internet Explorer.  Puede agregar opcionalmente validación y código personalizado para los controles probados utilizando un conjunto predefinido de propiedades, como lo haría normalmente para las pruebas de IU codificadas.  Para obtener más información, vea [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  No puede grabar pruebas de IU codificadas con los exploradores Google Chrome o Mozilla Firefox.  
  
 **Reproducción con Internet Explorer:** cuando no se especifica ningún explorador explícitamente, las pruebas se ejecutarán en Internet Explorer de forma predeterminada.  Puede indicar explícitamente el explorador que se utilizará estableciendo la propiedad **BrowserWindow.CurrentBrowser** en el código de prueba.  Con Internet Explorer, esta propiedad se debe establecer en **IE** o **Internet Explorer**.  
  
 **Reproducción con exploradores web que no son Internet Explorer:** para reproducir en exploradores web que no son Internet Explorer, cambie la propiedad BrowserWindow.CurrentBrowser del código de prueba a **Firefox** o **Chrome**.  
  
 Para reproducir pruebas en exploradores que no son IE, debe instalar los **Selenium components for Coded UI Cross Browser Testing**.  
  
#### Instalar componentes Selenium  
  
1.  En el menú **Herramientas**, elija **Extensiones y actualizaciones**.  
  
2.  En el cuadro de diálogo Extensiones y actualizaciones, busque `Selenium components for Cross Browser Testing`.  
  
3.  Resalte la extensión y elija **Descargar**.  
  
    > [!TIP]
    >  También puede descargar los componentes Selenium para pruebas de interfaz de usuario codificadas en distintos exploradores desde [aquí](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 Para obtener más información sobre cómo crear y usar pruebas de IU codificadas, vea [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### Habilitar depuración  
 Para habilitar la depuración de la aplicación web, debe completar las opciones de configuración siguientes:  
  
1.  Habilitar Solo mi código:  
  
    1.  En el menú **Herramientas**, elija **Opciones** y, después, **Depuración**.  
  
    2.  Seleccione **Habilitar Solo mi código**.  
  
2.  Deshabilitar excepciones de CLR:  
  
    1.  En el menú **Depurar**, elija **Excepciones**.  
  
    2.  Para **Excepciones de Common Language Runtime**, desactive **No controlada por el usuario**.  
  
##  <a name="generate"></a> *No se ve la opción para cambiar BrowserWindow.CurrentBrowser en la prueba de IU codificada.*  
 Puede que esté usando una versión de [!INCLUDE[vs2011_first](../test/includes/vs2011_first_md.md)] que no admite pruebas de IU codificadas en distintos exploradores web.  Para usar estas pruebas de IU, debe usar Visual Studio Enterprise.  
  
 *¿Qué más debería saber?*  
 **Notas**  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") El explorador web Apple Safari no se admite.  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") La acción de iniciar el explorador web debe formar parte de la prueba de IU codificada.  
  
     Si tiene un explorador web abierto y desea ejecutar pasos en él, la reproducción producirá un error a menos que se utilice Internet Explorer.  Por consiguiente, se recomienda incluir el inicio del explorador web como parte de las pruebas de IU codificadas.  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") No se admite la automatización de acciones de IU específicas del explorador como maximizar, minimizar y restaurar.  
  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Puede configurar la salida para incluir capturas de pantalla en los registros de IU codificados.  Para ello, debe establecer algunas opciones de configuración en el archivo QTAgent32.exe.config.  De forma predeterminada, este archivo se instala en la siguiente ubicación:  
  
     **C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Common7\\IDE**  
  
     Establezca los siguientes valores:  
  
    -   `EqtTraceLevel` en la sección `system.diagnostics`.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         Al establecer el valor en 3 o superior, se toman capturas de pantalla para cada acción.  Cuando el valor se establece en 1 o 2, las capturas de pantalla se toman solo para acciones de error.  
  
     Para obtener más información, vea [Analizar pruebas de IU codificadas usando los registros de pruebas de IU codificadas](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)  
  
## Recursos externos  
  
### Vídeos  
 [Grabación en IE y reproducción en cualquier lugar](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Crear pruebas en distintos exploradores con el generador de pruebas de IU codificadas](https://onedrive.live.com/?cid=ae5cd7309cccc43c&id=AE5CD7309CCCC43C%21184&sff=1&authkey=%21AKG8CSow_qmeTq8&v=3)  
  
 [Crear pruebas en distintos exploradores con codificación manual normal sin mapa de IU](https://onedrive.live.com/?cid=ae5cd7309cccc43c&id=AE5CD7309CCCC43C%21186&sff=1&authkey=%21AJaEvxJnsefyAT4&v=3)  
  
 [Ejecutar pruebas en varios exploradores secuencialmente](https://onedrive.live.com/?cid=ae5cd7309cccc43c&id=AE5CD7309CCCC43C%21187&sff=1&authkey=%21ADI8eCQkxHnpOR8&v=3)  
  
 [Solucionar problemas debidos a errores de pruebas en varios exploradores](https://onedrive.live.com/?cid=ae5cd7309cccc43c&id=AE5CD7309CCCC43C%21182&sff=1&authkey=%21AEpS48i295B49FI&v=3)  
  
### Guía  
 [Pruebas para la entrega continua con Visual Studio 2012 – Capítulo 2: Pruebas unitarias: prueba interna](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Pruebas para la entrega continua con Visual Studio 2012 – Capítulo 5: Automatización de las pruebas del sistema](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### Preguntas más frecuentes  
 [Preguntas más frecuentes sobre las pruebas de IU codificada \- 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Preguntas más frecuentes sobre las pruebas de IU codificada \- 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### Foro  
 [Pruebas de automatización de la interfaz de usuario de Visual Studio \(incluyen Coded UI\)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## Vea también  
 [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analizar pruebas de IU codificadas usando los registros de pruebas de IU codificadas](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)