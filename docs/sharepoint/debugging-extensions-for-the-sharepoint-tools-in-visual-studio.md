---
title: Depurar las extensiones para las herramientas de SharePoint en Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f838363b52a85faff022f49542fcc2fcc7e450d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950821"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Depurar extensiones para las herramientas de SharePoint en Visual Studio
  Puede depurar las extensiones de las herramientas de SharePoint en la instancia experimental o en la instancia normal de Visual Studio. Si necesita solucionar problemas relacionados con el comportamiento de una extensión, también puede modificar los valores del Registro para mostrar información adicional sobre los errores y configurar el modo en que Visual Studio ejecuta los comandos de SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Depurar extensiones en la instancia experimental de Visual Studio
 Para proteger el entorno de desarrollo de Visual Studio frente a daños accidentales por las extensiones no probadas, el SDK de Visual Studio proporciona una instancia alternativa de Visual Studio, llamada el *instancia experimental*, que puede usar Para instalar y probar extensiones. Las extensiones nuevas se desarrollan usando la instancia normal de Visual Studio, pero se depuran y ejecutan en la instancia experimental. Para obtener más información, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).

 Si para implementar la extensión se usa un proyecto de VSIX que es el proyecto de inicio de la solución, cuando se depura la solución, Visual Studio instala y ejecuta la extensión automáticamente en la instancia experimental. El proyecto de inicio es el proyecto que se inicia cuando se depura una solución que contiene varios proyectos. Para obtener más información sobre el uso de un proyecto de VSIX para implementar la extensión, vea [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Para obtener ejemplos en los que se muestra cómo depurar diversos tipos de extensiones en la instancia experimental de Visual Studio, vea los siguientes tutoriales:

-   [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [Tutorial: Crear elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [Tutorial: Extender el Explorador de servidores para mostrar elementos web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [Tutorial: Llamar al modelo de objetos de cliente de SharePoint en una extensión de explorador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Depurar extensiones en la instancia normal de Visual Studio
 Si desea depurar el proyecto de extensión en la instancia normal de Visual Studio, instale primero la extensión en la instancia normal. A continuación, adjunte el depurador a un segundo proceso de Visual Studio. Una vez finalizados, puede quitar la extensión para que no vuelva a cargarse en el equipo de desarrollo.

#### <a name="to-install-the-extension"></a>Para instalar la extensión

1.  Cierre todas las instancias de Visual Studio.

2.  En la carpeta de salida de compilación para el proyecto de extensión, abra el *.vsix* archivo haciendo doble clic en él o abriendo su menú contextual y, a continuación, eligiendo **abrir**:

3.  En el **instalador de extensiones de Visual Studio** diálogo cuadro, elija la edición de Visual Studio a la que desea instalar la extensión y, a continuación, elija el **instalar** botón.

     Visual Studio instala los archivos de extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*nombre del autor*\\*nombre de la extensión* \\ *versión*. Las tres últimas carpetas en esta ruta de acceso se construyen a partir del `Author`, `Name`, y `Version` elementos en el *extension.vsixmanifest* archivo para la extensión.

4.  Después de que Visual Studio instala la extensión, elija el **cerrar** botón.

#### <a name="to-debug-the-extension"></a>Para depurar la extensión

1.  Inicie Visual Studio con privilegios de administrador y abra el proyecto de extensión. Los pasos siguientes hacen referencia a esta instancia de Visual Studio como el *primero la instancia*.

2.  Inicie otra instancia de Visual Studio con privilegios de administrador. Los pasos siguientes hacen referencia a esta instancia de Visual Studio como el *segunda instancia*.

3.  Cambie a la primera instancia de Visual Studio.

4.  En la barra de menús, elija **depurar**, **asociar al proceso**.

5.  En el **procesos disponibles** elija *devenv.exe*. Esta entrada hace referencia a la segunda instancia de Visual Studio; esta es la instancia en la que desea depurar la extensión del proyecto.

6.  Elija la **adjuntar** botón.

     Visual Studio ejecuta el proyecto de extensión en modo de depuración.

7.  Cambie a la segunda instancia de Visual Studio.

8.  Cree un nuevo proyecto de SharePoint que cargue la extensión. Por ejemplo, si está depurando una extensión para los elementos de proyecto de definición de lista, cree un **definición de lista** proyecto.

9. Realice los pasos que sean necesarios para probar el código de la extensión.

10. Cuando finalice la depuración de la extensión, cierre la segunda instancia de Visual Studio.

#### <a name="to-remove-the-extension"></a>Para quitar la extensión

1.  En Visual Studio, en la barra de menús, elija **herramientas**, **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2.  En la lista de extensiones, elija el nombre de la extensión y, a continuación, elija el **desinstalar** botón.

3.  En el cuadro de diálogo que aparece, elija el **Sí** botón para confirmar que desea desinstalar la extensión.

4.  Elija la **reiniciar ahora** botón para completar la desinstalación.

## <a name="debug-sharepoint-commands"></a>Depurar comandos de SharePoint
 Si desea depurar un comando de SharePoint que forma parte de una extensión de herramientas de SharePoint, debe asociar el depurador el *vssphost4.exe* proceso. Se trata del proceso del host de 64 bits que ejecuta los comandos de SharePoint. Para obtener más información acerca de los comandos de SharePoint y *vssphost4.exe*, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Para asociar el depurador al proceso vssphost4.exe

1.  Inicie la depuración de la extensión en la instancia experimental de Visual Studio o en la instancia normal de Visual Studio; siga las instrucciones mencionadas anteriormente.

2.  En la instancia de Visual Studio en el que está ejecutando el depurador, en la barra de menús, elija **depurar**, **asociar al proceso**.

3.  En el **procesos disponibles** elija *vssphost.exe*.

    > [!NOTE]
    >  Si vssphost.exe no aparece en la lista, debe iniciar el *vssphost4.exe* procesos en la instancia de Visual Studio en el que está ejecutando la extensión. Normalmente, para ello, realizara una acción que haga que Visual Studio se conecte al sitio de SharePoint del equipo de desarrollo. Por ejemplo, Visual Studio inicia *vssphost4.exe* al expandir un nodo de conexión de sitio (es decir, un nodo que se muestra una dirección URL del sitio) bajo el **conexiones de SharePoint** nodo en el **Explorador de servidores**  ventana, o cuando se agregan ciertos elementos de proyecto de SharePoint, como **instancia de lista** o **receptor de eventos** elementos a un proyecto de SharePoint.

4.  Elija la **adjuntar** botón.

5.  En la instancia de Visual Studio que se está depurando, siga los pasos necesarios para ejecutar el comando.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificar los valores del registro para ayudar a depurar las extensiones de herramientas de SharePoint
 Cuando depure una extensión de herramientas de SharePoint en Visual Studio, puede modificar los valores del Registro para que le resulte más fácil solucionar los problemas relacionados con la extensión. Los valores se encuentran en el **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** clave. Estos valores no existen de forma predeterminada.

 Para que le resulte más fácil solucionar los problemas relacionados con las extensiones de herramientas de SharePoint, puede crear y establecer el valor EnableDiagnostics. En la siguiente tabla se describe este valor.

|Valor|Descripción|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD que especifica si se muestran mensajes de diagnóstico en el **salida** ventana.<br /><br /> Para mostrar los mensajes de diagnóstico, establezca este valor en 1. Para dejar de mostrar los mensajes, establezca este valor en 0 o elimínelo.<br /><br /> Para escribir mensajes en el **salida** extensión de herramientas de la ventana de SharePoint, utilice el servicio de proyecto de SharePoint. Para obtener más información, consulte [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Si la extensión contiene un comando de SharePoint, puede crear y establecer valores adicionales para que le resulte más fácil solucionar los problemas relacionados con el comando. En la siguiente tabla se describen estos valores.

|Valor|Descripción|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD que especifica si se debe mostrar un cuadro de diálogo que le permite adjuntar el depurador a *vssphost4.exe* en cuanto se inicia. Resulta útil si vssphost.exe ejecuta el comando que se desea depurar inmediatamente después de iniciarse y no hay suficiente tiempo para asociar manualmente el depurador antes de que se ejecute el comando. Para mostrar el cuadro de diálogo *vssphost4.exe* llamadas la <xref:System.Diagnostics.Debugger.Break%2A> método cuando se inicia.<br /><br /> Para habilitar este comportamiento, establezca este valor en 1. Para deshabilitar este comportamiento, establezca este valor en 0 o elimínelo.<br /><br /> Si establece este valor en 1, también puede aumentar el valor HostProcessStartupTimeout para disponer de suficiente tiempo para asociar el depurador antes de que Visual Studio espera *vssphost4.exe* para indicar que se inició correctamente.|
|ChannelOperationTimeout|REG_DWORD que especifica el tiempo, en segundos, que Visual Studio espera a que se ejecute un comando de SharePoint. Si el comando no se ejecuta a tiempo, se produce una excepción <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> El valor predeterminado es 120 segundos.|
|HostProcessStartupTimeout|REG_DWORD que especifica el tiempo, en segundos, que Visual Studio espera *vssphost4.exe* para indicar que se inició correctamente. Si *vssphost4.exe* no indica un inicio correcto en el tiempo, un <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> se produce.<br /><br /> El valor predeterminado es 60 segundos.|
|MaxReceivedMessageSize|REG_DWORD que especifica el tamaño máximo permitido, en bytes, de los mensajes de WCF que se pasan entre Visual Studio y *vssphost4.exe*.<br /><br /> El valor predeterminado es 1.048.576 (1 MB).|
|MaxStringContentLength|REG_DWORD que especifica el tamaño máximo permitido, en bytes, de cadenas que se pasan entre Visual Studio y *vssphost4.exe*.<br /><br /> El valor predeterminado es 1.048.576 (1 MB).|

## <a name="see-also"></a>Vea también

- [Extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
