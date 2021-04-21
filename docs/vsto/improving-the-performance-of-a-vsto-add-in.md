---
title: Mejora del rendimiento de un complemento de VSTO
description: Obtenga información sobre cómo optimizar los complementos de VSTO que cree para aplicaciones de Office para que se inicien, apaguen, abran elementos y realicen otras tareas rápidamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29035f4867421ed3f05e5f0c3a5c196f58b7ab34
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825126"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Mejora del rendimiento de un complemento de VSTO
  Puede ofrecer a los usuarios una mejor experiencia si optimiza los complementos de VSTO que cree para las aplicaciones de Office, de modo que se inicien, se cierren, abran elementos y realicen otras tareas rápidamente. Si el complemento de VSTO es para Outlook, también puede reducir la posibilidad de que se deshabilite debido a un bajo rendimiento. Puede aumentar el rendimiento del complemento de VSTO si implementa las estrategias siguientes:

- [Cargar complementos de VSTO a petición](#Load).

- [Publicar soluciones de Office mediante Windows Installer](#Publish).

- [Omitir reflexión de la cinta de opciones](#Bypass).

- [Realizar operaciones que consumen muchos recursos en un subproceso de ejecución independiente](#Perform).

  Para obtener más información sobre cómo optimizar un complemento de VSTO de Outlook, vea Criterios de rendimiento para mantener habilitados los [complementos de VSTO.](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> Carga de complementos de VSTO a petición
 Puede configurar un complemento de VSTO de modo que se cargue solo en las siguientes circunstancias:

- La primera vez que el usuario inicie la aplicación después de instalar el complemento de VSTO.

- La primera vez que el usuario interactúe con el complemento de VSTO después de iniciar la aplicación en cualquier otro momento.

  Por ejemplo, el complemento de VSTO podría rellenar una hoja de cálculo con datos cuando el usuario elige un botón personalizado con la etiqueta **Obtener mis datos.** La aplicación debe cargar el complemento de VSTO  al menos una vez para que el botón Obtener mis datos pueda aparecer en la cinta de opciones. Sin embargo, el complemento VSTO no se vuelve a cargar cuando el usuario inicia la aplicación la próxima vez. El complemento de VSTO solo se carga cuando el usuario elige el botón **Obtener mis datos** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar una solución ClickOnce para cargar complementos de VSTO a petición

1. En el **Explorador de soluciones**, elija el nodo de proyecto.

2. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

3. En la pestaña **Publicar** , seleccione el botón **Opciones** .

4. En el cuadro de diálogo **Opciones de publicación** , seleccione el elemento de lista **Configuración de Office** , la opción **Cargar a petición** y, a continuación, el botón **Aceptar** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar una solución de Windows Installer para cargar complementos de VSTO a petición

1. En el Registro, establezca la entrada de la clave raíz `LoadBehavior` **\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _Addins Add-in ID_** **en 0x10**.

     Para obtener más información, vea [Entradas del Registro para complementos de VSTO.](../vsto/registry-entries-for-vsto-add-ins.md)

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Para configurar una solución para cargar complementos de VSTO a petición mientras se depura la solución

1. Cree un script que establece la entrada de la clave raíz `LoadBehavior` **\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _Addins Add-in ID_** **en 0x10**.

     El código siguiente muestra un ejemplo de este script.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Cree un evento posterior a la compilación que actualice el Registro mediante el script.

     El código siguiente muestra un ejemplo de una cadena de comando que se puede agregar a un evento posterior a la compilación.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Para obtener información sobre cómo crear eventos posteriores a la compilación en un proyecto de C#, vea Cómo: Especificar eventos de [compilación &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Para obtener información sobre cómo crear un evento posterior a la compilación en un proyecto de Visual Basic, vea [Cómo: ](../ide/how-to-specify-build-events-visual-basic.md)Especificar eventos de compilación &#40;Visual Basic&#41;.

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Publicar soluciones de Office mediante Windows Installer
 Si publica la solución mediante Windows Installer, el entorno de ejecución de Visual Studio 2010 Tools for Office omite los pasos siguientes cuando se carga el complemento de VSTO.

- Validación del esquema del manifiesto.

- Comprobación automática de actualizaciones.

- Validación de las firmas digitales de los manifiestos de implementación.

  > [!NOTE]
  > Este enfoque no es necesario si implementa el complemento de VSTO en una ubicación segura en los equipos de los usuarios.

  Para obtener más información, vea [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Omisión de la reflexión de la cinta de opciones
 Si compila una solución mediante , asegúrese de que los usuarios han instalado la versión más reciente del entorno de ejecución de herramientas de Visual Studio 2010 para Office al implementar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] la solución. Las versiones anteriores del tiempo de ejecución de VSTO se reflejan en los ensamblados de la solución para buscar personalizaciones de la cinta de opciones. Este proceso puede hacer que el complemento de VSTO se cargue más lentamente.

 Como alternativa, puede impedir que cualquier versión de Visual Studio 2010 Tools for Office runtime use la reflexión para identificar las personalizaciones de la cinta de opciones. Para seguir esta estrategia, invalide el `CreateRibbonExtensibility` método y devuelva explícitamente objetos Ribbon. Si el complemento de VSTO no contiene ninguna personalización de cinta de opciones, vuelva `null` dentro del método .

 En el ejemplo siguiente se devuelve un objeto Ribbon basado en el valor de un campo.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs" id="Snippet1":::

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Realizar operaciones costosas en un subproceso de ejecución independiente
 Considere la posibilidad de realizar las tareas que consumen muchos recursos (por ejemplo, tareas de ejecución prolongada, conexiones de base de datos u otros tipos de llamadas de red) en un subproceso independiente. Para obtener más información, vea [Compatibilidad con subprocesos en Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Todo el código que llame al modelo de objetos de Office debe ejecutarse en el subproceso principal.

## <a name="see-also"></a>Consulte también

- [Complementos vsTO de carga a petición](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Retraso de la carga del CLR en los complementos de Office](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Crear complementos de VSTO para Office con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)