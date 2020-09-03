---
title: Crear carpetas de contenedores principales para soluciones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709094"
---
# <a name="create-parent-container-folders-for-solutions"></a>Crear carpetas de contenedores principales para las soluciones
En la API del complemento de control de código fuente versión 1,2, un usuario puede especificar un único destino de control de código fuente raíz para todos los proyectos Web de la solución. Esta única raíz se denomina raíz superunificada (SUR).

 En la API del complemento de control de código fuente versión 1,1, si el usuario agregó una solución de varios proyectos al control de código fuente, se le pedirá al usuario que especifique un destino de control de código fuente para cada proyecto Web.

## <a name="new-capability-flags"></a>Nuevas marcas de capacidad
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nuevas funciones
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE casi siempre crea una carpeta sur al agregar una solución al control de código fuente. En concreto, lo hace en los casos siguientes:

- El proyecto es un proyecto Web de recurso compartido de archivos.

- Hay diferentes unidades para el proyecto y el archivo de solución.

- Hay diferentes recursos compartidos para el proyecto y el archivo de solución.

- Los proyectos se agregaron por separado (en una solución controlada por código fuente).

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , se recomienda que el nombre de la carpeta sur sea el mismo que el nombre de la solución sin la extensión. En la tabla siguiente se resume el comportamiento de las dos versiones.

|Característica|API del complemento de control de código fuente versión 1,1|API del complemento de control de código fuente versión 1,2|
|-------------| - | - |
|Agregar solución a SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Agregar un proyecto a una solución controlada por código fuente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:**  Visual Studio supone que una solución es un elemento secundario directo de SUR.|

## <a name="examples"></a>Ejemplos
 En la tabla siguiente se muestran dos ejemplos. En ambos casos, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se solicita al usuario una ubicación de destino para la solución bajo control de código fuente hasta que el  *user_choice* se especifica como destino. Cuando se especifica el user_choice, se agregan la solución y dos proyectos sin preguntar al usuario sobre los destinos de control de código fuente.

|La solución contiene|En ubicaciones de disco|Estructura predeterminada de la base de datos|
|-----------------------|-----------------------|--------------------------------|
|*sln1. sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/web2|
|*sln1. sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 La carpeta SUR y las subcarpetas se crean independientemente de si la operación se ha cancelado o no debido a un error. No se quitan automáticamente en condiciones de cancelación o error.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el valor predeterminado es el comportamiento de la versión 1,1 si el complemento de control de código fuente no devuelve `SCC_CAP_CREATESUBPROJECT` ni `SCC_CAP_GETPARENTPROJECT` marcas de funcionalidad. Además, los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden optar por revertir al comportamiento de la versión 1,1 estableciendo el valor de la clave siguiente en *DWORD: 00000001*:

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateSolutionRootFolderInSourceControl**  =  *DWORD: 00000001*

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente versión 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
