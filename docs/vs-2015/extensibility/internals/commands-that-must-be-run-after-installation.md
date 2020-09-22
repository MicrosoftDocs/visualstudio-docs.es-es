---
title: Comandos que se deben ejecutar después de la instalación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843146"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que se deben ejecutar después de la instalación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Si implementa la extensión a través de un archivo. msi, debe ejecutar `devenv /setup` como parte de la instalación para que Visual Studio detecte las extensiones.  
  
> [!NOTE]
> La información de este tema se aplica a la búsqueda de DevEnv con Visual Studio 2008 y versiones anteriores. Para obtener información sobre cómo detectar DevEnv con versiones posteriores de Visual Studio, consulte [detectar requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Buscar devenv.exe  
 Puede localizar los devenv.exe de cada versión a partir de los valores del registro que los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] instaladores escriben, mediante la tabla RegLocator y la tabla AppSearch para almacenar los valores del registro como propiedades. Para obtener más información, consulte [detectar requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator filas de la tabla para buscar devenv.exe de distintas versiones de Visual Studio  
  
|Signature_|Root|Clave|Nombre|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch filas de la tabla de RegLocator correspondientes filas de la tabla  
  
|Propiedad|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Por ejemplo, el instalador de Visual Studio escribe el valor del registro de **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** como **C:\VS2008\Common7\IDE\devenv.exe**, una ruta de acceso completa al archivo ejecutable que debe ejecutar el instalador.  
  
 **Nota:** Dado que la columna de tipo RegLocator es 2, no es necesario especificar información de versión adicional en la tabla de firma.  
  
## <a name="running-devenvexe"></a>Ejecutar devenv.exe  
 Después de que la acción estándar AppSearch se ejecute en el instalador, cada propiedad de la tabla AppSearch tiene un valor que apunta al archivo devenv.exe para la versión correspondiente de Visual Studio. Si alguno de los valores especificados del registro no está presente, porque la versión de Visual Studio no está instalada, la propiedad especificada se establece en NULL.  
  
 Windows Installer admite la ejecución de un ejecutable al que una propiedad apunta a través del tipo de acción personalizada 50. La acción personalizada debe incluir las opciones de ejecución en el script, msidbCustomActionTypeInScript (1024) y msidbCustomActionTypeCommit (512), para asegurarse de que el VSPackage se ha instalado correctamente antes de integrarlo en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Para obtener más información, consulte la tabla CustomAction y la acción personalizada en las opciones de ejecución del script.  
  
 Las acciones personalizadas de tipo 50 especifican la propiedad que contiene el ejecutable como el valor de la columna de origen y los argumentos de la línea de comandos en la columna de destino.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Filas de la tabla CustomAction para ejecutar devenv.exe  
  
|Acción|Tipo|Source|Destino|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Las acciones personalizadas se deben crear en la tabla InstallExecuteSequence para programarlas para su ejecución durante la instalación. Utilice la propiedad correspondiente en cada fila de la columna condición para evitar que se ejecute la acción personalizada si esa versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no está instalada en el sistema.  
  
> [!NOTE]
> `Null` las propiedades se evalúan como `False` cuando se usan en condiciones.  
  
 El valor de la columna de secuencia para cada acción personalizada depende de otros valores de secuencia del paquete de Windows Installer. Los valores de secuencia deben ser de tal forma que las acciones personalizadas devenv.exe se ejecuten lo más cerca posible de inmediato antes de la acción estándar InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabla InstallExecuteSequence para programar las acciones personalizadas de devenv.exe  
  
|Acción|Condición|Secuencia|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Consulte también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
