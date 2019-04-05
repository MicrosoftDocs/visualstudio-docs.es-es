---
title: Creación de carpetas contenedoras primarias para soluciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58996737"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Creación de carpetas contenedoras primarias para soluciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la API de complemento de Control de origen de la versión 1.2, un usuario puede especificar un destino de control de origen de raíz única para todos los proyectos Web dentro de la solución. Esta raíz solo se llama a una raíz de Unified Super (SUR).  
  
 En la API de complemento de Control de origen de la versión 1.1, si el usuario agrega una solución de varios proyectos al control de código fuente, se solicita el usuario para especificar un destino de control de código fuente para cada proyecto Web.  
  
## <a name="new-capability-flags"></a>Marcadores de capacidad nueva  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE casi siempre crea una carpeta Surname al agregar una solución al control de código fuente. En concreto, lo hace en los casos siguientes:  
  
- El proyecto es un proyecto Web de recurso compartido de archivos.  
  
- Hay distintas unidades para el proyecto y el archivo de solución.  
  
- Existen diversos recursos compartidos para el proyecto y el archivo de solución.  
  
- Los proyectos se agregaron por separado (en una solución controlados por código fuente).  
  
  En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se sugiere que el nombre de la carpeta Surname ser el mismo que el nombre de la solución sin la extensión. En la tabla siguiente se resume el comportamiento en las dos versiones.  
  
|Característica|tSource API versión 1.1 de complemento de Control|Versión 1.2 de la API de complemento de Control de código fuente|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Agregar solución al control de código fuente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Agregar a solución controlados por código fuente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Note:**  Visual Studio, se da por supuesto que una solución es un elemento secundario directo del SUR.|  
  
## <a name="examples"></a>Ejemplos  
 En la tabla siguiente se muestra dos ejemplos. En ambos casos, el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usuario se le solicitará una ubicación de destino para la solución bajo control de código fuente hasta el *user_choice* se especifica como un destino. Cuando se especifica la user_choice, la solución y dos proyectos se agregan sin preguntar al usuario para destinos de control de código fuente.  
  
|Contiene la solución|En las ubicaciones de disco|Estructura de base de datos predeterminada|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 La carpeta SUR y subcarpetas se crean independientemente de si la operación se cancela o falla debido a un error. No se quitan automáticamente en las condiciones de error o cancelación.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el valor predeterminado es el comportamiento de versión 1.1 si el complemento de control de código fuente no devuelve `SCC_CAP_CREATESUBPROJECT` y `SCC_CAP_GETPARENTPROJECT` marcadores de capacidad. Además, los usuarios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puede revertir al comportamiento de la versión 1.1 mediante el valor de la siguiente clave DWORD: 00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
