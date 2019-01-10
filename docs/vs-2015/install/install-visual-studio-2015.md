---
title: Instalación de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: 55dad8adf4b3ce6e79214471c93052318f7228f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828061"
---
# <a name="install-visual-studio-2015"></a>Instalación de Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta página se incluye información detallada para ayudarle con la instalación de **Visual Studio 2015**, nuestro conjunto integrado de herramientas de productividad para desarrolladores. También hemos incluido vínculos para ayudarle a obtener rápidamente información sobre [características](https://www.visualstudio.com/news/vs2015-vs.aspx), [ediciones](http://go.microsoft.com/fwlink/?LinkID=242142), [requisitos del sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [descargas](http://go.microsoft.com/fwlink/?LinkId=517106)y mucho más.

## <a name="quick-links"></a>Vínculos rápidos

Antes de profundizar en los detalles, se muestra a continuación una lista de los vínculos solicitados con más frecuencia.

|||
|------------------|----------------|
|![Descargar Visual Studio](../install/media/downloads.png "descargas") |**Descargas** Para instalar Visual Studio 2015, puede descargar un archivo ejecutable de producto desde la [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) página (se requiere suscripción), o bien los medios de instalación de la caja del producto. [Más información sobre cómo descargar las versiones actuales o anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Más información sobre características](../install/media/features.png "características") |**Características** Para obtener más información acerca de las características de Visual Studio 2015, vea las notas de [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), y [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Conozca las novedades en cada SKU](../install/media/sku.png "SKU") |**SKU**: Para obtener información sobre el contenido disponible en cada edición de Visual Studio de 2015, vea nuestra página [Comparación de las ofertas de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142).|
|![Ver los requisitos del sistema](../install/media/system-requirements.png "requisitos del sistema") |**Requisitos del sistema**: Para ver los requisitos del sistema de cada edición de Visual Studio 2015, vea la página [Compatibilidad de Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs).|
|![Busque la clave de producto](../install/media/product-keys.png "las claves de producto") |**Claves de producto** Para encontrar la clave de producto, vea el [Cómo: Busque la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) tema.|
|![Obtenga información sobre las licencias](../install/media/licensing.png "Licensing") |**Licencias**: Para obtener información sobre las opciones para clientes individuales o empresariales, vea las notas del producto [Licencias de Visual Studio y MSDN](https://www.microsoft.com/download/details.aspx?id=13350).|

##  <a name="custom"></a> Instalación predeterminada frente a Instalación personalizada
 Cuando se instala Visual Studio de 2015, puede incluir o excluir componentes que usaría diariamente. Esto significa que la instalación predeterminada suele ocupar menos espacio e instalarse más rápido que una instalación personalizada. También significa que muchos componentes instalados de forma predeterminada en versiones anteriores ahora se consideran componentes personalizados que se deben seleccionar de forma explícita en esta versión.

 ![Cuadro de diálogo programa de instalación de Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Entre los componentes personalizados se incluye Visual C++, Visual F#, SQL Server Data Tools, herramientas y SDK móviles multiplataforma y SDK y extensiones. Puede instalar cualquiera de los componentes personalizados más adelante si no los selecciona durante la configuración inicial.

> [!NOTE]
>  Una instalación personalizada incluye automáticamente los componentes que se encuentran en una instalación predeterminada.

 La lista completa de componentes personalizados es la siguiente:

|Conjuntos de características|Componentes|
|------------------|----------------|
|**Actualizaciones**|Visual Studio 2015 Update 3|
|**Lenguajes de programación**|Visual C++<br />Visual F#<br />Python Tools para Visual Studio|
|**Desarrollo de Web y de Windows**|Herramientas de publicación de ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools para Visual Studio (3ª parte)<br />Kit de desarrollo de Silverlight<br />Herramientas de desarrollo de aplicaciones universales de Windows<br />SDK y herramientas de Windows 10<br />Herramientas de Windows 8.1 y Windows Phone 8.0/8.1<br />SDK y herramientas de Windows 8.1|
|**Desarrollo móvil multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desarrollo móvil de Visual C++ para iOS y Android<br />Clang con Microsoft CodeGen|
|**Herramientas comunes y Kits de desarrollo de Software**|Kit de desarrollo nativo de Android (3ª parte)<br /> SDK de Android [parte 3ª]<br />Las API de instalación de Android SDK (3ª parte)<br />Apache Ant (3ª parte)<br /> Kit de desarrollo de Java SE (3ª parte)<br /> Joyent Node.js (3ª parte)|
|**Herramientas comunes**|GIT para Windows (3ª parte)<br />Extensión de GitHub para Visual Studio (3ª parte)<br /> Herramientas de extensibilidad de Visual Studio|

##  <a name="installing"></a> Instalación de Visual Studio
 Puede instalar Visual Studio mediante el uso de medios de instalación (DVD), mediante el uso de su servicio de suscripción de Visual Studio desde el [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sitio Web, mediante la descarga un instalador web desde el [Visual Studio Descargas de](http://go.microsoft.com/fwlink/?LinkId=517106) sitio Web, o mediante la creación de un diseño de instalación sin conexión (consulte la [crear una sin conexión instalación de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) página para obtener más detalles).

> [!IMPORTANT]
>  Necesita credenciales de administrador para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, no las necesita para usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de su instalación.

 La cuenta de administrador local debe tener los siguientes privilegios habilitados para instalar todos los componentes en Visual Studio.

|Nombre para mostrar del objeto de directiva local|Derecho de usuario|
|--------------------------------------|----------------|
|Directorios y archivos de copia de seguridad|SeBackupPrivilege|
|Programas de depuración|SeDebugPrivilege|
|Administrar la auditoría y el registro de seguridad|SeSecurityPrivilege|

 Para obtener más información sobre este requisito de la cuenta de administrador local, vea el artículo de Knowledge Base [Se produce un error en la instalación de SQL Server si la cuenta de instalación no tiene ciertos derechos de usuario](https://support.microsoft.com/en-us/kb/2000257).

###  <a name="BKMK_Media"></a> Uso de medios de instalación
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el directorio raíz del disco de instalación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ejecute el archivo de instalación de la edición que desee:

|Edición|Archivo de instalación|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidad de Visual Studio|vs_community.exe|

###  <a name="BKMK_Website"></a> Descargar desde el sitio Web del producto
 Visite el [descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) página y seleccione la edición de Visual Studio que desee.

### <a name="downloading-from-your-subscription-service"></a>Descargar desde su servicio de suscripción
 Visite el [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) página y seleccione la edición de Visual Studio que desee.

###  <a name="BKMK_Offline"></a> Crear un diseño de instalación sin conexión
 Si no tienes el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] medios de instalación, o no tiene una suscripción de Visual Studio, o no desea instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con el instalador web, puede realizar una instalación "desconectada" creando lo que se conoce como sin conexión diseño de instalación. Para obtener más información, consulte el [crear una sin conexión instalación de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) página.

##  <a name="enterprise"></a> Implementación de Visual Studio en una empresa
 Para obtener información sobre cómo implementar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a través de una red, vea el [Guía del Administrador de Visual Studio](../install/visual-studio-administrator-guide.md).

###  <a name="BKMK_Virtualized"></a> Instalar Visual Studio en un entorno virtualizado.
 **Problemas de vídeo con Hyper-V**

 Si ejecuta Windows Server 2008 R2 con Hyper-V habilitado y un adaptador de gráficos acelerado, el sistema puede funcionar despacio.

 Para obtener más información, vea las siguientes páginas del sitio web de Microsoft [Rendimiento de vídeo puede disminuir cuando un equipo con Windows Server 2008 o equipo basada en Windows Server 2008 R2 tiene habilitado el rol de Hyper-V y un adaptador de pantalla acelerado](http://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulación de dispositivos con Hyper-V**

 Al instalar Visual Studio 2015 en hardware real sin virtualización, puede elegir características que habilitan la emulación de dispositivos Windows y Android mediante Hyper-V. Al instalar en Hyper-V, no podrá emular los dispositivos Windows o Android. Esto es así porque los emuladores son máquinas virtuales y actualmente no es posible hospedar una máquina virtual dentro de otra. La solución alternativa consiste en disponer de dispositivos reales Windows o Android en los que pueda implementar directamente la aplicación y depurarla.

##  <a name="optionalComponents"></a> Instalar componentes opcionales
 Si desea instalar los componentes que no haya seleccionado durante la instalación original, utilice el procedimiento siguiente.

#### <a name="to-install-optional-components"></a>Para instalar componentes opcionales

1.  En el **Panel de control**, en la página **Programas y características** , elija la edición del producto a la que desea agregar uno o más componentes y, a continuación, elija **Cambiar**.

2.  En el Asistente para la instalación, elija **Modificar**y elija los componentes que desea instalar.

3.  Elija **Siguiente**y siga las instrucciones restantes.

##  <a name="helpContent"></a> Instalación de contenido de ayuda sin conexión
 Después de instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede descargar contenido de ayuda adicional para que esté disponible sin conexión.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar o desinstalar el contenido de la Ayuda

1. En la barra de menús de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , elija **Ayuda**, **Agregar y quitar contenido de la Ayuda**.

2. En la pestaña **Administrar contenido** del **Visor de Ayuda de Microsoft**, seleccione el origen de instalación del contenido de la Ayuda.

3. Si está buscando una colección de ayuda específica, escriba el nombre o una palabra clave en el cuadro de texto **Buscar** y presione **Entrar**.

4. Al lado del nombre de la colección de Ayuda que desee, elija el vínculo **Agregar** o **Quitar** .

5. Haga clic en el botón **Actualizar**.

   Para obtener más información acerca de cómo instalar o implementar la Ayuda sin conexión, consulte el [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md).

##  <a name="serviceReleases"></a> Búsqueda de versiones Service Release y actualizaciones del producto
 Visual Studio no actualiza automáticamente las extensiones al realizar la actualización desde versiones anteriores porque no todas las extensiones son compatibles. Debe reinstalar las extensiones desde la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) o desde el Editor de software.

#### <a name="to-automatically-check-for-service-releases"></a>Para comprobar automáticamente si hay actualizaciones Service Release

1.  En la barra de menús, elija **Herramientas**, **Opciones**.

2.  En el cuadro de diálogo **Opciones** , expanda **Entorno**y, a continuación, seleccione **Extensiones y actualizaciones**. Asegúrese de que la casilla **Buscar actualizaciones automáticamente** está activada y haga clic en **Aceptar**.

## <a name="registering-visual-studio"></a>Registrar Visual Studio

1.  En la barra de menús, elija **Ayuda**, **Acerca de**.

     El cuadro de diálogo **Acerca de** muestra el número de identificación del producto (PID). Para registrar el producto, necesitará el PID y las credenciales de cuenta de Windows (por ejemplo, una dirección de correo electrónico de Hotmail o Outlook.com y la contraseña).

2.  En la barra de menús, elija **Ayuda**, **Registrar producto**.

##  <a name="repair"></a> Reparación de Visual Studio

#### <a name="to-repair-visual-studio"></a>Para reparar Visual Studio

1.  En el **Panel de control**, en la página **Programas y características** , elija la edición del producto que desea reparar y, a continuación, elija **Cambiar**.

2.  En el Asistente para la instalación, elija **Reparar**, elija **Siguiente**y siga las instrucciones restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Para reparar Visual Studio en los modos silencioso o pasivos (es decir, reparar desde el origen)

1.  En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.

2.  Escriba los parámetros siguientes:

     *DVDRoot* \\< archivo de instalación\> \</quiet&#124;/passive > [/norestart] /Repair

##  <a name="troubleshooting"></a> Solución de problemas de instalación
 Use estos recursos para obtener ayuda con los problemas de instalación y configuración:

-   [Foro sobre la configuración e instalación de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190) . Consulte las preguntas y respuestas de otras personas en la comunidad de Visual Studio. Si no encuentra lo que necesita, haga sus propias preguntas.

-   [Sitio web Soporte de Microsoft para Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019) . Lea los artículos de Knowledge Base (KB) y póngase en contacto con el servicio de soporte técnico de Microsoft para obtener información sobre los problemas con la instalación de Visual Studio.

##  <a name="relatedTopics"></a> Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describe cómo instalar Visual Studio cuando no están conectados a Internet.
|[Instalar distintas versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md)|Proporciona información sobre cómo instalar varias versiones de Visual Studio en el mismo equipo.|
|[Usar parámetros de la línea de comandos para instalar Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Muestra los parámetros de línea de comandos que puede usar al instalar Visual Studio desde un símbolo del sistema.|
|[Desinstalar Visual Studio](../install/uninstall-visual-studio.md)|Describe cómo desinstalar Visual Studio.|
|[Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)|Proporciona información sobre las opciones de implementación de Visual Studio.|
|[Biblioteca de imágenes de Visual Studio](../designers/the-visual-studio-image-library.md)|Proporciona información sobre cómo instalar gráficos que se pueden utilizar en las aplicaciones de Visual Studio.|
|[Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Incluye información y vínculos que pueden ayudarle a usar Visual Studio de forma más eficaz.|

## <a name="see-also"></a>Vea también

- [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md)