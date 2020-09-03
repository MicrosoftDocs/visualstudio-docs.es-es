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
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548049"
---
# <a name="install-visual-studio-2015"></a>Instalación de Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta página se incluye información detallada para ayudarle con la instalación de **Visual Studio 2015**, nuestro conjunto integrado de herramientas de productividad para desarrolladores. También hemos incluido vínculos para obtener información rápida sobre [características](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), [requisitos del sistema](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [descargas](https://visualstudio.microsoft.com/vs/older-downloads/)y mucho más.

## <a name="quick-links"></a>Vínculos rápidos

Antes de profundizar en los detalles, se muestra a continuación una lista de los vínculos solicitados con más frecuencia.

|Título|Descripción|
|------------------|----------------|
|![Descarga de Visual Studio](../install/media/downloads.png "Descargas") |**Descargas**: para instalar Visual Studio 2015, puede descargar un archivo ejecutable de producto desde la página  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (suscripción requerida) o usar los medios de instalación del producto en caja. [Obtenga más información sobre cómo descargar versiones actuales o anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Más información acerca de las características](../install/media/features.png "Características") |**Características**: para obtener más información sobre las características de Visual Studio 2015, consulte las notas de la versión de [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)y [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Ver los requisitos del sistema](../install/media/system-requirements.png "Requisitos del sistema") |**Requisitos del sistema**: para ver los requisitos del sistema para cada edición de visual Studio 2015, vea la página [compatibilidad y destinatarios de la plataforma de Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Busque la clave de producto](../install/media/product-keys.png "Claves de producto") |**Claves de producto**: para buscar la clave de producto, consulte el tema [Cómo: buscar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Obtener información acerca de las licencias](../install/media/licensing.png "Licencias") |**Licencias**: para obtener más información acerca de las opciones de licencia para los usuarios particulares o empresariales, consulte las notas del [producto sobre licencias de Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> Configuración predeterminada y personalizada
 Cuando se instala Visual Studio de 2015, puede incluir o excluir componentes que usaría diariamente. Esto significa que la instalación predeterminada suele ocupar menos espacio e instalarse más rápido que una instalación personalizada. También significa que muchos componentes instalados de forma predeterminada en versiones anteriores ahora se consideran componentes personalizados que se deben seleccionar de forma explícita en esta versión.

 ![Cuadro de diálogo del programa de instalación de Visual Studio de 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Entre los componentes personalizados se incluyen Visual C++, Visual F#, SQL Server Data Tools, SDK y herramientas móviles multiplataforma, y SDK y extensiones de terceros. Puede instalar cualquiera de los componentes personalizados más adelante si no los selecciona durante la configuración inicial.

> [!NOTE]
> Una instalación personalizada incluye automáticamente los componentes que se encuentran en una instalación predeterminada.

 La lista completa de componentes personalizados es la siguiente:

|Conjuntos de características|Componentes|
|------------------|----------------|
|**Actualizaciones**|Visual Studio 2015 Update 3|
|**Lenguajes de programación**|Visual C++<br />Visual F#<br />Python Tools para Visual Studio|
|**Desarrollo de Web y de Windows**|Herramientas de publicación de ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (de terceros)<br />Kit de desarrollo de Silverlight<br />Herramientas de desarrollo de aplicaciones universales de Windows<br />SDK y herramientas de Windows 10<br />Herramientas de Windows 8.1 y Windows Phone 8.0/8.1<br />SDK y herramientas de Windows 8.1|
|**Desarrollo móvil multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desarrollo móvil de Visual C++ para iOS y Android<br />Clang con Microsoft CodeGen|
|**Kits de desarrollo de software y herramientas comunes**|Kit de desarrollo nativo de Android (terceros)<br /> Android SDK [terceros]<br />Android SDK API de instalación (terceros)<br />Apache Ant (de terceros)<br /> Java SE Development Kit (de terceros)<br /> Node.js Joyent (de terceros)|
|**Herramientas comunes**|Git para Windows (tercero)<br />Extensión de GitHub para Visual Studio (de terceros)<br /> Herramientas de extensibilidad de Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a> Instalar Visual Studio
 Puede instalar Visual Studio mediante el uso de medios de instalación (DVDs), mediante el servicio de suscripción de Visual Studio desde el sitio web de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , si descarga un instalador web desde el sitio web de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) o si crea un diseño de instalación sin conexión (consulte la página [crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) para obtener más detalles).

> [!IMPORTANT]
> Necesita credenciales de administrador para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, no las necesita para usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de su instalación.

 La cuenta de administrador local debe tener los siguientes privilegios habilitados para instalar todos los componentes en Visual Studio.

|Nombre para mostrar del objeto de directiva local|Derecho de usuario|
|--------------------------------------|----------------|
|Directorios y archivos de copia de seguridad|SeBackupPrivilege|
|Programas de depuración|SeDebugPrivilege|
|Administrar la auditoría y el registro de seguridad|SeSecurityPrivilege|

 Para obtener más información sobre este requisito de la cuenta de administrador local, vea el artículo de Knowledge Base [Se produce un error en la instalación de SQL Server si la cuenta de instalación no tiene ciertos derechos de usuario](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> Usar medios de instalación
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el directorio raíz del disco de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ejecute el archivo de instalación de la edición que desee:

|Edición|Archivo de instalación|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidad de Visual Studio|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Descargar desde el sitio web del producto
 Visite la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) y seleccione la edición de Visual Studio que desee.

### <a name="download-from-your-subscription-service"></a>Descarga desde el servicio de suscripción
 Visite la página de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) y seleccione la edición de Visual Studio que desee.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Crear un diseño de instalación sin conexión
 Si no tiene el medio de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalación, o no tiene una suscripción de Visual Studio o no desea instalar mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el instalador Web, puede realizar una instalación "desconectada" creando lo que se conoce como diseño de instalación sin conexión. Para obtener más información, vea la página [crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Implementar Visual Studio en una empresa
 Para obtener información sobre cómo implementar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a través de una red, vea la [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Instalación de Visual Studio en un entorno virtualizado
 **Problemas de vídeo con Hyper-V**

 Si ejecuta Windows Server 2008 R2 con Hyper-V habilitado y un adaptador de gráficos acelerado, el sistema puede funcionar despacio.

 Para obtener más información, consulte [el rendimiento de vídeo puede disminuir cuando un equipo basado en Windows server 2008 o Windows server 2008 R2 tiene el rol Hyper-V habilitado y un adaptador de pantalla acelerado instalado](https://support.microsoft.com/kb/961661).

 **Emulación de dispositivos con Hyper-V**

 Al instalar Visual Studio 2015 en hardware real sin virtualización, puede elegir características que habilitan la emulación de dispositivos Windows y Android mediante Hyper-V. Al instalar en Hyper-V, no podrá emular los dispositivos Windows o Android. Esto es así porque los emuladores son máquinas virtuales y actualmente no es posible hospedar una máquina virtual dentro de otra. La solución alternativa consiste en disponer de dispositivos reales Windows o Android en los que pueda implementar directamente la aplicación y depurarla.

## <a name="install-optional-components"></a><a name="optionalComponents"></a> Instalación de componentes opcionales
 Si desea instalar componentes que es posible que no haya seleccionado durante la instalación original, use el procedimiento siguiente.

#### <a name="to-install-optional-components"></a>Para instalar componentes opcionales

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto a la que desea agregar uno o más componentes y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Modificar**y elija los componentes que desea instalar.

3. Elija **Siguiente**y siga las instrucciones restantes.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Instalar el contenido de la ayuda sin conexión
 Después de instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede descargar contenido de ayuda adicional para que esté disponible sin conexión.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar o desinstalar el contenido de la Ayuda

1. En la barra de menús de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , elija **Ayuda**, **Agregar y quitar contenido de la Ayuda**.

2. En la pestaña **Administrar contenido** del **Visor de Ayuda de Microsoft**, seleccione el origen de instalación del contenido de la Ayuda.

3. Si está buscando una colección de ayuda específica, escriba el nombre o una palabra clave en el cuadro de texto **Buscar** y presione **Entrar**.

4. Al lado del nombre de la colección de Ayuda que desee, elija el vínculo **Agregar** o **Quitar** .

5. Haga clic en el botón **Actualizar**.

   Para obtener más información sobre cómo instalar o implementar la ayuda sin conexión, vea la [Guía del administrador del visor de ayuda](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Comprobar las versiones del servicio y las actualizaciones del producto
 Visual Studio no actualiza automáticamente las extensiones al realizar la actualización desde versiones anteriores porque no todas las extensiones son compatibles. Debe volver a instalar las extensiones desde el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o desde el editor de software.

#### <a name="to-automatically-check-for-service-releases"></a>Para comprobar automáticamente si hay actualizaciones Service Release

1. En la barra de menús, elija **herramientas**, **Opciones**.

2. En el cuadro de diálogo **Opciones** , expanda **Entorno**y, a continuación, seleccione **Extensiones y actualizaciones**. Asegúrese de que la casilla **Buscar actualizaciones automáticamente** está activada y haga clic en **Aceptar**.

## <a name="register-visual-studio"></a>Registrar Visual Studio

1. En la barra de menús, elija **Ayuda**, **Acerca de**.

     El cuadro de diálogo **Acerca de** muestra el número de identificación del producto (PID). Para registrar el producto, necesitará el PID y las credenciales de cuenta de Windows (por ejemplo, una dirección de correo electrónico de Hotmail o Outlook.com y la contraseña).

2. En la barra de menús, elija **Ayuda**, **Registrar producto**.

## <a name="repair-visual-studio"></a><a name="repair"></a> Reparar Visual Studio

#### <a name="to-repair-visual-studio"></a>Para reparar Visual Studio

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto que desea reparar y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Reparar**, elija **Siguiente**y siga las instrucciones restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Para reparar Visual Studio en los modos silencioso o pasivo (es decir, para reparar desde el origen)

1. En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.

2. Escriba los siguientes parámetros:

     *DVDRoot* \\ DVDRoot < *Archivo* \> de instalación \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Solucionar problemas de una instalación
 Use estos recursos para obtener ayuda con los problemas de instalación y configuración:

- [Foro sobre la configuración e instalación de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Consulte las preguntas y respuestas de otras personas en la comunidad de Visual Studio. Si no encuentra lo que necesita, haga sus propias preguntas.

- [Obtener ayuda con Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Busque artículos de Knowledge base (KB) y aprenda a ponerse en contacto con Soporte técnico de Microsoft para obtener información sobre problemas con la instalación de Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a> Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describe cómo instalar Visual Studio cuando no está conectado a Internet.
|[Instalar versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md)|Proporciona información sobre cómo instalar varias versiones de Visual Studio en el mismo equipo.|
|[Usar parámetros de la línea de comandos para instalar Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Enumera los parámetros de línea de comandos que puede usar al instalar Visual Studio desde un símbolo del sistema.|
|[Desinstalar Visual Studio](../install/uninstall-visual-studio.md)|Describe cómo desinstalar Visual Studio.|
|[Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)|Proporciona información sobre las opciones de implementación de Visual Studio.|
|[La biblioteca de imágenes de Visual Studio](../designers/the-visual-studio-image-library.md)|Proporciona información sobre cómo instalar gráficos que se pueden utilizar en las aplicaciones de Visual Studio.|
|[Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Incluye información y vínculos que pueden ayudarle a usar Visual Studio de forma más eficaz.|

## <a name="see-also"></a>Consulte también

- [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)
