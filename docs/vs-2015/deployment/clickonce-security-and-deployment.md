---
title: Seguridad e implementación de ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 592bf358c24bee146290e8b3a00e28a0870f452d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263803"
---
# <a name="clickonce-security-and-deployment"></a>Seguridad e implementación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es una tecnología de implementación que permite crear aplicaciones basadas en Windows de actualización automática que se pueden instalar y ejecutar con una interacción mínima del usuario. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona compatibilidad completa para publicar y actualizar las aplicaciones implementadas con la tecnología ClickOnce si ha desarrollado sus proyectos con Visual Basic y Visual C#. Para obtener información sobre la implementación de aplicaciones Visual C++, vea [implementación de ClickOnce para aplicaciones de Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] la implementación supera tres problemas principales en la implementación:  
  
- **Dificultades en la actualización de aplicaciones.** Con Microsoft Windows Installer implementación, cada vez que se actualiza una aplicación, el usuario puede instalar una actualización, un archivo MSP y aplicarla al producto instalado. con la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación, puede proporcionar las actualizaciones automáticamente. Solo se descargan las partes de la aplicación que han cambiado y, a continuación, se vuelve a instalar la aplicación completa y actualizada desde una nueva carpeta en paralelo.  
  
- **Impacto en el equipo del usuario.** Con Windows Installer implementación, las aplicaciones a menudo se basan en componentes compartidos, con la posibilidad de que se produzcan conflictos de control de versiones. con la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación, cada aplicación es independiente y no puede interferir con otras aplicaciones.  
  
- **Permisos de seguridad.** Windows Installer implementación requiere permisos administrativos y solo permite una instalación limitada del usuario; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] la implementación permite a los usuarios no administrativos instalar y conceder solo los permisos de seguridad de acceso del código necesarios para la aplicación.  
  
  En el pasado, estos problemas a veces hacían que los desarrolladores decidieran crear aplicaciones web en lugar de aplicaciones basadas en Windows, con lo que se sacrificaba una interfaz de usuario enriquecida para facilitar la instalación. Mediante el uso de aplicaciones implementadas con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , puede tener las mejores tecnologías.  
  
## <a name="what-is-a-clickonce-application"></a>¿Qué es una aplicación ClickOnce?  
 Una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación es cualquier Windows Presentation Foundation (. XBAP), Windows Forms (. exe), una aplicación de consola (. exe) o una solución de Office (. dll) publicada mediante [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnología. Puede publicar una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación de tres maneras diferentes: desde una página web, desde un recurso compartido de archivos de red o desde un medio, como un CD-ROM. Una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se puede instalar en el equipo de un usuario final y ejecutarse localmente incluso cuando el equipo está sin conexión, o bien se puede ejecutar en modo de solo conexión sin tener que instalar nada permanentemente en el equipo del usuario final. Para más información, consulte el artículo [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las aplicaciones pueden actualizarse automáticamente. pueden comprobar si hay versiones más recientes a medida que estén disponibles y reemplazar automáticamente los archivos actualizados. El desarrollador puede especificar el comportamiento de actualización, y un administrador de red puede igualmente controlar las estrategias del proceso, por ejemplo, al marcar actualizaciones como obligatorias. El usuario final o un administrador también pueden revertir las actualizaciones a una versión anterior. Para obtener más información, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Dado [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que las aplicaciones están aisladas, la instalación o ejecución de una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación no puede interrumpir las aplicaciones existentes. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las aplicaciones son independientes; cada [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se instala y se ejecuta desde una caché segura por usuario y por aplicación. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] las aplicaciones se ejecutan en las zonas de seguridad de Internet o intranet. Si resultara necesario, la aplicación puede solicitar permisos de seguridad elevados. Para más información, consulte [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Cómo funciona la seguridad de ClickOnce  
 La [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] seguridad básica se basa en los certificados, las directivas de seguridad de acceso del código y el mensaje de confianza de ClickOnce.  
  
### <a name="certificates"></a>Certificados  
 Los certificados Authenticode se usan para comprobar la autenticidad del publicador de la aplicación. Mediante el uso de Authenticode para la implementación de aplicaciones, ClickOnce ayuda a impedir que un programa perjudicial se represente como un programa legítimo procedente de un origen establecido y de confianza. Opcionalmente, los certificados también se pueden usar para firmar la aplicación y los manifiestos de implementación para demostrar que los archivos no se han alterado. Para obtener más información, vea [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md). Los certificados también se pueden usar para configurar los equipos cliente para que tengan una lista de editores de confianza. Si una aplicación procede de un editor de confianza, se puede instalar sin interacción del usuario. Para obtener más información, vea [información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Seguridad de acceso del código  
 La seguridad de acceso del código ayuda a limitar el acceso que el código tiene a los recursos protegidos. En la mayoría de los casos, puede elegir las zonas de Internet o Intranet local para limitar los permisos. Use la página de **seguridad** de **ProjectDesigner** para solicitar la zona adecuada para la aplicación. También puede depurar aplicaciones con permisos restringidos para emular la experiencia del usuario final. Para más información, vea [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md) (Seguridad de acceso del código para aplicaciones ClickOnce).  
  
### <a name="clickonce-trust-prompt"></a>Solicitud de fiabilidad de ClickOnce  
 Si la aplicación solicita más permisos de los que permite la zona, se puede solicitar al usuario final que tome una decisión de confianza. El usuario final puede decidir si las aplicaciones ClickOnce, como Windows Forms aplicaciones, las aplicaciones de Windows Presentation Foundation, las aplicaciones de consola, las aplicaciones de explorador XAML y las soluciones de Office son de confianza para ejecutarse. Para obtener más información, consulte [Cómo: configurar el comportamiento del mensaje de confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Cómo funciona la implementación ClickOnce  
 La [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquitectura de implementación principal se basa en dos archivos de manifiesto XML: un manifiesto de aplicación y un manifiesto de implementación. Los archivos se usan para describir el lugar desde el que se instalan las aplicaciones ClickOnce, cómo se actualizan y cuándo se actualizan.  
  
### <a name="publishing-clickonce-applications"></a>Publicar aplicaciones ClickOnce  
 El manifiesto de aplicación describe la propia aplicación. Esto incluye los ensamblados, las dependencias y los archivos que componen la aplicación, los permisos necesarios y la ubicación en la que estarán disponibles las actualizaciones. El desarrollador de aplicaciones crea el manifiesto de aplicación mediante el Asistente para publicación de Visual Studio o el Herramienta de generación y edición de manifiestos (Mage.exe) en [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 El manifiesto de implementación describe cómo se implementa la aplicación. Esto incluye la ubicación del manifiesto de aplicación y la versión de la aplicación que deben ejecutar los clientes.  
  
### <a name="deploying-clickonce-applications"></a>Implementar aplicaciones ClickOnce  
 Una vez creada, el manifiesto de implementación se copia en la ubicación de implementación. Puede tratarse de un servidor web, un recurso compartido de archivos de red o algún otro medio (por ejemplo, un CD-ROM). El manifiesto de aplicación y todos los archivos de aplicación también se copian en una ubicación de implementación que se especifica en el manifiesto de implementación. Puede ser la misma que la ubicación de implementación o una ubicación diferente. Cuando se usa el **Asistente para publicación** en Visual Studio, las operaciones de copia se realizan automáticamente.  
  
### <a name="installing-clickonce-applications"></a>Instalación de aplicaciones ClickOnce  
 Una vez implementada en la ubicación de implementación, los usuarios finales pueden descargar e instalar la aplicación haciendo clic en un icono que representa el archivo de manifiesto de implementación en una página web o en una carpeta. En la mayoría de los casos, al usuario final se le presenta un sencillo cuadro de diálogo que pide al usuario que confirme la instalación, tras lo cual la instalación continúa y la aplicación se inicia sin intervención adicional. En los casos en los que la aplicación requiere permisos elevados o si la aplicación no está firmada por un certificado de confianza, el cuadro de diálogo también solicita al usuario que conceda permiso para que la instalación pueda continuar. Aunque las instalaciones de ClickOnce son por usuario, es posible que se requiera la elevación de permisos si hay requisitos previos que requieran privilegios de administrador. Para obtener más información sobre los permisos elevados, vea [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Los certificados pueden ser de confianza en el nivel de equipo o de empresa, por lo que las aplicaciones ClickOnce firmadas con un certificado de confianza se pueden instalar de forma silenciosa. Para obtener más información sobre los certificados de confianza, consulte [información general](../deployment/trusted-application-deployment-overview.md)sobre la implementación de aplicaciones de confianza.  
  
 La aplicación se puede Agregar al menú **Inicio** del usuario y al grupo **Agregar o quitar programas** del **Panel de control**. A diferencia de otras tecnologías de implementación, no se agrega nada a la carpeta **archivos de programa** o al registro, y no se requieren derechos administrativos para la instalación.  
  
> [!NOTE]
> También es posible impedir que la aplicación se agregue al menú **Inicio** y al grupo **Agregar o quitar programas** , en efecto que se comporte como una aplicación Web. Para más información, consulte el artículo [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Actualizar aplicaciones ClickOnce  
 Cuando los desarrolladores de aplicaciones crean una versión actualizada de la aplicación, generan un nuevo manifiesto de aplicación y copian los archivos en una ubicación de implementación, normalmente una carpeta relacionada en la carpeta de implementación de la aplicación original. El administrador actualiza el manifiesto de implementación para que apunte a la ubicación de la nueva versión de la aplicación.  
  
> [!NOTE]
> El **Asistente para publicación** de Visual Studio se puede usar para realizar estos pasos.  
  
 Además de la ubicación de implementación, el manifiesto de implementación también contiene una ubicación de actualización (una página web o un recurso compartido de archivos de red) donde la aplicación comprueba si hay versiones actualizadas. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Las propiedades de **publicación** se utilizan para especificar el momento y la frecuencia con que la aplicación debe comprobar si hay actualizaciones. El comportamiento de actualización se puede especificar en el manifiesto de implementación, o bien se puede presentar como elección del usuario en la interfaz de usuario de la aplicación mediante las [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API. Además, las propiedades **Publish** se pueden emplear para que las actualizaciones sean obligatorias o para deshacer la instalación y volver a una versión anterior. Para obtener más información, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instaladores de terceros  
 Puede personalizar el instalador de ClickOnce para instalar componentes de terceros junto con la aplicación. Debe tener el paquete redistribuible (archivo. exe o. msi) y describir el paquete con un manifiesto de producto independiente del lenguaje y un manifiesto de paquete específico del idioma. Para obtener más información, vea [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Herramientas ClickOnce  
 En la tabla siguiente se muestran las herramientas que puede usar para generar, editar, firmar y volver a firmar los manifiestos de aplicación e implementación.  
  
|Herramienta|Descripción|  
|----------|-----------------|  
|[Página Seguridad, Diseñador de proyectos](../ide/reference/security-page-project-designer.md)|Firma los manifiestos de aplicación y de implementación.|  
|[Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)|Genera y edita los manifiestos de aplicación y de implementación para las aplicaciones de Visual Basic y Visual C#.|  
|[Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Genera los manifiestos de aplicación y de implementación para las aplicaciones de Visual Basic, Visual C# y Visual C++.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.<br /><br /> Se puede ejecutar desde scripts por lotes y desde el símbolo del sistema.|  
|[MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Genera y edita los manifiestos de aplicación e implementación.<br /><br /> Firma y vuelve a firmar los manifiestos de aplicación e implementación.|  
|[GenerateApplicationManifest (tarea)](../msbuild/generateapplicationmanifest-task.md)|Genera el manifiesto de aplicación.<br /><br /> Se puede ejecutar desde MSBuild. Para más información, consulte la [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest (tarea)](../msbuild/generatedeploymentmanifest-task.md)|Genera el manifiesto de implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para más información, consulte la [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|[SignFile (tarea)](../msbuild/signfile-task.md)|Firma los manifiestos de aplicación y de implementación.<br /><br /> Se puede ejecutar desde MSBuild. Para más información, consulte la [Referencia de MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desarrolle su propia aplicación para generar los manifiestos de aplicación y de implementación.|  
  
 En la tabla siguiente se muestra la versión .NET Framework necesaria para admitir aplicaciones ClickOnce en estos exploradores.  
  
|Explorador|Versión de .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Consulte también  
 [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implementar componentes COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilar aplicaciones ClickOnce desde la línea de comandos](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurar aplicaciones ClickOnce que utilizan System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
