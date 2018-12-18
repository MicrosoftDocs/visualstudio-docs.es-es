---
title: Seguridad e implementación ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd089b57fb50d20c8805c932b0043bb8c0dba82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926454"
---
# <a name="clickonce-security-and-deployment"></a>Seguridad e implementación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es una tecnología de implementación que le permite crear aplicaciones de actualización automática basado en Windows que se pueden instalar y ejecutar con interacción mínima del usuario. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona compatibilidad completa para publicar y actualizar las aplicaciones implementadas con la tecnología ClickOnce si ha desarrollado sus proyectos con Visual Basic y Visual C#. Para obtener información sobre cómo implementar aplicaciones de Visual C++, vea [implementación de ClickOnce para aplicaciones de Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la implementación supera tres problemas principales de implementación:  
  
- **Dificultades para actualizar las aplicaciones.** Con la implementación de Microsoft Windows Installer, siempre que se actualiza una aplicación, el usuario puede instalar una actualización, un archivo msp y se aplican para el producto instalado; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación, puede proporcionar actualizaciones automáticamente. Se descargan sólo aquellas partes de la aplicación que han cambiado y, a continuación, se vuelve a instalar la aplicación completa y actualizada de una nueva carpeta en paralelo.  
  
- **Impacto en el equipo del usuario.** Con la implementación de Windows Installer, las aplicaciones normalmente utilizan componentes compartidos, con la posibilidad de conflictos de control de versiones; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación, cada aplicación es independiente y no interfiere con otras aplicaciones.  
  
- **Permisos de seguridad.** Implementación de Windows Installer requiere permisos administrativos y permite sólo la instalación de usuario limitada; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación permite a los usuarios sin derechos administrativos instalar y concede sólo los permisos de seguridad de acceso del código necesarios para la aplicación.  
  
  En el pasado, estos problemas causados a veces, los desarrolladores a crear aplicaciones Web en lugar de aplicaciones basadas en Windows, tener que sacrificar una interfaz de usuario enriquecida para facilitar la instalación. Mediante el uso de las aplicaciones implementadas mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], puede tener el mejor de ambas tecnologías.  
  
## <a name="what-is-a-clickonce-application"></a>¿Qué es una aplicación ClickOnce?  
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación es cualquier Windows Presentation Foundation (*.xbap*), Windows Forms (*.exe*), aplicación de consola (*.exe*), o una solución de Office (*.dll*) publicada utilizando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnología. Puede publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación de tres maneras diferentes: desde una página Web, desde un recurso compartido de red o desde medios, como un CD-ROM. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación puede ser instalada en el equipo de un usuario final y ejecutar localmente incluso cuando el equipo está sin conexión o se puede ejecutar en un modo de solo en línea sin instalar nada de forma permanente en el equipo del usuario final. Para obtener más información, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones se pueden actualizar automáticamente; se buscan versiones más recientes cuando estén disponibles y reemplazar automáticamente los archivos actualizados. El desarrollador puede especificar el comportamiento de actualización; También puede controlar un administrador de red estrategias de actualización, por ejemplo, marcar una actualización como obligatoria. Las actualizaciones también se revierte a una versión anterior por el usuario final o un administrador. Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Dado que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones están aisladas, instalar o ejecutar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación no puede interrumpir las aplicaciones existentes. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones son independientes; cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se instala para y ejecutar desde un seguro caché por usuario, por aplicación. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones se ejecutan en las zonas de seguridad de Internet o Intranet. Si es necesario, la aplicación puede solicitar permisos de seguridad con privilegios elevados. Para obtener más información, consulte [aplicaciones ClickOnce Secure](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Cómo funciona la seguridad de ClickOnce  
 El núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se basa en certificados, las directivas de seguridad de acceso de código y el aviso de confianza de ClickOnce.  
  
### <a name="certificates"></a>Certificados  
 Certificados de Authenticode se usan para comprobar la autenticidad del publicador de la aplicación. Mediante el uso de Authenticode para la implementación de la aplicación, ClickOnce le ayuda a impedir que un programa dañino creado por presente como un programa legítimo procedente de una fuente de confianza establecida. Si lo desea, también se pueden usar certificados para firmar la aplicación y los manifiestos de implementación para demostrar que los archivos no se han alterado. Para obtener más información, consulte [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Los certificados también pueden utilizarse para configurar equipos cliente para tener una lista de editores de confianza. Si una aplicación procede de un editor de confianza, se puede instalar sin ninguna interacción del usuario. Para obtener más información, consulte [información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Seguridad de acceso del código  
 Secrity de acceso del código ayuda a limitar el acceso del código a los recursos protegidos. En la mayoría de los casos, puede elegir las zonas de Internet o Intranet Local para limitar los permisos. Use la **seguridad** página en el **ProjectDesigner** para solicitar la zona correspondiente a la aplicación. También puede depurar las aplicaciones con permisos restringidos para emular la experiencia del usuario final. Para más información, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Aviso de confianza de ClickOnce  
 Si la aplicación solicita más permisos que permite que la zona, se puede solicitar al usuario final para tomar una decisión de confianza. El usuario final puede decidir si las aplicaciones ClickOnce, como las aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, las aplicaciones de consola, aplicaciones de explorador XAML y soluciones de Office son de confianza. Para obtener más información, consulte [Cómo: configurar el comportamiento del mensaje de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Cómo funciona la implementación de ClickOnce  
 El núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquitectura de implementación se basa en dos archivos de manifiesto XML: un manifiesto de aplicación y un manifiesto de implementación. Los archivos se utilizan para describir dónde se instalan las aplicaciones ClickOnce desde, cómo se actualizan y cuando se actualizan.  
  
### <a name="publish-clickonce-applications"></a>Publicar aplicaciones ClickOnce  
 El manifiesto de aplicación describe la propia aplicación. Esto incluye los ensamblados, las dependencias y los archivos que componen la aplicación, los permisos necesarios y la ubicación dónde estarán disponibles las actualizaciones. El desarrollador de aplicaciones crea el manifiesto de aplicación mediante el Asistente para publicar en Visual Studio o Manifest Generation and Editing Tool (*Mage.exe*) en el [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 El manifiesto de implementación describe cómo se implementa la aplicación. Esto incluye la ubicación del manifiesto de aplicación y la versión de la aplicación que los clientes deben ejecutar.  
  
### <a name="deploy-clickonce-applications"></a>Implementar aplicaciones con ClickOnce  
 Después de crearlo, el manifiesto de implementación se copia en la ubicación de implementación. Puede tratarse de un servidor Web, recurso compartido de red o medios como un CD. El manifiesto de aplicación y todos los archivos de aplicación también se copian en una ubicación de implementación que se especifica en el manifiesto de implementación. Esto puede ser la misma que la ubicación de implementación, o puede ser una ubicación diferente. Cuando se usa el **Asistente para publicación** en Visual Studio, las operaciones de copia se realizan automáticamente.  
  
### <a name="install-clickonce-applications"></a>Instalar las aplicaciones ClickOnce  
 Una vez que se implementa en la ubicación de implementación, los usuarios finales puede descargar e instalar la aplicación, haga clic en un icono que representa el archivo de manifiesto de implementación en una página Web o en una carpeta. En la mayoría de los casos, el usuario final se presentará un cuadro de diálogo simple que pide al usuario que confirme la instalación, tras el cual la instalación continúa y la aplicación se inicia sin intervención adicional. En casos donde la aplicación requiere permisos elevados o si la aplicación no está firmada por un certificado de confianza, el cuadro de diálogo también le pide al usuario que conceda permiso para que pueda continuar la instalación. Aunque las instalaciones de ClickOnce son por usuario, puede requerir elevación de permisos si hay requisitos previos que requieren privilegios de administrador. Para obtener más información sobre permisos elevados, consulte [aplicaciones ClickOnce protección](../deployment/securing-clickonce-applications.md).  
  
 Los certificados se pueden confiar en el nivel de equipo o de empresa, para que las aplicaciones ClickOnce firmadas con un certificado de confianza se pueden instalar en modo silencioso. Para obtener más información acerca de los certificados de confianza, consulte [información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
 Se puede agregar la aplicación para el usuario **iniciar** menú y a la **agregar o quitar programas** grupo en el **Panel de Control**. A diferencia de otras tecnologías de implementación, se agrega nada a la **archivos de programa** carpeta o el registro y sin derechos administrativos son necesarios para la instalación  
  
> [!NOTE]
>  También es posible impedir que la aplicación que se va a agregar a la **iniciar** menú y **agregar o quitar programas** grupo, en efecto lo que se comportan como una aplicación Web. Para obtener más información, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="update-clickonce-applications"></a>Actualizar las aplicaciones ClickOnce  
 Cuando los desarrolladores de aplicaciones crean una versión actualizada de la aplicación, genera un nuevo manifiesto de aplicación y copiar archivos en una ubicación de implementación, normalmente una carpeta del mismo nivel en la carpeta de implementación de aplicación original. El administrador actualiza el manifiesto de implementación para que apunte a la ubicación de la nueva versión de la aplicación.  
  
> [!NOTE]
>  El **Asistente para publicación** en Visual Studio puede utilizarse para realizar estos pasos.  
  
 Además de la ubicación de implementación, el manifiesto de implementación también contiene una ubicación de actualización (una página Web o red recurso compartido de archivos), donde la aplicación comprueba las versiones actualizadas. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publicar** propiedades se utilizan para especificar cuándo y con qué frecuencia debe buscar actualizaciones la aplicación. Se puede especificar el comportamiento de actualización en el manifiesto de implementación, o se puede presentar como opciones del usuario en la interfaz de usuario de la aplicación por medio de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API. Además, **publicar** propiedades se pueden emplear para realizar las actualizaciones obligatorias o revertir a una versión anterior. Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instaladores de terceros  
 Puede personalizar el instalador de ClickOnce para instalar componentes de terceros junto con la aplicación. Debe tener el paquete redistribuible (archivo .exe o .msi) y describen el paquete con un manifiesto de producto independiente del idioma y un manifiesto del paquete de idioma específico. Para obtener más información, consulte [crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Herramientas de ClickOnce  
 La siguiente tabla muestra las herramientas que puede usar para generar, editar, inicie sesión y volver a firmar los manifiestos de aplicación e implementación.  
  
|Herramienta|Descripción|  
|----------|-----------------|  
|[Página Seguridad, Diseñador de proyectos](../ide/reference/security-page-project-designer.md)|Signos de los manifiestos de aplicación e implementación.|  
|[Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)|Genera y edita los manifiestos de aplicación e implementación de aplicaciones de Visual Basic y Visual C#.|  
|[*Mage.exe* (generación y la herramienta de edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Genera los manifiestos de aplicación e implementación de aplicaciones de Visual Basic, Visual C# y Visual C++.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde scripts por lotes y el símbolo del sistema.|  
|[*MageUI.exe* (manifiestos de generación y edición Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Genera y edita los manifiestos de aplicación e implementación.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.|  
|[GenerateApplicationManifest (Tarea)](../msbuild/generateapplicationmanifest-task.md)|Genera el manifiesto de aplicación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarea GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Genera el manifiesto de implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[SignFile (Tarea)](../msbuild/signfile-task.md)|Signos de los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desarrolle su propia aplicación para generar los manifiestos de aplicación e implementación.|  
  
 En la tabla siguiente se muestra la versión de .NET Framework necesaria para admitir las aplicaciones ClickOnce en estos exploradores.  
  
|Explorador|Versión de .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1 DE, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Vea también  
 [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implementar componentes COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilar aplicaciones ClickOnce desde la línea de comandos](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)