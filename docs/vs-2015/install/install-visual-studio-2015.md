---
title: Instalación de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298046"
---
# <a name="install-visual-studio-2015"></a>Instalación de Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta página se incluye información detallada para ayudarle con la instalación de **Visual Studio 2015**, nuestro conjunto integrado de herramientas de productividad para desarrolladores. También hemos incluido vínculos para ayudarle a obtener rápidamente información sobre [características](https://www.visualstudio.com/news/vs2015-vs.aspx), [ediciones](https://go.microsoft.com/fwlink/?LinkID=242142), [requisitos del sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [descargas](https://go.microsoft.com/fwlink/?LinkId=517106)y mucho más.

## <a name="quick-links"></a>Vínculos rápidos

Antes de profundizar en los detalles, se muestra a continuación una lista de los vínculos solicitados con más frecuencia.

|||
|------------------|----------------|
|![Descarga de Visual Studio](../install/media/downloads.png "Descargas") |**Downloads**: To install Visual Studio 2015, you can download a product executable file from the  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page (subscription required), or use the installation media from the boxed product. [Learn more about how to download current or previous versions of Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Learn more about features](../install/media/features.png "Características") |**Features**: To learn  more about the features in Visual Studio 2015, see the release notes for [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), and [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Find out what's in each SKU](../install/media/sku.png "SKU") |**SKU**: Para obtener información sobre el contenido disponible en cada edición de Visual Studio de 2015, vea nuestra página [Comparación de las ofertas de Visual Studio](https://go.microsoft.com/fwlink/?LinkID=242142).|
|![View system requirements](../install/media/system-requirements.png "Requisitos del sistema") |**System Requirements**: To view the system requirements for each edition of Visual Studio 2015, see the [Visual Studio 2015 Compatibility](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) page.|
|![Locate your Product Key](../install/media/product-keys.png "Claves de producto") |**Product Keys**: To locate your product key, see the [How to: Locate the Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) topic.|
|![Find out about licensing](../install/media/licensing.png "Licencias") |**Licensing**: To find out about licensing options for both individuals or enterprise customers, see  the [Visual Studio and MSDN Licensing](https://www.microsoft.com/download/details.aspx?id=13350) white paper.|

## <a name="custom"></a> Default vs. Custom Setup
 Cuando se instala Visual Studio de 2015, puede incluir o excluir componentes que usaría diariamente. Esto significa que la instalación predeterminada suele ocupar menos espacio e instalarse más rápido que una instalación personalizada. También significa que muchos componentes instalados de forma predeterminada en versiones anteriores ahora se consideran componentes personalizados que se deben seleccionar de forma explícita en esta versión.

 ![Visual Studio 2015 Setup Dialog](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Entre los componentes personalizados se incluye Visual C++, Visual F#, SQL Server Data Tools, herramientas y SDK móviles multiplataforma y SDK y extensiones. Puede instalar cualquiera de los componentes personalizados más adelante si no los selecciona durante la configuración inicial.

> [!NOTE]
> Una instalación personalizada incluye automáticamente los componentes que se encuentran en una instalación predeterminada.

 La lista completa de componentes personalizados es la siguiente:

|Feature Sets|Componentes|
|------------------|----------------|
|**Actualizaciones**|Visual Studio 2015 Update 3|
|**Lenguajes de programación**|Visual C++<br />Visual F#<br />Python Tools para Visual Studio|
|**Desarrollo de Web y de Windows**|Herramientas de publicación de ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (3rd Party)<br />Kit de desarrollo de Silverlight<br />Herramientas de desarrollo de aplicaciones universales de Windows<br />SDK y herramientas de Windows 10<br />Herramientas de Windows 8.1 y Windows Phone 8.0/8.1<br />SDK y herramientas de Windows 8.1|
|**Desarrollo móvil multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desarrollo móvil de Visual C++ para iOS y Android<br />Clang con Microsoft CodeGen|
|**Common Tools and Software Development Kits**|Android Native Development Kit (3rd Party)<br /> Android SDK [3rd Party]<br />Android SDK Setup APIs (3rd Party)<br />Apache Ant (3rd Party)<br /> Java SE Development Kit (3rd Party)<br /> Joyent Node.js (3rd Party)|
|**Herramientas comunes**|Git for Windows (3rd Party)<br />GitHub Extension for Visual Studio (3rd Party)<br /> Herramientas de extensibilidad de Visual Studio|

## <a name="installing"></a> Instalación de Visual Studio
 You can install Visual Studio by using installation media (DVDs), by using your Visual Studio subscription service from the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) website, by downloading  a web installer from the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) website, or by creating an offline installation layout (see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page for more details).

> [!IMPORTANT]
> Necesita credenciales de administrador para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, no las necesita para usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de su instalación.

 La cuenta de administrador local debe tener los siguientes privilegios habilitados para instalar todos los componentes en Visual Studio.

|Nombre para mostrar del objeto de directiva local|Derecho de usuario|
|--------------------------------------|----------------|
|Directorios y archivos de copia de seguridad|SeBackupPrivilege|
|Programas de depuración|SeDebugPrivilege|
|Administrar la auditoría y el registro de seguridad|SeSecurityPrivilege|

 Para obtener más información sobre este requisito de la cuenta de administrador local, vea el artículo de Knowledge Base [Se produce un error en la instalación de SQL Server si la cuenta de instalación no tiene ciertos derechos de usuario](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a> Using installation media
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el directorio raíz del disco de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ejecute el archivo de instalación de la edición que desee:

|Edición|Archivo de instalación|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidad de Visual Studio|vs_community.exe|

### <a name="BKMK_Website"></a> Downloading from the product website
 Visit the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) page, and select the edition of Visual Studio that you want.

### <a name="downloading-from-your-subscription-service"></a>Downloading from your subscription service
 Visit  the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page, and select the edition of Visual Studio that you want.

### <a name="BKMK_Offline"></a> Creating an offline installation layout
 If you do not have the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installation media, or you do not have a Visual Studio subscription,  or you do not want to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] by using the web installer, you can perform a "disconnected" installation by creating what is known as an offline installation layout. For more information, see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page.

## <a name="enterprise"></a> Deploying Visual Studio in an Enterprise
 For information about how to deploy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] over a network, see the [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a> Installing Visual Studio in a virtualized environment
 **Problemas de vídeo con Hyper-V**

 Si ejecuta Windows Server 2008 R2 con Hyper-V habilitado y un adaptador de gráficos acelerado, el sistema puede funcionar despacio.

 Para obtener más información, vea la página siguiente en el sitio web de Microsoft: [El rendimiento de vídeo puede disminuir cuando un equipo basado en Windows Server 2008 o Windows Server 2008 R2 tiene habilitado el rol de Hyper-V y tiene instalado un adaptador de pantalla acelerado](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulación de dispositivos con Hyper-V**

 Al instalar Visual Studio 2015 en hardware real sin virtualización, puede elegir características que habilitan la emulación de dispositivos Windows y Android mediante Hyper-V. Al instalar en Hyper-V, no podrá emular los dispositivos Windows o Android. Esto es así porque los emuladores son máquinas virtuales y actualmente no es posible hospedar una máquina virtual dentro de otra. La solución alternativa consiste en disponer de dispositivos reales Windows o Android en los que pueda implementar directamente la aplicación y depurarla.

## <a name="optionalComponents"></a> Installing optional components
 If you want to install components that you might not have selected during your original installation, use the following procedure.

#### <a name="to-install-optional-components"></a>To install optional components

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto a la que desea agregar uno o más componentes y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Modificar**y elija los componentes que desea instalar.

3. Elija **Siguiente**y siga las instrucciones restantes.

## <a name="helpContent"></a> Instalación de contenido de ayuda sin conexión
 Después de instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede descargar contenido de ayuda adicional para que esté disponible sin conexión.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar o desinstalar el contenido de la Ayuda

1. En la barra de menús de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , elija **Ayuda**, **Agregar y quitar contenido de la Ayuda**.

2. En la pestaña **Administrar contenido** del **Visor de Ayuda de Microsoft**, seleccione el origen de instalación del contenido de la Ayuda.

3. Si está buscando una colección de ayuda específica, escriba el nombre o una palabra clave en el cuadro de texto **Buscar** y presione **Entrar**.

4. Al lado del nombre de la colección de Ayuda que desee, elija el vínculo **Agregar** o **Quitar** .

5. Haga clic en el botón **Actualizar**.

   For more information about how to install or deploy offline Help, see the [Help Viewer Administrator Guide](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Búsqueda de versiones Service Release y actualizaciones del producto
 Visual Studio no actualiza automáticamente las extensiones al realizar la actualización desde versiones anteriores porque no todas las extensiones son compatibles. You must reinstall the extensions from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) or from the software publisher.

#### <a name="to-automatically-check-for-service-releases"></a>Para comprobar automáticamente si hay actualizaciones Service Release

1. En la barra de menús, elija **Herramientas**, **Opciones**.

2. En el cuadro de diálogo **Opciones** , expanda **Entorno**y, a continuación, seleccione **Extensiones y actualizaciones**. Asegúrese de que la casilla **Buscar actualizaciones automáticamente** está activada y haga clic en **Aceptar**.

## <a name="registering-visual-studio"></a>Registrar Visual Studio

1. En la barra de menús, elija **Ayuda**, **Acerca de**.

     El cuadro de diálogo **Acerca de** muestra el número de identificación del producto (PID). Para registrar el producto, necesitará el PID y las credenciales de cuenta de Windows (por ejemplo, una dirección de correo electrónico de Hotmail o Outlook.com y la contraseña).

2. En la barra de menús, elija **Ayuda**, **Registrar producto**.

## <a name="repair"></a> Reparación de Visual Studio

#### <a name="to-repair-visual-studio"></a>Para reparar Visual Studio

1. En el **Panel de control**, en la página **Programas y características** , elija la edición del producto que desea reparar y, a continuación, elija **Cambiar**.

2. En el Asistente para la instalación, elija **Reparar**, elija **Siguiente**y siga las instrucciones restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>To repair Visual Studio in silent or passive modes (that is, to repair from source)

1. En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.

2. Escriba los parámetros siguientes:

     *DVDRoot* \\<Installation File\> \</quiet&#124;/passive> [/norestart]/Repair

## <a name="troubleshooting"></a> Troubleshooting an installation
 Use estos recursos para obtener ayuda con los problemas de instalación y configuración:

- [Foro sobre la configuración e instalación de Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190) . Consulte las preguntas y respuestas de otras personas en la comunidad de Visual Studio. Si no encuentra lo que necesita, haga sus propias preguntas.

- [Sitio web Soporte de Microsoft para Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019) . Lea los artículos de Knowledge Base (KB) y póngase en contacto con el servicio de soporte técnico de Microsoft para obtener información sobre los problemas con la instalación de Visual Studio.

## <a name="relatedTopics"></a> Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describes how to install Visual Studio when you are not connected to the Internet.
|[Instalar distintas versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md)|Proporciona información sobre cómo instalar varias versiones de Visual Studio en el mismo equipo.|
|[Usar parámetros de la línea de comandos para instalar Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Lists the command-line parameters that you can use when you install Visual Studio from a command prompt.|
|[Desinstalar Visual Studio](../install/uninstall-visual-studio.md)|Describes how to uninstall Visual Studio.|
|[Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)|Proporciona información sobre las opciones de implementación de Visual Studio.|
|[Biblioteca de imágenes de Visual Studio](../designers/the-visual-studio-image-library.md)|Proporciona información sobre cómo instalar gráficos que se pueden utilizar en las aplicaciones de Visual Studio.|
|[Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Includes information and links that can help you use Visual Studio more effectively.|

## <a name="see-also"></a>Vea también

- [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)