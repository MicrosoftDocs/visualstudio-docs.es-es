---
title: Entradas de registro para complementos VSTO
ms.date: 08/14/2019
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
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416528"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Entradas de registro para complementos VSTO
  Debe crear un conjunto específico de entradas del registro al implementar complementos de VSTO creados con Visual Studio. Dichas entradas del registro proporcionan información que permite que la aplicación de Microsoft Office detecte y cargue el complemento de VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Al compilar el proyecto, Visual Studio crea estas entradas del registro en el equipo de desarrollo para que el complemento de VSTO se pueda ejecutar y depurar fácilmente. Si usa ClickOnce para implementar el complemento VSTO, las entradas del Registro se crean automáticamente en el equipo del usuario final. Si utiliza Windows Installer para implementar el complemento VSTO, debe configurar el proyecto InstallShield Limited Edition para crear las entradas del registro en el equipo del usuario final.

 Para obtener más información acerca de cómo se usan las entradas de registro durante el proceso de carga de los complementos VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> En este tema, el texto *Identificador de complemento* es un identificador único para el complemento de VSTO. De forma predeterminada, el identificador es el nombre del ensamblado del complemento de VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrar complementos de VSTO para el usuario actual frente a todos los usuarios
 Cuando se instala un complemento de VSTO, se puede registrar de dos formas:

- Solo para el usuario actual (es decir, solo está disponible para el usuario que ha iniciado sesión en el equipo cuando se instala el complemento VSTO). En este caso, las entradas del registro se crean en la **HKEY_CURRENT_USER**.

- Para todos los usuarios (es decir, cualquier usuario que inicie sesión en el equipo puede usar el complemento VSTO). En este caso, las entradas del registro se crean en **HKEY_LOCAL_MACHINE**.

  Todos los complementos de VSTO que cree mediante Visual Studio pueden registrarse para el usuario actual. Sin embargo, los complementos de VSTO pueden registrarse para todos los usuarios solo en determinados escenarios. Estos escenarios dependen de la versión de Microsoft Office del equipo y de cómo se implementó el complemento de VSTO.

### <a name="deployment-type"></a>Tipo de implementación
 Si usa ClickOnce para implementar un complemento de VSTO, el complemento de VSTO se puede registrar únicamente para el usuario actual. Esto se debe a que ClickOnce solo admite la creación de claves en **HKEY_CURRENT_USER**. Si desea registrar un complemento de VSTO para todos los usuarios de un equipo, debe usar Windows Installer para implementarlo. Para obtener más información acerca de estos tipos de implementación, vea Implementar una solución de [Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e Implementar una [solución](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)de Office mediante Windows Installer .

## <a name="registry-entries"></a>Entradas del registro
 Las entradas de registro del complemento VSTO necesarias se encuentran en las siguientes claves del Registro donde *Root* es **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE** dependiendo de si la instalación es para el usuario actual o para todos los usuarios.

|Aplicación de oficina|Ruta de acceso de configuración|
|------------------|------------------|
|Visio|*Identificador*\\de*complemento* de raíz\\de Microsoft*Visio*|
|Todos los demás|*Raíz*de nombre de\\*aplicación*\\*add-in ID* de la aplicación de La raíz de Microsoft Office|

> [!NOTE]
> Si el instalador se dirige a todos los usuarios de Windows de 64 bits, se recomienda que incluya dos\\entradas del Registro, una bajo el HKEY_LOCAL_MACHINE Software-Microsoft y otra bajo el HKEY_LOCAL_MACHINE software**WOW6432Node**. Esto se debe a que es posible que los usuarios usen versiones de 32 bits o 64 bits de Office en el equipo.
>
>Si el instalador tiene como destino el usuario actual, no es necesario instalar en WOW6432Node porque se comparte la ruta de acceso de HKEY_CURRENT_USER software.
>
>Para obtener más información, consulte Datos de aplicación de [32 y 64 bits en el Registro](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 En la tabla siguiente se enumeran las entradas que figuran en esta clave del Registro.

|Entrada|Tipo|Value|
|-----------|----------|-----------|
|**Descripción**|REG_SZ|Necesario. Breve descripción del complemento de VSTO.<br /><br /> Esta descripción se muestra cuando el usuario selecciona el complemento de VSTO en el panel **Complementos** del cuadro de diálogo **Opciones** de la aplicación de Microsoft Office.|
|**FriendlyName**|REG_SZ|Necesario. Nombre descriptivo del complemento de VSTO que se muestra en el cuadro de diálogo **Complementos COM** de la aplicación de Microsoft Office. El valor predeterminado es el identificador del complemento de VSTO.|
|**LoadBehavior**|REG_DWORD|Necesario. Valor que especifica cuándo la aplicación intenta cargar el complemento de VSTO y el estado actual del complemento de VSTO (cargado o sin cargar).<br /><br /> De forma predeterminada, esta entrada se establece en 3, lo que especifica que el complemento de VSTO se carga al inicio. Para obtener más información, consulte [Valores LoadBehavior](#LoadBehavior). **Nota:**  Si un usuario deshabilita el complemento VSTO, esa acción modifica el valor **LoadBehavior** en el **HKEY_CURRENT_USER** subárbol del Registro. Para cada usuario, el valor del valor **LoadBehavior** del HKEY_CURRENT_USER subárbol reemplaza el valor predeterminado **LoadBehavior** definido en el **HKEY_LOCAL_MACHINE** subárbol.|
|**Manifest**|REG_SZ|Necesario. Ruta de acceso completa del manifiesto de implementación para el complemento de VSTO. La ruta de acceso puede ser una ubicación en el equipo local, un recurso compartido de red (UNC) o un servidor web (HTTP).<br /><br /> Si usa Windows Installer para implementar la solución, debe agregar el prefijo **file:///** a la ruta de acceso del **manifiesto** . También debe anexar la cadena **&#124;vstolocal** (es decir, el carácter de canalización **&#124;** seguido de **vstolocal**) al final de esta ruta de acceso. Esto garantiza que la solución se cargue desde la carpeta de instalación, no desde la memoria caché de ClickOnce. Para obtener más información, vea [Implementar una solución](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)de Office mediante Windows Installer . **Nota:**  Al compilar un complemento de VSTO en el equipo de desarrollo, Visual Studio anexa automáticamente la&#124;cadena **vstolocal** a esta entrada del Registro.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Entradas de registro para las regiones de formulario de Outlook
 Si crea un área del formulario personalizada en un complemento de VSTO para Outlook, se usarán entradas del registro adicionales para registrar dicha área en Outlook. Estas entradas se crean en una clave del Registro diferente para cada clase de mensaje que sea compatible con el área del formulario. Estas claves del Registro se encuentran en la siguiente ubicación, donde *Root* es **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE**.

 *Raíz*de la clase de mensaje\\raíz de la raíz de la raíz de la raíz de la raíz de la raíz de la aplicación de la página de mensaje de la raíz de la raíz de la aplicación de la*raíz* de la

 Al igual que las demás entradas del registro compartidas por todos los complementos de VSTO, Visual Studio crea las entradas del registro de las áreas del formulario en el equipo de desarrollo al compilar el proyecto. Si usa ClickOnce para implementar el complemento VSTO, las entradas del Registro se crean automáticamente en el equipo del usuario final. Si utiliza Windows Installer para implementar el complemento VSTO, debe configurar el proyecto InstallShield Limited Edition para crear las entradas del registro en el equipo del usuario final.

 Para obtener más información acerca de las entradas del registro del área de formulario, vea Especificar la ubicación de un área de [formulario en un formulario personalizado.](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form) Para obtener más información acerca de las regiones de formulario de Outlook, vea [Crear regiones](../vsto/creating-outlook-form-regions.md)de formulario de Outlook .

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>Valores LoadBehavior
 La*application name*entrada **LoadBehavior,** en *la*clave\\de identificador de\\complemento*Desidentificador* de complementos de la raíz de software de Microsoft, Office, contiene una combinación bit a bit de valores que especifican el comportamiento de tiempo de ejecución del complemento VSTO. El bit de ordenación más bajo (valores 0 y 1) indica si el complemento de VSTO está cargado o no. Otros bits indican el momento en que la aplicación intenta cargar el complemento de VSTO.

 Normalmente, la entrada **LoadBehavior** está diseñada para establecerse en 0, 3 o 16 (en decimal) cuando el complemento VSTO está instalado en equipos de usuario final. De forma predeterminada, Visual Studio establece la entrada **LoadBehavior** del complemento de VSTO en 3 al compilarlo o publicarlo.

 En la siguiente tabla se enumeran todos los valores posibles de la entrada **LoadBehavior** . Algunas descripciones de esta tabla hacen referencia a cargar un complemento de VSTO manualmente o mediante programación. Para cargar un complemento de VSTO manualmente, active la casilla que encontrará junto al complemento de VSTO en el cuadro de diálogo **Complementos COM** de la aplicación. Para cargar un complemento de VSTO mediante programación, establezca la propiedad <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> del objeto <xref:Microsoft.Office.Core.COMAddIn> que representa el complemento de VSTO en **true**.

|Valor (en forma decimal)|Estado del complemento de VSTO|Comportamiento de carga de complementos de VSTO|Descripción|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Descargado|No cargar automáticamente|La aplicación nunca intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si el complemento de VSTO se carga correctamente, el valor **LoadBehavior** sigue siendo 0, pero el estado del complemento de VSTO en el cuadro de diálogo **Complementos COM** se actualiza para indicar que el complemento de VSTO está cargado.|
|1|Cargado|No cargar automáticamente|La aplicación nunca intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Aunque el cuadro de diálogo **Complementos COM** indica que el complemento VSTO se carga después de que se inicia la aplicación, el complemento VSTO no se carga hasta que se carga manualmente o mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 0 y sigue siendo 0 una vez que se cierra la aplicación.|
|2|Descargado|Cargar al inicio|La aplicación no intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 3 y sigue siendo 3 una vez que se cierra la aplicación.|
|3|Cargado|Cargar al inicio|La aplicación intenta cargar el complemento de VSTO cuando se inicia la aplicación. Este es el valor predeterminado al compilar o publicar un complemento de VSTO en Visual Studio.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** sigue siendo 3. Si se produce un error al cargar el complemento de VSTO, el valor **LoadBehavior** cambia a 2 y sigue siendo 2 una vez que se cierra la aplicación.|
|8|Descargado|Cargar a petición|La aplicación no intenta cargar el complemento de VSTO automáticamente. El usuario puede intentar cargar manualmente el complemento de VSTO o el complemento de VSTO se puede cargar mediante programación.<br /><br /> Si la aplicación carga correctamente el complemento de VSTO, el valor **LoadBehavior** cambia a 9.|
|9|Cargado|Cargar a petición|El complemento de VSTO se cargará solo cuando la aplicación lo requiera, como en el caso de que un usuario haga clic en un elemento de interfaz de usuario que use alguna funcionalidad en el complemento de VSTO (por ejemplo, un botón personalizado en la cinta de opciones).<br /><br /> Si la aplicación carga el complemento de VSTO correctamente, el valor **LoadBehavior** sigue siendo 9, pero el estado del complemento de VSTO en el cuadro de diálogo **Complementos COM** se actualiza para indicar que el complemento de VSTO está cargado. Si se produce un error al cargar el complemento de VSTO, el valor **LoadBehavior** cambia a 8.|
|16|Cargado|Cargar la primera vez y, a continuación, cargar a petición|Establezca este valor si desea que el complemento de VSTO se cargue según demanda. La aplicación carga el complemento de VSTO cuando el usuario ejecuta la aplicación por primera vez. La próxima vez que el usuario ejecute la aplicación, la aplicación cargará los elementos de la interfaz de usuario definidos por el complemento de VSTO, pero el complemento de VSTO no se cargará hasta que el usuario haga clic en un elemento de la interfaz de usuario que esté asociado al complemento de VSTO.<br /><br /> Cuando la aplicación carga correctamente el complemento de VSTO por primera vez, el valor **LoadBehavior** sigue siendo 16 mientras el complemento de VSTO esté cargado. Después de cerrar la aplicación, el valor **LoadBehavior** cambia a 9.|

## <a name="see-also"></a>Consulte también
- [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Crear soluciones de Office](../vsto/building-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
 