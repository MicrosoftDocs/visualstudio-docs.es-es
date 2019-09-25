---
title: Mejorar el rendimiento de un complemento de VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79f1c4a55321a1b039cc2702b1040e2ab9d4ac9d
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255643"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Mejorar el rendimiento de un complemento de VSTO
  Puede ofrecer a los usuarios una mejor experiencia si optimiza los complementos de VSTO que cree para las aplicaciones de Office, de modo que se inicien, se cierren, abran elementos y realicen otras tareas rápidamente. Si el complemento de VSTO es para Outlook, también puede reducir la posibilidad de que se deshabilite debido a un bajo rendimiento. Puede aumentar el rendimiento del complemento de VSTO si implementa las estrategias siguientes:

- [Cargar complementos de VSTO a petición](#Load).

- [Publicar soluciones de Office mediante Windows Installer](#Publish).

- [Omitir reflexión de la cinta](#Bypass)de opciones.

- [Realizar operaciones que consumen muchos recursos en un subproceso de ejecución independiente](#Perform).

  Para obtener más información sobre cómo optimizar un complemento de VSTO para Outlook, vea [criterios de rendimiento para mantener los complementos de VSTO habilitados](http://go.microsoft.com/fwlink/?LinkID=266503).

## <a name="Load"></a> Cargar complementos de VSTO a petición
 Puede configurar un complemento de VSTO de modo que se cargue solo en las siguientes circunstancias:

- La primera vez que el usuario inicie la aplicación después de instalar el complemento de VSTO.

- La primera vez que el usuario interactúe con el complemento de VSTO después de iniciar la aplicación en cualquier otro momento.

  Por ejemplo, el complemento de VSTO podría rellenar una hoja de cálculo con datos cuando el usuario elige un botón personalizado con la etiqueta **obtener mis datos**. La aplicación debe cargar el complemento de VSTO al menos una vez para que el botón **obtener mis datos** pueda aparecer en la cinta de opciones. Sin embargo, el complemento de VSTO no se carga de nuevo cuando el usuario inicia la aplicación la próxima vez. El complemento de VSTO solo se carga cuando el usuario elige el botón **Obtener mis datos** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar una solución ClickOnce para cargar complementos de VSTO a petición

1. En el **Explorador de soluciones**, elija el nodo de proyecto.

2. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

3. En la pestaña **Publicar** , seleccione el botón **Opciones** .

4. En el cuadro de diálogo **Opciones de publicación** , seleccione el elemento de lista **Configuración de Office** , la opción **Cargar a petición** y, a continuación, el botón **Aceptar** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar una solución de Windows Installer para cargar complementos de VSTO a petición

1. En el registro, establezca la `LoadBehavior` entrada de la clave **_raíz_\Software\Microsoft\Office\\_applicationName_\Addins\\de_identificador de complemento_** en **0x10**.

     Para obtener más información, vea [entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Para configurar una solución para cargar complementos de VSTO a petición mientras se depura la solución

1. Cree un script que establezca la `LoadBehavior` entrada de la clave **_raíz_\Software\Microsoft\Office\\_applicationName_\Addins\\de_identificador de complemento_** en **0x10**.

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

     Para obtener información sobre cómo crear un evento posterior a la compilación C# en un proyecto [de, consulte Cómo: Especifique &#40;eventos de compilación&#35;&#41;](../ide/how-to-specify-build-events-csharp.md)C.

     Para obtener información sobre cómo crear un evento posterior a la compilación en un proyecto de Visual Basic [, consulte Cómo: Especifique eventos &#40;de compilación&#41;](../ide/how-to-specify-build-events-visual-basic.md)Visual Basic.

## <a name="Publish"></a>Publicar soluciones de Office mediante Windows Installer
 Si publica la solución mediante Windows Installer, el motor en tiempo de ejecución de Visual Studio 2010 Tools para Office omite los pasos siguientes cuando se carga el complemento de VSTO.

- Validación del esquema del manifiesto.

- Comprobación automática de actualizaciones.

- Validación de las firmas digitales de los manifiestos de implementación.

  > [!NOTE]
  > Este enfoque no es necesario si implementa el complemento de VSTO en una ubicación segura en los equipos de los usuarios.

  Para obtener más información, vea [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Bypass"></a>Omitir reflexión de cinta
 Si compila una solución [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]mediante, asegúrese de que los usuarios hayan instalado la versión más reciente del motor en tiempo de ejecución de las herramientas de Visual Studio 2010 para Office al implementar la solución. Las versiones anteriores del tiempo de ejecución de VSTO se reflejaban en los ensamblados de la solución para buscar las personalizaciones de la cinta. Este proceso puede hacer que el complemento de VSTO se cargue más lentamente.

 Como alternativa, puede evitar que cualquier versión del motor en tiempo de ejecución de Visual Studio 2010 Tools para Office use la reflexión para identificar las personalizaciones de la cinta. Para seguir esta estrategia, invalide el método y devuelva explícitamente los `CreateRibbonExtensibility` objetos de la cinta de opciones. Si el complemento de VSTO no contiene ninguna personalización de la cinta de `null` opciones, devuelva dentro del método.

 En el ejemplo siguiente se devuelve un objeto Ribbon basado en el valor de un campo.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="Perform"></a>Realizar operaciones costosas en un subproceso de ejecución independiente
 Considere la posibilidad de realizar las tareas que consumen muchos recursos (por ejemplo, tareas de ejecución prolongada, conexiones de base de datos u otros tipos de llamadas de red) en un subproceso independiente. Para obtener más información, vea [compatibilidad de subprocesos en Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Todo el código que llame al modelo de objetos de Office debe ejecutarse en el subproceso principal.

## <a name="see-also"></a>Vea también

- [Carga de complementos de VSTO a petición](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Retrasar la carga de CLR en los complementos de Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Crear complementos de VSTO para Office con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
