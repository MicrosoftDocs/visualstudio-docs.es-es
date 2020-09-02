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
ms.openlocfilehash: 8206e199acc3ccb76cf89603d48bed0173129218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66746059"
---
# <a name="application-deployment-prerequisites"></a>Requisitos previos para la implementación de aplicaciones

Para que la aplicación se instale y se ejecute correctamente, instale primero todos los componentes de los que depende la aplicación en el equipo de destino. Por ejemplo, la mayoría de las aplicaciones creadas mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tienen una dependencia en el .NET Framework. En este caso, la versión correcta del Common Language Runtime debe estar presente en el equipo de destino antes de instalar la aplicación.

 Puede seleccionar estos requisitos previos en el **cuadro de diálogo requisitos previos** e instalar el .NET Framework y cualquier otro redistribuible como parte de la instalación. Este procedimiento se conoce como *arranque*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un programa ejecutable de Windows denominado *Setup.exe*, también conocido como *arranque*. El programa previo es responsable de la instalación de estos requisitos previos antes de que se ejecute la aplicación. Para obtener más información acerca de cómo seleccionar estos requisitos previos, consulte el [cuadro de diálogo requisitos previos](../ide/reference/prerequisites-dialog-box.md).

 Cada requisito previo es un paquete de programa previo. Un paquete de programa previo es un grupo de directorios y archivos que contiene los archivos de manifiesto que describen cómo se instalan los requisitos previos. Si los requisitos previos de su aplicación no están en la lista del **cuadro de diálogo Requisitos previos**, puede crear paquetes de programa previo personalizados y agregarlos a Visual Studio. Después, puede seleccionar los requisitos previos en el **cuadro de diálogo Requisitos previos**. Para obtener más información, vea [crear paquetes de programa previo](../deployment/creating-bootstrapper-packages.md).

 De forma predeterminada, el arranque está habilitado para la implementación ClickOnce. El programa previo generado por la implementación ClickOnce está firmado. Puede deshabilitar el arranque de un componente, pero solo si está seguro de que la versión correcta del componente ya está instalada en todos los equipos de destino.

## <a name="bootstrapping-and-clickonce-deployment"></a>Arranque e implementación ClickOnce
 Antes de instalar una aplicación en un equipo cliente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] examina el cliente para asegurarse de que tiene los requisitos especificados en el manifiesto de aplicación. Entre ellos se incluyen los siguientes requisitos:

- La versión mínima necesaria de Common Language Runtime, que se especifica como una dependencia de ensamblado en el manifiesto de la aplicación.

- La versión mínima del sistema operativo Windows requerida por la aplicación, tal y como se especifica en el manifiesto de la aplicación mediante el elemento `<osVersionInfo>`. (Vea el [ \<dependency> elemento](../deployment/dependency-element-clickonce-application.md)).

- Versión mínima de todos los ensamblados que se deben preinstalar en la caché de ensamblados global (GAC), tal y como se especifica en las declaraciones de dependencias de ensamblado en el manifiesto del ensamblado.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede detectar los requisitos previos que faltan y puede instalar los requisitos previos mediante un programa previo. Para obtener más información, consulte [Cómo: instalar requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Para cambiar los valores en los manifiestos generados por herramientas tales como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y *MageUI.exe*, necesita editar el manifiesto de la aplicación en un editor de texto y, después, volver a firmar los manifiestos de la aplicación y de la implementación. Para obtener más información, vea [Cómo: volver a firmar manifiestos de aplicación y de implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Si usa Visual Studio y ClickOnce para implementar su aplicación, los paquetes de programa previo se seleccionan de forma predeterminada según la versión de .NET Framework en la solución. Sin embargo, si cambia la versión de .NET Framework de destino, debe actualizar manualmente las opciones en el **cuadro de diálogo Requisitos previos**.

|.NET Framework de destino|Paquetes de programa previo seleccionados|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Con la implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la página *Publish.htm* generada por el Asistente para publicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] apunta a un vínculo que instala solo la aplicación o a un vínculo que instala tanto la aplicación como los componentes de arranque.

 Si genera el programa previo mediante el Asistente para publicación de ClickOnce o la página de publicación en Visual Studio, el *Setup.exe* se firma automáticamente. Sin embargo, si quiere usar el certificado de cliente para firmar el programa previo, puede firmar el archivo más adelante.

## <a name="bootstrapping-and-msbuild"></a>Arranque y MSBuild
 Si no usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , sino compilar las aplicaciones en la línea de comandos, puede crear la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación de arranque mediante una tarea de Microsoft Build Engine (MSBuild). Para obtener más información, vea [tarea GenerateBootstrapper (](../msbuild/generatebootstrapper-task.md).

 Como alternativa al arranque, puede realizar una implementación previa de los componentes usando un sistema electrónico de distribución de software, como Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumentos de la línea de comandos del programa previo (Setup.exe)
 Los *Setup.exe* generados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y las tareas de MSBuild admiten el siguiente conjunto de argumentos de línea de comandos. Cualquier otro argumento se reenvía al instalador de la aplicación.

 Si cambia las opciones de arranque, debe cambiar el programa previo sin firmar y, después, firmar el archivo de programa previo.

| Argumento de línea de comandos | Descripción |
| - | - |
| **-?, -h, -help** | Muestra el cuadro de diálogo Ayuda. |
| **-url, -componentsurl** | Muestra la dirección URL almacenada y la dirección URL de los componentes para esta instalación. |
| **-URL =**`location` | Establece la dirección URL donde *Setup.exe* buscará la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. |
| **-componentsurl=** `location` | Establece la dirección URL donde *Setup.exe* buscarán las dependencias, como la .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Cuando `true` es, descarga las dependencias de la ubicación preferida en el sitio del proveedor. Esta configuración invalida el valor **-componentsurl** . Cuando es `false` , descarga las dependencias de la dirección URL especificada por **-componentsurl**. |

## <a name="operating-system-support"></a>Compatibilidad con sistema operativo
 El programa previo de Visual Studio no se admite en Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, ya que proporcionan un entorno de servidor de bajo mantenimiento con funcionalidad limitada. Por ejemplo, la opción de instalación Server Core solo admite el perfil .NET Framework 3,5 Server Core, que no puede ejecutar las características de Visual Studio que dependen de la .NET Framework completa.

## <a name="see-also"></a>Consulte también
- [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)