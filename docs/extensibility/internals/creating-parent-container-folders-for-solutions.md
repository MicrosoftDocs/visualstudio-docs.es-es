---
title: "Creaci&#243;n de carpetas de contenedor primario para soluciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluciones, crear contenedores de primario"
  - "origen control complementos, crear contenedores de primario"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de carpetas de contenedor primario para soluciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En la versión de 1,2 de la API de Control de código fuente, un usuario puede especificar un único destino de control de origen de la raíz para todos los proyectos web dentro de la solución.  Esta única raíz se denomina raíz \(SUR\) de Super Unified.  
  
 En la versión de 1,1 de la API de Control de código fuente, si el usuario ha agregado una solución de multiproject al control de código fuente, ha preguntado al usuario especificar un destino de control de código fuente para cada proyecto web.  
  
## Nuevos marcadores de capacidad  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## nuevas funciones  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE crea casi siempre una carpeta de SUR al agregar una solución al control de código fuente.  Específicamente, lo hace en los casos siguientes:  
  
-   El proyecto es un proyecto web de la acción de archivo.  
  
-   Hay diferentes unidades para el proyecto y el archivo de solución.  
  
-   Hay distintas acciones para el proyecto y el archivo de solución.  
  
-   Los proyectos se agregaron por separado \(en una solución bajo control de código\).  
  
 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se sugiere que el nombre de la carpeta de SUR es igual que el nombre de la solución sin extensión.  La tabla siguiente se resume el comportamiento de las dos versiones.  
  
|Característica|versión de complemento 1,1 de la API del Control de tSource|Versión 1,2 de la API del complemento de control de código fuente|  
|--------------------|-----------------------------------------------------------------|-----------------------------------------------------------------------|  
|Agregar la solución al SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|agregue el proyecto a la solución bajo control de código|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio supone que una solución es un elemento secundario directo de SUR.|  
  
## Ejemplos  
 La tabla siguiente se muestran dos ejemplos.  En ambos casos, el usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para una ubicación de destino para la solución bajo control de código fuente hasta que *user\_choice* se especifique como destino. Cuando se especifica el user\_choice, la solución y dos proyectos se agregan sin pedir al usuario para los destinos de control de código fuente.  
  
|la solución contiene|En ubicaciones del disco|estructura predeterminada de la base de datos|  
|--------------------------|------------------------------|---------------------------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C: \\Solutions \\ sln1<br /><br /> C: \\Inetpub\\wwwroot\\Web 1<br /><br /> \\ \\ servidor \\ wwwroot$ \\ web2|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C: \\Solutions \\ sln1<br /><br /> d: \\Inetpub\\wwwroot\\Web 1<br /><br /> C: \\solutions\\sln1\\Win 1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 La carpeta y subcarpetas de SUR se crean independientemente de si se cancela la operación o se produce un error debido a un error.  Automáticamente no se quitan de la cancelación o condiciones de error.  
  
 valores predeterminados de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al comportamiento de la versión 1,1 si el complemento de control de código fuente no devuelve `SCC_CAP_CREATESUBPROJECT` y los marcadores de la capacidad de `SCC_CAP_GETPARENTPROJECT` .  Además, los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden elegir para revertir al comportamiento de la versión 1,1 estableciendo el valor de la clave siguiente a DWORD: 00000001:  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl ": 00000001  
  
## Vea también  
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)