---
title: "Los comandos que se deben ejecutar después de la instalación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fef2c76364c1ca1398aef3b94226e7a9a365cf1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que se deben ejecutar después de la instalación
Si implementa la extensión a través de un archivo .msi, debe ejecutar `devenv /setup` como parte de la instalación en orden para Visual Studio detectar las extensiones.  
  
> [!NOTE]
>  La información de este tema se aplica a la búsqueda de DevEnv con Visual Studio 2008 y versiones anteriores. Para obtener información sobre cómo detectar DevEnv con versiones posteriores de Visual Studio, vea [requisitos de sistema de detectar](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Buscar devenv.exe  
 Puede buscar cada versión devenv.exe del registro de los valores que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] escriben instaladores, con las tablas RegLocator y AppSearch para almacenar los valores del registro como propiedades. Para obtener más información, consulte [requisitos de sistema de detectar](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Filas de la tabla de RegLocator busque devenv.exe de distintas versiones de Visual Studio  
  
|Signature_|Raíz|Key|Name|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Filas de la tabla AppSearch para filas de tabla RegLocator correspondientes  
  
|Propiedad|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Por ejemplo, el instalador de Visual Studio escribe el valor del registro de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** como **C:\VS2008\Common7\IDE\devenv.exe**, una ruta de acceso completa al archivo ejecutable debe ejecutar el programa de instalación.  
  
 **Tenga en cuenta** porque la columna de tipo RegLocator es 2, no es necesario especificar información de versión adicional en la tabla de firma.  
  
## <a name="running-devenvexe"></a>Ejecuta devenv.exe  
 Después de AppSearch acción estándar se ejecuta en el programa de instalación, cada propiedad en la tabla AppSearch tiene un valor que señala el archivo devenv.exe para la versión correspondiente de Visual Studio. Si alguno de los valores del registro especificada no están presente, porque no está instalada esa versión de Visual Studio, la propiedad especificada se establece en null.  
  
 Admite Windows Installer ejecuta un ejecutable a la que señala una propiedad a través de la acción personalizada escriba 50. La acción personalizada debe incluir las opciones de ejecución de secuencia de comandos, msidbCustomActionTypeInScript (1024) y msidbCustomActionTypeCommit (512), para asegurarse de que el VSPackage se ha instalado correctamente antes de integrarlo en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, vea la tabla CustomAction y opciones de ejecución de secuencia de comandos de acción personalizado.  
  
 Acciones personalizadas de tipo 50 especifican la propiedad que contiene el archivo ejecutable como el valor de la columna de origen y los argumentos de línea de comandos en la columna de destino.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Filas de la tabla CustomAction ejecute devenv.exe  
  
|Acción|Tipo|Origen|Destino|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Acciones personalizadas se deben crear en la tabla InstallExecuteSequence y programar su ejecución durante la instalación. Use la propiedad correspondiente en cada fila de la columna de condición para evitar que la acción personalizada que se va a ejecutar si esa versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no está instalado en el sistema.  
  
> [!NOTE]
>  `Null`propiedades que se evalúan como `False` cuando se utiliza en las condiciones.  
  
 El valor de la columna de secuencia para cada acción personalizada depende de otros valores de secuencia en el paquete de Windows Installer. Valores de secuencia deben ser tal que las acciones personalizadas de devenv.exe de identificación de cerca posible inmediatamente antes de la acción estándar InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabla InstallExecuteSequence para programar las acciones personalizadas de devenv.exe  
  
|Acción|Condición|Secuencia|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)