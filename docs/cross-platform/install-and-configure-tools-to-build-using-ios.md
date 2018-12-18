---
title: Instalar y configurar herramientas para compilar con iOS | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: cbc9e2b0016fde990e2fbd6d79b083907ced5060
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881090"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalar y configurar herramientas para compilar con iOS

Puede usar Visual C++ para el desarrollo móvil multiplataforma para editar, depurar e implementar código de iOS en el simulador de iOS o en un dispositivo de iOS; sin embargo, debido a las restricciones de licencia, el código se debe compilar y ejecutar de manera remota en un equipo Mac. Para compilar y ejecutar aplicaciones de iOS con Visual Studio, debe instalar y configurar el agente remoto [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)en el equipo Mac. El agente remoto controla las solicitudes de compilación de Visual Studio y ejecuta la aplicación en un dispositivo de iOS conectado al equipo Mac o en el simulador de iOS del equipo Mac.

> [!NOTE]
> Para información sobre el uso de servicios Mac hospedados en la nube en lugar de un equipo Mac, vea [Configure Visual Studio to connect to your cloud hosted Mac](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac) (Configurar Visual Studio para conectarse al servicio Mac basado en la nube). Las instrucciones sirven para compilar con Visual Studio Tools para Apache Cordova. Para usar las instrucciones para compilar con C++, sustituya vcremote por remotebuild.

Una vez instaladas las herramientas para compilar con iOS, consulte este tema para obtener información sobre maneras rápidas de configurar y actualizar al agente remoto para el desarrollo de iOS en Visual Studio y en el equipo Mac.

## <a name="prerequisites"></a>Requisitos previos

Para instalar y usar el agente remoto para desarrollar código para iOS, primero debe cumplir estos requisitos previos:

- Un equipo Mac con OS X Mavericks (versión 10.9 o posterior)

- Debe disponer de un [ID de Apple](https://appleid.apple.com/)

- Debe contar con una cuenta activa del [programa para desarrolladores de iOS](https://developer.apple.com/programs/ios/) con Apple

- [Xcode](https://developer.apple.com/xcode/downloads/), versión 6 o posterior.

   Xcode se puede descargar desde App Store.

- Herramientas de línea de comandos de Xcode

   Para instalar las herramientas de línea de comandos de Xcode, abra la aplicación Terminal en su equipo Mac y escriba el siguiente comando:

   `xcode-select --install`

- Debe tener una identidad de firma de iOS configurada en Xcode.

   Para obtener información detallada sobre cómo obtener una identidad de firma de iOS, vea [Mantener sus certificados e identidades de firma](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) en la biblioteca de desarrolladores de iOS. Para ver o establecer la identidad de firma en Xcode, abra el menú **Xcode** y elija **Preferencias**. Seleccione **Cuentas** y elija su Apple ID. A continuación, elija el botón **Ver detalles** .

- Si usa un dispositivo iOS para el desarrollo, necesitará un perfil de aprovisionamiento en Xcode para el dispositivo.

   Para obtener información detallada sobre la creación de perfiles de aprovisionamiento, vea [Creación de perfiles de aprovisionamiento mediante el centro de miembros](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) en la biblioteca de desarrolladores de iOS.

- [Node.js](https://nodejs.org/)

   Instale la versión más reciente de compatibilidad a largo plazo (LTS), 8.x, de Node.js en el equipo Mac. Tenga en cuenta que es posible que otras versiones de la versión más reciente no admitan algunos módulos que se usan en vcremote y pueden impedir la instalación de vcremote.

- Versión actualizada de npm.

   La versión de npm que viene con Node.js puede no ser suficientemente reciente como para instalar vcremote. Para actualizar npm, abra la aplicación Terminal en su Mac y escriba el siguiente comando:

   `sudo npm install -g npm@latest`

##  <a name="Install"></a> Instalar al agente remoto para iOS

Cuando se instala Visual C++ para el desarrollo móvil multiplataforma, Visual Studio puede comunicarse con [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988), un agente remoto que se ejecuta en el equipo Mac para transferir archivos, compilar y ejecutar la aplicación de iOS, así como para enviar comandos de depuración.

Antes de instalar el agente remoto, asegúrese de que se cumplen los [Requisitos previos](#Prerequisites) y de que se ha instalado [Visual C++ para el desarrollo móvil multiplataforma](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

###  <a name="DownloadInstall"></a> Para descargar e instalar el agente remoto

- Desde la aplicación Terminal del Mac, escriba:

   `sudo npm install -g --unsafe-perm vcremote`

   El conmutador de instalación global (**-g**) es recomendable, pero no obligatorio.

   Durante la instalación, se instalará vcremote y se activará el modo de desarrollador en su Mac. También se instalarán[Homebrew](https://brew.sh/) y dos paquetes de npm, vcremote-lib y vcremote-utils. Cuando se complete la instalación, puede pasar por alto las advertencias sobre dependencias opcionales omitidas.

   > [!NOTE]
   > Para instalar Homebrew, debe disponer de acceso sudo (administrador). Si necesita instalar vcremote sin sudo, puede instalar Homebrew manualmente en una ubicación usr/local y agregar su carpeta bin a la ruta de acceso. Para obtener más información, vea la [documentación de Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Para habilitar manualmente el modo de desarrollador, escriba este comando en la aplicación Terminal: `DevToolsSecurity -enable`

Si ha actualizado a una nueva versión de Visual Studio, deberá actualizar también a la versión actual del agente remoto. Para actualizar el agente remoto, repita los pasos para descargar e instalar el agente remoto.

##  <a name="Start"></a> Iniciar el agente remoto

El agente remoto debe estar ejecutándose para que Visual Studio pueda compilar y ejecutar el código de iOS. Visual Studio se debe emparejar con el agente remoto para que puedan comunicarse. De forma predeterminada, el agente remoto se ejecuta en modo de conexión segura, que requiere un código PIN para emparejarse con Visual Studio.

###  <a name="RemoteAgentStartServer"></a> Para iniciar el agente remoto

- Desde la aplicación Terminal del Mac, escriba:

   `vcremote`

   Esto iniciará el agente remoto con el directorio de compilación predeterminado ~/vcremote. Para obtener opciones de configuración adicionales, vea [Configure the remote agent on the Mac](#ConfigureMac).

‎La primera vez que inicie el agente y cuando cree un nuevo certificado de cliente, se le facilitará la información necesaria para configurar el agente en Visual Studio, incluido el nombre de host, el puerto y el código PIN.

![Usar vcremote para generar un PIN seguro](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

Si tiene pensado configurar el agente remoto en Visual Studio usando el nombre de host, haga ping al equipo Mac desde Windows usando el nombre de host para comprobar que es accesible. De lo contrario, puede que necesite usar la dirección IP.

El código PIN generado es de un solo uso y solo es válido durante un tiempo limitado. Si no empareja Visual Studio con el agente remoto antes de que expire el tiempo, deberá generar un nuevo código PIN. Para obtener más información, consulta [Generate a new security PIN](#GeneratePIN).

Puede usar el agente remoto en modo no seguro. En modo no seguro, el agente remoto puede emparejarse a Visual Studio sin código PIN.

#### <a name="to-disable-secured-connection-mode"></a>Para deshabilitar el modo de conexión segura

- Para deshabilitar el modo de conexión segura en vcremote, escriba este comando en la aplicación Terminal en su equipo Mac:

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Para habilitar el modo de conexión segura

- Para habilitar el modo de conexión segura, escriba este comando:

   `vcremote --secure true`

Una vez iniciado el agente remoto, puede usarlo desde Visual Studio hasta que lo detenga.

#### <a name="to-stop-the-remote-agent"></a>Para detener el agente remoto

- En la ventana de Terminal en la que se esté ejecutando vcremote, escriba **Control**+**C**.

##  <a name="ConfigureVS"></a> Configurar el agente remoto en Visual Studio

Para conectar con el agente remoto desde Visual Studio, debe especificar la configuración remota en las opciones de Visual Studio.

#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Para configurar el agente remoto desde Visual Studio

1. Si el agente no se está ejecutando en su Mac, siga los pasos que se describen en [Iniciar el agente remoto](#Start). Su equipo Mac debe ejecutar vcremote para que Visual Studio se empareje, se conecte y compile el proyecto correctamente.

1. Obtenga el nombre de host o dirección IP de su Mac.

   Use el comando **ifconfig** en una ventana de Terminal para obtener la dirección IP. Use la dirección de entrada que aparece en la interfaz de red activa.

1. En la barra de menús de Visual Studio, elija **Herramientas**, **Opciones**.

1. En el cuadro de diálogo **Opciones** , expanda **Multiplataforma**, **C++**, **iOS**.

1. En los campos **Nombre de host** y **Puerto** , escriba los valores especificados por el agente remoto cuando se inició. El nombre de host puede ser el nombre DNS o dirección IP de su equipo Mac. El puerto predeterminado es 3030.

   > [!NOTE]
   > Si no puede hacer ping al equipo Mac usando el nombre de host, puede que necesite usar la dirección IP.

1. Si usa el agente remoto en el modo de conexión segura predeterminado, active la casilla **Seguro** y, a continuación, escriba el valor de PIN especificado por el agente remoto en el campo **Pin** . Si usa el agente remoto en el modo de conexión no segura, desactive la casilla **Seguro** y deje el campo **Pin** en blanco.

1. Pulse **Emparejar** para habilitar el emparejamiento.

   ![Configurar conexión de vcremote para compilaciones de iOS](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   El emparejamiento continúa hasta que se cambie el nombre de host o el puerto. Si cambia el nombre de host o del puerto en el cuadro de diálogo **Opciones** , para deshacer el cambio, elija el botón **Revertir** para volver al emparejamiento anterior.

   Si el emparejamiento no se realiza correctamente, compruebe que se está ejecutando el agente remoto. Para ello, siga los pasos que se describen en [Start the remote agent](#Start). Si ha pasado demasiado tiempo desde que se generó el PIN de agente remoto, siga los pasos descritos en [Generate a new security PIN](#GeneratePIN) en el equipo Mac y vuelva a intentarlo. Si va a usar el nombre de host del equipo Mac, pruebe a usar la dirección IP en el **Nombre de host** en su lugar.

1. Actualice el nombre de la carpeta en el campo **Raíz remota** para especificar la carpeta que usará el agente remoto en el directorio de inicio (*~*) del equipo Mac. De forma predeterminada, el agente remoto usa /Users/`username`/vcremote como la raíz remota.

1. Elija **Aceptar** para guardar la configuración de conexión de emparejamiento remota.

Visual Studio usa la misma información para conectar con el agente remoto en su equipo Mac cada vez que lo use. No necesitará emparejar Visual Studio con el agente remoto de nuevo a menos que genere un nuevo certificado de seguridad en su equipo Mac o que cambie su nombre de host o dirección IP.

##  <a name="GeneratePIN"></a> Generate a new security PIN

Al iniciar el agente remoto por primera vez, el PIN generado se valida durante un tiempo limitado (10 minutos de forma predeterminada). Si no empareja Visual Studio con el agente remoto antes de que expire el tiempo, deberá generar un nuevo PIN.

#### <a name="to-generate-a-new-pin"></a>Para generar un código PIN nuevo

1. Detenga el agente o abra una segunda ventana de la aplicación Terminal en su Mac y úsela para escribir el comando.

1. Especifique el comando siguiente en la aplicación Terminal:

   `vcremote generateClientCert`

   El agente remoto genera un nuevo PIN temporal. Para emparejar Visual Studio usando el nuevo PIN, repita los pasos descritos en [Configurar el agente remoto en Visual Studio](#ConfigureVS).

##  <a name="GenerateCert"></a> Generar un nuevo certificado de servidor

Por motivos de seguridad, los certificados de servidor que emparejan Visual Studio con el agente remoto están asociados a la dirección IP o el nombre de host de su equipo Mac. Si estos valores cambian, deberá generar un nuevo certificado de servidor y volver a configurar después Visual Studio con los nuevos valores.

#### <a name="to-generate-a-new-server-certificate"></a>Para generar un nuevo certificado de servidor

1. Detenga el agente vcremote.

1. Especifique el comando siguiente en la aplicación Terminal:

   `vcremote resetServerCert`

1. Cuando se le solicite confirmación, escriba `Y`.

1. Especifique el comando siguiente en la aplicación Terminal:

   `vcremote generateClientCert`

   Esto generará un nuevo PIN temporal.

1. Para emparejar Visual Studio usando el nuevo PIN, repita los pasos descritos en [Configurar el agente remoto en Visual Studio](#ConfigureVS).

##  <a name="ConfigureMac"></a> Configure the remote agent on the Mac

Puede configurar el agente remoto usando varias opciones de línea de comando. Así, puede especificar el puerto para escuchar las solicitudes de compilación y especificar el número máximo de compilaciones que mantener en el sistema de archivos. El límite predeterminado es de 10 compilaciones. El agente remoto quitará las compilaciones que excedan este valor máximo al apagar el equipo.

#### <a name="to-configure-the-remote-agent"></a>Para configurar el agente remoto

- Para ver una lista completa de comandos del agente remoto, escriba lo siguiente en la ventana de la aplicación Terminal:

   `vcremote --help`

- Para deshabilitar el modo seguro y habilitar las conexiones sencillas basadas en HTTP, escriba:

   `vcremote --secure false`

   Cuando use esta opción, desactive la casilla **Seguro** y deje en blanco el campo **Pin** cuando configure el agente en Visual Studio.

- Para especificar una ubicación para los archivos del agente remoto, especifique:

   `vcremote --serverDir directory_path`

   Donde *directory_path* es la ubicación de su equipo Mac donde se guardarán los archivos de registro, las compilaciones y los certificados de servidor. De forma predeterminada, esta ubicación es */Users/\<nombre de usuario>/vcremote*. Las compilaciones aparecerán organizadas por número de compilación.

- Para usar un proceso en segundo plano para capturar `stdout` y `stderr` en un archivo con el nombre server.log, escriba:

   `vcremote > server.log 2>&1 &`

   El archivo server.log puede ayudarle a resolver problemas de compilación.

- Para ejecutar el agente mediante un archivo de configuración en lugar de con los parámetros de línea de comandos, especifique:

   `vcremote --config config_file_path`

   Donde *config_file_path* es la ruta de acceso a un archivo de configuración en formato JSON. Las opciones de inicio y sus valores no deben incluir guiones.

## <a name="see-also"></a>Vea también

- [Instalar Visual C++ para el desarrollo móvil multiplataforma](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
