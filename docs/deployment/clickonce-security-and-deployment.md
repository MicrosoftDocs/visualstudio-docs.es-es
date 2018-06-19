---
title: Seguridad e implementación ClickOnce | Documentos de Microsoft
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
ms.openlocfilehash: 4ec2e74623c39640517ae73786d7865143bf1505
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562837"
---
# <a name="clickonce-security-and-deployment"></a>Seguridad e implementación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es una tecnología de implementación que le permite crear auto-actualización aplicaciones basadas en Windows que se pueden instalar y ejecutar con interacción mínima del usuario. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona compatibilidad completa para publicar y actualizar las aplicaciones implementadas con tecnología ClickOnce si ha desarrollado los proyectos con Visual Basic y Visual C#. Para obtener información sobre cómo implementar aplicaciones de Visual C++, vea [implementación de ClickOnce para aplicaciones de Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la implementación supera tres problemas importantes de implementación:  
  
-   **Dificultades para actualizar las aplicaciones.** Con la implementación de Microsoft Windows Installer, siempre que se actualiza una aplicación, el usuario puede instalar una actualización, un archivo msp y aplicarlo al producto instalado; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación, puede proporcionar actualizaciones automáticamente. Se descargan solo aquellas partes de la aplicación que han cambiado y, a continuación, se vuelve a instalar la aplicación completa y actualizada de una nueva carpeta en paralelo.  
  
-   **Impacto en el equipo del usuario.** Con la implementación de Windows Installer, las aplicaciones normalmente utilizan componentes compartidos, con la posibilidad de conflictos de versiones; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación, cada aplicación es independiente y no puede interferir con otras aplicaciones.  
  
-   **Permisos de seguridad.** Implementación de Windows Installer requiere permisos administrativos y permite solo la instalación de usuario limitada; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación permite a los usuarios no administrativos instalar y concede sólo los permisos de seguridad de acceso del código necesarios para la aplicación.  
  
 En el pasado, estos problemas deben en ocasiones a los desarrolladores decidir crear aplicaciones Web en lugar de aplicaciones basadas en Windows, renunciar a una interfaz de usuario enriquecida para facilitar la instalación. Mediante el uso de las aplicaciones implementadas mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], puede aprovechar lo mejor de ambas tecnologías.  
  
## <a name="what-is-a-clickonce-application"></a>¿Qué es una aplicación ClickOnce?  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación es cualquier Windows Presentation Foundation (XBAP), Windows Forms (.exe), aplicación de consola (.exe) o solución de Office (.dll) publicada mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnología. Puede publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación de tres maneras diferentes: desde una página Web, desde un recurso compartido de red o desde medios, como un CD-ROM. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se puede instalar en el equipo de un usuario final y ejecutarse localmente incluso cuando el equipo está sin conexión o se puede ejecutar en un modo solo en línea sin instalar nada de manera permanente en el equipo del usuario final. Para más información, consulte el artículo [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones se pueden actualizar automáticamente; puede comprobar si hay nuevas versiones cuando estén disponibles y reemplazar automáticamente los archivos actualizados. El desarrollador puede especificar el comportamiento de actualización; un administrador de red puede controlar estrategias de actualización, por ejemplo, marcando una actualización como obligatoria. Las actualizaciones también se revierte a una versión anterior que el usuario final o un administrador. Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Dado que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones están aisladas, instalar o ejecutar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación no puede interrumpir las aplicaciones existentes. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones son independientes; cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se instala para y ejecutar desde un seguro caché por usuario, según la aplicación. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones que se ejecutan en las zonas de seguridad de Internet o Intranet. Si es necesario, la aplicación puede solicitar permisos de seguridad con privilegios elevados. Para más información, consulte [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Cómo funciona la seguridad de ClickOnce  
 El núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] seguridad se basa en certificados, directivas de seguridad de acceso de código y el aviso de confianza de ClickOnce.  
  
### <a name="certificates"></a>Certificados  
 Certificados de Authenticode se usan para comprobar la autenticidad del publicador de la aplicación. Mediante el uso de Authenticode para la implementación de aplicaciones, ClickOnce ayuda a impedir que un programa dañino se presente como un programa legítimo procedentes de un origen de confianza establecido. Si lo desea, también se pueden utilizar certificados para firmar la aplicación y los manifiestos de implementación para demostrar que los archivos no han sido alterados. Para obtener más información, consulte [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Certificados también pueden utilizarse para configurar los equipos cliente para tener una lista de editores de confianza. Si una aplicación procede de un editor de confianza, se puede instalar sin ninguna interacción del usuario. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Seguridad de acceso del código  
 Seguridad de acceso del código ayuda a limitar el acceso del código a los recursos protegidos. En la mayoría de los casos, puede elegir las zonas de Internet o Intranet Local para limitar los permisos. Use la **seguridad** página en el **ProjectDesigner** para solicitar la zona correspondiente a la aplicación. También puede depurar las aplicaciones con permisos restringidos para emular la experiencia del usuario final. Para más información, vea [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md) (Seguridad de acceso del código para aplicaciones ClickOnce).  
  
### <a name="clickonce-trust-prompt"></a>Solicitud de fiabilidad de ClickOnce  
 Si la aplicación solicita más permisos que permite que la zona, le solicitará al usuario final para tomar una decisión de confianza. El usuario final puede decidir si las aplicaciones ClickOnce, como aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de consola, aplicaciones de explorador XAML y soluciones de Office son de confianza para ejecutarse. Para obtener más información, consulte [Cómo: configurar el comportamiento de solicitud de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Cómo funciona la implementación de ClickOnce  
 El núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquitectura de implementación se basa en dos archivos de manifiesto XML: un manifiesto de aplicación y un manifiesto de implementación. Los archivos se utilizan para describir dónde se instalan las aplicaciones ClickOnce desde, cómo se actualizan y cuando se actualizan.  
  
### <a name="publishing-clickonce-applications"></a>Publicar aplicaciones ClickOnce  
 El manifiesto de aplicación describe la propia aplicación. Esto incluye los ensamblados, las dependencias y los archivos que componen la aplicación, los permisos necesarios y la ubicación donde las actualizaciones estarán disponibles. El desarrollador de aplicaciones crea el manifiesto de aplicación utilizando el Asistente para publicación de Visual Studio o la herramienta de edición (Mage.exe) y generación de manifiestos en el [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 El manifiesto de implementación describe cómo se implementa la aplicación. Esto incluye la ubicación del manifiesto de aplicación y la versión de la aplicación que los clientes deben ejecutar.  
  
### <a name="deploying-clickonce-applications"></a>Implementar aplicaciones ClickOnce  
 Una vez creado, el manifiesto de implementación se copia en la ubicación de implementación. Puede tratarse de un servidor Web, recurso compartido de red o un medio, como un CD. El manifiesto de aplicación y todos los archivos de aplicación también se copian en una ubicación de implementación que se especifica en el manifiesto de implementación. Esto puede ser el mismo que la ubicación de implementación, o puede ser una ubicación diferente. Cuando se usa el **Asistente para publicación** en Visual Studio, las operaciones de copia se realizan automáticamente.  
  
### <a name="installing-clickonce-applications"></a>Instalar aplicaciones ClickOnce  
 Después de que se implementa en la ubicación de implementación, los usuarios finales pueden descargar e instalar la aplicación haciendo clic en un icono que representa el archivo de manifiesto de implementación en una página Web o en una carpeta. En la mayoría de los casos, el usuario final se presentará un cuadro de diálogo simple pidiendo al usuario que confirme la instalación, tras el cual la instalación continúa y la aplicación se inicia sin intervención adicional. En casos donde la aplicación requiere permisos elevados o si la aplicación no está firmada por un certificado de confianza, el cuadro de diálogo también le pide al usuario que conceda permiso para que pueda continuar la instalación. Aunque las instalaciones de ClickOnce son por usuario, pueden requerir elevación de permisos si existen requisitos previos que requieren privilegios de administrador. Para obtener más información sobre permisos elevados, consulte [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certificados sean de confianza en el nivel de equipo o de empresa, para que las aplicaciones ClickOnce firmadas con un certificado de confianza se pueden instalar en modo silencioso. Para obtener más información acerca de los certificados de confianza, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
 Puede agregar la aplicación para el usuario **iniciar** menú y a la **agregar o quitar programas** grupo en el **el Panel de Control**. A diferencia de otras tecnologías de implementación, se agrega nada a la **archivos de programa** carpeta o el registro y sin derechos administrativos son necesarios para la instalación  
  
> [!NOTE]
>  También es posible impedir que la aplicación que se va a agregar a la **iniciar** menú y **agregar o quitar programas** grupo, en vigor lo que se comportan como una aplicación Web. Para más información, consulte el artículo [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Actualizar las aplicaciones ClickOnce  
 Cuando los desarrolladores de aplicaciones crearon una versión actualizada de la aplicación, genera un nuevo manifiesto de aplicación y copie los archivos en una ubicación de implementación, normalmente una carpeta secundaria de a la carpeta de implementación de aplicación original. El administrador actualiza el manifiesto de implementación para que señale a la ubicación de la nueva versión de la aplicación.  
  
> [!NOTE]
>  El **Asistente para publicación** en Visual Studio puede usarse para realizar estos pasos.  
  
 Además de la ubicación de implementación, el manifiesto de implementación también contiene una ubicación de actualización (una página Web o una red de recurso compartido de archivos) donde se comprueba si hay versiones actualizadas. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publicar** propiedades se utilizan para especificar cuándo y con qué frecuencia debe buscar actualizaciones la aplicación. Comportamiento de actualización se puede especificar en el manifiesto de implementación o se puede presentar como opciones del usuario en la interfaz de usuario de la aplicación por medio de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API. Además, **publicar** propiedades se pueden emplear para realizar las actualizaciones obligatorias o revertir a una versión anterior. Para obtener más información, consulte [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instaladores de otros fabricantes  
 Puede personalizar el instalador de ClickOnce para instalar componentes de terceros junto con la aplicación. Debe tener el paquete redistribuible (archivo .exe o .msi) y describir el paquete con un manifiesto de producto independiente del idioma y un manifiesto del paquete de idioma específico. Para obtener más información, consulte [crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Herramientas de ClickOnce  
 En la tabla siguiente se muestra las herramientas que puede utilizar para generar, modificar, firmar y volver a firmar los manifiestos de aplicación e implementación.  
  
|Herramienta|Descripción|  
|----------|-----------------|  
|[Página Seguridad, Diseñador de proyectos](../ide/reference/security-page-project-designer.md)|Firma los manifiestos de aplicación e implementación.|  
|[Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)|Genera y edita los manifiestos de aplicación e implementación para las aplicaciones de Visual Basic y Visual C#.|  
|[Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Genera los manifiestos de aplicación e implementación para las aplicaciones de Visual Basic, Visual C# y Visual C++.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde scripts por lotes y el símbolo del sistema.|  
|[MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Genera y edita los manifiestos de aplicación e implementación.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.|  
|[Tarea GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)|Genera el manifiesto de aplicación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarea GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Genera el manifiesto de implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarea SignFile](../msbuild/signfile-task.md)|Firma los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para obtener más información, consulte [referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desarrolle su propia aplicación para generar los manifiestos de aplicación e implementación.|  
  
 En la tabla siguiente se muestra la versión de .NET Framework necesaria para admitir aplicaciones ClickOnce en estos exploradores.  
  
|Explorador|Versión de .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Vea también  
 [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implementar componentes COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilar aplicaciones ClickOnce desde la línea de comandos](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurar aplicaciones ClickOnce que usan System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)