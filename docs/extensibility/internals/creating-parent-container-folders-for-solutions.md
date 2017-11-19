---
title: "La creación de carpetas de contenedor primario para soluciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>La creación de carpetas de contenedor primario para soluciones
En la API de complemento de Control de origen de la versión 1.2, un usuario puede especificar un destino de control de código fuente de raíz única para todos los proyectos Web dentro de la solución. Esta raíz solo se llama a una raíz de unificado Super (SUR).  
  
 En la API de complemento de Control de origen de la versión 1.1, si el usuario agregó una solución con varios proyectos al control de código fuente, se pedirá al usuario para especificar un destino de control de código fuente para cada proyecto Web.  
  
## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE casi siempre crea una carpeta SUR al agregar una solución al control de código fuente. En concreto, lo hace en los casos siguientes:  
  
-   El proyecto es un proyecto Web de recurso compartido de archivos.  
  
-   Hay distintas unidades para el proyecto y el archivo de solución.  
  
-   Hay diversos recursos compartidos para el proyecto y el archivo de solución.  
  
-   Proyectos se han agregado por separado (en una solución controlada por código fuente).  
  
 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se recomienda que el nombre de la carpeta SUR sea el mismo que el nombre de la solución sin la extensión. En la tabla siguiente se resume el comportamiento en las dos versiones.  
  
|Característica|tSource API versión 1.1 de complemento de Control|Versión 1.2 de la API de complemento de Control de código fuente|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Agregar solución al control de código fuente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Agregar proyecto a la solución controlados por código fuente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Nota:** Visual Studio, se da por supuesto que una solución es un elemento secundario directo del SUR.|  
  
## <a name="examples"></a>Ejemplos  
 En la tabla siguiente se muestra dos ejemplos. En ambos casos, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se pedirá al usuario una ubicación de destino para la solución bajo control de código fuente hasta el *user_choice* se especifica como un destino. Cuando se especifica la user_choice, la solución y dos proyectos se agregan sin preguntar al usuario para destinos de control de código fuente.  
  
|Contiene la solución|En ubicaciones de disco|Estructura de base de datos predeterminada|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\Web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*  /sln1/win1|  
  
 La carpeta SUR y subcarpetas se crean independientemente de si la operación se cancela o falla debido a un error. No se quitan automáticamente en las condiciones de error o cancel.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]valores predeterminados al comportamiento de la versión 1.1, si el complemento de control de código fuente no devuelve `SCC_CAP_CREATESUBPROJECT` y `SCC_CAP_GETPARENTPROJECT` marcas de capacidad. Además, los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , puede revertir al comportamiento de versión 1.1 estableciendo el valor de la siguiente clave en DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)