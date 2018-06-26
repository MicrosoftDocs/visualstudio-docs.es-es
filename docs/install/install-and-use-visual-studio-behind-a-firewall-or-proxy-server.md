---
title: Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy | Microsoft Docs
description: Revise las direcciones URL de dominio, los puertos y los protocolos que quiere incluir en la lista de permitidos o abrir si la organización usa un firewall o un servidor proxy
ms.custom: ''
ms.date: 02/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2aeb7b1fc308247d5eebb810113aba1ed4afe89c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765673"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy

Si usted o su organización utiliza medidas de seguridad como un firewall o un servidor proxy, hay direcciones URL de dominio que quizá desee "incluir en una lista blanca", así como puertos y protocolos que desea abrir para tener la mejor experiencia al instalar y utilizar Visual Studio y los servicios de Azure.

* **[Instalación de Visual Studio](#install-visual-studio)**: en estas tablas se indican las direcciones URL de dominio que se van a incluir en la lista de permitidos para que tenga acceso a todos los componentes y las cargas de trabajo que desee.

* **[Uso de Visual Studio y de servicios de Azure](#use-visual-studio-and-azure-services)**: en esta tabla se indican las direcciones URL de dominio que se van a incluir en la lista blanca, así como los puertos y protocolos que se van a abrir para que tenga acceso a todas las características y servicios que desee.

## <a name="install-visual-studio"></a>Instalar Visual Studio

### <a name="urls-to-whitelist"></a>Direcciones URL para incluir en la lista blanca

Debido a que el Instalador de Visual Studio descarga archivos de varios dominios y sus servidores de descarga, aquí se muestran las direcciones URL de los dominios que pueden incluirse en la lista blanca como de confianza en la interfaz de usuario o en los scripts de implementación.

#### <a name="microsoft-domains"></a>Dominios de Microsoft

| Dominio | Propósito |
| ------ | ------- |
| go.microsoft.com | Configurar URL de resolución |
| aka.ms | Configurar URL de resolución |
| download.visualstudio.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.visualstudio.com | Configurar ubicación de descarga de los paquetes |
| dl.xamarin.com | Configurar ubicación de descarga de los paquetes |
| visualstudiogallery.msdn.microsoft.com | Ubicación de descarga de las extensiones de Visual Studio |
| www.visualstudio.com | Ubicación de la documentación |
| docs.microsoft.com | Ubicación de la documentación |
| msdn.microsoft.com | Ubicación de la documentación |
| www.microsoft.com | Ubicación de la documentación |
| *.windows.net | Ubicación de inicio de sesión |
| *.microsoftonline.com | Ubicación de inicio de sesión |
| *.live.com | Ubicación de inicio de sesión |
|  |  | |

#### <a name="non-microsoft-domains"></a>Dominios que no son de Microsoft

| Dominio | Instala estas cargas de trabajo. |
| ------ | ------- |
| archive.apache.org |  Desarrollo para dispositivos móviles con JavaScript (Cordova) |
| cocos2d-x.org | Desarrollo de juegos con C++ (Cocos) |
| download.epicgames.com | Desarrollo de juegos con C++ (Unreal Engine) |
| download.oracle.com | Desarrollo para dispositivos móviles con JavaScript (Java SDK) <br /><br />Desarrollo para dispositivos móviles con .NET (Java SDK) |
| download.unity3d.com | Desarrollo de juegos con Unity (Unity) |
| netstorage.unity3d.com | Desarrollo de juegos con Unity (Unity) |
| dl.google.com | Desarrollo para dispositivos móviles con JavaScript (emulador, NDK y SDK de Android) <br /><br />Desarrollo para dispositivos móviles con .NET (emulador, NDK y SDK de Android) |
| www.incredibuild.com | Desarrollo de juegos con C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desarrollo de juegos con C++ (IncrediBuild) |
| www.python.org | Desarrollo de Python (Python) <br /><br />Aplicaciones analíticas y de ciencia de datos (Python) |
|  |  | |

## <a name="use-visual-studio-and-azure-services"></a>Uso de Visual Studio y de servicios de Azure

### <a name="urls-to-whitelist-and-ports-and-protocols-to-open"></a>Direcciones URL para incluir en la lista blanca y puertos y protocolos para abrir

Para asegurarse de que tiene acceso a todo lo que necesita cuando utiliza Visual Studio o servicios de Azure detrás de un firewall o servidor proxy, estas son las direcciones URL que debe incluir en la lista blanca, así como los puertos y protocolos que puede querer abrir.

| Servicio o escenario | Punto de conexión DNS | Protocolo | Puerto | Description |
| --- | --- | --- | --- | --- |
| Resolución<br>dirección URL | go.microsoft.com<br><br>aka.ms | | |Se utiliza para acortar las direcciones URL que, después, se resuelven en direcciones URL más largas.
| Página de inicio | vsstartpage.blob.core.windows.net | | 443| Se utiliza para mostrar las noticias del desarrollador que aparecen en la página de inicio en Visual Studio. |
| Servicio de<br> notificación <br>dirigido | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443| Se utiliza para filtrar una lista global de notificaciones a una lista que solo se aplica a tipos específicos de máquinas/escenarios de uso. |
| Comprobación de actualización <br>de la extensión | visualstudiogallery.msdn.microsoft.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com  | | 443 | Se utiliza para proporcionar notificaciones cuando una extensión instalada tiene una actualización disponible. <br><br> Se utiliza como ubicación de inicio de sesión.|
| Integración <br>de proyectos de AI | az861674.vo.msecnd.net  | | 443<br> | Se utiliza para configurar nuevos proyectos y enviar datos de uso a su cuenta de Application Insights registrada. |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | |443 | Se utiliza para proporcionar información en el editor sobre cuándo se actualizó por última vez un archivo, la escala de tiempo de los cambios, los elementos de trabajo con los que se asocian los cambios, los creadores y mucho más.|
|Habilitación de características <br>experimentales  | visualstudio-devdiv-c2s.msedge.net | |80 | Se utiliza para activar los cambios de características o de nuevas características experimentales. |
| Distintivo de identidad <br>(nombre de usuario y avatar)<br>y <br>configuración de itinerancia | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net  | |443 | Se utiliza para mostrar el nombre del usuario y el avatar en el IDE. <br><br> Se utiliza para asegurarse de que los cambios de configuración pasan de una máquina a otra. |
| Configuración remota | az700632.vo.msecnd.net | | 443| Se utiliza para desactivar las extensiones que suelen causar problemas en Visual Studio.   |
| Herramientas de Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com |https |443 | Se usa en los escenarios de almacén de aplicaciones de Windows.  |
| Detección <br>de esquema JSON <br><br>Definición <br>de esquema JSON<br><br>Compatibilidad de <br>esquema JSON para <br>recursos de Azure| json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com| http<br>https<br><br>http<br><br>https |80<br>443 <br><br> 443<br><br>443 | Se utiliza para detectar y descargar esquemas JSON que el usuario puede emplear al editar los documentos JSON. <br><br>Se usa para obtener el esquema de validación de metadatos de JSON.<br><br>Sirve para obtener el esquema actual para las plantillas de implementación de Azure Resource Manager.|
| Detección de <br>paquetes NPM  |Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io  | https<br><br>http/s<br><br>https | 443<br><br>80/443<br><br>443| Es necesario para la búsqueda de paquetes NPM y se utiliza para la instalación del paquete de scripts de cliente en los proyectos web. |
|Iconos de<br> paquetes Bower<br><br>Búsqueda de <br>paquetes Bower  |Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https|80<br><br>443<br>80<br>443 |Proporciona el icono de paquete Bower predeterminado.  <br><br>Permite buscar paquetes Bower. |
|NuGet<br><br>Detección de<br> paquetes NuGet | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com  | https<br><br>http/s |443<br><br>80/443<br> |Se usa para comprobar paquetes NuGet firmados.<br><br>Necesario para la búsqueda de versiones y paquetes NuGet. |
|Información sobre el repositorio de GitHub  |api.github.com  |https | 443| Necesario para obtener información adicional acerca de los paquetes Bower. |
| Linter web|Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org  | http|80 | |
| Detección de<br>plantillas del explorador<br>de cookiecutter <br><br>Creación de <br>proyectos del explorador<br> de cookiecutter | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org  | https | 443<br> | Se usa para detectar plantillas en línea de nuestra fuente recomendada y de repositorios github. <br><br>Se utiliza para crear un proyecto de una plantilla de cookiecutter que requiere una única instalación a petición de un paquete Python cookiecutter desde el índice de paquetes Python (PyPI).|
| Detección de <br>paquetes Python<br><br>Administración <br>de paquetes Python<br><br>Plantillas de <br>nuevo proyecto <br>Python| pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com| https| 443| Permite buscar paquetes pip.<br><br>Se utiliza para instalar un paquete pip automáticamente si falta. <br><br> Se utiliza para crear <br><br>Se utiliza para resolver las siguiente plantillas de proyecto Python en el cuadro de diálogo Nuevo proyecto a direcciones URL de la plantilla de cookiecutter:<br> - Proyecto de clasificador<br>- Proyecto de agrupación en clústeres <br> - Proyecto de regresión <br> - PyGame con PyKinect <br> - Proyecto de Pyvot |
| Servicio <br>de comprobación <br> de manifiesto <br>para complementos <br>web de Office | verificationservice.osi.office.net | https | 443 | Se utiliza para validar los manifiestos para complementos web de Office |
| Complementos de Office <br>y SharePoint | sharepoint.com | https | 443 | Se utiliza para publicar y probar los complementos de Office y SharePoint en SharePoint Online |
| Host del servicio <br>de pruebas del<br> administrador de flujos de trabajo |  | http | 12292 | Una regla de firewall que se crea automáticamente para probar los complementos de SharePoint con los flujos de trabajo |
| Estadísticas de confiabilidad <br>automáticamente recopiladas <br>y otros <br>Programas para la mejora <br>de la experiencia del usuario (CEIP)<br> para Azure SDK y <br>herramientas de SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com |https | 443| Se usa para enviar estadísticas de confiabilidad (datos de bloqueo o de falta de respuesta) del usuario a Microsoft. Los volcados de memoria reales sobre los bloqueos o las faltas de respuesta se siguen cargando si el Informe de errores de Windows está habilitado; solo se eliminará la información estadística. <br>Se usa para revelar patrones de uso anónimos para la extensión de SDK de herramientas de Azure para Visual Studio y para los patrones de uso para el conjunto de herramientas SQL para Visual Studio |
| Programa para la mejora <br> de la experiencia del usuario (CEIP) <br>de Visual Studio <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https| 443 | Sirve para recopilar registros de error y patrones de uso anónimos. <br><br>Se utiliza para realizar el seguimiento de problemas de inmovilización de la interfaz de usuario.|
| Creación y<br>administración de <br>recursos de Azure | management.azure.com <br>management.core.windows.net   | https | 443 | Se utiliza para crear sitios web de Azure u otros recursos para admitir la publicación de aplicaciones web, instancias de Azure Functions o WebJobs. |
| Recomendaciones de <br>comprobaciones y extensión de <br>herramientas de publicación web actualizadas  | marketplace.visualstudio.com  <br> visualstudiogallery.msdn.microsoft.com  | https | 443 | Se utiliza para comprobar la disponibilidad de herramientas de publicación actualizadas. Si se deshabilita esta opción, es posible que no se muestre la posible extensión recomendada para la publicación web. |
| Información de puntos de conexión y creación <br>de recursos de Azure actualizados  | *.blob.core.windows.net | https | 443 | Se utiliza para actualizar los puntos de conexión usados para crear recursos de Azure para determinados servicios de Azure. Si está deshabilitado, se utilizan en su lugar las últimas ubicaciones del punto de conexión descargadas o integradas. |
| Depuración remota y <br>generación remota de perfiles de <br>Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Se utiliza para adjuntar el depurador remoto a Azure Websites. Si se deshabilita, no servirá adjuntar el depurador remoto a Azure Websites. |
| Grafo de <br>Active Directory | graph.windows.net | https | 443 | Se usa para aprovisionar nuevas aplicaciones de Azure Active Directory. También lo utiliza el proveedor de servicios conectados de Office 365 MSGraph. |
| Comprobación de <br>actualización de la CLI <br>de Azure Functions | functionscdn.azureedge.net | https | 443 | Se utiliza para comprobar las versiones actualizadas de la CLI de Azure Functions. Si se deshabilita, se utilizará en su lugar una copia en caché (o la copia realizada por el componente de Azure Functions) de la CLI. |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | Se utiliza HTTP para las descargas de Gradle durante la compilación; HTTPS se utiliza para incluir complementos de Cordova en los proyectos.|
| Cloud Explorer | 1. &#60;punto de conexión en clúster&#62; <br>Service Fabric <br>2. &#60;punto de conexión de administración&#62;<br>Exp. general de nube <br>3. &#60;punto de conexión del grafo&#62;<br>Exp. general de nube<br>4. &#60;punto de conexión de la cuenta de almacenamiento&#62;<br>Nodos de almacenamiento <br>5. &#60;Direcciones URL de Azure Portal&#62;<br>Exp. general de nube <br>6. &#60;puntos de conexión del almacén de claves&#62; <br>Nodos de máquinas virtuales de Azure Resource Manager<br>7. &#60;Dirección IP pública del clúster&#62;<br>Depuración remota de Service Fabric y seguimientos de ETW |   <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: tcp| 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dinámico   | 1. Ejemplo: test12.eastus.cloudapp.com<br>2. Recupera las suscripciones y recupera o administra los recursos de Azure.<br>3. Recupera las suscripciones de Azure Stack.<br>4. Administra los recursos de almacenamiento (ejemplo: mystorageaccount.blob.core.windows.net).<br>5. Opción del menú contextual "Abrir en el portal" (abre un recurso en Azure Portal).<br>6. Crea y utiliza los almacenes de claves para la depuración de máquinas virtuales (ejemplo: myvault.vault.azure.net). <br><br>7. Asigna de forma dinámica el bloque de puertos en función del número de nodos en el clúster y los puertos disponibles. <br><br>Un bloque de puertos intentará obtener tres veces el número de nodos con un mínimo de 10 puertos.<br><br>Para seguimientos de streaming, se realiza un intento de obtener el bloque de puertos de 810. Si ya se utiliza alguno de estos bloques de puertos, se realiza un intento para obtener el bloque siguiente y así sucesivamente. (Si el equilibrador de carga está vacío, lo más probable es que se usen los puertos de 810). <br><br>De forma similar que para la depuración, se reservan cuatro conjuntos de los bloques de puertos: <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- forwarderPortx86: 31399,<br>- fileUploadPort: 32398<br>|
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;servicio en la nube del usuario&#62;.cloudapp.net <br> &#60;máquina virtual del usuario&#62;.&#60;región&#62;.azure.com | 1. rdp <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6. a) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1.  Escritorio remoto para la máquina virtual de Cloud Services <br><br> 2.  Componente de la cuenta de almacenamiento de la configuración de diagnósticos privada <br><br> 3.  Azure Portal <br><br> 4. Explorador de servidores: Azure Storage& #42; es una cuenta de almacenamiento designada por el cliente  <br><br> 5.  Vínculos para abrir el portal &#47; Descarga del certificado de suscripción &#47; Archivo de configuración de publicación <br><br>6. a) Puerto local del conector para realizar la depuración remota del servicio en la nube y máquinas virtuales<br> 6. b) Puerto público del conector para la depuración remota del servicio en la nube y máquinas virtuales <br> 6. c) Puerto local de reenviador para realizar la depuración remota del servicio en la nube y máquinas virtuales <br> 6. d.) Puerto público del reenviador para la depuración remota del servicio en la nube y máquinas virtuales  <br> 6. e) Puerto local del usuario de carga de archivos para la depuración remota del servicio en la nube y máquinas virtuales <br> 6. f) Puerto público del usuario de carga de archivos para la depuración remota del servicio en la nube y máquinas virtuales |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. Documentación <br><br> 2. Creación de la característica de clúster <br><br>3. &#42; es el nombre del almacén de claves de Azure (por ejemplo: test11220180112110108.vault.azure.net)  <br><br>  4. &#42; es dinámico (por ejemplo: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Depurador de <br>instantáneas | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (dependiente de la versión de Visual Studio) | 1. Archivo .json de consulta para el tamaño de SKU del servicio de aplicación <br>2. Varias llamadas de Azure RM <br>3. Llamada de preparación de sitio  <br>4. Punto de conexión de Kudu del servicio de aplicación dirigido del cliente <br>5. Versión de la extensión de sitio de consulta publicada en nuget.org <br>6. Canal de depuración remota |
|Azure Stream Analytics <br><br>HDInsight | Management.azure.com |https|443 |Se utiliza para ver, enviar, ejecutar y administrar trabajos de ASA. <br><br> Se utiliza para examinar clústeres de HDI y para enviar, diagnosticar y depurar trabajos de HDI. |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Se utiliza para compilar, enviar, ver, diagnosticar y depurar trabajos; también para examinar archivos ADLS, y para cargar y descargar archivos. |
|Servicio de empaquetado | [cuenta].visualstudio.com <br/> [cuenta].*.visualstudio.com <br/> *.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | *.npmjs.org, *.nuget.org y *.nodejs.org solo son necesarios para determinados escenarios de tareas de compilación (por ejemplo, el Instalador de la herramienta NuGet o el Instalador de herramientas de nodo) o si se van a usar canales de subida públicos con las fuentes. Los otros tres dominios son necesarios para la funcionalidad principal del servicio de empaquetado. |
|||||||

## <a name="troubleshoot-network-related-errors"></a>Solución de problemas de errores relacionados con la red

A veces, es posible que se ejecuten errores relacionados con la red o con el proxy cuando se instala o se utiliza Visual Studio detrás de un firewall o de un servidor proxy. Para más información sobre las soluciones de dichos mensajes de error, consulte la página [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Obtener soporte técnico

Aquí tiene algunas opciones más de soporte técnico:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Solución de problemas de errores relacionados con la red en Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)

