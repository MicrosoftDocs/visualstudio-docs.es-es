---
title: "Comandos que se deben ejecutar despu&#233;s de la instalaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos posteriores a la instalación"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Comandos que se deben ejecutar despu&#233;s de la instalaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si implementa la extensión a través de un archivo .msi, debe ejecutar `devenv /setup` como parte de su instalación en orden para Visual Studio descubrir sus extensiones.  
  
> [!NOTE]
>  La información de este tema se aplica a la búsqueda de DevEnv en Visual Studio 2008 y versiones anteriores. Para obtener información sobre cómo detectar DevEnv con versiones posteriores de Visual Studio, consulte [Detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## Buscar devenv.exe  
 Puede buscar cada versión devenv.exe desde el registro, los valores que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] escriben instaladores, utilizando la tabla RegLocator y AppSearch para almacenar los valores del registro como propiedades. Para obtener más información, consulta [Detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### Filas de la tabla de RegLocator busque devenv.exe de diferentes versiones de Visual Studio  
  
|Signature\_|Raíz|Tecla|Nombre|Tipo|  
|-----------------|----------|-----------|------------|----------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### Filas de tabla AppSearch correspondiente RegLocator filas de tabla  
  
|Propiedad|Signature\_|  
|---------------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 Por ejemplo, el instalador de Visual Studio escribe el valor del registro de **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** como **C:\\VS2008\\Common7\\IDE\\devenv.exe**, una ruta de acceso completa al archivo ejecutable debe ejecutar el programa de instalación.  
  
 **Nota** porque la columna de tipo RegLocator es 2, no es necesario especificar información de versión adicional en la tabla de la firma.  
  
## Ejecuta devenv.exe  
 Después de AppSearch acción estándar se ejecuta en el programa de instalación, cada propiedad de la tabla AppSearch tiene un valor que señala el archivo devenv.exe para la versión correspondiente de Visual Studio. Si cualquiera de los valores del registro especificada no están presente, porque esa versión de Visual Studio no está instalada, se establece la propiedad especificada en null.  
  
 Windows Installer admite la ejecuta un archivo ejecutable al que señala una propiedad a través de la acción personalizada del tipo 50. La acción personalizada debe incluir las opciones de ejecución de secuencia de comandos, msidbCustomActionTypeInScript \(1024\) y msidbCustomActionTypeCommit \(512\), para asegurarse de que se ha instalado correctamente el VSPackage antes de integrar en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte la tabla CustomAction y opciones de ejecución de secuencia de comandos de acción personalizada.  
  
 Acciones personalizadas de tipo 50 especifican la propiedad que contiene el archivo ejecutable como el valor de la columna de origen y los argumentos de línea de comandos en la columna de destino.  
  
### Filas de la tabla CustomAction ejecute devenv.exe  
  
|Acción|Tipo|Origen|Destino|  
|------------|----------|------------|-------------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/Setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/Setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/Setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/Setup|  
  
 Acciones personalizadas deben crearse en la tabla InstallExecuteSequence para programar su ejecución durante la instalación. Utilice la propiedad correspondiente en cada fila de la columna condición para evitar que la acción personalizada que se va a ejecutar si esa versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no está instalado en el sistema.  
  
> [!NOTE]
>  `Null` propiedades que se evalúan como `False` cuando se utiliza en las condiciones.  
  
 El valor de la columna de secuencia para cada acción personalizada depende de otros valores de secuencia en el paquete de Windows Installer. Los valores de secuencia deben ser tal que las acciones personalizadas de devenv.exe ejecutar como cerca posible inmediatamente antes de la acción de InstallFinalize estándar.  
  
### Tabla InstallExecuteSequence para programar las acciones personalizadas de devenv.exe  
  
|Acción|Condición|Secuencia|  
|------------|---------------|---------------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## Vea también  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)