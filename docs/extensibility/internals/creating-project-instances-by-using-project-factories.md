---
title: Creación de instancias de proyecto mediante generadores de proyectos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfde36f5e2b4854dbcee494ddd83ff4610982530
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936923"
---
# <a name="create-project-instances-by-using-project-factories"></a>Crear instancias de proyecto mediante generadores de proyectos
Tipos de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizar un *generador de proyectos* para crear instancias de objetos del proyecto. Un generador de proyectos es similar a un generador de clases estándar para los objetos COM cocreatable. Sin embargo, no son cocreatable; objetos del proyecto solo se pueden crear mediante el uso de un generador de proyectos.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE llama implementado en el paquete de VS, cuando un usuario carga un proyecto existente o crea un nuevo proyecto en el generador de proyectos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El nuevo objeto de proyecto proporciona el IDE con la suficiente información para rellenar **el Explorador de soluciones**. El nuevo objeto de proyecto también proporciona las interfaces necesarias para admitir todas las acciones de interfaz de usuario pertinentes iniciadas por el IDE.  
  
 Puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz en una clase en el proyecto. Normalmente, se encuentra en su propio módulo.  
  
 Los proyectos que admiten ser agregados por un propietario deben conservar una clave de propietario en el archivo de proyecto. Cuando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> método se llama en un proyecto con una clave de propietario, el proyecto propietario convierte su clave de propietario a un generador de proyectos, GUID, a continuación, llama a la `CreateProject` método en este generador de proyectos para realizar la creación real.  
  
## <a name="create-an-owned-project"></a>Crear un proyecto que se poseen  
 Un propietario, crea un proyecto propietario en dos fases:  
  
1. Mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> método. Esto proporciona al proyecto propietario una oportunidad para crear un objeto de proyecto agregado basado en la entrada que controla `IUnknown`. El proyecto propietario pasa interno `IUnknown` y el objeto agregado al proyecto propietario. Esto proporciona al proyecto propietario una oportunidad para almacenar interno `IUnknown`.  
  
2. Mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> método. El proyecto propietario no la creación de instancias cuando se llama a este método en lugar de llamar `IVsProjectFactory::CreateProject` como sería el caso de los proyectos que no pertenecen. La entrada `VSOWNEDPROJECTOBJECT` enumeración normalmente es el proyecto propietario agregado. El proyecto propietario puede usar esta variable para determinar si se ha creado su objeto de proyecto (cookie no es igual a NULL) o debe crearse (cookie es igual a NULL).  
  
   Tipos de proyecto se identifican mediante un único GUID, similar al CLSID de un objeto COM cocreatable del proyecto. Normalmente, un proyecto factory controla la creación de instancias de un tipo de proyecto único, aunque es posible tener un generador de proyectos controla más de un GUID de tipo de proyecto.  
  
   Tipos de proyecto están asociados con una extensión de nombre de archivo determinado. Cuando un usuario intenta abrir un archivo de proyecto existente o se intenta crear un nuevo proyecto mediante la clonación de una plantilla, el IDE usa la extensión en el archivo para determinar el GUID del proyecto correspondiente.  
  
   Tan pronto como el IDE determina si debe crear un nuevo proyecto o abra un proyecto existente de un tipo determinado, el IDE usa la información de registro del sistema en **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  para encontrar el VSPackage implementa el generador de proyectos necesarios. El IDE carga este VSPackage. En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método, el VSPackage debe registrar su generador de proyectos con el IDE mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> método.  
  
   El método principal de la `IVsProjectFactory` interfaz es <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, que debe controlar los dos escenarios: abrir un proyecto existente y crear un nuevo proyecto. La mayoría de los proyectos almacenan su estado de proyecto en un archivo de proyecto. Normalmente, los proyectos nuevos se crean por realizar una copia del archivo de plantilla que se pasa a la `CreateProject` método y, a continuación, abra la copia. Los proyectos existentes se crean instancias por directamente abriendo el archivo de proyecto pasado a `CreateProject` método. El `CreateProject` método puede mostrar las características de interfaz de usuario adicionales al usuario según sea necesario.  
  
   Un proyecto también puede no usar ningún archivo y, en su lugar, almacenar el estado de su proyecto en un mecanismo de almacenamiento que no sea el sistema de archivos, como un servidor Web o una base de datos. En este caso, el parámetro de nombre de archivo pasado a la `CreateProject` método no es realmente una ruta de acceso de sistema de archivos, pero una cadena única, una dirección URL, para identificar los datos del proyecto. No es necesario copiar los archivos de plantilla que se pasan a `CreateProject` para desencadenar la secuencia de construcción adecuadas que se ejecutará.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)