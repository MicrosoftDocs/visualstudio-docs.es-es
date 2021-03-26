---
title: Administrar asociaciones de archivo en paralelo | Microsoft Docs
description: Si el VSPackage proporciona asociaciones de archivo, decida cómo administrar las instalaciones en paralelo en las que una versión concreta de Visual Studio abre un archivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 083eef2454a9e805b1cb8b3e85a6d7d81263a0dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073071"
---
# <a name="manage-side-by-side-file-associations"></a>Administrar asociaciones de archivos en paralelo

Si el VSPackage proporciona asociaciones de archivo, debe decidir cómo administrar las instalaciones en paralelo en las que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se debe invocar una versión determinada de para abrir un archivo. Los formatos de archivo incompatibles han compuesto el problema.

Los usuarios esperan que una nueva versión de un producto sea compatible con versiones anteriores, de modo que los archivos existentes se puedan cargar en una nueva versión sin perder datos. Idealmente, el VSPackage puede cargar y guardar los formatos de archivo de las versiones anteriores. Si no es así, debe ofrecer para actualizar el formato de archivo a la nueva versión del VSPackage. El inconveniente de este enfoque es que el archivo actualizado no se puede abrir en la versión anterior.

Para evitar este problema, puede cambiar las extensiones cuando los formatos de archivo sean incompatibles. Por ejemplo, la versión 1 del VSPackage podría usar la extensión, *. mypkg10* y la versión 2 podría usar la extensión, *. mypkg20*. Esta diferencia identifica el VSPackage que abre un archivo determinado. Si agrega VSPackages más recientes a la lista de programas que están asociados a una extensión anterior, los usuarios pueden hacer clic con el botón derecho en el archivo y elegir abrirlo en un VSPackage más reciente. En ese momento, el VSPackage puede ofrecer para actualizar el archivo al nuevo formato o abrir el archivo y mantener la compatibilidad con versiones anteriores del VSPackage.

> [!NOTE]
> Puede combinar estos enfoques. Por ejemplo, puede ofrecer compatibilidad con versiones anteriores si carga un archivo y una oferta más antiguos para actualizar el formato de archivo cuando el usuario lo guarda.

## <a name="face-the-problem"></a>Enfrente del problema

Si desea que varios VSPackages en paralelo usen la misma extensión, debe elegir la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está asociada con la extensión. A continuación se muestran dos alternativas:

- Abra el archivo en la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalada en el equipo de un usuario.

   En este enfoque, el instalador es responsable de determinar la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e incluirlo en la entrada del registro escrita para la Asociación de archivos. En un paquete de Windows Installer, puede incluir acciones personalizadas para establecer una propiedad que indica la versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > En este contexto, "más reciente" significa "última versión admitida". Estas entradas del instalador no detectarán automáticamente una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Las entradas para [detectar los requisitos del sistema](../extensibility/internals/detecting-system-requirements.md) y en los [comandos que deben ejecutarse después](../extensibility/internals/commands-that-must-be-run-after-installation.md) de la instalación son similares a las que se presentan aquí y son necesarias para admitir versiones adicionales de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Las siguientes filas de la tabla CustomAction establecen la propiedad DEVENV_EXE_LATEST como una propiedad establecida por las tablas AppSearch y RegLocator descritas en los [comandos que se deben ejecutar después](../extensibility/internals/commands-that-must-be-run-after-installation.md)de la instalación. Las filas de la tabla InstallExecuteSequence programan las acciones personalizadas al principio de la secuencia de ejecución. Los valores de la columna condición hacen que la lógica funcione:

  - Visual Studio .NET 2002 es la versión más reciente si es la única versión presente.

  - Visual Studio .NET 2003 es la versión más reciente solo si está presente y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no está presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es la versión más reciente si se trata de la única versión presente.

    El resultado neto es que DEVENV_EXE_LATEST contiene la ruta de acceso de la versión más reciente de devenv.exe.

  **Filas de la tabla CustomAction que determinan la versión más reciente de Visual Studio**

  |Acción|Tipo|Source|Destino|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence filas de la tabla que determinan la versión más reciente de Visual Studio**

  |Acción|Condición|Secuencia|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 Y NO (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 Y NO DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Puede usar la propiedad DEVENV_EXE_LATEST de la tabla del registro del paquete de Windows Installer para escribir el valor predeterminado de HKEY_CLASSES_ROOT la clave **ShellOpenCommand *ProgID*** , [DEVENV_EXE_LATEST] "%1".

- Ejecute un programa iniciador compartido que pueda tomar la mejor elección de las versiones disponibles de VSPackage.

   Los desarrolladores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eligen este enfoque para controlar los requisitos complejos de los distintos formatos de soluciones y proyectos que se derivan de muchas versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . En este enfoque, se registra un programa iniciador como el controlador de extensiones. El iniciador examina el archivo y decide qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y el VSPackage puede controlar ese archivo en particular. Por ejemplo, si un usuario abre un archivo que se guardó por última vez en una versión determinada del VSPackage, el iniciador puede iniciar ese VSPackage en la versión correspondiente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Además, un usuario puede configurar el iniciador para que siempre inicie la versión más reciente. Un iniciador también puede pedir a un usuario que actualice el formato del archivo. Si el formato del archivo incluye un número de versión, el iniciador podría informar a un usuario si el formato de archivo es de una versión posterior a uno o varios de los VSPackages instalados.

   El iniciador debe encontrarse en un componente de Windows Installer que se comparte con todas las versiones del VSPackage. Este proceso garantiza que la versión más reciente esté siempre instalada y no se quitará hasta que se desinstalen todas las versiones del VSPackage. De esta manera, las asociaciones de archivos y otras entradas del registro del componente del iniciador se conservan incluso si se desinstala una versión del VSPackage.

## <a name="uninstall-and-file-associations"></a>Desinstalar y asociaciones de archivo

Al desinstalar un VSPackage que escribe las entradas del registro para las asociaciones de archivo, se quitan las asociaciones de archivo. Por lo tanto, la extensión no tiene ningún programa asociado. Windows Installer no "recupera" las entradas del registro que se agregaron cuando se instaló el VSPackage. A continuación se indican algunas maneras de corregir las asociaciones de archivo de un usuario:

- Use un componente iniciador compartido como se ha descrito anteriormente.

- Indique al usuario que ejecute una reparación de la versión del VSPackage en la que el usuario desea poseer la Asociación de archivos.

- Proporcione un programa ejecutable independiente que reescriba las entradas adecuadas del registro.

- Proporcione una página o un cuadro de diálogo de opciones de configuración que permita a los usuarios elegir asociaciones de archivos y reclamar asociaciones perdidas. Indicar a los usuarios que lo ejecuten después de la desinstalación.

## <a name="see-also"></a>Consulte también

- [Registrar las extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrar verbos para las extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
