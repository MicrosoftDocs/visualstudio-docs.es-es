---
title: "Solucionar problemas de errores espec&#237;ficos de las implementaciones de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired"
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, solucionar problemas"
  - "implementar aplicaciones, ClickOnce"
  - "solucionar problemas en implementaciones ClickOnce"
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# Solucionar problemas de errores espec&#237;ficos de las implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se recogen los errores comunes que pueden producirse cuando se implementa una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y se describen los pasos que deben seguirse para resolver cada problema.  
  
## Errores generales  
  
#### Cuando se intenta buscar un archivo .application, no ocurre nada, se representa XML en Internet Explorer o aparece el cuadro de diálogo Ejecutar o Guardar como.  
 Este error suele estar causado por tipos de contenido \(también conocido como tipos MIME\) que no se registran correctamente en el servidor o en el cliente.  
  
 En primer lugar, asegúrese de que el servidor esté configurado de modo que asocie la extensión .application al tipo de contenido "application\/x\-ms\-application".  
  
 Si el servidor está correctamente configurado, asegúrese de que [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] está instalado en el equipo.  Si [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] está instalado y todavía aparece este problema, pruebe a desinstalar y a volver a instalar [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] para registrar de nuevo el tipo de contenido en el cliente.  
  
#### Aparece el mensaje de error: "No se puede recuperar la aplicación.Faltan archivos en la implementación" o "Se ha interrumpido la descarga de la aplicación, compruebe si hay errores de red e inténtelo de nuevo".  
 Este mensaje indica que no se pueden descargar uno o varios archivos a los que hacen referencia los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La manera más fácil de depurar este error es intentar descargar la dirección URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no puede descargar.  Éstas son algunas posibles causas:  
  
-   Si el archivo de registro indica "\(403\) Prohibido" o "\(404\) No encontrado", compruebe que el servidor Web está configurado para que no bloquee la descarga de este archivo.  Para obtener más información, vea [Problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Si el servidor está bloqueando el archivo .config, vea la sección "Error de descarga al intentar instalar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que tiene un archivo .config", que figura más adelante.  
  
-   Determine si esto se ha producido porque la dirección URL de `deploymentProvider` en el manifiesto de implementación está señalando una ubicación diferente que la dirección URL utilizada para la activación.  
  
-   Asegúrese de que todos los archivos están presentes en el servidor; el registro de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] debe especificar el archivo que no se ha encontrado.  
  
-   Compruebe si hay problemas de conectividad de red; puede que aparezca este mensaje si el equipo cliente estuvo sin conexión durante la descarga.  
  
#### Error de descarga al intentar instalar una aplicación ClickOnce que tiene un archivo .config  
 De forma predeterminada, una aplicación basada en Windows de Visual Basic incluye un archivo App.config.  Surgirá un problema cuando un usuario intente instalar desde un servidor Web con Windows Server 2003, porque ese sistema operativo bloquea la instalación de archivos .config por razones de seguridad.  Para poder instalar el archivo .config, haga clic en **Utilizar la extensión de archivo ".deploy"** en el cuadro de diálogo **Opciones de publicación**.  
  
 También debe establecer apropiadamente los tipos de contenido \(también conocidos como tipos MIME\) para archivos .application, .manifest y .deploy.  Para obtener más información, consulte la documentación del servidor Web.  
  
 Para obtener más información, vea "Windows Server 2003: Tipos de contenido bloqueados" en [Problemas de configuración de servidor y cliente en implementaciones de ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### Mensaje de error: "La aplicación tiene un formato incorrecto"; el archivo de registro contiene "La firma XML no es válida".  
 Asegúrese de que ha actualizado el archivo de manifiesto y lo ha firmado de nuevo.  Vuelva a publicar la aplicación con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o utilice Mage para volver a firmar la aplicación.  
  
#### Se ha actualizado la aplicación en el servidor, pero el cliente no descarga la actualización.  
 Este problema puede resolverse realizando una de las siguientes tareas:  
  
-   Compruebe la dirección URL de `deploymentProvider` en el manifiesto de implementación.  Asegúrese de que está actualizando los bits en la misma ubicación a la que `deploymentProvider` señala.  
  
-   Compruebe el intervalo de actualización en el manifiesto de implementación.  Si se establece en un intervalo periódico, como una vez cada seis horas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no detectará ninguna actualización hasta que este intervalo haya pasado.  Se puede cambiar el manifiesto para que se compruebe la existencia de una actualización cada vez que se inicia la aplicación.  El cambio del intervalo de actualización es una opción muy eficaz durante el desarrollo para comprobar la instalación de actualizaciones, pero ralentiza la activación de la aplicación.  
  
-   Intente de nuevo iniciar la aplicación desde el menú Inicio.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede haber detectado la actualización en segundo plano, pero solicitará que instale los bits en la siguiente activación.  
  
#### Durante la actualización se recibe un mensaje de error con la siguiente entrada de registro: "La referencia en la implementación no coincide con la identidad definida en el manifiesto de aplicación".  
 Este error puede producirse porque se han editado manualmente los manifiestos de implementación y de aplicación, por lo que la descripción de la identidad de un ensamblado en un manifiesto no está sincronizada con la del otro manifiesto.  La identidad de un ensamblado se compone de su nombre, versión, referencia cultural y símbolo \(token\) de clave pública.  Compruebe las descripciones de identidad en los manifiestos y corrija cualquier diferencia.  
  
#### La primera activación desde el disco local o CD\-ROM es correcta, pero se genera un error en la siguiente activación desde el menú Inicio.  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza la dirección URL del proveedor de implementación para obtener las actualizaciones de la aplicación.  Compruebe que la ubicación a la que señala la dirección URL es correcta.  
  
#### Error: "No se puede iniciar la aplicación".  
 Este mensaje de error suele indicar que hay un problema al instalar esta aplicación en el almacén de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La aplicación tiene un error o el almacén está dañado.  El archivo de registro puede indicar dónde se ha producido el error.  
  
 Debe hacer lo siguiente:  
  
-   Compruebe que la identidad del manifiesto de implementación, la identidad del manifiesto de aplicación y la identidad de la aplicación principal EXE son únicas.  
  
-   Compruebe que las rutas de acceso a los archivos no contienen más de 100 caracteres.  Si la aplicación contiene rutas de acceso que son demasiado largas, puede que se superen las limitaciones en la ruta de acceso máxima que se puede almacenar.  Intente acortar las rutas de acceso e instale de nuevo.  
  
#### No se acepta la configuración PrivatePath en el archivo de configuración de la aplicación.  
 Para utilizar PrivatePath \(Fusión que busca las rutas de acceso\), la aplicación debe solicitar un permiso de plena confianza.  Pruebe a cambiar el manifiesto de aplicación de modo que se solicite plena confianza e inténtelo de nuevo.  
  
#### Durante la desinstalación, aparece el mensaje "No se pudo desinstalar la aplicación".  
 Este mensaje suele indicar que la aplicación ya se ha quitado o que el almacén está dañado.  Después de hacer clic en **Aceptar**, se quitará la entrada **Agregar o quitar programa**.  
  
#### Durante la instalación, aparece un mensaje que indica que no se han instalado las dependencias de la plataforma.  
 Falta un requisito previo en la caché global de ensamblados que la aplicación necesita para poder ejecutarse.  
  
## Publicar con Visual Studio  
  
#### Se genera un error en la publicación en Visual Studio  
 Asegúrese de que tiene derecho para publicar en el servidor al que se dirige.  Por ejemplo, si está registrado en un equipo de Terminal Server como usuario normal, no como un administrador, es probable que no tenga los derechos necesarios para publicar en el servidor Web local.  
  
 Si está publicando con una dirección URL, asegúrese de que el equipo de destino tiene habilitadas las Extensiones de servidor de FrontPage.  
  
#### Mensaje de error: No se puede crear el sitio web '\< sitio \>'.Los componentes necesarios para la comunicación con las Extensiones de servidor de FrontPage no están instalados.  
 Asegúrese de que tiene el Componente de creación web de Microsoft Visual Studio instalado en el equipo en el que está realizando la publicación.  En lo que respecta a los usuarios de la versión Express, este componente no se instala de forma predeterminada.  Para obtener más información, vea [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### mensaje de error: No encuentra el archivo “Microsoft.Windows.Common\-Controls, Version\= 6.0.0.0, Culture\=\*, PublicKeyToken\=6595b64144ccf1df, ProcessorArchitecture\=\*, Type\=win32”  
 Este mensaje de error cuando intenta publicar una aplicación WPF con estilos visuales habilitados.  para resolver este problema, vea [Cómo: Publicar una aplicación WPF con estilos visuales habilitados](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## Utilizar Mage  
  
#### Se ha intentado firmar con un certificado del almacén de certificados y aparece un cuadro de mensaje en blanco.  
 En el cuadro de diálogo **Firma**, debe:  
  
-   Seleccionar **Firmar con un certificado almacenado** y  
  
-   Seleccionar un certificado de la lista; el primer certificado no está seleccionado de manera predeterminada.  
  
#### Se produce una excepción al hacer clic en el botón "No firmar".  
 Este problema es un error conocido.  Es necesario firmar todos los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Elija una de las opciones de firma y, a continuación, haga clic en **Aceptar**.  
  
## Errores adicionales  
 En la siguiente tabla se recogen algunos mensajes de error comunes que el usuario de un equipo de cliente puede recibir al instalar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Cada mensaje de error se muestra junto con una descripción de la causa más probable del error.  
  
|Mensaje de error.|Descripción|  
|-----------------------|-----------------|  
|La aplicación no se puede iniciar.  Póngase en contacto con el editor de la aplicación.<br /><br /> No se puede iniciar la aplicación.  Póngase en contacto con el proveedor de la aplicación para obtener ayuda.|Éstos son mensajes de error genéricos que aparecen cuando no se puede iniciar la aplicación y no se encuentra ningún otro motivo más concreto.  Con frecuencia, esto significa que la aplicación está dañada de algún modo o que el almacén de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] está dañado.|  
|No se puede continuar.  La aplicación tiene un formato incorrecto.  Póngase en contacto con el editor de la aplicación para obtener ayuda.<br /><br /> La validación de la aplicación no se realizó correctamente.  No se puede continuar.<br /><br /> No se pueden recuperar los archivos de la aplicación.  Archivos dañados en la implementación.|Uno de los archivos de manifiesto de la implementación no es sintácticamente válido o contiene un hash que no puede reconciliarse con el archivo correspondiente.  Este error también puede indicar que el manifiesto se incrustó dentro de un ensamblado dañado.  Vuelva a crear la implementación y vuelva a compilar la aplicación o busque y corrija manualmente los errores en los manifiestos.|  
|No se puede recuperar la aplicación.  Error de autenticación.<br /><br /> La instalación de la aplicación no se realizó correctamente.  No se han encontrado los archivos de la aplicación en el servidor.  Póngase en contacto con el editor de la aplicación o con su administrador para obtener ayuda.|No se pueden descargar uno o varios archivos de la implementación porque no se dispone de permiso para obtener acceso a los mismos.  Esto puede deberse a un error 403 Prohibido devuelto por un servidor Web, lo que puede producirse si uno de los archivos de la implementación termina con una extensión que hace que el servidor Web lo considere como un archivo protegido.  Además, un directorio que contenga uno o varios de los archivos de la aplicación podría requerir un nombre de usuario y una contraseña para poder obtener acceso al mismo.|  
|No se puede descargar la aplicación.  La aplicación carece de los archivos necesarios.  Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|Uno o varios de los archivos que se muestran en el manifiesto de aplicación no pueden encontrarse en el servidor.  Compruebe que haya cargado todos los archivos dependientes de la implementación e inténtelo de nuevo.|  
|La descarga de la aplicación no se realizó correctamente.  Compruebe la conexión de red o póngase en contacto con el administrador del sistema o el proveedor de servicios de red.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no puede establecer una conexión de red con el servidor.  Compruebe la disponibilidad del servidor y el estado de la red.|  
|URLDownloadToCacheFile dio el error HRESULT '\<número\>'.  Error al intentar descargar '\<archivo\>'.|Si un usuario ha establecido la opción Seguridad avanzada de Internet Explorer "Avisar si se cambia entre los modos seguro y no seguro" en el equipo de destino de implementación, y si la dirección URL donde se va a instalar la aplicación ClickOnce se redirige de un sitio no seguro a un sitio seguro \(o al contrario\), se producirá un error en la instalación porque la advertencia de Internet Explorer la interrumpe.<br /><br /> Para solucionarlo, realice una de las acciones siguientes:<br /><br /> -   Borre la opción de seguridad.<br />-   Asegúrese de que la dirección URL de instalación no se redirige de manera que cambie los modos de seguridad.<br />-   Quite completamente la redirección y señale a la dirección URL de instalación real.|  
|Se ha producido un error al escribir en el disco duro.  Es posible que el espacio disponible en disco sea insuficiente.  Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|Esto puede indicar que no hay espacio en disco suficiente como para almacenar la aplicación, pero también puede indicar un error de E\/S más general al intentar guardar los archivos de la aplicación en la unidad.|  
|No se puede iniciar la aplicación.  No hay suficiente espacio disponible en disco.|El disco duro está lleno.  Libere espacio e intente ejecutar de nuevo la aplicación.|  
|Hay demasiadas activaciones implementadas intentando cargarse a la vez.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] limita el número de aplicaciones distintas que pueden iniciarse al mismo tiempo.  El objetivo principal es ayudar a protegerse frente a intentos malintencionados de instigación de ataques por denegación de servicio contra el servicio local de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]; los usuarios que intenten iniciar la misma aplicación repetidamente, en una sucesión rápida, sólo conseguirán iniciar una única instancia de la aplicación.|  
|Los accesos directos no pueden activarse a través la red.|Los accesos directos a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sólo pueden iniciarse en el disco duro local.  No pueden iniciarse abriendo una dirección URL que señale un archivo de acceso directo en un servidor remoto.|  
|La aplicación es demasiado grande como para ejecutarse en línea con confianza parcial.  Póngase en contacto con el proveedor de la aplicación o con el administrador del sistema para obtener ayuda.|Una aplicación que se ejecuta con confianza parcial no puede superar la mitad del tamaño de la cuota de aplicación en línea, que es de 250 MB de forma predeterminada.|  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)