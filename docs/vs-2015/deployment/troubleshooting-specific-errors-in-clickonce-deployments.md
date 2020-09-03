---
title: Solución de problemas de errores específicos en las implementaciones de ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81bb9bcecf37d2ed3fca29a4edc57738732de1a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917279"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Solucionar problemas de errores específicos de las implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se enumeran los siguientes errores comunes que pueden producirse al implementar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación de y se proporcionan los pasos necesarios para resolver cada problema.  
  
## <a name="general-errors"></a>Errores generales  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Al intentar buscar un archivo. Application, no se produce nada o se representa XML en Internet Explorer, o cuando se recibe un cuadro de diálogo Ejecutar o guardar como  
 Este error puede deberse a que los tipos de contenido (también conocidos como tipos MIME) no se están registrando correctamente en el servidor o cliente.  
  
 En primer lugar, asegúrese de que el servidor está configurado para asociar la extensión. Application con el tipo de contenido "application/x-MS-Application".  
  
 Si el servidor está configurado correctamente, asegúrese de que [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] está instalado en el equipo. Si [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] está instalado y sigue viendo este problema, intente desinstalar y reinstalar [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] para volver a registrar el tipo de contenido en el cliente.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>El mensaje de error indica "no se puede recuperar la aplicación. Faltan archivos en la implementación "o" se ha interrumpido la descarga de la aplicación, compruebe si hay errores de red y vuelva a intentarlo más tarde "  
 Este mensaje indica que no se pueden descargar uno o varios archivos a los que hacen referencia los [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiestos. La forma más fácil de depurar este error es intentar descargar la dirección URL que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dice que no se puede descargar. Estas son algunas causas posibles:  
  
- Si el archivo de registro dice "(403) prohibido" o "(404) no encontrado", compruebe que el servidor web está configurado para que no bloquee la descarga de este archivo. Para obtener más información, vea [Problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
- Si el servidor está bloqueando el archivo. config, vea la sección "error de descarga al intentar instalar una aplicación con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] un archivo. config" más adelante en este tema.  
  
- Determine si esto ocurrió porque la `deploymentProvider` dirección URL del manifiesto de implementación apunta a una ubicación diferente de la dirección URL que se usa para la activación.  
  
- Asegúrese de que todos los archivos están presentes en el servidor; el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] registro debería indicarle qué archivo no se ha encontrado.  
  
- Ver si hay problemas de conectividad de red; puede recibir este mensaje si el equipo cliente se desconectó durante la descarga.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Error de descarga al intentar instalar una aplicación ClickOnce que tiene un archivo. config  
 De forma predeterminada, una aplicación basada en Windows Visual Basic incluye un archivo App.config. Habrá un problema cuando un usuario intente instalar desde un servidor Web que usa Windows Server 2003, ya que el sistema operativo bloquea la instalación de los archivos. config por motivos de seguridad. Para habilitar el archivo. config que se va a instalar, haga clic en **usar la extensión de archivo ". deploy"** en el cuadro de diálogo **Opciones de publicación** .  
  
 También debe establecer los tipos de contenido (también conocidos como tipos MIME) correctamente para los archivos. Application,. manifest e. deploy. Para obtener más información, consulte la documentación del servidor Web.  
  
 Para obtener más información, vea "Windows Server 2003: tipos de contenido bloqueados" en [problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Mensaje de error: "la aplicación tiene un formato incorrecto;" El archivo de registro contiene "XML Signature is invalid"  
 Asegúrese de que ha actualizado el archivo de manifiesto y lo ha firmado de nuevo. Vuelva a publicar la aplicación mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o use Mage para volver a firmar la aplicación.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Ha actualizado la aplicación en el servidor, pero el cliente no descarga la actualización  
 Para solucionar este problema, realice una de las siguientes tareas:  
  
- Examine la `deploymentProvider` dirección URL en el manifiesto de implementación. Asegúrese de que está actualizando los bits en la misma ubicación `deploymentProvider` a la que apunta.  
  
- Compruebe el intervalo de actualización en el manifiesto de implementación. Si este intervalo se establece en un intervalo periódico, como una vez cada seis horas, no buscará [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] una actualización hasta que se haya superado este intervalo. Puede cambiar el manifiesto para buscar una actualización cada vez que se inicie la aplicación. Cambiar el intervalo de actualización es una opción práctica durante el tiempo de desarrollo para comprobar que se instalan las actualizaciones, pero ralentiza la activación de la aplicación.  
  
- Intente volver a iniciar la aplicación en el menú Inicio. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es posible que haya detectado la actualización en segundo plano, pero le pedirá que instale los bits en la siguiente activación.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante la actualización, recibirá un error con la siguiente entrada de registro: "la referencia de la implementación no coincide con la identidad definida en el manifiesto de aplicación"  
 Este error puede producirse porque ha editado manualmente los manifiestos de implementación y de aplicación, y ha provocado que la descripción de la identidad de un ensamblado en un manifiesto deje de estar sincronizada con la otra. La identidad de un ensamblado consta de su nombre, versión, referencia cultural y token de clave pública. Examine las descripciones de identidad de los manifiestos y corrija las diferencias.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>La primera vez que la activación desde el disco local o el CD-ROM se realiza correctamente, pero la activación posterior del menú Inicio no se realiza correctamente  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usa la dirección URL del proveedor de implementación para recibir actualizaciones de la aplicación. Compruebe que la ubicación a la que apunta la dirección URL es correcta.  
  
#### <a name="error-cannot-start-the-application"></a>Error: "no se puede iniciar la aplicación"  
 Este mensaje de error suele indicar que hay un problema al instalar esta aplicación en el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] almacén. La aplicación tiene un error o el almacén está dañado. El archivo de registro puede indicarle dónde se produjo el error.  
  
 Debe hacer lo siguiente:  
  
- Compruebe que la identidad del manifiesto de implementación, la identidad del manifiesto de aplicación y la identidad del archivo EXE de la aplicación principal son únicas.  
  
- Compruebe que las rutas de acceso de archivo no tengan más de 100 caracteres. Si la aplicación contiene rutas de acceso de archivo demasiado largas, es posible que se superen las limitaciones de la ruta de acceso máxima que se puede almacenar. Intente acortar las rutas de acceso y vuelva a instalar.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>No se respeta la configuración de PrivatePath en el archivo de configuración de la aplicación  
 Para usar PrivatePath (las rutas de acceso de sondeo de fusión), la aplicación debe solicitar el permiso plena confianza. Intente cambiar el manifiesto de aplicación para solicitar plena confianza e inténtelo de nuevo.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la desinstalación, aparece un mensaje que indica que se ha producido un error al desinstalar la aplicación  
 Este mensaje suele indicar que la aplicación ya se ha quitado o que el almacén está dañado. Después de hacer clic en **Aceptar**, se quitará la entrada **Agregar o quitar programa** .  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante la instalación, aparece un mensaje que indica que las dependencias de la plataforma no están instaladas  
 Falta un requisito previo en la GAC (caché global de ensamblados) que la aplicación necesita para ejecutarse.  
  
## <a name="publishing-with-visual-studio"></a>Publicar con Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Se produce un error en la publicación en Visual Studio  
 Asegúrese de que tiene el derecho de publicar en el servidor de destino. Por ejemplo, si ha iniciado sesión en un equipo de Terminal Server como un usuario normal, no como administrador, es probable que no tenga los derechos necesarios para publicar en el servidor Web local.  
  
 Si está publicando con una dirección URL, asegúrese de que el equipo de destino tiene Extensiones de servidor de FrontPage habilitado.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Mensaje de error: no se puede crear el sitio web ' \<site> '. Los componentes para comunicarse con Extensiones de servidor de FrontPage no están instalados.  
 Asegúrese de que tiene instalado el componente de creación Web Microsoft Visual Studio en el equipo desde el que se va a publicar. En el caso de los usuarios de Express, este componente no se instala de forma predeterminada.  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Mensaje de error: no se encontró el archivo ' Microsoft. Windows. Common-Controls, version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture = \* , Type = Win32 '  
 Este mensaje de error aparece al intentar publicar una aplicación WPF con estilos visuales habilitados. Para resolver este problema, consulte [Cómo: publicar una aplicación WPF con estilos visuales habilitados](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Usar Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Ha intentado firmar con un certificado en el almacén de certificados y un cuadro de mensaje en blanco recibido  
 En el cuadro de diálogo **firma** , debe:  
  
- Seleccione **firmar con un certificado almacenado**y  
  
- Seleccione un certificado de la lista. el primer certificado no es la selección predeterminada.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Al hacer clic en el botón "no firmar", se produce una excepción  
 Este problema es un error conocido. Es [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] necesario que todos los manifiestos estén firmados. Simplemente seleccione una de las opciones de firma y, a continuación, haga clic en **Aceptar**.  
  
## <a name="additional-errors"></a>Errores adicionales  
 En la tabla siguiente se muestran algunos mensajes de error comunes que un usuario de equipo cliente puede recibir cuando el usuario instala una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Cada mensaje de error aparece junto a una descripción de la causa más probable del error.  
  
|Mensaje de error|Descripción|  
|-------------------|-----------------|  
|No se puede iniciar la aplicación. Póngase en contacto con el editor de la aplicación.<br /><br /> No se puede iniciar la aplicación. Póngase en contacto con el proveedor de la aplicación para obtener ayuda.|Se trata de mensajes de error genéricos que se producen cuando no se puede iniciar la aplicación y no se puede encontrar ningún otro motivo concreto. Con frecuencia, esto significa que la aplicación está dañada o que el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] almacén está dañado.|  
|No se puede continuar. La aplicación tiene un formato incorrecto. Póngase en contacto con el editor de la aplicación para obtener ayuda.<br /><br /> La validación de la aplicación no se realizó correctamente. No se puede continuar.<br /><br /> No se pueden recuperar los archivos de aplicación. Archivos dañados en la implementación.|Uno de los archivos de manifiesto de la implementación no es válido sintácticamente o contiene un hash que no se puede reconciliar con el archivo correspondiente. Este error también puede indicar que el manifiesto incrustado dentro de un ensamblado está dañado. Vuelva a crear la implementación y vuelva a compilar la aplicación, o busque y corrija los errores manualmente en los manifiestos.|  
|No se puede recuperar la aplicación. Error de autenticación.<br /><br /> La instalación de la aplicación no se realizó correctamente. No se encuentran los archivos de aplicaciones en el servidor. Póngase en contacto con el editor de la aplicación o con el administrador para obtener ayuda.|No se pueden descargar uno o varios archivos de la implementación porque no tiene permiso para obtener acceso a ellos. Esto puede deberse a un error 403 prohibido devuelto por un servidor Web, que puede producirse si uno de los archivos de la implementación finaliza con una extensión que hace que el servidor web lo trate como un archivo protegido. Además, un directorio que contenga uno o varios archivos de la aplicación podría requerir un nombre de usuario y una contraseña para tener acceso a.|  
|No se puede descargar la aplicación. Faltan archivos necesarios en la aplicación. Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|No se encuentran uno o más de los archivos enumerados en el manifiesto de aplicación en el servidor. Compruebe que ha cargado todos los archivos dependientes de la implementación y vuelva a intentarlo.|  
|La descarga de la aplicación no se realizó correctamente. Compruebe la conexión de red o póngase en contacto con el administrador del sistema o el proveedor de servicios de red.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no se puede establecer una conexión de red con el servidor. Examine la disponibilidad del servidor y el estado de la red.|  
|Error de URLDownloadToCacheFile con HRESULT ' \<number> '. Error al intentar descargar ' \<file> '.|Si un usuario ha establecido la opción de seguridad avanzada de Internet Explorer "advertir si se cambia entre el modo seguro y no seguro" en el equipo de destino de la implementación, y si la dirección URL de configuración de la aplicación ClickOnce que se está instalando se redirige desde un sitio no seguro a uno seguro (o viceversa), se producirá un error en la instalación porque la advertencia de<br /><br /> Para solucionarlo, puede realizar una de las siguientes acciones:<br /><br /> -Desactive la opción de seguridad.<br />-Asegúrese de que la dirección URL de instalación no se redirige de forma que cambie los modos de seguridad.<br />-Quitar la redirección completamente y apuntar a la dirección URL de instalación real.|  
|Error al escribir en el disco duro. Puede que no haya suficiente espacio disponible en el disco. Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|Esto puede indicar que no hay suficiente espacio en disco para almacenar la aplicación, pero también puede indicar un error de e/s más general cuando se intenta guardar los archivos de aplicación en la unidad.|  
|No se puede iniciar la aplicación. No hay suficiente espacio disponible en el disco.|El disco duro está lleno. Desactive el espacio e intente ejecutar la aplicación de nuevo.|  
|Hay demasiadas activaciones implementadas intentando cargarse a la vez.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] limita el número de aplicaciones diferentes que pueden iniciarse al mismo tiempo. Esto es en gran medida para ayudar a protegerse frente a intentos malintencionados de provocar ataques por denegación de servicio en el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] servicio local; los usuarios que intenten iniciar la misma aplicación repetidamente, en una sucesión rápida, solo terminarán con una única instancia de la aplicación.|  
|Los accesos directos no se pueden activar a través de la red.|Los accesos directos a una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación solo se pueden iniciar en el disco duro local. No se pueden iniciar abriendo una dirección URL que apunte a un archivo de acceso directo en un servidor remoto.|  
|La aplicación es demasiado grande para ejecutarse en línea en confianza parcial. Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|Una aplicación que se ejecuta en confianza parcial no puede ser mayor que la mitad del tamaño de la cuota de aplicación en línea, que de forma predeterminada es 250 MB.|  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad e implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
