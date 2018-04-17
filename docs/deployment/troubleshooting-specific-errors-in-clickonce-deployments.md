---
title: Solución de problemas de errores específicos de las implementaciones de ClickOnce | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b52caad3b6e4c98dd78e6c6be9835c11ac4d4175
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Solucionar problemas de errores específicos de las implementaciones de ClickOnce
Este tema enumeran los siguientes errores comunes que pueden producirse al implementar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación y proporciona los pasos necesarios para resolver cada problema.  
  
## <a name="general-errors"></a>Errores generales  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Cuando intenta buscar un archivo Application, no ocurre nada, se representa XML en Internet Explorer o aparece un cuadro de diálogo Ejecutar o guardar como  
 Este error se debe probablemente a tipos de contenido (también conocido como tipos MIME) no está registrados correctamente en el servidor o cliente.  
  
 En primer lugar, asegúrese de que el servidor está configurado para asociar la extensión Application con el tipo de contenido "application/x-ms-application".  
  
 Si el servidor está configurado correctamente, asegúrese de que el [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] está instalado en el equipo. Si el [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] está instalado, y todavía aparece este problema, pruebe a desinstalar y volver a instalar el [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] para volver a registrar el tipo de contenido en el cliente.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Mensaje de error: "no se puede recuperar de la aplicación. Faltan archivos en la implementación "o"se ha interrumpido la descarga de la aplicación, comprobar si hay errores de red y vuelva a intentarlo "  
 Este mensaje indica que uno o varios archivos al que hace referencia el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no se puede descargar los manifiestos. La manera más fácil de depurar este error es intentar descargar la dirección URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indica no se puede descargar. Estas son algunas causas posibles:  
  
-   Si el archivo de registro dice "(403) prohibido" o "(404) no encontrado", compruebe que el servidor Web está configurado para que esto no bloquea la descarga de este archivo. Para obtener más información, vea [Problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Si el servidor está bloqueando el archivo .config, vea la sección "error de descarga al intentar instalar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que tiene un archivo .config" más adelante en este tema.  
  
-   Determinar si se ha producido porque la `deploymentProvider` dirección URL del manifiesto de implementación apunta a una ubicación diferente de la dirección URL utilizada para la activación.  
  
-   Asegúrese de que todos los archivos están presentes en el servidor; el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] registro debería indicar el archivo que no se encontró.  
  
-   Vea si hay problemas de conectividad de red; puede recibir este mensaje si el equipo cliente se puso sin conexión durante la descarga.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Error de descarga al intentar instalar una aplicación ClickOnce que tiene un archivo .config  
 De forma predeterminada, una aplicación basada en Windows de Visual Basic incluye un archivo App.config. Habrá un problema cuando un usuario intenta instalar desde un servidor Web que utiliza Windows Server 2003, porque ese sistema operativo bloquea la instalación de archivos .config por razones de seguridad. Para habilitar el archivo .config para instalarse, haga clic en **usar la extensión de archivo ".deploy"** en el **opciones de publicación** cuadro de diálogo.  
  
 También debe establecer los tipos de contenido (también conocido como tipos MIME) correctamente para Application Manifest, archivos y ".deploy". Para obtener más información, consulte la documentación del servidor Web.  
  
 Para obtener más información, vea "Windows Server 2003: tipos de contenido bloqueados" en [servidor y problemas de configuración de cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Mensaje de error: "Aplicación de formato no es correcto;" Archivo de registro contiene "la firma XML no es válido"  
 Asegúrese de que ha actualizado el archivo de manifiesto y vuelve a estar firmada. Volver a publicar la aplicación mediante el uso de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o utilice Mage para firmar la aplicación de nuevo.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Actualiza la aplicación en el servidor, pero el cliente no descarga la actualización  
 Este problema puede resolverse realizando una de las tareas siguientes:  
  
-   Examine el `deploymentProvider` dirección URL del manifiesto de implementación. Asegúrese de que está actualizando los bits en la misma ubicación que `deploymentProvider` apunta a.  
  
-   Compruebe el intervalo de actualización en el manifiesto de implementación. Si este intervalo se establece en un intervalo periódico, como una vez cada seis horas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no se examinarán para una actualización hasta que haya transcurrido este intervalo. Puede cambiar el manifiesto para que busque una actualización cada vez que se inicie la aplicación. Cambiar el intervalo de actualización es una opción recomendable durante el tiempo de desarrollo para comprobar las actualizaciones se están instalando, pero ralentiza la activación de la aplicación.  
  
-   Intente volver a iniciar la aplicación en el menú Inicio. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede haber detectado la actualización en segundo plano, pero se le pedirá que instale los bits en la siguiente activación.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante la actualización se recibe un error que tiene la siguiente entrada del registro: "la referencia en la implementación no coincide con la identidad definida en el manifiesto de aplicación"  
 Este error puede producirse porque se han editado manualmente los manifiestos de aplicación e implementación y haber producido la descripción de la identidad de un ensamblado en un manifiesto para que dejen de estar sincronizados con las demás. La identidad de un ensamblado consta de su nombre, la versión, la referencia cultural y el token de clave pública. Examine las descripciones de identidad en los manifiestos y corrija cualquier diferencia.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Activación desde el disco local o CD-ROM de primera vez que se realiza correctamente, pero no se realiza correctamente la activación posterior desde el menú Inicio  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa la dirección URL del proveedor de implementación para recibir las actualizaciones de la aplicación. Compruebe que la ubicación que apunta a la dirección URL es correcta.  
  
#### <a name="error-cannot-start-the-application"></a>Error: "no se puede iniciar la aplicación"  
 Este mensaje de error suele indica que hay un problema al instalar esta aplicación en el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] almacenar. La aplicación tiene un error o el almacén está dañado. El archivo de registro puede indicar dónde se produjo el error.  
  
 Debe hacer lo siguiente:  
  
-   Compruebe que la identidad del manifiesto de implementación, la identidad del manifiesto de aplicación y la identidad de la aplicación principal EXE son únicas.  
  
-   Compruebe que las rutas de acceso de archivo no tengan más de 100 caracteres. Si la aplicación contiene rutas de acceso de archivo que son demasiado largos, puede superar las limitaciones en la ruta de acceso máxima que se puede almacenar. Intente acortar las rutas de acceso y vuelva a instalar.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>No se acepta la configuración PrivatePath en el archivo de configuración de aplicación  
 Para utilizar PrivatePath (rutas de búsqueda de fusión), la aplicación debe solicitar permiso de plena confianza. Pruebe a cambiar el manifiesto de aplicación para solicitar la plena confianza y, a continuación, vuelva a intentarlo.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante la desinstalación aparece el mensaje, "No se pudo desinstalar la aplicación"  
 Este mensaje suele indica que ya se ha quitado la aplicación o el almacén está dañado. Tras hacer clic en **Aceptar**, **agregar o quitar programas** entrada que se va a quitar.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante la instalación, aparece un mensaje que dice que no están instaladas las dependencias de plataforma  
 Falta un requisito previo en la GAC (caché global de ensamblados) que la aplicación necesita para ejecutarse.  
  
## <a name="publishing-with-visual-studio"></a>Publicación con Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Se produce un error en la publicación en Visual Studio  
 Asegúrese de que tiene el derecho a publicar en el servidor de destino. Por ejemplo, si ha iniciado sesión un equipo de servidor de terminal server como usuario normal, no como administrador, probablemente no tendrá los derechos necesarios para publicar en el servidor Web local.  
  
 Si va a publicar con una dirección URL, asegúrese de que el equipo de destino tiene habilitadas las extensiones de servidor de FrontPage.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Mensaje de error: No se puede crear el sitio Web '\<sitio >'. No se instalan los componentes para la comunicación con las extensiones de servidor de FrontPage.  
 Asegúrese de que tiene Microsoft Visual Studio Web Authoring Component instalado en el equipo que va a publicar en. Para los usuarios de Express, este componente no está instalado de forma predeterminada. Para obtener más información, vea [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Mensaje de error: No se pudo encontrar el archivo ' Microsoft.Windows.Common-controles, Version = 6.0.0.0, referencia cultural = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, tipo = win32'  
 Este mensaje de error aparece cuando intenta publicar una aplicación WPF con estilos visuales habilitados. Para resolver este problema, consulte [Cómo: publicar una aplicación de WPF con estilos Visual habilitados](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Utilizar Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Has intentado iniciar sesión con un certificado en el almacén de certificados y un cuadro de mensaje en blanco.  
 En el **firma** cuadro de diálogo, debe:  
  
-   Seleccione **inicio de sesión con un certificado almacenado**, y  
  
-   Seleccione un certificado de la lista; el primer certificado no es la selección predeterminada.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Haga clic en el botón "No firmar" se produce una excepción  
 Este problema es un error conocido. Todos los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos se exige la firma. Seleccione una de las opciones de firma y, a continuación, haga clic en **Aceptar**.  
  
## <a name="additional-errors"></a>Errores adicionales  
 La tabla siguiente muestran algunos mensajes de error comunes que puede recibir un equipo cliente cuando el usuario instala una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Cada mensaje de error se muestra junto con una descripción de la causa más probable del error.  
  
|Mensaje de error|Descripción|  
|-------------------|-----------------|  
|No se puede iniciar la aplicación. Póngase en contacto con el Editor de la aplicación.<br /><br /> No se puede iniciar la aplicación. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación.|Se trata de mensajes de error genérico que se producen cuando no se puede iniciar la aplicación y no se encuentra ningún otro motivo más concreto. Con frecuencia esto significa que la aplicación está dañada de algún modo, o que la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] almacén está dañado.|  
|No puede continuar. La aplicación de formato no es correcto. Para obtener ayuda, póngase en contacto con el Editor de la aplicación.<br /><br /> Validación de la aplicación no se realizó correctamente. No se puede continuar.<br /><br /> No se puede recuperar archivos de la aplicación. Archivos dañados en la implementación.|Uno de los archivos de manifiesto de la implementación no es sintácticamente válida o contiene un hash que no puede reconciliarse con el archivo correspondiente. Este error también puede indicar que el manifiesto incrustado en un ensamblado está dañado. Volver a crear la implementación y vuelva a compilar la aplicación, o buscar y corregir los errores manualmente en los manifiestos.|  
|No se puede recuperar de la aplicación. Error de autenticación.<br /><br /> Instalación de la aplicación no se realizó correctamente. No puede encontrar archivos de aplicaciones en el servidor. Para obtener ayuda, póngase en contacto con el Editor de la aplicación o con el administrador.|No se puede descargar uno o varios archivos en la implementación porque no tiene permiso para tener acceso a ellos. Esto puede deberse a un error 403 Prohibido devuelto por un servidor Web, que puede producirse si uno de los archivos de la implementación finaliza con una extensión que hace que el servidor Web tratarlo como un archivo protegido. Además, para tener acceso a un directorio que contiene uno o varios de los archivos de la aplicación podría requerir un nombre de usuario y una contraseña.|  
|No se puede descargar la aplicación. Falta archivos necesarios en la aplicación. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Uno o varios de los archivos enumerados en el manifiesto de aplicación no se encuentra en el servidor. Compruebe que ha cargado todos los archivos de implementación dependientes y vuelva a intentarlo.|  
|Descarga de la aplicación no se realizó correctamente. Compruebe la conexión de red o póngase en contacto con el administrador del sistema o el proveedor de servicios de red.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no se puede establecer una conexión de red al servidor. Examine la disponibilidad del servidor y el estado de la red.|  
|URLDownloadToCacheFile dio el error HRESULT '\<número >'. Se produjo un error al intentar descargar '\<archivo >'.|Si un usuario ha establecido la opción de seguridad avanzada de Internet Explorer "Advertir si se cambia entre seguro y un modo no seguro" en el equipo de destino de implementación, y si se ha redirigido el valor de la dirección URL de instalación de la aplicación ClickOnce que se está instalada desde no seguras a un sitio seguro (o a la inversa), la instalación se producirá un error porque la advertencia de Internet Explorer interrumpe.<br /><br /> Para resolver este problema, siga uno de los siguientes:<br /><br /> -Desactive la opción de seguridad.<br />-Compruebe que la dirección URL de instalación no se redirige de manera que cambie los modos de seguridad seguro.<br />-Quite completamente la redirección y apunte a la dirección URL de instalación real.|  
|Error al escribir en el disco duro. Puede haber suficiente espacio disponible en el disco. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Puede tratarse de espacio en disco suficiente para almacenar la aplicación, pero también puede indicar un error de E/S más general cuando se intenta guardar los archivos de aplicación en la unidad.|  
|No se puede iniciar la aplicación. No hay suficiente espacio disponible en el disco.|El disco duro está lleno. Libere espacio e intente ejecutar de nuevo la aplicación.|  
|Hay demasiadas activaciones implementadas están intentando cargar al mismo tiempo.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] limita el número de aplicaciones distintas que pueden iniciarse al mismo tiempo. Esto es en gran medida para ayudar a proteger frente a intentos malintencionados para realizar ataques de denegación de servicio en la variable local [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] servicio; los usuarios que vuelva a intentar iniciar la misma aplicación varias veces, en una sucesión rápida, sólo terminará con una única instancia de la aplicación.|  
|No se puede activar accesos directos a través de la red.|Accesos directos a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sólo se puede iniciar la aplicación en el disco duro local. No pueden iniciarse abriendo una dirección URL que apunta a un archivo de acceso directo en un servidor remoto.|  
|La aplicación es demasiado grande para ejecutarse en línea con confianza parcial. Para obtener ayuda, póngase en contacto con el proveedor de la aplicación o el administrador del sistema.|Una aplicación que se ejecuta con confianza parcial no puede ser mayor que la mitad del tamaño de la cuota de aplicación en línea, cuyo valor predeterminado es 250 MB.|  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)