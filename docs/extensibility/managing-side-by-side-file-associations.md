---
title: Administrar las asociaciones de archivo Side-by-Side | Documentos de Microsoft
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
ms.openlocfilehash: e9144125786e7aa5f2a70823a033d49ac3fa2990
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="managing-side-by-side-file-associations"></a>Administrar las asociaciones de archivo Side-by-Side
Si el VSPackage proporciona las asociaciones de archivo, debe decidir cómo controlar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se debe invocar para abrir un archivo. Formatos de archivo incompatibles compuesta el problema.  
  
 Los usuarios esperan una nueva versión de un producto para ser compatible con versiones anteriores, por lo que se pueden cargar los archivos existentes en una nueva versión sin perder datos. Idealmente, el VSPackage puede cargar y guardar los formatos de archivo de las versiones anteriores. Si esto no es cierto, debe ofrecer actualizar el formato de archivo a la nueva versión del paquete de VS. El inconveniente de este enfoque es que no se puede abrir el archivo actualizado en la versión anterior.  
  
 Para evitar este problema, puede cambiar las extensiones cuando formatos de archivo sean incompatibles. Por ejemplo, podría utilizar la versión 1 del paquete de VS la extensión, .mypkg10 y versión 2 podría utilizar la extensión .mypkg20. Esta diferencia identifica el VSPackage que se abre un archivo determinado. Si agrega VSPackages más reciente a la lista de programas que están asociados con la extensión anterior, los usuarios pueden haga clic en el archivo y elija Abrir en un paquete VSPackage más reciente. En ese momento, el paquete de VS puede ofrecer actualizar el archivo al nuevo formato o abra el archivo y mantener la compatibilidad con versiones anteriores de VSPackage.  
  
> [!NOTE]
>  Puede combinar estos métodos. Por ejemplo, puede ofrecer compatibilidad con versiones anteriores mediante la carga de un archivo anterior y ofrecer a actualizar el formato de archivo cuando el usuario lo guarda.  
  
## <a name="facing-the-problem"></a>Orientada hacia el problema  
 Si desea que varias VSPackages side-by-side para utilizar la misma extensión, debe elegir la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está asociado con la extensión. Estas son dos alternativas:  
  
-   Abra el archivo en la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalado en el equipo del usuario.  
  
     En este enfoque, el instalador es responsable de determinar la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que se incluyen con la entrada del registro escrita para la asociación de archivo. En un paquete de Windows Installer, puede incluir acciones personalizadas para establecer una propiedad que indica la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  En este contexto, "más reciente" significa "última versión admitida." Estas entradas de instalador no detecta automáticamente una versión futura de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Las entradas de [requisitos de sistema de detectar](../extensibility/internals/detecting-system-requirements.md) y en [comandos que debe ser ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md) son similares a los que se presenta aquí y son necesarios para admitir versiones adicionales de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Las siguientes filas de la tabla CustomAction establecen la propiedad DEVENV_EXE_LATEST como una propiedad definida por el AppSearch y RegLocator tablas se describen en [comandos que debe ser ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md). Filas en la tabla InstallExecuteSequence programación las acciones personalizadas al principio de la secuencia de ejecución. Valores de la marca de la columna de condición la lógica de trabajo:  
  
    -   Visual Studio .NET 2002 es la versión más reciente, si es la versión solo está presente.  
  
    -   Visual Studio .NET 2003 es la versión más reciente solo si está presente y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no está presente.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es la versión más reciente si es la versión solo está presente.  
  
     El resultado neto es que DEVENV_EXE_LATEST contiene la ruta de acceso de la última versión de devenv.exe.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Filas de la tabla de CustomAction que determinan la versión más reciente de Visual Studio  
  
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
  
     Puede usar la propiedad DEVENV_EXE_LATEST en la tabla de registro del paquete de Windows Installer para escribir HKEY_CLASSES_ROOT*ProgId*valor predeterminado de la clave ShellOpenCommand, [DEVENV_EXE_LATEST] "%1"  
  
-   Ejecutar un programa de iniciador compartido que puede elegir la mejor opción de versiones disponibles de VSPackage.  
  
     Los desarrolladores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elige este enfoque para controlar los requisitos de los varios formatos de soluciones y proyectos que son el resultado de muchas versiones de complejo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En este enfoque, registra un programa de iniciador como el controlador de extensión. El iniciador examina el archivo y decide qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y el VSPackage puede administrar ese archivo en particular. Por ejemplo, si un usuario abre un archivo que se guardó por última vez mediante una versión concreta del paquete de VS, el iniciador puede iniciar ese VSPackage en la versión correspondiente del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Además, un usuario puede configurar el iniciador para iniciar siempre la versión más reciente. Un iniciador también podría solicitar al usuario que actualice el formato del archivo. Si el formato del archivo incluye un número de versión, el iniciador podría informar a un usuario si el formato de archivo es de una versión posterior a uno o varios de los VSPackages instalados.  
  
     El iniciador debe estar en un componente de Windows Installer que se comparte con todas las versiones del paquete de VS. Este proceso garantiza que la versión más reciente siempre se instala y no se quita hasta que se desinstalen todas las versiones del paquete de VS. De esta forma, se conservan las asociaciones de archivo y otras entradas del registro del componente iniciador incluso si se desinstala una versión de VSPackage.  
  
## <a name="uninstall-and-file-associations"></a>Desinstale y las asociaciones de archivo  
 Desinstalar un paquete VSPackage que escribe las entradas del registro para las asociaciones de archivo, quita las asociaciones de archivo. Por lo tanto, la extensión no tiene ningún programa asociado. Windows Installer no "recuperar" las entradas del registro que se agregaron cuando se instaló el VSPackage. Aquí se muestran algunas maneras de corregir las asociaciones de archivo de un usuario:  
  
-   Utilice un componente compartido iniciador como se describió anteriormente.  
  
-   Pedir al usuario que ejecute una reparación de la versión de VSPackage que desea que el usuario posee la asociación de archivo.  
  
-   Proporcione un programa ejecutable independiente que vuelve a escribir las entradas del Registro adecuados.  
  
-   Proporcione un configuración opciones página o cuadro de diálogo que permite a los usuarios elegir las asociaciones de archivo y para reclamar asociaciones perdidas. Indique a los usuarios para que se ejecute después de la desinstalación.  
  
## <a name="see-also"></a>Vea también  
 [Registrar las extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)