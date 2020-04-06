---
title: Comandos que se deben ejecutar después de la instalación . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709469"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que se deben ejecutar después de la instalación
Si implementa la extensión a través de un archivo *.msi,* debe ejecutar **devenv /setup** como parte de la instalación para que Visual Studio detecte las extensiones.

> [!NOTE]
> La información de este tema se aplica a la búsqueda *de devenv.exe* con Visual Studio 2008 y versiones anteriores. Para obtener información acerca de cómo detectar *devenv.exe* con versiones posteriores de Visual Studio, vea [Detectar requisitos](../../extensibility/internals/detecting-system-requirements.md)del sistema .

## <a name="find-devenvexe"></a>Encontrar devenv.exe
 Puede localizar *devenv.exe* de cada versión [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a partir de los valores del Registro que escriben los instaladores, mediante la tabla RegLocator y las tablas de AppSearch para almacenar los valores del Registro como propiedades. Para obtener más información, consulte [Detectar requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Filas de tabla RegLocator para localizar devenv.exe de diferentes versiones de Visual Studio

|Signature|Root|Clave|Nombre|Tipo|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE-Microsoft-VisualStudio-7.0-Setup-VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE-Microsoft-VisualStudio-7.1-Setup-VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE-Microsoft-VisualStudio-8.0-Setup-VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE-Microsoft-VisualStudio-9.0-Setup-VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Filas de tabla de AppSearch para las filas de tabla RegLocator correspondientes

|Propiedad|Signature|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Por ejemplo, el instalador de Visual Studio escribe el valor del Registro de **HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 9,0, Configuración, VS, EnvironmentPath,** como *C:- VS2008, Common7, IDE, devenv.exe,* una ruta de acceso completa al archivo ejecutable que debe ejecutar el instalador.

> [!NOTE]
> Dado que la columna Type de la tabla RegLocator es 2, no es necesario especificar información de versión adicional en la tabla Signature.

## <a name="run-devenvexe"></a>Ejecutar devenv.exe
 Después de que la acción estándar de AppSearch se ejecuta en el instalador, cada propiedad de la tabla AppSearch tiene un valor que apunta al archivo *devenv.exe* para la versión correspondiente de Visual Studio. Si alguno de los valores del Registro especificados no está presente, porque esa versión de Visual Studio no está instalada, la propiedad especificada se establece en null.

 Windows Installer admite la ejecución de un ejecutable al que apunta una propiedad a través del tipo de acción personalizado 50. La acción personalizada debe incluir las `msidbCustomActionTypeInScript` opciones de ejecución en `msidbCustomActionTypeCommit` script, (1024) y (512), para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]asegurarse de que el VSPackage se ha instalado correctamente antes de integrarlo en . Para obtener más información, consulte [Tabla CustomAction](/windows/desktop/msi/customaction-table) y Opciones de ejecución de [acción personalizada en script](/windows/desktop/msi/custom-action-in-script-execution-options).

 Las acciones personalizadas de tipo 50 especifican la propiedad que contiene el ejecutable como el valor de la columna Origen y los argumentos de línea de comandos de la columna Destino.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Filas de tabla CustomAction para ejecutar devenv.exe

|Acción|Tipo|Source|Destino|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Las acciones personalizadas se deben crear en la tabla InstallExecuteSequence para programarlas para su ejecución durante la instalación. Utilice la propiedad correspondiente en cada fila de la columna Condición [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para evitar que se ejecute la acción personalizada si esa versión de no está instalada en el sistema.

> [!NOTE]
> Las propiedades con valores `False` null se evalúan cuando se usan en condiciones.

 El valor de la columna Secuencia para cada acción personalizada depende de otros valores de secuencia del paquete de Windows Installer. Los valores de secuencia deben ser tales que las acciones personalizadas *devenv.exe* se ejecuten lo más cerca posible de inmediatamente antes de la acción estándar InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence tabla para programar las acciones personalizadas devenv.exe

|Acción|Condición|Secuencia|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Vea también
- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
