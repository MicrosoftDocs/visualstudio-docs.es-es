---
title: Entradas del registro para complementos de VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8360194e9efc59634162781fd3b4e0787c1c3260
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870170"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Entradas del registro para complementos de VSTO
  Debe crear un conjunto específico de entradas del registro al implementar complementos de VSTO creados con Visual Studio. Dichas entradas del registro proporcionan información que permite que la aplicación de Microsoft Office detecte y cargue el complemento de VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Al compilar el proyecto, Visual Studio crea estas entradas del registro en el equipo de desarrollo para que el complemento de VSTO se pueda ejecutar y depurar fácilmente. Si usa ClickOnce para implementar el complemento VSTO, las entradas del registro se crean automáticamente en el equipo del usuario final. Si usa a Windows Installer para implementar el complemento VSTO, debe configurar el proyecto de InstallShield Limited Edition para crear las entradas del registro en el equipo del usuario final.  
  
 Para obtener más información acerca de cómo se usan las entradas de registro durante el proceso de carga de los complementos VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  En este tema, el texto *Identificador de complemento* es un identificador único para el complemento de VSTO. De forma predeterminada, el identificador es el nombre del ensamblado del complemento de VSTO.  
  
## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrar complementos VSTO para el usuario actual frente a todos los usuarios  
 Cuando se instala un complemento de VSTO, se puede registrar de dos formas:  
  
- Solo el usuario actual (es decir, está disponible solo para el usuario que ha iniciado sesión en el equipo cuando se instala el complemento de VSTO). En este caso, se crean las entradas del registro bajo la **HKEY_CURRENT_USER**.  
  
- Para todos los usuarios (es decir, cualquier usuario que inicie sesión en el equipo puede utilizar el complemento de VSTO). En este caso, se crean las entradas del registro bajo **HKEY_LOCAL_MACHINE**.  
  
  Todos los complementos de VSTO que cree mediante Visual Studio pueden registrarse para el usuario actual. Sin embargo, los complementos de VSTO pueden registrarse para todos los usuarios solo en determinados escenarios. Estos escenarios dependen de la versión de Microsoft Office del equipo y de cómo se implementó el complemento de VSTO.  
  
### <a name="microsoft-office-version"></a>Versión de Microsoft Office  
 Aplicaciones de Office pueden cargar complementos VSTO que están registrados en **HKEY_LOCAL_MACHINE** o **HKEY_CURRENT_USER**.  
  
 Para cargar complementos VSTO que están registrados en **HKEY_LOCAL_MACHINE**, los equipos deben tener el paquete de actualización 976477 instalado. Para obtener más información, vea [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Tipo de implementación  
 Si usa ClickOnce para implementar un complemento de VSTO, el complemento de VSTO se puede registrar únicamente para el usuario actual. Esto es porque ClickOnce solo permite crear claves en **HKEY_CURRENT_USER**. Si desea registrar un complemento de VSTO para todos los usuarios de un equipo, debe usar Windows Installer para implementarlo. Para obtener más información acerca de estos tipos de implementación, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) y [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Entradas del registro  
 Las entradas de registro necesarias de complementos de VSTO se encuentran en la siguiente clave del registro para todas las aplicaciones excepto Visio, donde *raíz* es **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE** .  
  
 **Todas las aplicaciones excepto Visio**  
  
|Versión de Office|Ruta de acceso de configuración|  
|--------------------|------------------------|  
|32 bits|*Raíz*\Software\Microsoft\Office\\*nombre de la aplicación*\Addins\\*ID de complemento*|  
|64 bits|*Raíz*\Software\Wow6432Node\Microsoft\Office\\*nombre de la aplicación*\Addins\\*ID de complemento*|  
  
 **Visio**  
  
|Versión de Office|Ruta de acceso de configuración|  
|--------------------|------------------------|  
|32 bits|*Raíz*\Software\Microsoft\Visio\Addins\\*ID de complemento*|  
|64 bits|*Raíz*\Software\Wow6432Node\Visio\Addins\\*ID de complemento*|  
  
 En la tabla siguiente se enumeran las entradas que figuran en esta clave del Registro.  
  
|Entrada|Tipo|Valor|  
|-----------|----------|-----------|  
|**Descripción**|REG_SZ|Obligatorio. Breve descripción del complemento de VSTO.<br /><br /> Esta descripción se muestra cuando el usuario selecciona el complemento de VSTO en el panel **Complementos** del cuadro de diálogo **Opciones** de la aplicación de Microsoft Office.|  
|**FriendlyName**|REG_SZ|Obligatorio. Nombre descriptivo del complemento de VSTO que se muestra en el cuadro de diálogo **Complementos COM** de la aplicación de Microsoft Office. El valor predeterminado es el identificador del complemento de VSTO.|  
|**LoadBehavior**|REG_DWORD|Obligatorio. Valor que especifica cuándo la aplicación intenta cargar el complemento de VSTO y el estado actual del complemento de VSTO (cargado o sin cargar).<br /><br /> De forma predeterminada, esta entrada se establece en 3, lo que especifica que el complemento de VSTO se carga al inicio. Para obtener más información, consulte [valores de LoadBehavior](#LoadBehavior). **Nota:**  Si un usuario deshabilita el complemento de VSTO, esa acción modifica **LoadBehavior** valor en el **HKEY_CURRENT_USER** subárbol del registro. Para cada usuario, el valor de la **LoadBehavior** valor en el subárbol HKEY_CURRENT_USER invalida el valor predeterminado **LoadBehavior** definido en el **HKEY_LOCAL_MACHINE** hive.|  
|**Manifest**|REG_SZ|Obligatorio. Ruta de acceso completa del manifiesto de implementación para el complemento de VSTO. La ruta de acceso puede ser una ubicación en el equipo local, un recurso compartido de red (UNC) o un servidor web (HTTP).<br /><br /> Si usa Windows Installer para implementar la solución, debe agregar el prefijo **file:///** a la ruta de acceso del **manifiesto** . También debe agregar la cadena  **&#124;vstolocal** (es decir, el carácter de canalización **&#124;** seguido **vstolocal**) al final de esta ruta de acceso. Esto garantiza que la solución se cargue desde la carpeta de instalación, no desde la memoria caché de ClickOnce. Para obtener más información, consulte [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Nota:**  Al compilar un complemento VSTO en el equipo de desarrollo, Visual Studio agrega automáticamente el  **&#124;vstolocal** cadena para esta entrada del registro.|  
  
###  <a name="OutlookEntries"></a> Entradas del registro para las áreas de formulario de Outlook  
 Si crea un área del formulario personalizada en un complemento de VSTO para Outlook, se usarán entradas del registro adicionales para registrar dicha área en Outlook. Estas entradas se crean en una clave del Registro diferente para cada clase de mensaje que sea compatible con el área del formulario. Estas claves del registro se encuentran en la ubicación siguiente, donde *raíz* es **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE**.  
  
 *Raíz*\Software\Microsoft\Office\Outlook\FormRegions\\*message (clase)*  
  
 Al igual que las demás entradas del registro compartidas por todos los complementos de VSTO, Visual Studio crea las entradas del registro de las áreas del formulario en el equipo de desarrollo al compilar el proyecto. Si usa ClickOnce para implementar el complemento VSTO, las entradas del registro se crean automáticamente en el equipo del usuario final. Si usa a Windows Installer para implementar el complemento VSTO, debe configurar el proyecto de InstallShield Limited Edition para crear las entradas del registro en el equipo del usuario final.  
  
 Para obtener más información acerca de las entradas de registro de la región de formulario, consulte [especificar la ubicación de un área de formulario en un formulario personalizado](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Para obtener más información acerca de las áreas de formulario de Outlook, consulte [crear áreas de formulario](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> Valores de LoadBehavior  
 El **LoadBehavior** entrada bajo el *raíz*\Software\Microsoft\Office\\*nombre de la aplicación*\Addins\\*complemento Id. de* clave contiene una combinación bit a bit de valores que especifican el comportamiento de tiempo de ejecución del complemento VSTO. El bit de ordenación más bajo (valores 0 y 1) indica si el complemento de VSTO está cargado o no. Otros bits indican el momento en que la aplicación intenta cargar el complemento de VSTO.  
  
 Normalmente, el **LoadBehavior** entrada está pensada para establecerse en 0, 3 o 16 (en formato decimal) cuando el complemento de VSTO está instalado en equipos de usuario final. De forma predeterminada, Visual Studio establece la entrada **LoadBehavior** del complemento de VSTO en 3 al compilarlo o publicarlo.  
  
 En la siguiente tabla se enumeran todos los valores posibles de la entrada **LoadBehavior** . Algunas descripciones de esta tabla hacen referencia a cargar un complemento de VSTO manualmente o mediante programación. Para cargar un complemento de VSTO manualmente, active la casilla que encontrará junto al complemento de VSTO en el cuadro de diálogo **Complementos COM** de la aplicación. Para cargar un complemento de VSTO mediante programación, establezca la propiedad <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> del objeto <xref:Microsoft.Office.Core.COMAddIn> que representa el complemento de VSTO en **true**.  
  
|Valor (en forma decimal)|Estado del complemento de VSTO|Comportamiento de carga de complementos de VSTO|Descripción|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Descargado|No cargar automáticamente|La aplicación nunca intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si el complemento de VSTO se carga correctamente, el valor **LoadBehavior** sigue siendo 0, pero el estado del complemento de VSTO en el cuadro de diálogo **Complementos COM** se actualiza para indicar que el complemento de VSTO está cargado.|  
|1|Cargado|No cargar automáticamente|La aplicación nunca intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Aunque el **complementos COM** cuadro de diálogo indica que el complemento de VSTO se carga tras iniciar la aplicación, el complemento de VSTO no está cargado hasta que se cargue manualmente o mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 0 y sigue siendo 0 una vez que se cierra la aplicación.|  
|2|Descargado|Cargar al inicio|La aplicación no intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 3 y sigue siendo 3 una vez que se cierra la aplicación.|  
|3|Cargado|Cargar al inicio|La aplicación intenta cargar el complemento de VSTO cuando se inicia la aplicación. Este es el valor predeterminado al compilar o publicar un complemento de VSTO en Visual Studio.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** sigue siendo 3. Si se produce un error al cargar el complemento de VSTO, el valor **LoadBehavior** cambia a 2 y sigue siendo 2 una vez que se cierra la aplicación.|  
|8|Descargado|Cargar a petición|La aplicación no intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 9.|  
|9|Cargado|Cargar a petición|El complemento de VSTO se cargará solo cuando la aplicación lo requiera, como en el caso de que un usuario haga clic en un elemento de interfaz de usuario que use alguna funcionalidad en el complemento de VSTO (por ejemplo, un botón personalizado en la cinta de opciones).<br /><br /> Si la aplicación carga el complemento de VSTO correctamente, el valor **LoadBehavior** sigue siendo 9, pero el estado del complemento de VSTO en el cuadro de diálogo **Complementos COM** se actualiza para indicar que el complemento de VSTO está cargado. Si se produce un error al cargar el complemento de VSTO, el valor **LoadBehavior** cambia a 8.|  
|16|Cargado|Cargar la primera vez y, a continuación, cargar a petición|Establezca este valor si desea que el complemento de VSTO se cargue según demanda. La aplicación carga el complemento de VSTO cuando el usuario ejecuta la aplicación por primera vez. La próxima vez que el usuario ejecute la aplicación, la aplicación cargará los elementos de la interfaz de usuario definidos por el complemento de VSTO, pero el complemento de VSTO no se cargará hasta que el usuario haga clic en un elemento de la interfaz de usuario que esté asociado al complemento de VSTO.<br /><br /> Cuando la aplicación carga correctamente el complemento de VSTO por primera vez, el valor **LoadBehavior** sigue siendo 16 mientras el complemento de VSTO esté cargado. Después de cerrar la aplicación, el valor **LoadBehavior** cambia a 9.|  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
