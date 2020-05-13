---
title: Gestión de asociaciones de archivos en paralelo Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702759"
---
# <a name="manage-side-by-side-file-associations"></a>Administrar asociaciones de archivos en paralelo

Si el VSPackage proporciona asociaciones de archivos, debe decidir cómo controlar las [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalaciones en paralelo en las que se debe invocar una versión determinada de debe invocarse para abrir un archivo. Los formatos de archivo incompatibles agravan el problema.

Los usuarios esperan que una nueva versión de un producto sea compatible con versiones anteriores, de modo que los archivos existentes se puedan cargar en una nueva versión sin perder datos. Idealmente, el VSPackage puede cargar y guardar los formatos de archivo de versiones anteriores. Si eso no es cierto, debe ofrecer actualizar el formato de archivo a la nueva versión de su VSPackage. La desventaja de este enfoque es que el archivo actualizado no se puede abrir en la versión anterior.

Para evitar este problema, puede cambiar las extensiones cuando los formatos de archivo se vuelvan incompatibles. Por ejemplo, la versión 1 de su VSPackage podría usar la extensión *,mypkg10*y la versión 2 podría usar la extensión *.mypkg20*. Esta diferencia identifica el VSPackage que abre un archivo determinado. Si agrega VSPackages más recientes a la lista de programas que están asociados con una extensión antigua, los usuarios pueden hacer clic con el botón derecho en el archivo y elegir abrirlo en un VSPackage más reciente. En ese momento, el VSPackage puede ofrecer actualizar el archivo al nuevo formato o abrir el archivo y mantener la compatibilidad con versiones anteriores del VSPackage.

> [!NOTE]
> Puede combinar estos enfoques. Por ejemplo, puede ofrecer compatibilidad con versiones anteriores cargando un archivo anterior y ofrecer actualizar el formato de archivo cuando el usuario lo guarde.

## <a name="face-the-problem"></a>Enfréntate al problema

Si desea que varios VSPackages en paralelo para usar la misma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión, debe elegir la versión de que está asociada con la extensión. Aquí hay dos alternativas:

- Abra el archivo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la versión más reciente de instalado en el equipo del usuario.

   En este enfoque, el instalador es responsable [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de determinar la versión más reciente de la entrada del registro escrita para la asociación de archivos e incluirla en ella. En un paquete de Windows Installer, puede incluir acciones personalizadas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]para establecer una propiedad que indique la versión más reciente de .

  > [!NOTE]
  > En este contexto, "último" significa "última versión compatible." Estas entradas del instalador no detectarán [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automáticamente una versión posterior de . Las entradas en [Detectar requisitos](../extensibility/internals/detecting-system-requirements.md) del sistema y en [Comandos que deben ejecutarse después](../extensibility/internals/commands-that-must-be-run-after-installation.md) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de la instalación son similares a las que se presentan aquí y son necesarias para admitir versiones adicionales de .

   Las siguientes filas de la tabla CustomAction establecen la propiedad DEVENV_EXE_LATEST para que sea una propiedad establecida por las tablas AppSearch y RegLocator que se describen en [Comandos que se deben ejecutar después](../extensibility/internals/commands-that-must-be-run-after-installation.md)de la instalación. Las filas de la tabla InstallExecuteSequence programan las acciones personalizadas al principio de la secuencia de ejecución. Los valores de la columna Condición hacen que la lógica funcione:

  - Visual Studio .NET 2002 es la versión más reciente si es la única versión actual.

  - Visual Studio .NET 2003 es la versión [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] más reciente solo si está presente y no está presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]es la última versión si es la única versión actual.

    El resultado neto es que DEVENV_EXE_LATEST contiene la ruta de acceso de la última versión de devenv.exe.

  **Filas de tabla CustomAction que determinan la versión más reciente de Visual Studio**

  |Acción|Tipo|Source|Destino|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence filas de tabla que determinan la versión más reciente de Visual Studio**

  |Acción|Condición|Secuencia|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 Y NO (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 Y NO DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Puede usar la propiedad DEVENV_EXE_LATEST de la tabla Registry del paquete de Windows Installer para escribir el valor predeterminado de la clave ***HKEY_CLASSES_ROOT ProgId*ShellOpenCommand,** [DEVENV_EXE_LATEST] "%1"

- Ejecute un programa de iniciador compartido que puede hacer la mejor elección de las versiones de VSPackage disponibles.

   Los desarrolladores eligieron [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] este enfoque para manejar los complejos requisitos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]los múltiples formatos de soluciones y proyectos que resultan de muchas versiones de . En este enfoque, se registra un programa de iniciador como el controlador de extensión. El iniciador examina el archivo y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] decide qué versión de y el VSPackage puede controlar ese archivo en particular. Por ejemplo, si un usuario abre un archivo que se guardó por última vez por una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]versión determinada de su VSPackage, el iniciador puede iniciar ese VSPackage en la versión coincidente de . Además, un usuario podría configurar el lanzador para iniciar siempre la última versión. Un lanzador también podría pedir a un usuario que actualice el formato del archivo. Si el formato del archivo incluye un número de versión, el iniciador podría informar a un usuario si el formato de archivo procede de una versión posterior a uno o varios de los VSPackages instalados.

   El iniciador debe estar en un componente de Windows Installer que se comparte con todas las versiones de su VSPackage. Este proceso garantiza que la versión más reciente siempre está instalada y no se quita hasta que se desinstalan todas las versiones del VSPackage. De este modo, las asociaciones de archivos y otras entradas del registro del componente de iniciador se conservan incluso si se desinstala una versión del VSPackage.

## <a name="uninstall-and-file-associations"></a>Desinstalación y asociaciones de archivos

Desinstalación de un VSPackage que escribe entradas del Registro para asociaciones de archivos quita las asociaciones de archivos. Por lo tanto, la extensión no tiene programas asociados. Windows Installer no "recupera" las entradas del Registro que se agregaron cuando se instaló el VSPackage. Aquí hay algunas maneras de arreglar las asociaciones de archivos de un usuario:

- Utilice un componente de iniciador compartido como se ha descrito anteriormente.

- Indique al usuario que ejecute una reparación de la versión del VSPackage que el usuario desea poseer la asociación de archivos.

- Proporcione un programa ejecutable independiente que vuelva a escribir las entradas de registro adecuadas.

- Proporcione una página de opciones de configuración o un cuadro de diálogo que permita a los usuarios elegir asociaciones de archivos y reclamar asociaciones perdidas. Indique a los usuarios que lo ejecuten después de la desinstalación.

## <a name="see-also"></a>Vea también

- [Registrar extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrar verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
