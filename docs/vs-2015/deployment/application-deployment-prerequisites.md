---
title: Requisitos previos de implementación de aplicaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e382c5d312a2de69281bdeda92e9c275e2877932
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891003"
---
# <a name="application-deployment-prerequisites"></a>Requisitos previos para la implementación de aplicaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para asegurarse de que su aplicación se instalará y se ejecutará correctamente, primero debe asegurarse de que todos los componentes de los que depende su aplicación ya estén instalados en el equipo de destino. Por ejemplo, la mayoría de las aplicaciones creadas con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tienen una dependencia de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]; antes de instalar la aplicación, el equipo de destino debe tener la versión correcta de Common Language Runtime.  
  
 Puede seleccionar estos requisitos previos en el **Prerequisites Dialog Box** e instalar .NET Framework y otros redistribuibles como parte de la instalación. Esta práctica se conoce como *arranque*. A continuación, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera un programa ejecutable de Windows llamado Setup.exe, también conocido como un *arranque*. El programa previo es responsable de la instalación de estos requisitos previos antes de que se ejecute la aplicación. Para obtener más información acerca de cómo seleccionar estos requisitos previos, consulte [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md).  
  
 Cada requisito previo es un paquete de programa previo. Un paquete de programa previo es un grupo de directorios y archivos que contienen archivos de manifiesto que describen cómo se debe instalar el requisito previo. Si no se enumeran los requisitos previos de la aplicación en el **cuadro de diálogo requisitos previos**, puede crear paquetes de arranque personalizados y agregarlos a Visual Studio. Después, puede seleccionar los requisitos previos en el **Prerequisites Dialog Box**. Para obtener más información, consulte [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).  
  
 De forma predeterminada, el arranque está habilitado para la implementación ClickOnce. El programa previo generado por la implementación ClickOnce está firmado. Puede deshabilitar el arranque para un componente, pero hágalo solo si está seguro de que la versión correcta del componente ya está instalada en todos los equipos de destino.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Arranque e implementación ClickOnce  
 Antes de instalar una aplicación en un equipo cliente, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] examinará el cliente para asegurarse de que cumple determinados requisitos especificados en el manifiesto de la aplicación. Entre ellas se incluyen las siguientes:  
  
- La versión mínima necesaria de Common Language Runtime, que se especifica como una dependencia de ensamblado en el manifiesto de la aplicación.  
  
- La versión mínima del sistema operativo Windows requerida por la aplicación, tal y como se especifica en el manifiesto de la aplicación mediante el elemento `<osVersionInfo>`. (Consulte [ \<dependencia > elemento](../deployment/dependency-element-clickonce-application.md))  
  
- La versión mínima de todos y cada uno de los ensamblados que deben estar preinstalados en la caché global de ensamblados (GAC), tal y como se especifica en las declaraciones de dependencias de ensamblados en el manifiesto del ensamblado.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] puede detectar requisitos previos que falten, y puede instalar los requisitos previos mediante el uso de un programa previo. Para obtener más información, consulte [Cómo: instalar los requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Para cambiar los valores en los manifiestos generados por herramientas tales como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y MageUI.exe, necesita editar el manifiesto de la aplicación en un editor de texto y, después, volver a firmar los manifiestos de la aplicación y de la implementación. Para obtener más información, consulta [Cómo: Volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Si usa Visual Studio y ClickOnce para implementar su aplicación, los paquetes de programa previo se seleccionan de forma predeterminada según la versión de .NET Framework en la solución. Sin embargo, si cambia la versión de .NET Framework de destino, debe actualizar las opciones de la **Prerequisites Dialog Box** manualmente.  
  
|.NET Framework de destino|Paquetes de programa previo seleccionados|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Con la implementación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], la página Publish.htm generada por el Asistente para publicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] apunta a un vínculo que instala solo la aplicación o a un vínculo que instala tanto la aplicación como los componentes de arranque.  
  
 Si genera el programa previo con el Asistente para publicación de ClickOnce o la página Publicar en Visual Studio, el archivo Setup.exe se firma automáticamente. Sin embargo, si quiere usar el certificado de cliente para firmar el programa previo, puede firmar el archivo más adelante.  
  
## <a name="bootstrapping-and-msbuild"></a>Arranque y MSBuild  
 Si no usa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pero compila sus aplicaciones en la línea de comandos, puede crear la aplicación de arranque [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]usando una tarea de Microsoft Build Engine (MSBuild). Para obtener más información, consulte [GenerateBootstrapper (tarea)](../msbuild/generatebootstrapper-task.md).  
  
 Como alternativa al arranque, puede realizar una implementación previa de los componentes usando un sistema electrónico de distribución de software, como Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumentos de la línea de comandos del programa previo (Setup.exe)  
 El archivo Setup.exe generado por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y las tareas de MSBuild admiten el siguiente conjunto reducido de argumentos de la línea de comandos. Cualquier otro argumento aparte de estos que se suministre a la aplicación de arranque se reenviará al instalador de aplicaciones.  
  
 Si cambia las opciones del programa previo, debe cambiar el programa previo sin firmar y firmarlo después.  
  
|Argumento de la línea de comandos|Descripción|  
|---------------------------|-----------------|  
|**-?, -h, - ayuda**|Muestra el cuadro de diálogo Ayuda.|  
|**-dirección url, - componentsurl**|Muestra la dirección URL almacenada y la dirección URL de los componentes para esta instalación.|  
|**-url =** `location`|Establece la dirección URL donde Setup.exe buscará la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].|  
|**-componentsurl =** `location`|Establece la dirección URL donde Setup.exe buscará las dependencias, como [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|**-homesite =** `true`**&#124;** `false`|Cuando `true`, descarga las dependencias de la ubicación preferida en el sitio del proveedor. Esto invalida el **- componentsurl** configuración. Cuando `false`, descarga las dependencias de la dirección URL especificada por **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Compatibilidad con sistemas operativos  
 El programa previo de Visual Studio no se admite en Windows Server 2008 Server Core ni Windows Server 2008 R2 Server Core, que proporcionan un entorno de servidor de bajo mantenimiento con una funcionalidad limitada. Por ejemplo, la opción de instalación Server Core solo admite el perfil .NET Framework 3.5 Server Core, por lo que las características de Visual Studio que dependen de la versión completa de .NET Framework no se pueden ejecutar.  
  
## <a name="see-also"></a>Vea también  
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)



