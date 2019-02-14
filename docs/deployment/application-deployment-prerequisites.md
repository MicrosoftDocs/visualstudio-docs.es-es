---
title: Requisitos previos para la implementación de aplicaciones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3525d12bfbb745c54bb452a16d12cd65394023ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995692"
---
# <a name="application-deployment-prerequisites"></a>Requisitos previos para la implementación de aplicaciones

Para que la aplicación para instalar y ejecutar correctamente, debe instalar primero todos los componentes que la aplicación depende en el equipo de destino. Por ejemplo, mayoría de las aplicaciones creada con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tienen una dependencia en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. En este caso, la versión correcta de common language runtime debe estar presente en el equipo de destino antes de instalar la aplicación.  

 Puede seleccionar estos requisitos previos en el **Prerequisites Dialog Box** e instalar .NET Framework y cualquier otro redistribuible como parte de la instalación. Este procedimiento se conoce como *arranque*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un programa ejecutable de Windows denominado *Setup.exe*, también conocida como un *arranque*. El programa previo es responsable de la instalación de estos requisitos previos antes de que se ejecute la aplicación. Para obtener más información acerca de cómo seleccionar estos requisitos previos, consulte [cuadro de diálogo de requisitos previos](../ide/reference/prerequisites-dialog-box.md).  

 Cada requisito previo es un paquete de programa previo. Un paquete de programa previo es un grupo de directorios y archivos que contiene los archivos de manifiesto que describen cómo se instalan los requisitos previos. Si los requisitos previos de su aplicación no están en la lista del **cuadro de diálogo Requisitos previos**, puede crear paquetes de programa previo personalizados y agregarlos a Visual Studio. Después, puede seleccionar los requisitos previos en el **cuadro de diálogo Requisitos previos**. Para obtener más información, consulte [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).  

 De forma predeterminada, el arranque está habilitado para la implementación ClickOnce. El programa previo generado por la implementación ClickOnce está firmado. Puede deshabilitar el arranque para un componente, pero solo si está seguro de que la versión correcta del componente ya está instalada en todos los equipos de destino.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Arranque e implementación ClickOnce  
 Antes de instalar una aplicación en un equipo cliente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] examina el cliente para asegurarse de que tiene los requisitos especificados en el manifiesto de aplicación. Estos son los siguientes requisitos:  

- La versión mínima necesaria de Common Language Runtime, que se especifica como una dependencia de ensamblado en el manifiesto de la aplicación.  

- La versión mínima del sistema operativo Windows requerida por la aplicación, tal y como se especifica en el manifiesto de la aplicación mediante el elemento `<osVersionInfo>`. (Consulte [ \<dependencia > elemento](../deployment/dependency-element-clickonce-application.md).)  

- La versión mínima de todos los ensamblados que deben estar preinstalados en la caché global de ensamblados (GAC), según lo especificado por las declaraciones de dependencias de ensamblado en el manifiesto del ensamblado.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede detectar requisitos previos que falten, y puede instalar los requisitos previos mediante el uso de un programa previo. Para obtener más información, consulte [Cómo: instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Para cambiar los valores en los manifiestos generados por herramientas tales como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y *MageUI.exe*, necesita editar el manifiesto de la aplicación en un editor de texto y, después, volver a firmar los manifiestos de la aplicación y de la implementación. Para obtener más información, consulta [How to: Re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Si usa Visual Studio y ClickOnce para implementar su aplicación, los paquetes de programa previo se seleccionan de forma predeterminada según la versión de .NET Framework en la solución. Sin embargo, si cambia la versión de .NET Framework de destino, debe actualizar manualmente las opciones en el **cuadro de diálogo Requisitos previos**.  

|.NET Framework de destino|Paquetes de programa previo seleccionados|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  

 Con la implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la página *Publish.htm* generada por el Asistente para publicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] apunta a un vínculo que instala solo la aplicación o a un vínculo que instala tanto la aplicación como los componentes de arranque.  

 Si genera el programa previo con el Asistente para publicación de ClickOnce o la página Publicar en Visual Studio, el archivo *Setup.exe* se firma automáticamente. Sin embargo, si quiere usar el certificado de cliente para firmar el programa previo, puede firmar el archivo más adelante.  

## <a name="bootstrapping-and-msbuild"></a>Arranque y MSBuild  
 Si no usas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pero en su lugar compila sus aplicaciones en la línea de comandos, puede crear el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación de arranque mediante una tarea de Microsoft Build Engine (MSBuild). Para obtener más información, consulte [GenerateBootstrapper (tarea)](../msbuild/generatebootstrapper-task.md).  

 Como alternativa al arranque, puede realizar una implementación previa de los componentes usando un sistema electrónico de distribución de software, como Microsoft Systems Management Server (SMS).  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumentos de la línea de comandos del programa previo (Setup.exe)  
 El *Setup.exe* generados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y las tareas de MSBuild es compatible con el siguiente conjunto de argumentos de línea de comandos. Todos los demás argumentos se reenvían al instalador de la aplicación.  

 Si cambia las opciones del programa previo, debe cambiar al programa previo sin firmar y, a continuación, iniciar sesión más adelante el archivo de programa previo.  


| Argumento de la línea de comandos | Descripción |
| - | - |
| **-?, -h, -help** | Muestra el cuadro de diálogo Ayuda. |
| **-url, -componentsurl** | Muestra la dirección URL almacenada y la dirección URL de los componentes para esta instalación. |
| **-url=** `location` | Establece la dirección URL donde *Setup.exe* buscará la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. |
| **-componentsurl=** `location` | Establece la dirección URL donde *Setup.exe* buscará las dependencias, como [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite=** `true` **&#124;** `false` | Cuando `true`, descarga las dependencias de la ubicación preferida en el sitio del proveedor. Esta configuración invalida la **- componentsurl** configuración. Cuando `false`, descarga las dependencias de la dirección URL especificada por **- componentsurl**. |

## <a name="operating-system-support"></a>Compatibilidad con el sistema operativo  
 El programa previo de Visual Studio no se admite en Server Core de Windows Server 2008 o Windows Server 2008 R2 Server Core, ya que proporcionan un entorno de servidor de bajo mantenimiento con funcionalidad limitada. Por ejemplo, la opción de instalación Server Core solo admite el perfil de .NET Framework 3.5 Server Core, que no se puede ejecutar las características de Visual Studio que dependen de la versión completa de .NET Framework.  

## <a name="see-also"></a>Vea también  
 [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)