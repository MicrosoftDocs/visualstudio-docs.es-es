---
title: Creación de carpetas de contenedores principales para soluciones ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709094"
---
# <a name="create-parent-container-folders-for-solutions"></a>Crear carpetas de contenedor principales para soluciones
En la versión 1.2 de la API de complemento de Control de código fuente, un usuario puede especificar un único destino de control de código fuente raíz para todos los proyectos web dentro de la solución. Esta raíz única se llama una raíz súper unificada (SUR).

 En la versión 1.1 de la API de complemento de Control de código fuente, si el usuario agregó una solución multiproyecto al control de código fuente, se le pidió al usuario que especificara un destino de control de código fuente para cada proyecto web.

## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nuevas funciones
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE casi siempre crea una carpeta SUR al agregar una solución al control de código fuente. Concretamente, lo hace en los siguientes casos:

- El proyecto es un proyecto web de recurso compartido de archivos.

- Hay diferentes unidades para el proyecto y el archivo de solución.

- Hay diferentes recursos compartidos para el proyecto y el archivo de solución.

- Los proyectos se agregaron por separado (en una solución controlada por código fuente).

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se sugiere que el nombre de la carpeta SUR sea el mismo que el nombre de la solución sin la extensión. En la tabla siguiente se resume el comportamiento de las dos versiones.

|Característica|Source Control Plug-in API Versión 1.1|Source Control Plug-in API Versión 1.2|
|-------------| - | - |
|Añadir solución a SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Agregar proyecto a la solución controlada por código fuente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:**  Visual Studio supone que una solución es un elemento secundario directo de SUR.|

## <a name="examples"></a>Ejemplos
 En la tabla siguiente se enumeran dos ejemplos. En ambos casos, se solicita al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario una ubicación de destino para la solución bajo control de código fuente hasta que se especifique el *user_choice* como destino. Cuando se especifica el user_choice, la solución y dos proyectos se agregan sin solicitar al usuario destinos de control de código fuente.

|La solución contiene|En ubicaciones de disco|Estructura predeterminada de la base de datos|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:-Soluciones-sln1*<br /><br /> *C:-Inetpub-wwwroot-Web1*<br /><br /> \\"servidor" (servidor) y "wwwroot".|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<>/Web2 user_choice 2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:-Soluciones-sln1*<br /><br /> *D:-Inetpub-wwwroot-Web1*<br /><br /> *C:-soluciones-sln1-Win1*|$/<user_choice>/sln1<br /><br /> $/<> user_choice/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 La carpeta SUR y las subcarpetas se crean independientemente de si la operación se cancela o se produce un error debido a un error. No se eliminan automáticamente en condiciones de cancelación o error.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de forma predeterminada, el comportamiento de la versión `SCC_CAP_CREATESUBPROJECT` 1.1 si el complemento de control de código fuente no devuelve y `SCC_CAP_GETPARENTPROJECT` los indicadores de capacidad. Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los usuarios pueden optar por volver al comportamiento de la versión 1.1 estableciendo el valor de la siguiente clave en *dword:00000001*:

 **[HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8.0, SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Vea también
- [Novedades de la API de complemento de Control de código fuente versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
