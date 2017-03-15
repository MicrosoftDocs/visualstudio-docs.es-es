---
title: "Administrar asociaciones de archivos en paralelo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verbos, valor predeterminado"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Administrar asociaciones de archivos en paralelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si el paquete VSPackage proporciona las asociaciones de archivo, debe decidir cómo controlar en paralelo las instalaciones en las que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se debe invocar para abrir un archivo.  Los formatos de archivo incompatibles constituyen el problema.  
  
 Los usuarios esperan que una nueva versión de un producto es compatible con versiones anteriores, para poder cargar archivos existentes en una nueva versión sin datos colocados.  Idealmente, el Paquete puede cargar y guardar formatos de archivo de versiones anteriores.  Si eso no es true, debe proporcionar para actualizar el formato de archivo a la nueva versión del Paquete.  El inconveniente de este enfoque es que el archivo actualizado no se puede abrir en la versión anterior.  
  
 Para evitar este problema, puede cambiar extensiones cuando los formatos de archivo pasan a ser incompatibles.  Por ejemplo, la versión 1 del Paquete puede usar la extensión, .mypkg10, y la versión 2 podría utilizar la extensión, .mypkg20.  Esta diferencia identifica el Paquete que abra un archivo determinado.  Si agrega un VSPackages posterior a la lista de programas que está asociado a una antigua extensión, los usuarios pueden hacer clic con el botón secundario en el archivo y elegir para abrirla en un VSPackage más reciente.  En ese momento, el Paquete puede proporcionar para actualizar el archivo al nuevo formato o abrir el archivo y para mantener la compatibilidad con versiones anteriores del Paquete.  
  
> [!NOTE]
>  Puede combinar estos enfoques.  Por ejemplo, puede proporcionar compatibilidad con versiones anteriores cargando un más antiguos archivo y ofrecen para actualizar el formato de archivo cuando el usuario lo guarda.  
  
## Cumplir el Problema  
 Si desea que el múltiplo de en paralelo VSPackages para utilizar la misma extensión, debe elegir la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está asociado a la extensión.  Éstos son dos alternativas:  
  
-   Abra el archivo en la última versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalado en el equipo de usuario.  
  
     En este enfoque, el instalador es responsable de determinar la última versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e incluir que en la entrada de Registro escrita para la asociación de archivo.  En un paquete de Windows Installer, puede incluir acciones personalizadas para establecer una propiedad que indica la última versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  En este contexto, “el más reciente” significa “la última versión compatible.” Estas entradas de instalador automáticamente no detectan una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Las entradas de [Detectar los requisitos del sistema](../extensibility/internals/detecting-system-requirements.md) y en [Comandos que se deben ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md) son similares a las que se muestran aquí y se necesitan para versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Las siguientes filas de la tabla CustomAction establecen la propiedad de DEVENV\_EXE\_LATEST sea una propiedad establecida por las tablas de AppSearch y de RegLocator descritas en [Comandos que se deben ejecutar después de la instalación](../extensibility/internals/commands-that-must-be-run-after-installation.md).  Las filas de la tabla de InstallExecuteSequence programan las acciones personalizadas al flujo de ejecución.  Los valores de la columna de la condición crea el trabajo de lógica:  
  
    -   Visual Studio .NET 2002 es la última versión si es la única versión actual.  
  
    -   Visual Studio .NET 2003 es la última versión sólo si está presente y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no está presente.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es la última versión si es la única versión actual.  
  
     El marcado neto es que DEVENV\_EXE\_LATEST contiene la ruta de la última versión de devenv.exe.  
  
    ### Filas de la tabla CustomAction que determinan la última versión de Visual Studio  
  
    |Acción|Tipo|Origen|Destino|  
    |------------|----------|------------|-------------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2002\]|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2003\]|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2005\]|  
  
    ### filas de la tabla de InstallExecuteSequence que determinan la última versión de Visual Studio  
  
    |Acción|Condition|secuencia|  
    |------------|---------------|---------------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 AND NOT \(DEVENV\_EXE\_2003 OR DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003 AND NOT DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     Puede utilizar la propiedad de DEVENV\_EXE\_LATEST en la tabla de registro del paquete de Windows Installer para escribir el HKEY\_CLASSES\_ROOT \\*ProgID*\\Shell\\Open\\Command key's default value, \[DEVENV\_EXE\_LATEST\] “%1 "  
  
-   Ejecute un programa compartido de inicio que pueda tomar la mejor decisión de versiones disponibles de VSPackage.  
  
     Los desarrolladores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eligieron este enfoque para controlar los requisitos complejos de varios formatos de soluciones y proyectos ese resultado de muchas versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En este enfoque, se registra un programa de inicio como controlador de extensión.  El iniciador examina el archivo y decidir qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y controlar el paquete VSPackage ese archivo.  Por ejemplo, si un usuario abre un archivo que se guardó por última vez por una versión determinada de VSPackage, el iniciador puede iniciar ese Paquete en la versión correspondiente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Además, un usuario podría configurar el iniciador iniciar siempre la última versión.  Un selector también podría pedir un usuario actualizar el formato del archivo.  Si el formato de archivo incluye un número de versión, el iniciador podría informar al usuario si el formato de archivo es de una versión posterior a uno o más de VSPackages instalado.  
  
     El iniciador debe estar en un componente de Windows Installer que se comparte con todas las versiones de VSPackage.  Este proceso garantiza que la última versión instalada siempre y no se quitará hasta que todas las versiones de VSPackage se desinstalen.  De esta manera, siguen las asociaciones de archivo y otras entradas de Registro de componente de inicio aunque una versión del Paquete se desinstala.  
  
## desinstale y las asociaciones de archivo  
 Desinstalar un VSPackage que escriba las entradas del Registro de las asociaciones de archivo quita las asociaciones de archivo.  Por consiguiente, la extensión no tiene un programa asociado.  Windows Installer “no recupera” las entradas del Registro que se agregaron cuando el Paquete se instaló.  He aquí algunas maneras de corregir las asociaciones de archivo de un usuario:  
  
-   Utilizar un componente compartido de inicio como se describió anteriormente.  
  
-   Indique al usuario para ejecutar una reparación de la versión del Paquete que desea poseer la asociación de archivo.  
  
-   Proporcione un programa ejecutable independiente que vuelva a escribir las entradas de Registro adecuadas.  
  
-   Las opciones de configuración la página o el cuadro de diálogo que permiten a los usuarios elegir las asociaciones de archivo y reclamar las asociaciones perdidas.  Pida a los usuarios para ejecutarla después de la desinstalación.  
  
## Vea también  
 [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrar los verbos de extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)