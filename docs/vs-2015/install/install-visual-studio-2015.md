---
title: Instalación de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445082"
---
# <a name="install-visual-studio-2015"></a>Instalación de Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta página se incluye información detallada para ayudarle con la instalación de **Visual Studio 2015**, nuestro conjunto integrado de herramientas de productividad para desarrolladores. También hemos incluido enlaces para obtener rápidamente información sobre [características,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history)requisitos del [sistema,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs) [descargas](https://visualstudio.microsoft.com/vs/older-downloads/)y más.

## <a name="quick-links"></a>Vínculos rápidos

Antes de profundizar en los detalles, se muestra a continuación una lista de los vínculos solicitados con más frecuencia.

|||
|------------------|----------------|
|![Descargar Visual Studio](../install/media/downloads.png "Descargas") |**Descargas:** para instalar Visual Studio 2015, puede descargar un archivo ejecutable del producto desde la página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (se requiere suscripción) o usar los medios de instalación del producto en caja. [Obtenga más información sobre cómo descargar versiones actuales o anteriores de Visual Studio.](https://www.visualstudio.com/vs/older-downloads/)|
|![Más información sobre las funciones](../install/media/features.png "Características") |**Características:** Para obtener más información sobre las características de Visual Studio 2015, vea las notas de la versión de [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)y [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Ver los requisitos del sistema](../install/media/system-requirements.png "Requisitos del sistema") |**Requisitos**del sistema: para ver los requisitos del sistema para cada edición de Visual Studio 2015, vea la página Desconexión y compatibilidad de plataforma de [Visual Studio 2015.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Localice su clave de producto](../install/media/product-keys.png "Claves de producto") |**Claves de**producto: para buscar la clave de producto, vea el tema [Cómo: buscar la clave](../install/how-to-locate-the-visual-studio-product-key.md) de producto de Visual Studio.|
|![Infórmese sobre las licencias](../install/media/licensing.png "Licencias") |**Licencias**: Para obtener información sobre las opciones de licencia tanto para individuos como para clientes empresariales, consulte el Libro Técnico de Licencias de [Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Configuración predeterminada frente a configuración personalizada
 Cuando se instala Visual Studio de 2015, puede incluir o excluir componentes que usaría diariamente. Esto significa que la instalación predeterminada suele ocupar menos espacio e instalarse más rápido que una instalación personalizada. También significa que muchos componentes instalados de forma predeterminada en versiones anteriores ahora se consideran componentes personalizados que se deben seleccionar de forma explícita en esta versión.

 ![Cuadro de diálogo del programa de instalación de Visual Studio de 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Los componentes personalizados incluyen Visual C+, Visual F, SQL Server Data Tools, herramientas móviles multiplataforma y SDK, y SDK y extensiones de terceros. Puede instalar cualquiera de los componentes personalizados más adelante si no los selecciona durante la configuración inicial.

> [!NOTE]
> Una instalación personalizada incluye automáticamente los componentes que se encuentran en una instalación predeterminada.

 La lista completa de componentes personalizados es la siguiente:

|Conjuntos de características|Componentes|
|------------------|----------------|
|**Actualizaciones**|Visual Studio 2015 Update 3|
|**Idiomas de programación**|Visual C++<br />Visual F#<br />Python Tools para Visual Studio|
|**Desarrollo de Web y de Windows**|Herramientas de publicación de ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />Herramientas de PowerShell para Visual Studio (3a parte)<br />Kit de desarrollo de Silverlight<br />Herramientas de desarrollo de aplicaciones universales de Windows<br />SDK y herramientas de Windows 10<br />Herramientas de Windows 8.1 y Windows Phone 8.0/8.1<br />SDK y herramientas de Windows 8.1|
|**Desarrollo móvil multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desarrollo móvil de Visual C++ para iOS y Android<br />Clang con Microsoft CodeGen|
|**Herramientas comunes y kits de desarrollo de software**|Kit de desarrollo nativo de Android (3a parte)<br /> Android SDK [3rd Party]<br />API de instalación del SDK de Android (3a parte)<br />Hormiga Apache (3a parte)<br /> Kit de desarrollo Java SE (3a parte)<br /> Joyent Node.js (3a parte)|
|**Herramientas comunes**|Git para Windows (3a parte)<br />Extensión de GitHub para Visual Studio (3a parte)<br /> Herramientas de extensibilidad de Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Instalar Visual Studio
 Puede instalar Visual Studio mediante medios de instalación (DVD), mediante el servicio de suscripción de Visual Studio desde el sitio web [de My.VisualStudio.com,](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) descargando un instalador web desde el sitio web de descargas de [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) o creando un diseño de instalación sin conexión (consulte la página Crear una [instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) para obtener más detalles).

> [!IMPORTANT]
> Necesita credenciales de administrador para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, no las necesita para usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de su instalación.

 La cuenta de administrador local debe tener los siguientes privilegios habilitados para instalar todos los componentes en Visual Studio.

|Nombre para mostrar del objeto de directiva local|Derecho de usuario|
|--------------------------------------|----------------|
|Directorios y archivos de copia de seguridad|SeBackupPrivilege|
|Programas de depuración|SeDebugPrivilege|
|Administrar la auditoría y el registro de seguridad|SeSecurityPrivilege|

 Para obtener más información sobre este requisito de la cuenta de administrador local, vea el artículo de Knowledge Base [Se produce un error en la instalación de SQL Server si la cuenta de instalación no tiene ciertos derechos de usuario](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Utilizar medios de instalación
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el directorio raíz del disco de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ejecute el archivo de instalación de la edición que desee:

|Edición|Archivo de instalación|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidad de Visual Studio|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Descargar desde el sitio web del producto
 Visite la página Descargas de [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) y seleccione la edición de Visual Studio que desee.

### <a name="download-from-your-subscription-service"></a>Descargar desde su servicio de suscripción
 Visite la página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) y seleccione la edición de Visual Studio que desee.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Crear un diseño de instalación sin conexión
 Si no tiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] los medios de instalación, o no tiene una suscripción [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a Visual Studio o no desea instalar mediante el instalador web, puede realizar una instalación "desconectada" creando lo que se conoce como un diseño de instalación sin conexión. Para obtener más información, vea la página [Crear una instalación sin conexión de Visual Studio.](../install/create-an-offline-installation-of-visual-studio.md)

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Implementar Visual Studio en una empresa
 Para obtener información [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] acerca de cómo implementar a través de una red, vea la [Guía del administrador](../install/visual-studio-administrator-guide.md)de Visual Studio .

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Instalar Visual Studio en un entorno virtualizado
 **Problemas de vídeo con Hyper-V**

 Si ejecuta Windows Server 2008 R2 con Hyper-V habilitado y un adaptador de gráficos acelerado, el sistema puede funcionar despacio.

 Para obtener más información, vea Rendimiento de vídeo [puede disminuir cuando un equipo basado en Windows Server 2008 o Windows Server 2008 R2 tiene habilitado el rol de Hyper-V y un adaptador de pantalla acelerada instalado.](https://support.microsoft.com/kb/961661)

 **Emulación de dispositivos con Hyper-V**

 Al instalar Visual Studio 2015 en hardware real sin virtualización, puede elegir características que habilitan la emulación de dispositivos Windows y Android mediante Hyper-V. Al instalar en Hyper-V, no podrá emular los dispositivos Windows o Android. Esto es así porque los emuladores son máquinas virtuales y actualmente no es posible hospedar una máquina virtual dentro de otra. La solución alternativa consiste en disponer de dispositivos reales Windows o Android en los que pueda implementar directamente la aplicación y depurarla.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Instalar componentes opcionales
 Si desea instalar componentes que es posible que no haya seleccionado durante la instalación original, utilice el siguiente procedimiento.

#### <a name="to-install-optional-components"></a>Para instalar componentes opcionales

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto a la que desea agregar uno o más componentes y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Modificar**y elija los componentes que desea instalar.

3. Elija **Siguiente**y siga las instrucciones restantes.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Instalar contenido de Ayuda sin conexión
 Después de instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede descargar contenido de ayuda adicional para que esté disponible sin conexión.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar o desinstalar el contenido de la Ayuda

1. En la barra de menús de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , elija **Ayuda**, **Agregar y quitar contenido de la Ayuda**.

2. En la pestaña **Administrar contenido** del **Visor de Ayuda de Microsoft**, seleccione el origen de instalación del contenido de la Ayuda.

3. Si está buscando una colección de ayuda específica, escriba el nombre o una palabra clave en el cuadro de texto **Buscar** y presione **Entrar**.

4. Al lado del nombre de la colección de Ayuda que desee, elija el vínculo **Agregar** o **Quitar** .

5. Haga clic en el botón **Actualizar**.

   Para obtener más información acerca de cómo instalar o implementar la Ayuda sin conexión, consulte la [Guía del administrador del Visor de ayuda](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Compruebe si hay versiones de servicio y actualizaciones de productos
 Visual Studio no actualiza automáticamente las extensiones al realizar la actualización desde versiones anteriores porque no todas las extensiones son compatibles. Debe volver a instalar las extensiones desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o desde el editor de software.

#### <a name="to-automatically-check-for-service-releases"></a>Para comprobar automáticamente si hay actualizaciones Service Release

1. En la barra de menús, elija **Herramientas**, **Opciones**.

2. En el cuadro de diálogo **Opciones** , expanda **Entorno**y, a continuación, seleccione **Extensiones y actualizaciones**. Asegúrese de que la casilla **Buscar actualizaciones automáticamente** está activada y haga clic en **Aceptar**.

## <a name="register-visual-studio"></a>Registrar Visual Studio

1. En la barra de menús, elija **Ayuda**, **Acerca de**.

     El cuadro de diálogo **Acerca de** muestra el número de identificación del producto (PID). Para registrar el producto, necesitará el PID y las credenciales de cuenta de Windows (por ejemplo, una dirección de correo electrónico de Hotmail o Outlook.com y la contraseña).

2. En la barra de menús, elija **Ayuda**, **Registrar producto**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Reparar Visual Studio

#### <a name="to-repair-visual-studio"></a>Para reparar Visual Studio

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto que desea reparar y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Reparar**, elija **Siguiente**y siga las instrucciones restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Para reparar Visual Studio en modos silenciosos o pasivos (es decir, para reparar desde el origen)

1. En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.

2. Escriba los siguientes parámetros:

     \\ < *Installation File* Archivo\> *DVDRoot* \< de instalación DVDRoot> [/`norestart` `/quiet|/passive` ]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Solucionar problemas de instalación
 Use estos recursos para obtener ayuda con los problemas de instalación y configuración:

- [Foro sobre la configuración e instalación de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Consulte las preguntas y respuestas de otras personas en la comunidad de Visual Studio. Si no encuentra lo que necesita, haga sus propias preguntas.

- [Obtenga ayuda con Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Encuentre artículos de Knowledge Base (KB) y obtenga información sobre cómo ponerse en contacto con el soporte técnico de Microsoft para obtener información acerca de los problemas con la instalación de Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describe cómo instalar Visual Studio cuando no está conectado a Internet.
|[Instalar versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md)|Proporciona información sobre cómo instalar varias versiones de Visual Studio en el mismo equipo.|
|[Usar parámetros de línea de comandos para instalar Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Enumera los parámetros de línea de comandos que puede usar al instalar Visual Studio desde un símbolo del sistema.|
|[Desinstalar Visual Studio](../install/uninstall-visual-studio.md)|Describe cómo desinstalar Visual Studio.|
|[Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)|Proporciona información sobre las opciones de implementación de Visual Studio.|
|[La biblioteca de imágenes de Visual Studio](../designers/the-visual-studio-image-library.md)|Proporciona información sobre cómo instalar gráficos que se pueden utilizar en las aplicaciones de Visual Studio.|
|[Introducción a el desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Incluye información y vínculos que pueden ayudarle a usar Visual Studio de forma más eficaz.|

## <a name="see-also"></a>Consulte también

- [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)
