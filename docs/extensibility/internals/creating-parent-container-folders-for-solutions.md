---
title: Creación de carpetas contenedoras primarias para soluciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87fbda8cb55d0d2a6ef9f21a2a7878d4babd3fe6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830697"
---
# <a name="create-parent-container-folders-for-solutions"></a>Crear carpetas de contenedor para las soluciones de primario
En el origen de Control de complemento de API versión 1.2, un usuario puede especificar un destino de control de origen de raíz única para todos los proyectos web dentro de la solución. Esta raíz solo se llama a una raíz de Unified Super (SUR).  
  
 En fuente Control complemento API versión 1.1, si el usuario agrega una solución de varios proyectos al control de código fuente, se solicita el usuario para especificar un destino de control de código fuente para cada proyecto web.  
  
## <a name="new-capability-flags"></a>Marcadores de capacidad nueva  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE casi siempre crea una carpeta Surname al agregar una solución al control de código fuente. En concreto, lo hace en los casos siguientes:  
  
-   El proyecto es un proyecto web de recurso compartido de archivos.  
  
-   Hay distintas unidades para el proyecto y el archivo de solución.  
  
-   Existen diversos recursos compartidos para el proyecto y el archivo de solución.  
  
-   Los proyectos se agregaron por separado (en una solución controlados por código fuente).  
  

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se recomienda que el nombre de la carpeta Surname ser el mismo que el nombre de la solución sin la extensión. En la tabla siguiente se resume el comportamiento en las dos versiones.  
  
|Característica|Versión 1.1 de API de complemento de Control de código fuente|Versión 1.2 de la API de complemento de Control de código fuente|  
|-------------| - | - |  
|Agregar solución al control de código fuente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Agregar a solución controlados por código fuente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:** Visual Studio, se da por supuesto que una solución es un elemento secundario directo del SUR.|  
  
## <a name="examples"></a>Ejemplos  
 En la tabla siguiente se muestra dos ejemplos. En ambos casos, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario se le solicitará una ubicación de destino para la solución bajo control de código fuente hasta el *user_choice* se especifica como un destino. Cuando se especifica la user_choice, la solución y dos proyectos se agregan sin preguntar al usuario para destinos de control de código fuente.  
  
|Contiene la solución|En las ubicaciones de disco|Estructura de base de datos predeterminada|  
|-----------------------|-----------------------|--------------------------------|  
|*sln1.sln*<br /><br /> Web1<br /><br /> WEB2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/C/Web1<br /><br /> $/ < user_choice > / Web2|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/D/web1<br /><br /> $/ < user_choice >/sln1/win1|  
  
 La carpeta SUR y subcarpetas se crean independientemente de si la operación se cancela o falla debido a un error. No se quitan automáticamente en las condiciones de error o cancelación.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el valor predeterminado es el comportamiento de versión 1.1 si el complemento de control de código fuente no devuelve `SCC_CAP_CREATESUBPROJECT` y `SCC_CAP_GETPARENTPROJECT` marcadores de capacidad. Además, los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede elegir revertir al comportamiento de la versión 1.1 estableciendo el valor de la siguiente clave a *DWORD: 00000001*:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *DWORD: 00000001*
  
## <a name="see-also"></a>Vea también  
 [Novedades de la versión 1.2 de origen Control complemento de API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)