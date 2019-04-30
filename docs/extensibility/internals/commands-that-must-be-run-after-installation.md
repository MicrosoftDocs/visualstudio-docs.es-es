---
title: Los comandos que se deben ejecutar después de la instalación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76960ae9ffce9cc43510ae1ffd34b8350d58214c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418709"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que se deben ejecutar después de la instalación
Si implementa la extensión a través de un *.msi* archivo, debe ejecutar **devenv /setup** como parte de la instalación en orden para Visual Studio detectar sus extensiones.

> [!NOTE]
> La información de este tema se aplica a buscar *devenv.exe* con Visual Studio 2008 y versiones anteriores. Para obtener información sobre cómo detectar *devenv.exe* con versiones posteriores de Visual Studio, consulte [detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Buscar devenv.exe
 Puede encontrar cada versión *devenv.exe* del registro de los valores que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los instaladores escriben, uso la tabla RegLocator y AppSearch tablas para almacenar los valores del registro como propiedades. Para obtener más información, consulte [detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Filas de la tabla RegLocator busque devenv.exe de diferentes versiones de Visual Studio

|Signatura|Raíz|Key|Name|Tipo|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Filas de tabla AppSearch correspondiente RegLocator filas de tablas

|Propiedad|Signatura|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Por ejemplo, el instalador de Visual Studio escribe el valor del registro de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** como *C:\VS2008\Common7\IDE\devenv.exe*, una ruta de acceso completa al archivo ejecutable debe ejecutar el programa de instalación.

> [!NOTE]
> Dado que la columna de tipo de la tabla RegLocator es 2, no es necesario especificar información de versión adicionales en la tabla de la firma.

## <a name="run-devenvexe"></a>Ejecuta devenv.exe
 Después de la acción estándar se ejecuta en el instalador AppSearch, cada propiedad en la tabla AppSearch tiene un valor que apunta a la *devenv.exe* archivo para la versión correspondiente de Visual Studio. Si cualquiera de los valores del registro especificada no están presente, porque no está instalada esa versión de Visual Studio, la propiedad especificada se establece en null.

 Admite Windows Installer que ejecuta un archivo ejecutable al que señala una propiedad a través de la acción personalizada escriba 50. La acción personalizada debe incluir las opciones de ejecución de secuencia de comandos, `msidbCustomActionTypeInScript` (1024) y `msidbCustomActionTypeCommit` (512), para asegurarse de que el VSPackage se ha instalado correctamente antes de integrarlos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [tabla CustomAction](https://docs.microsoft.com/windows/desktop/msi/customaction-table) y [opciones de ejecución de script de acción personalizada](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Acciones personalizadas de tipo 50 especifican la propiedad que contiene el archivo ejecutable como el valor de la columna de origen y los argumentos de línea de comandos en la columna de destino.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Filas de la tabla CustomAction ejecute devenv.exe

|Acción|Tipo|Source|Destino|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Acciones personalizadas se deben crear en la tabla InstallExecuteSequence para programar su ejecución durante la instalación. Utilice la propiedad correspondiente en cada fila de la columna de la condición para evitar que la acción personalizada que se va a ejecutar si esa versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no está instalado en el sistema.

> [!NOTE]
> Propiedades con valores NULL se evalúan como `False` cuando se usa en las condiciones.

 El valor de la columna de secuencia para cada acción personalizada depende de otros valores de secuencia en el paquete de Windows Installer. Los valores de secuencia deben ser tal que la *devenv.exe* cerca de las acciones personalizadas que se ejecutan como posible inmediatamente antes de la acción estándar InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabla InstallExecuteSequence para programar las acciones personalizadas de devenv.exe

|Acción|Condición|Secuencia|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Vea también
- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)