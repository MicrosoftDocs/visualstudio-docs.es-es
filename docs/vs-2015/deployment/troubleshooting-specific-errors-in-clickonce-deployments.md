---
title: Solución de problemas de errores específicos en las implementaciones de ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: d0b7e53eba21372641bad683c442e796648a4765
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213647"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Solucionar problemas de errores específicos de las implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tema enumeran los siguientes errores comunes que pueden producirse al implementar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación y proporciona los pasos para solucionar cada problema.  
  
## <a name="general-errors"></a>Errores generales  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Cuando intenta buscar un archivo .application, no ocurre nada, se representa XML en Internet Explorer o aparece un cuadro de diálogo Ejecutar o guardar como  
 Este error se debe probablemente a tipos de contenido (también conocido como tipos MIME) no está registrados correctamente en el servidor o cliente.  
  
 En primer lugar, asegúrese de que el servidor está configurado para asociar la extensión .application al tipo de contenido "application/x-ms-application".  
  
 Si el servidor está configurado correctamente, asegúrese de que el [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] está instalado en el equipo. Si el [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] está instalado, y sigue apareciendo este problema, pruebe a desinstalar y reinstalar el [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] para volver a registrar el tipo de contenido en el cliente.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Mensaje de error: "no se puede recuperar la aplicación. No se encuentra en la implementación de archivos"o"se ha interrumpido la descarga de la aplicación, compruebe si hay errores de red y vuelva a intentarlo más tarde"  
 Este mensaje indica que uno o varios archivos que se hace referencia el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no se puede descargar los manifiestos. La manera más fácil de depurar este error es intentar descargar la dirección URL que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no puede descargar. Estas son algunas causas posibles:  
  
-   Si el archivo de registro dice "(403) prohibido" o "(404) no encontrado", compruebe que el servidor Web está configurado para que no bloquea la descarga de este archivo. Para obtener más información, vea [Problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Si el servidor está bloqueando el archivo .config, consulte la sección "error de descarga al intentar instalar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación que tiene un archivo .config" más adelante en este tema.  
  
-   Determinar si esto se produjo porque la `deploymentProvider` dirección URL del manifiesto de implementación está señalando a una ubicación diferente a la dirección URL usada para la activación.  
  
-   Asegúrese de que todos los archivos están presentes en el servidor. el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] registro debe indicarle qué archivos no se encontró.  
  
-   Si hay problemas de conectividad de red; puede recibir este mensaje si el equipo cliente estuvo sin conexión durante la descarga.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Error de descarga al intentar instalar una aplicación ClickOnce que tiene un archivo .config  
 De forma predeterminada, una aplicación basada en Windows de Visual Basic incluye un archivo App.config. Habrá un problema cuando un usuario intenta instalar desde un servidor Web que utiliza Windows Server 2003, porque ese sistema operativo bloquea la instalación de los archivos .config por motivos de seguridad. Para habilitar el archivo .config para instalarse, haga clic en **usar extensión de archivo ".deploy"** en el **opciones de publicación** cuadro de diálogo.  
  
 También se deben establecer los tipos de contenido (también conocido como tipos MIME) adecuadamente para .application, .manifest y archivos. deploy. Para obtener más información, consulte la documentación del servidor Web.  
  
 Para obtener más información, vea "Windows Server 2003: tipos de contenido bloqueados" en [Server y problemas de configuración de cliente en implementaciones ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Mensaje de error: "Aplicación de formato no es correcto;" Archivo de registro contiene "la firma XML es válido"  
 Asegúrese de que ha actualizado el archivo de manifiesto y se vuelve a estar firmada. Volver a publicar la aplicación mediante el uso de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o usar Mage para firmar la aplicación de nuevo.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Actualiza la aplicación en el servidor, pero el cliente no descarga la actualización  
 Este problema podría resolverse realizando una de las tareas siguientes:  
  
-   Examine el `deploymentProvider` dirección URL del manifiesto de implementación. Asegúrese de que está actualizando los bits en la misma ubicación que `deploymentProvider` apunta a.  
  
-   Compruebe el intervalo de actualización en el manifiesto de implementación. Si este intervalo se establece en un intervalo periódico, como una vez cada seis horas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no examinará una actualización hasta que haya transcurrido este intervalo. Puede cambiar el manifiesto para buscar una actualización cada vez que se inicia la aplicación. Cambiar el intervalo de actualización es una opción recomendable durante el tiempo de desarrollo para comprobar las actualizaciones se instalan pero ralentiza la activación de la aplicación.  
  
-   Pruebe a iniciar la aplicación de nuevo en el menú Inicio. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es posible que haya detectado la actualización en segundo plano, pero se le solicitará que instale los bits en la siguiente activación.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante la actualización se recibe un error que tiene la siguiente entrada del registro: "la referencia en la implementación no coincide con la identidad definida en el manifiesto de aplicación"  
 Este error puede producirse porque se han editado manualmente los manifiestos de aplicación e implementación y haber causado la descripción de la identidad de un ensamblado en un manifiesto para que dejen de estar sincronizados con las demás. La identidad de un ensamblado consta de su nombre, versión, referencia cultural y token de clave pública. Examine las descripciones de identidad en los manifiestos y corrija cualquier diferencia.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Activación desde el disco local o CD-ROM de primera vez que se realiza correctamente, pero no se realiza correctamente la activación posterior desde el menú Inicio  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usa la dirección URL del proveedor de implementación para recibir las actualizaciones de la aplicación. Compruebe que la ubicación en la que apunta a la dirección URL es correcta.  
  
#### <a name="error-cannot-start-the-application"></a>Error: "no se puede iniciar la aplicación"  
 Este mensaje de error suele indica que hay un problema al instalar esta aplicación en el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] almacenar. La aplicación tiene un error o el almacén está dañado. El archivo de registro puede indicarle que se produjo el error.  
  
 Debe hacer lo siguiente:  
  
-   Compruebe que la identidad del manifiesto de implementación, la identidad del manifiesto de aplicación y la aplicación principal EXE son únicas.  
  
-   Compruebe que las rutas de acceso de archivo no son más de 100 caracteres. Si la aplicación contiene las rutas de acceso de archivo que son demasiado grandes, puede superar las limitaciones en la ruta de acceso máxima que puede almacenar. Intente acortar las rutas de acceso y vuelva a instalar.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>No se respeta la configuración PrivatePath en el archivo de configuración de aplicación  
 Para utilizar PrivatePath (rutas de búsqueda de fusión), la aplicación debe solicitar permiso de plena confianza. Pruebe a cambiar el manifiesto de aplicación para solicitar la plena confianza y, a continuación, vuelva a intentarlo.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la desinstalación aparece el mensaje, "No se pudo desinstalar la aplicación"  
 Este mensaje suele indica que la aplicación ya se ha quitado o el almacén está dañado. Tras hacer clic en **Aceptar**, **agregar o quitar programa** entrada se quitará.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante la instalación, aparece un mensaje que dice que no están instaladas las dependencias de plataforma  
 Falta un requisito previo en la GAC (caché global de ensamblados) que la aplicación necesita para ejecutarse.  
  
## <a name="publishing-with-visual-studio"></a>Publicación con Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Se produce un error en la publicación en Visual Studio  
 Asegúrese de que tiene el derecho a publicar en el servidor de destino. Por ejemplo, si ha iniciado sesión un equipo de servidor de terminal server como un usuario normal, no como administrador, probablemente no tendrá los derechos necesarios para publicar en el servidor Web local.  
  
 Si va a publicar con una dirección URL, asegúrese de que el equipo de destino tiene habilitadas las extensiones de servidor de FrontPage.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Mensaje de error: No se puede crear el sitio Web '\<sitio >'. No se instalan los componentes para comunicarse con extensiones de servidor.  
 Asegúrese de que tiene Microsoft Visual Studio Web Authoring componente instalado en la máquina que va a publicar en. Para los usuarios de Express, este componente no está instalado de forma predeterminada. Para obtener más información, vea [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Mensaje de error: No se pudo encontrar el archivo ' Microsoft.Windows.Common-controles, Version = 6.0.0.0, referencia cultural = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, tipo = win32'  
 Este mensaje de error aparece cuando se intenta publicar una aplicación WPF con estilos visuales habilitados. Para resolver este problema, consulte [Cómo: publicar una aplicación de WPF con estilos Visual habilitados](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Utilizar Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Se intentó iniciar sesión con un certificado en el almacén de certificados y un cuadro de mensaje en blanco.  
 En el **firma** cuadro de diálogo, debe:  
  
-   Seleccione **firmar con un certificado almacenado**, y  
  
-   Seleccione un certificado de la lista. el primer certificado no es la selección predeterminada.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Al hacer clic en el botón "Inicio de sesión no" produce una excepción  
 Este problema es un problema conocido. Todos los [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiestos son debe estar firmado. Seleccione una de las opciones de firma y, a continuación, haga clic en **Aceptar**.  
  
## <a name="additional-errors"></a>Otros errores  
 La siguiente tabla muestra algunos mensajes de error comunes que puede recibir un equipo cliente cuando el usuario instala una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación. Cada mensaje de error aparece junto con una descripción de la causa más probable del error.  
  
|Mensaje de error|Descripción|  
|-------------------|-----------------|  
|No se puede iniciar la aplicación. Póngase en contacto con el Editor de la aplicación.<br /><br /> No se puede iniciar la aplicación. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación.|Estos son los mensajes de error genérico que se producen cuando no se puede iniciar la aplicación y no se puede encontrar ninguna otra razón específica. Con frecuencia esto significa que la aplicación está dañada de algún modo, o que el [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] almacén está dañado.|  
|No puede continuar. La aplicación de formato no es correcto. Para obtener ayuda, póngase en contacto con el Editor de la aplicación.<br /><br /> No se realizó correctamente la validación de la aplicación. No se puede continuar.<br /><br /> No se puede recuperar archivos de la aplicación. Archivos dañados en la implementación.|Uno de los archivos de manifiesto de la implementación no es sintácticamente válido o contiene un hash que no puede reconciliarse con el archivo correspondiente. Este error también puede indicar que el manifiesto incrustado en un ensamblado está dañado. Volver a crear la implementación y volver a compilar la aplicación, o busque y corrija los errores de forma manual en los manifiestos.|  
|No se puede recuperar la aplicación. Error de autenticación.<br /><br /> No se realizó correctamente la instalación de la aplicación. No puede encontrar los archivos de las aplicaciones en el servidor. Para obtener ayuda, póngase en contacto con el Editor de la aplicación o el administrador.|No se puede descargar uno o varios archivos en la implementación porque no tiene permiso para tener acceso a ellos. Esto puede deberse a un error 403 Prohibido devuelto por un servidor Web, lo que puede producirse si uno de los archivos en la implementación finaliza con una extensión que hace que el servidor Web tratarlo como un archivo protegido. Además, para tener acceso a un directorio que contiene uno o varios de los archivos de la aplicación podría requerir un nombre de usuario y una contraseña.|  
|No se puede descargar la aplicación. Falta archivos necesarios en la aplicación. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Uno o varios de los archivos enumerados en el manifiesto de aplicación no se encuentra en el servidor. Compruebe que ha cargado todos los archivos de implementación dependientes e inténtelo de nuevo.|  
|Descarga de la aplicación no se realizó correctamente. Compruebe la conexión de red o póngase en contacto con su administrador del sistema o el proveedor de servicios de red.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no se puede establecer una conexión de red al servidor. Examine la disponibilidad del servidor y el estado de la red.|  
|URLDownloadToCacheFile dio el error HRESULT '\<número >'. Se produjo un error al intentar descargar '\<archivo >'.|Si un usuario ha establecido la opción de seguridad avanzada de Internet Explorer "Advertir si se cambia entre seguro y un modo no seguro" en el equipo de destino de implementación, y si se redirige la dirección URL de instalación de la aplicación ClickOnce se instala desde no seguro a un sitio seguro (o a la inversa), la instalación producirá un error porque la interrumpe la advertencia de Internet Explorer.<br /><br /> Para resolver este problema, puede realizar una de las siguientes acciones:<br /><br /> -Desactive la opción de seguridad.<br />-Asegúrese está seguro de que la dirección URL de instalación no se redirige de manera que cambia el modo de seguridad.<br />-Quite completamente la redirección y apunte a la dirección URL real del programa de instalación.|  
|Error al escribir en el disco duro. Puede haber suficiente espacio disponible en el disco. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Esto puede indicar el espacio en disco suficiente para almacenar la aplicación, pero también puede indicar un error de E/S más general cuando se intenta guardar los archivos de aplicación en la unidad.|  
|No se puede iniciar la aplicación. No hay suficiente espacio disponible en el disco.|El disco duro está lleno. Libere espacio e intente ejecutar de nuevo la aplicación.|  
|Hay demasiadas activaciones implementadas están intentando cargar a la vez.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] limita el número de aplicaciones diferentes que pueden iniciarse al mismo tiempo. Esto es en gran medida ayudar a proteger frente a intentos malintencionados para elaborar los ataques de denegación de servicio contra local [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] servicio; los usuarios que intentan iniciar la misma aplicación varias veces, en una sucesión rápida, sólo terminará con una sola instancia de la aplicación.|  
|Métodos abreviados no se puede activar a través de la red.|Accesos directos a un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] solo se puede iniciar la aplicación en el disco duro local. No pueden iniciarse abriendo una dirección URL que apunta a un archivo de acceso directo en un servidor remoto.|  
|La aplicación es demasiado grande para ejecutarse en línea con confianza parcial. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Una aplicación que se ejecuta en confianza parcial no puede ser mayor que la mitad del tamaño de la cuota de aplicación en línea, cuyo valor predeterminado es 250 MB.|  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



