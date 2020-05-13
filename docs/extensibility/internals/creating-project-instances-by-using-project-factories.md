---
title: Creación de instancias de proyecto mediante el uso de generadores de proyectos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709060"
---
# <a name="create-project-instances-by-using-project-factories"></a>Crear instancias de proyecto mediante fábricas de proyectos
Tipos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto en uso un generador de *proyectos* para crear instancias de objetos de proyecto. Un generador de proyectos es similar a un generador de clases estándar para objetos COM cocreables. Sin embargo, los objetos de proyecto no son cocreables; sólo se pueden crear mediante una fábrica de proyectos.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE llama al generador de proyectos implementado en el VSPackage cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]un usuario carga un proyecto existente o crea un nuevo proyecto en . El nuevo objeto de proyecto proporciona al IDE suficiente información para rellenar el Explorador de **soluciones.** El nuevo objeto de proyecto también proporciona las interfaces necesarias para admitir todas las acciones de interfaz de usuario relevantes iniciadas por el IDE.

 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> la interfaz en una clase del proyecto. Normalmente, reside en su propio módulo.

 Los proyectos que admiten la agregación de un propietario deben conservar una clave de propietario en el archivo de proyecto. Cuando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> se llama al método en un proyecto con una clave de propietario, el `CreateProject` proyecto de propiedad convierte su clave de propietario en un GUID de generador de proyectos y, a continuación, llama al método en este generador de proyectos para realizar la creación real.

## <a name="create-an-owned-project"></a>Crear un proyecto propio
 Un propietario crea un proyecto propio en dos fases:

1. Llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> método. Esto da al proyecto propietario la oportunidad de crear un `IUnknown`objeto de proyecto agregado basado en el control de entrada. El proyecto de propiedad `IUnknown` pasa el objeto interno y agregado al proyecto propietario. Esto le da al proyecto propio `IUnknown`la oportunidad de almacenar el archivo .

2. Llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> método. El proyecto de propiedad realiza toda su creación de `IVsProjectFactory::CreateProject` instancias cuando se llama a este método en lugar de llamar como sería el caso de los proyectos que no son propiedad. La `VSOWNEDPROJECTOBJECT` enumeración de entrada suele ser el proyecto de propiedad agregado. El proyecto de propiedad puede usar esta variable para determinar si su objeto de proyecto ya se ha creado (cookie no es igual a NULL) o debe crearse (cookie es igual a NULL).

   Los tipos de proyecto se identifican mediante un GUID de proyecto único, similar al CLSID de un objeto COM cocreable. Normalmente, un generador de proyectos controla la creación de instancias de un único tipo de proyecto, aunque es posible tener un generador de proyectos controlar más de un GUID de tipo de proyecto.

   Los tipos de proyecto están asociados a una extensión de nombre de archivo determinada. Cuando un usuario intenta abrir un archivo de proyecto existente o intenta crear un nuevo proyecto clonando una plantilla, el IDE usa la extensión en el archivo para determinar el GUID del proyecto correspondiente.

   Tan pronto como el IDE determina si debe crear un nuevo proyecto o abrir un proyecto existente de un tipo determinado, el IDE usa la información en el registro del sistema en **[HKEY_LOCAL_MACHINE, Software, Microsoft, VisualStudio, 8.0, Projects]** para buscar qué VSPackage implementa el generador de proyectos necesario. El IDE carga este VSPackage. En <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> el método, el VSPackage debe registrar su generador <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> de proyectos con el IDE mediante una llamada al método.

   El método principal `IVsProjectFactory` de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>la interfaz es , que debe controlar dos escenarios: abrir un proyecto existente y crear un nuevo proyecto. La mayoría de los proyectos almacenan su estado de proyecto en un archivo de proyecto. Normalmente, los nuevos proyectos se crean haciendo una `CreateProject` copia del archivo de plantilla pasado al método y, a continuación, abriendo la copia. Se crean instancias de los proyectos `CreateProject` existentes abriendo directamente el archivo de proyecto pasado al método. El `CreateProject` método puede mostrar características de interfaz de usuario adicionales al usuario según sea necesario.

   Un proyecto también puede usar ningún archivo y, en su lugar, almacenar su estado de proyecto en un mecanismo de almacenamiento distinto del sistema de archivos, como una base de datos o un servidor web. En este caso, el parámetro `CreateProject` de nombre de archivo pasado al método no es realmente una ruta de acceso del sistema de archivos, sino una cadena única (una dirección URL) para identificar los datos del proyecto. No es necesario copiar los archivos de `CreateProject` plantilla que se pasan para desencadenar la secuencia de construcción adecuada que se va a ejecutar.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Lista de verificación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
