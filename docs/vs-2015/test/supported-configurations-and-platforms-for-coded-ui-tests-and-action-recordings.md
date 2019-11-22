---
title: Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a4a049bca7ecb51a4b518c84b15d7dfa4ed3290f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301207"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la tabla siguiente se enumeran las configuraciones y plataformas compatibles con las pruebas de IU codificadas de Visual Studio Enterprise. Estas configuraciones también se aplican a las grabaciones de acciones creadas mediante [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].

> [!NOTE]
> El proceso de prueba de IU codificada debe tener los mismos privilegios que la aplicación en prueba.

 **Requisitos**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Configuraciones compatibles

|Configuración|Compatible|
|-------------------|---------------|
|Sistemas operativos|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|
|Compatibilidad con 32 y 64 bits|El sistema operativo Windows de 32 bits que ejecuta [!INCLUDE[TCMext](../includes/tcmext-md.md)] de 32 bits puede probar aplicaciones de 32 bits.<br /><br /> El sistema operativo Windows de 64 bits donde se ejecuta [!INCLUDE[TCMext](../includes/tcmext-md.md)] de 32 bits puede probar aplicaciones WOW de 32 bits que tengan sincronización de IU.<br /><br /> El sistema operativo Windows de 64 bits que ejecuta [!INCLUDE[TCMext](../includes/tcmext-md.md)] de 32 bits puede probar aplicaciones de Windows Forms y WPF de 64 bits que no tienen sincronización de la interfaz de usuario.|
|Arquitectura|x86 y x64 **Nota:**  Internet Explorer no es compatible en modo de 64 bits excepto cuando se ejecuta en [!INCLUDE[win8](../includes/win8-md.md)] o versiones posteriores.|
|.NET|.NET 2.0, 3.0, 3.5, 4 y 4.5. **Nota:**  [!INCLUDE[TCMext](../includes/tcmext-md.md)] y Visual Studio requieren .NET 4 para funcionar. Sin embargo, se admiten las aplicaciones desarrolladas con las versiones de .NET enumeradas.|

> [!NOTE]
> *Sincronización de la interfaz de usuario* es una característica que comprueba la reproducción en la cola de mensajes de cada control. Si un control no respondiera al evento que se le envió, el evento se envía de nuevo.

## <a name="platform-support"></a>Compatibilidad de la plataforma

|Plataforma|Nivel de compatibilidad|
|--------------|----------------------|
|Aplicaciones de Windows Phone|Solo se admiten aplicaciones de Phone basadas en WinRT-XAML.|
|Aplicaciones de la Tienda Windows|Solo se admiten aplicaciones de la Tienda basadas en XAML.|
|Aplicaciones Windows universales|Solo se admiten aplicaciones universales de Windows basadas en XAML en el teléfono y el escritorio.|
|Borde|En Visual Studio 2015 Update 2 y posterior mediante la [extensión de prueba entre navegadores de IU codificada](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Importante:**  Internet Explorer 10 solo es compatible en el escritorio. <br /><br /> Internet Explorer 11 **Importante:**  Internet Explorer 11 solo es compatible  en el escritorio.|Totalmente compatible.<br /><br /> -   **Compatibilidad con HTML5 en Internet Explorer 9 o Internet Explorer 10:** las pruebas de IU codificadas admiten grabación, reproducción, y validación de los controles HTML5: audio, vídeo, barra de progreso y control deslizante. Para obtener más información, consulte [Usar controles HTML5 en pruebas de IU codificada](../test/using-html5-controls-in-coded-ui-tests.md). **Advertencia:**      Si crea pruebas de IU codificadas en Internet Explorer 10, podría no ejecutarse con Internet Explorer 9 o Internet Explorer 8. Esto es porque Internet Explorer 10 incluye controles HTML5, como audio, vídeo, barra de progreso y control deslizante. Internet Explorer 9 o Internet Explorer 8 no reconocen estos controles HTML5. Igualmente, la prueba de IU codificada mediante Internet Explorer 9 podría incluir algunos controles HTML5 que tampoco reconoce Internet Explorer 8.<br />-   **Compatibilidad con la revisión ortográfica de Internet Explorer 10:** Internet Explorer 10 incluye funciones de revisión ortográfica para todos los cuadros de texto. Esto permite elegir entre una lista de correcciones sugeridas. Las pruebas de IU codificadas omitirán acciones de usuario como seleccionar una sugerencia ortográfica alternativa. Se grabará únicamente el texto final escrito en el cuadro de texto.<br />     Las siguientes acciones se graban para las pruebas de IU codificadas que utilicen el control de revisión ortográfica: agregar al diccionario, copiar, seleccionar todo y omitir.<br />-   **Compatibilidad con Internet Explorer 64 bits que se ejecuta en Windows 8:** previamente, las versiones de 64 bits de Internet Explorer no se admitían para grabar y reproducir. Con [!INCLUDE[win8](../includes/win8-md.md)] y [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], las pruebas de IU codificadas se han habilitado para las versiones de 64 bits de Internet Explorer. **Advertencia:**      La compatibilidad con 64 bits para Internet Explorer solo se aplica cuando se ejecuta [!INCLUDE[win8](../includes/win8-md.md)] o posterior.<br />-   **Compatibilidad con los sitios anclados en Internet Explorer 9:** en Internet Explorer 9, se han incorporado sitios anclados. Con sitios anclados, puede ir a los sitios favoritos directamente desde la barra de tareas de Windows, sin tener que abrir Internet Explorer primero. Las pruebas de IU codificadas ahora pueden generar acciones teniendo en cuenta los sitios anclados. Para obtener más información sobre sitios anclados, vea [Sitios anclados](https://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Compatibilidad con etiquetas semánticas de Internet Explorer 9:** Internet Explorer 9 incorpora las siguientes etiquetas semánticas: section, nav, article, aside, hgroup, header, footer, figure, figcaption y mark. Las pruebas de IU codificadas omiten todas estas etiquetas semánticas durante la grabación. Puede agregar aserciones en estas etiquetas mediante el generador de pruebas de IU codificadas. Puede utilizar el marcado de navegación del generador de pruebas de IU codificadas para navegar a cualquiera de estos elementos y ver sus propiedades.<br />-   **Control eficiente de los espacios en blanco en las distintas versiones de Internet Explorer:** existen diferencias en el control de los espacios en blanco entre Internet Explorer 8, Internet Explorer 9 e Internet Explorer 10. La prueba de IU codificada controla estas diferencias sin problemas. Por lo tanto, una prueba de IU codificada creada en Internet Explorer 8, por ejemplo, se reproducirá correctamente en Internet Explorer 9 e Internet Explorer 10.<br />-   **El área de notificaciones de Internet Explorer ahora se graba con el atributo "Continuar en caso de error" establecido:** Todas las acciones del área de notificaciones de Internet Explorer ahora se graban con el atributo "Continuar en caso de error" establecido. Si no aparece la barra de notificación durante la reproducción, se omitirán las acciones en esta y la prueba de IU codificada continuará con la siguiente acción.|
|Controles de terceros en Windows Forms y WPF|Totalmente compatible.<br /><br /> Para habilitar controles de terceros en Windows Forms y aplicaciones WPF, debe agregar referencias y código. Para obtener más información, consulte [Habilitar pruebas de IU codificadas en los controles](../test/enable-coded-ui-testing-of-your-controls.md).|
|Internet Explorer 6<br /><br /> Internet Explorer 7|No se admite.|
|Chrome<br /><br /> Firefox|No se admite la grabación de pasos de acción. Las pruebas de IU codificadas pueden reproducirse en Chrome y exploradores de Firefox con Visual Studio 2012 Update 4 o posterior. Haga clic [aquí](https://msdn.microsoft.com/library/jj835758.aspx) para obtener más detalles.|
|Opera<br /><br /> Safari|No se admite.|
|Silverlight|No se admite.<br /><br /> Para Visual Studo 2013, sin embargo, puede descargar el [Complemento de prueba de interfaz de usuario codificada de Microsoft Visual Studio 2013 para Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) desde la Galería de Visual Studio.|
|Flash/Java|No se admite.|
|Windows Forms 2.0 y versiones posteriores|Totalmente compatible. **Nota:**  Los controles NetFx son totalmente compatibles, pero hay controles de otros fabricantes que no lo son.|
|WPF 3.5 y posterior.|Totalmente compatible.<br /><br /> **Nota** Los controles NetFx son totalmente compatibles, pero hay controles de otros fabricantes que no lo son.|
|Windows Win32|Puede funcionar con algunos problemas conocidos, aunque oficialmente no se admite.|
|MFC|Compatibilidad parcial. Vea el siguiente [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkId=206511) para obtener detalles de las características que se admiten.|
|SharePoint|Totalmente compatible.|
|Aplicaciones cliente de Office|No se admite.|
|Cliente web Dynamics CRM|Totalmente compatible.|
|Cliente Dynamics (Ax) 2012|La grabación y reproducción de acciones se admiten parcialmente. Vea el siguiente [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkId=232677) para obtener más información.|
|SAP|No se admite.|
|Citrix/Terminal Services|No recomendamos grabar acciones en un servidor Terminal Server. La grabadora no admite la ejecución simultánea de varias instancias.|
|PowerBuilder|Compatibilidad parcial.<br /><br /> La compatibilidad depende del grado en que se haya habilitado la accesibilidad para controles PowerBuilder.|

 Para obtener información acerca de cómo crear extensiones compatibles con otras plataformas, consulte [Habilitar pruebas de IU codificadas en los controles](../test/enable-coded-ui-testing-of-your-controls.md) y [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Vea también
 [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md) [Generating a Coded UI Test from an Existing Action Recording](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
