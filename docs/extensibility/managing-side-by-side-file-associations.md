---
title: Administrar asociaciones de archivo Side-by-Side | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5bbc06ba777939857876221a2796eef6786ec44c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928014"
---
# <a name="manage-side-by-side-file-associations"></a>Administrar asociaciones de archivos en paralelo
Si el paquete VSPackage proporciona las asociaciones de archivo, debe decidir cómo tratar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe invocarse para abrir un archivo. Formatos de archivo incompatibles compuesta el problema.  
  
 Los usuarios esperan una nueva versión de un producto que sean compatibles con versiones anteriores, por lo que se pueden cargar los archivos existentes en una nueva versión sin perder datos. Idealmente, el VSPackage puede cargar y guardar los formatos de archivo de las versiones anteriores. Si no es así, debe ofrecer actualizar el formato de archivo a la nueva versión del paquete VSPackage. La desventaja de este enfoque es que no se puede abrir el archivo actualizado en la versión anterior.  
  
 Para evitar este problema, puede cambiar las extensiones de los formatos de archivo a medida que estén incompatibles. Por ejemplo, la versión 1 del paquete VSPackage podría usar la extensión, *.mypkg10*y la versión 2 podría usar la extensión, *.mypkg20*. Esta diferencia identifica el VSPackage que se abre un archivo determinado. Si agrega más reciente VSPackages a la lista de programas que están asociados con la extensión anterior, los usuarios pueden haga clic en el archivo y elija abrirla en un VSPackage más reciente. En ese momento, el paquete de VS puede ofrecer actualizar el archivo al nuevo formato o abra el archivo y mantener la compatibilidad con versiones anteriores del VSPackage.  
  
> [!NOTE]
>  Puede combinar estos métodos. Por ejemplo, puede ofrecer compatibilidad con versiones anteriores al cargar un archivo anterior y la oferta actualizar el formato de archivo cuando el usuario lo guarda.  
  
## <a name="face-the-problem"></a>Se plantea el problema  
 Si desea que varios VSPackages en paralelo para usar la misma extensión, debe elegir la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está asociado con la extensión. Existen dos alternativas:  
  
- Abra el archivo en la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalado en el equipo del usuario.  
  
   En este enfoque, es responsable de determinar la versión más reciente del instalador del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que se incluyen con la entrada del registro escrita para la asociación de archivo. En un paquete de Windows Installer, puede incluir acciones personalizadas para establecer una propiedad que indica la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
  > [!NOTE]
  >  En este contexto, "latest" significa "última versión compatible." Estas entradas del instalador no detecta automáticamente una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Las entradas de [detectar requisitos del sistema](../extensibility/internals/detecting-system-requirements.md) y en [comandos que debe ser ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md) son similares a los que se presenta aquí y son necesarios para admitir versiones adicionales de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   Las siguientes filas de la tabla CustomAction establecen la propiedad DEVENV_EXE_LATEST sea una propiedad definida por el AppSearch y RegLocator tablas se tratan en [comandos que se deben ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md). Las filas de la tabla InstallExecuteSequence programación las acciones personalizadas al principio de la secuencia de ejecución. Los valores de la marca de columna condición la lógica de trabajo:  
  
  - Visual Studio .NET 2002 es la versión más reciente si es la versión solo están presente.  
  
  - Visual Studio .NET 2003 es la versión más reciente solo si está presente y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no está presente.  
  
  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es la versión más reciente si es la versión solo están presente.  
  
    El resultado neto es que DEVENV_EXE_LATEST contiene la ruta de acceso de la última versión de devenv.exe.  
  
  ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Filas de tabla CustomAction que determinan la versión más reciente de Visual Studio  
  
  |Acción|Tipo|Origen|Destino|  
  |------------|----------|------------|------------|  
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
  ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Filas de tabla InstallExecuteSequence que determinan la versión más reciente de Visual Studio  
  
  |Acción|Condición|Secuencia|  
  |------------|---------------|--------------|  
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 Y NO (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|  
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 Y NO DEVENV_EXE_2005|420|  
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
   Puede usar la propiedad DEVENV_EXE_LATEST en la tabla del registro del paquete de Windows Installer para escribir el **HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand** valor predeterminado de la clave, [DEVENV_EXE_LATEST] "%1"  
  
- Ejecutar un programa de iniciador compartido que puede elegir la mejor opción de versiones disponibles de VSPackage.  
  
   Los desarrolladores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elige este enfoque para controlar los requisitos complejos de los varios formatos de soluciones y proyectos que se derivan de muchas versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En este enfoque, debe registrar un programa selector como el controlador de extensión. El iniciador examina el archivo y decide qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y su VSPackage puede controlar ese archivo en particular. Por ejemplo, si un usuario abre un archivo que se guardó por última vez mediante una versión concreta del paquete de VS, el iniciador puede iniciar esa VSPackage en la versión coincidente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Además, un usuario puede configurar el iniciador para iniciar siempre la versión más reciente. Un iniciador también podría solicitar al usuario que actualice el formato del archivo. Si el formato del archivo incluye un número de versión, el iniciador podría informar a un usuario si el formato de archivo pertenece a una versión posterior a uno o varios de los VSPackages instalados.  
  
   El selector debe estar en un componente de Windows Installer que se comparte con todas las versiones del paquete VSPackage. Este proceso garantiza que la versión más reciente siempre se instala y no se quita hasta que se desinstalen todas las versiones del paquete VSPackage. De este modo, las asociaciones de archivo y otras entradas del registro del componente del iniciador se conservan incluso si se desinstala una versión de VSPackage.  
  
## <a name="uninstall-and-file-associations"></a>Desinstale y las asociaciones de archivo  
 Desinstalación de un VSPackage que escribe entradas del registro para las asociaciones de archivo quita las asociaciones de archivo. Por lo tanto, la extensión no tiene ningún programa asociado. Windows Installer no "recover" las entradas del registro que se agregaron cuando instaló el VSPackage. Estas son algunas maneras de corregir las asociaciones de archivo de un usuario:  
  
-   Utilice un componente compartido iniciador como se describió anteriormente.  
  
-   Indique al usuario que ejecute una reparación de la versión del VSPackage que el usuario quiere ser dueño de la asociación de archivo.  
  
-   Proporcionar un programa ejecutable independiente que se vuelve a escribir las entradas del registro correspondientes.  
  
-   Proporcione un configuración opciones página o cuadro de diálogo que permite a los usuarios elegir las asociaciones de archivo y reclamar asociaciones perdidas. Indique a los usuarios para ejecutarlo después de la desinstalación.  
  
## <a name="see-also"></a>Vea también  
 [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrar los verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)