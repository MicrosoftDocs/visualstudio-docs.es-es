---
title: Instalación y uso detrás de un firewall o proxy
description: Revise las direcciones URL de dominio, los puertos y los protocolos que quiera incluir en una lista de permitidas o abrir si la organización usa un firewall o un servidor proxy
ms.date: 06/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 09340940796e20f679c3c9bbad3d55880b25ab7a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283481"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy

Si usted o la organización usa medidas de seguridad como un firewall o un servidor proxy, hay direcciones URL de dominio que quizá quiera agregar a una "lista de permitidas", así como puertos y protocolos que quiera abrir para tener la mejor experiencia posible a la hora de instalar y usar Visual Studio y los servicios de Azure.

* **[Instalación de Visual Studio](#install-visual-studio)** : en estas tablas se incluyen las direcciones URL de dominio que se van a agregar a una lista de permitidas para que tenga acceso a todos los componentes y las cargas de trabajo que quiera.

* **[Uso de Visual Studio y de servicios de Azure](#use-visual-studio-and-azure-services)** : en esta tabla se incluyen las direcciones URL de dominio que se van a agregar a una lista de permitidas, así como los puertos y protocolos que se van a abrir para que tenga acceso a todas las características y los servicios que quiera.

> [!NOTE]
> Este artículo se ha escrito para Visual Studio en Windows, pero alguna información también se aplica a la [Instalación de Visual Studio para Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) detrás de un servidor proxy o firewall.

## <a name="install-visual-studio"></a>Instalar Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>Direcciones URL que se van a agregar a una lista de permitidas

Debido a que el Instalador de Visual Studio descarga archivos de varios dominios y sus servidores de descarga, estas son las direcciones URL de dominio que debe agregar a una lista de permitidas como de confianza en la interfaz de usuario o en los scripts de implementación.

#### <a name="microsoft-domains"></a>Dominios de Microsoft

| Dominio | Propósito |
| - | - |
| go.microsoft.com | Configurar URL de resolución |
| aka.ms | Configurar URL de resolución |
| download.visualstudio.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.microsoft.com | Configurar ubicación de descarga de los paquetes |
| download.visualstudio.com | Configurar ubicación de descarga de los paquetes |
| dl.xamarin.com | Configurar ubicación de descarga de los paquetes |
| xamarin-downloads.azureedge.net | Ubicación de la lista de descarga de paquetes de Android SDK |
| marketplace.visualstudio.com | Ubicación de descarga de las extensiones de Visual Studio |
| \*.gallerycdn.vsassets.io  | Ubicación de descarga de las extensiones de Visual Studio |
| visualstudio.microsoft.com | Ubicación de la documentación |
| docs.microsoft.com | Ubicación de la documentación |
| msdn.microsoft.com | Ubicación de la documentación |
| www\.microsoft.com | Ubicación de la documentación |
| \*.windows.net | Ubicación de inicio de sesión |
| \*.microsoftonline.com | Ubicación de inicio de sesión |
| \*.live.com | Ubicación de inicio de sesión |
| | |

#### <a name="non-microsoft-domains"></a>Dominios que no son de Microsoft

| Dominio | Instala estas cargas de trabajo. |
| - | - |
| archive.apache.org | Desarrollo para dispositivos móviles con JavaScript (Cordova) |
| cocos2d-x.org | Desarrollo de juegos con C++ (Cocos) |
| download.epicgames.com | Desarrollo de juegos con C++ (Unreal Engine) |
| download.oracle.com | Desarrollo para dispositivos móviles con JavaScript (Java SDK) <br /><br />Desarrollo para dispositivos móviles con .NET (Java SDK) |
| download.unity3d.com | Desarrollo de juegos con Unity (Unity) |
| netstorage.unity3d.com | Desarrollo de juegos con Unity (Unity) |
| dl.google.com | Desarrollo para dispositivos móviles con JavaScript (emulador, NDK y SDK de Android) <br /><br />Desarrollo para dispositivos móviles con .NET (emulador, NDK y SDK de Android) |
| www\.incredibuild.com | Desarrollo de juegos con C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desarrollo de juegos con C++ (IncrediBuild) |
| www\.python.org | Desarrollo de Python (Python) <br /><br />Aplicaciones analíticas y de ciencia de datos (Python) |
| developerservices2.apple.com | Aprovisionamiento de Xamarin.iOS |
| developer.apple.com | Aprovisionamiento de Xamarin.iOS |
| appstoreconnect.apple.com | Aprovisionamiento de Xamarin.iOS |
| idmsa.apple.com | Aprovisionamiento de Xamarin.iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Uso de Visual Studio y de servicios de Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Direcciones URL que se van a incluir en una lista de permitidas y puertos y protocolos que se van a abrir

Para asegurarse de que tiene acceso a todo lo que quiere cuando usa Visual Studio o los servicios de Azure detrás de un firewall o servidor proxy, estas son las direcciones URL que debe agregar a una lista de permitidas y los puertos y protocolos que debe abrir.

| Servicio o escenario | Punto de conexión DNS | Protocolo<br/>/Port | Descripción |
| - | - | -: | - | - |
| Resolución<br>dirección URL | go.microsoft.com<br><br>aka.ms | | Se utiliza para acortar las direcciones URL que, después, se resuelven en direcciones URL más largas. |
| Página de inicio | vsstartpage.blob.core.windows.net | 443 | Se utiliza para mostrar las noticias del desarrollador que aparecen en la página de inicio (solo en Visual Studio 2017). |
| Servicio de<br> notificación <br>web de Office | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Se utiliza para filtrar una lista global de notificaciones a una lista que solo se aplica a tipos específicos de máquinas/escenarios de uso. |
| Comprobación de actualización <br>de la extensión | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Se utiliza para proporcionar notificaciones cuando una extensión instalada tiene una actualización disponible. <br><br> Se utiliza como ubicación de inicio de sesión. |
| Integración <br>de proyectos de AI | az861674.vo.msecnd.net | 443<br> | Se utiliza para configurar nuevos proyectos y enviar datos de uso a su cuenta de Application Insights registrada. |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Se utiliza para proporcionar información en el editor sobre cuándo se actualizó por última vez un archivo, la escala de tiempo de los cambios, los elementos de trabajo con los que se asocian los cambios, los creadores y mucho más. |
| Habilitación de características <br>experimentales | visualstudio-devdiv-c2s.msedge.net | 80 | Se utiliza para activar los cambios de características o de nuevas características experimentales. |
| "Distintivo" de identidad <br>(nombre de usuario y avatar)<br>y <br>configuración de itinerancia | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Se utiliza para mostrar el nombre del usuario y el avatar en el IDE. <br><br> Se utiliza para asegurarse de que los cambios de configuración pasan de una máquina a otra. |
| Configuración remota | az700632.vo.msecnd.net | 443 | Se utiliza para desactivar las extensiones que suelen causar problemas en Visual Studio. |
| Herramientas de Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Se usa en los escenarios de almacén de aplicaciones de Windows. |
| Detección <br>de esquema JSON <br><br>Definición <br>de esquema JSON<br><br>Compatibilidad de <br>esquema JSON para <br>recursos de Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Se utiliza para detectar y descargar esquemas JSON que el usuario puede emplear al editar los documentos JSON. <br><br>Se usa para obtener el esquema de validación de metadatos de JSON.<br><br>Sirve para obtener el esquema actual para las plantillas de implementación de Azure Resource Manager. |
| Detección de <br>paquetes NPM | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Es necesario para la búsqueda de paquetes NPM y se utiliza para la instalación del paquete de scripts de cliente en los proyectos web. |
| Iconos de<br> paquetes Bower<br><br>Búsqueda de <br>paquetes Bower | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Proporciona el icono de paquete Bower predeterminado.  <br><br>Permite buscar paquetes Bower. |
| NuGet<br><br>Detección de<br> paquetes Python | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Se usa para comprobar paquetes NuGet firmados.<br><br>Necesario para la búsqueda de versiones y paquetes NuGet. |
| Información sobre el repositorio de GitHub | api.github.com | https/443 | Necesario para obtener información adicional acerca de los paquetes Bower. |
| Linter web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Creación de<br>plantillas del explorador<br>de cookiecutter <br><br>Creación de <br>proyectos del explorador<br> de cookiecutter | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Se usa para detectar plantillas en línea de nuestra fuente recomendada y de repositorios GitHub. <br><br>Se utiliza para crear un proyecto de una plantilla de cookiecutter que requiere una única instalación a petición de un paquete Python cookiecutter desde el índice de paquetes Python (PyPI). |
| Detección de <br>paquetes Python<br><br>Administración <br>de paquetes Python<br><br>Nuevo <br>Python <br> proyecto <br>Python | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Permite buscar paquetes pip.<br><br>Se utiliza para instalar un paquete pip automáticamente si falta. <br><br>Se utiliza para resolver las siguiente plantillas de proyecto de Python en direcciones URL de la plantilla de Cookiecutter:<br> - Proyecto de clasificador<br>- Proyecto de agrupación en clústeres <br> - Proyecto de regresión <br> - PyGame con PyKinect <br> - Proyecto de Pyvot |
| Servicio <br>de comprobación <br> de manifiesto <br>para complementos <br>web de Office | verificationservice.osi.office.net | https/443 | Se utiliza para validar los manifiestos para complementos web de Office |
| Complementos de Office <br>y SharePoint | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Se usa para publicar y probar los complementos de Office y SharePoint en SharePoint Online y Office 365. |
| Host del servicio <br>de pruebas del<br> administrador de flujos de trabajo | | http/12292 | Una regla de firewall que se crea automáticamente para probar los complementos de SharePoint con los flujos de trabajo |
| Estadísticas de confiabilidad <br>automáticamente recopiladas <br>y otros <br>Programas para la mejora <br>de la experiencia del usuario (CEIP)<br> para Azure SDK y <br>herramientas de SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Se usa para enviar estadísticas de confiabilidad (datos de bloqueo o de falta de respuesta) del usuario a Microsoft. Los volcados de memoria reales sobre los bloqueos o las faltas de respuesta se siguen cargando si el Informe de errores de Windows está habilitado; solo se eliminará la información estadística. <br>Se usa para revelar patrones de uso anónimos para la extensión de SDK de herramientas de Azure para Visual Studio y para los patrones de uso para el conjunto de herramientas SQL para Visual Studio |
| Programa para la mejora <br> de la experiencia del usuario (CEIP) <br>de Visual Studio <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Sirve para recopilar registros de error y patrones de uso anónimos. <br><br>Se utiliza para realizar el seguimiento de problemas de inmovilización de la interfaz de usuario. |
| Creación y<br>administración de <br>recursos de Azure | management.azure.com <br>management.core.windows.net | https/443 | Se utiliza para crear sitios web de Azure u otros recursos para admitir la publicación de aplicaciones web, instancias de Azure Functions o WebJobs. |
| Recomendaciones de <br>comprobaciones y extensión de <br>herramientas de publicación web actualizadas | marketplace.visualstudio.com | https/443 | Se utiliza para comprobar la disponibilidad de herramientas de publicación actualizadas. Si se deshabilita esta opción, es posible que no se muestre la posible extensión recomendada para la publicación web. |
| Información de puntos de conexión y creación <br>de recursos de Azure actualizados | \*.blob.core.windows.net | https/443 | Se utiliza para actualizar los puntos de conexión usados para crear recursos de Azure para determinados servicios de Azure. Si está deshabilitado, se utilizan en su lugar las últimas ubicaciones del punto de conexión descargadas o integradas. |
| Depuración remota y <br>generación remota de perfiles de <br>Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Se utiliza para adjuntar el depurador remoto a Azure Websites. Si se deshabilita, no servirá adjuntar el depurador remoto a Azure Websites. |
| Grafo de <br>Active Directory | graph.windows.net | https/443 | Se usa para aprovisionar nuevas aplicaciones de Azure Active Directory. También lo utiliza el proveedor de servicios conectados de Office 365 MSGraph. |
| Comprobación de <br>actualización de la CLI <br>de Azure Functions | functionscdn.azureedge.net | https/443 | Se utiliza para comprobar las versiones actualizadas de la CLI de Azure Functions. Si se deshabilita, se utilizará en su lugar una copia en caché (o la copia realizada por el componente de Azure Functions) de la CLI. |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | Se utiliza HTTP para las descargas de Gradle durante la compilación; HTTPS se utiliza para incluir complementos de Cordova en los proyectos. |
| Cloud Explorer | 1. &#60;punto de conexión en clúster&#62; <br>Service Fabric <br>2. &#60;punto de conexión de administración&#62;<br>Exp. general de nube <br>3. &#60;punto de conexión del grafo&#62;<br>Exp. general de nube<br>4. &#60;punto de conexión de la cuenta de almacenamiento&#62;<br>Nodos de almacenamiento <br>5. &#60;Direcciones URL de Azure Portal&#62;<br>Exp. general de nube <br>6. &#60;puntos de conexión del almacén de claves&#62; <br>Nodos de máquinas virtuales de Azure Resource Manager<br>7. &#60;Dirección IP pública del clúster&#62;<br>Depuración remota de Service Fabric y seguimientos de ETW | <br>1. https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7. tcp/dynamic | 1. Ejemplo: test12.eastus.cloudapp.com<br>2. Recupera las suscripciones y recupera o administra los recursos de Azure.<br>3. Recupera las suscripciones de Azure Stack.<br>4. Administra los recursos de almacenamiento (ejemplo: mystorageaccount.blob.core.windows.net).<br>5. Opción del menú contextual "Abrir en el portal" (abre un recurso en Azure Portal).<br>6. Crea y utiliza los almacenes de claves para la depuración de máquinas virtuales (ejemplo: myvault.vault.azure.net). <br><br>7. Asigna de forma dinámica el bloque de puertos en función del número de nodos en el clúster y los puertos disponibles. <br><br>Un bloque de puertos intentará obtener tres veces el número de nodos con un mínimo de 10 puertos.<br><br>Para seguimientos de streaming, se realiza un intento de obtener el bloque de puertos de 810. Si ya se utiliza alguno de estos bloques de puertos, se realiza un intento para obtener el bloque siguiente y así sucesivamente. (Si el equilibrador de carga está vacío, lo más probable es que se usen los puertos de 810). <br><br>De forma similar que para la depuración, se reservan cuatro conjuntos de los bloques de puertos: <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- forwarderPortx86: 31399,<br>- fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;servicio en la nube del usuario&#62;.cloudapp.net <br> &#60;máquina virtual del usuario&#62;.&#60;región&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1.  Escritorio remoto para la máquina virtual de Cloud Services <br><br> 2.  Componente de la cuenta de almacenamiento de la configuración de diagnósticos privada <br><br> 3.  Azure Portal <br><br> 4. Explorador de servidores: Azure Storage &#42; es una cuenta de almacenamiento designada por el cliente  <br><br> 5.  Vínculos para abrir el portal &#47; Descarga del certificado de suscripción &#47; Archivo de configuración de publicación <br><br>6. a) Puerto local del conector para realizar la depuración remota del servicio en la nube y máquinas virtuales<br> 6. b) Puerto público del conector para la depuración remota del servicio en la nube y máquinas virtuales <br> 6. c) Puerto local de reenviador para realizar la depuración remota del servicio en la nube y máquinas virtuales <br> 6. d.) Puerto público del reenviador para la depuración remota del servicio en la nube y máquinas virtuales  <br> 6. e) Puerto local del usuario de carga de archivos para la depuración remota del servicio en la nube y máquinas virtuales <br> 6. f) Puerto público del usuario de carga de archivos para la depuración remota del servicio en la nube y máquinas virtuales |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Documentación <br><br> 2. Creación de la característica de clúster <br><br>3. &#42; es el nombre del almacén de claves de Azure (por ejemplo: test11220180112110108.vault.azure.net)  <br><br>  4. &#42; es dinámico (por ejemplo: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Depurador de <br>instantáneas | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Dirección IP/FQDN de servidores/servicios remotos | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022 (dependiente de la versión de Visual Studio) | 1. Archivo .json de consulta para el tamaño de SKU del servicio de aplicación <br>2. Varias llamadas de Azure RM <br>3. Llamada de preparación de sitio  <br>4. Punto de conexión de Kudu del servicio de aplicación dirigido del cliente <br>5. Versión de la extensión de sitio de consulta publicada en nuget.org <br>6. [Depuración remota](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | Se utiliza para ver, enviar, ejecutar y administrar trabajos de ASA. <br><br> Se utiliza para examinar clústeres de HDI y para enviar, diagnosticar y depurar trabajos de HDI. |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Se utiliza para compilar, enviar, ver, diagnosticar y depurar trabajos; también para examinar archivos ADLS, y para cargar y descargar archivos. |
| Servicio de empaquetado | [cuenta].visualstudio.com <br/> [cuenta].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | \*.npmjs.org, \*.nuget.org y \*.nodejs.org solo son necesarios para determinados escenarios de tareas de compilación (por ejemplo: Instalador de la herramienta NuGet, Instalador de la herramienta Node) o si piensa usar orígenes ascendentes públicos con las fuentes. Los otros tres dominios son necesarios para la funcionalidad principal del servicio de empaquetado. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Usado para conectar con Azure DevOps Services |
| Azure Service Bus | \*.servicebus.windows.net | ampq/5671 y 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Se usa para crear las colas, los temas y las suscripciones. </br> También se usa para enviar/recibir mensajes a/de temas y colas de Service Bus. |
| Azure Cosmos DB | \*.documents.azure.com | https/443 | Se usa para llamar a las API de base de datos de documentos principales. |
| Comunidad de desarrolladores | sendvsfeedback2.azurewebsites.net/api | https/443 | Se usa para llamar a las API de la herramienta de comentarios de la comunidad de desarrolladores (mis problemas, buscar, votar, comentario, enviar, cargar, reanudar). |
| IntelliCode | \*.intellicode.vsengsaas.visualstudio.com | https/443 | Se usa para llamar a las API de IntelliCode. |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 | Se usa para llamar a las API de Live Share. |
| Visual Studio Codespaces | \*.online.visualstudio.com | https/443 | Se usa para llamar a las API de Visual Studio Codespaces. |
| Adquisición automática de tipos de JavaScript | registry.npmjs.org | https/443 | Se usa para instalar definiciones de tipos de TypeScript con el fin de proporcionar IntelliSense para las bibliotecas de JavaScript más populares. |
| Servicio de licencias de suscripciones de Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licensing/ClientRights | https/443 | Licencias para la activación en línea |
| instantáneas | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon.\*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Se usa para descargar bits del depurador para la depuración de .NET Core en Unix o macOS a través de SSH. <br><br>2. <br>Se usa para descargar bits del depurador para la depuración remota de contenedores de Docker de Windows.<br><br> 3. Se usa para la ejecución paso a paso de código fuente de .NET Framework. <br><br> 4. <br>(Si el usuario opta por participar) Se usa para descargar símbolos publicados en el servidor de símbolos de nuget.org.<br><br> 5. (Si el usuario opta por participar) Se usa para descargar símbolos y archivos binarios de MS; es posible que también se necesite para depurar código administrado en volcados de memoria. |
| Visual Studio Codespaces| \*.online.visualstudio.com | https/443 | Se usa para llamar a las API de Visual Studio Codespaces. |
| Publicación de aplicaciones de Xamarin Android | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Se usa para interactuar con el servicio Google Play Store para publicar o cargar aplicaciones de Xamarin Android directamente desde Visual Studio. |
| Azure Container Registry | *.azurecr.io | https/443 | Acceso a los registros de contenedores hospedados en Azure, para la configuración de canalizaciones de CI/CD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Solución de problemas de errores relacionados con la red

A veces, es posible que se ejecuten errores relacionados con la red o con el proxy cuando se instala o se utiliza Visual Studio detrás de un firewall o de un servidor proxy. Para más información sobre las soluciones de dichos mensajes de error, consulte la página [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Obtener soporte técnico

Se ofrece una opción de soporte técnico de [**chat de instalación**](https://visualstudio.microsoft.com/vs/support/#talktous) para incidencias relacionadas con la instalación (solo en inglés).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md) que aparece en el instalador y en el IDE de Visual Studio.
* Sugiera una característica, realice el seguimiento de los problemas del producto y encuentre respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* Finalmente, puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio) usando su cuenta de [GitHub](https://github.com/).

## <a name="see-also"></a>Vea también

* [Requisitos de conectividad de Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Solución de problemas de errores relacionados con la red en Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Instalación y uso de Visual Studio para Mac detrás de un firewall o servidor proxy](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
