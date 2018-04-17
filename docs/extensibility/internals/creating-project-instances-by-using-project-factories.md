---
title: Creación de instancias de proyecto mediante generadores de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b3a59eee6701caf0b4d3b56df273b280f8bf6ece
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-project-instances-by-using-project-factories"></a>Crear instancias de Project mediante generadores de proyectos
Tipos de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizar un *generador de proyectos* para crear instancias de objetos del proyecto. Un generador de proyectos es similar a un generador de clases estándar para los objetos COM cocreatable. Sin embargo, los objetos del proyecto no son cocreatable: sólo se puede crear mediante el uso de un generador de proyectos.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE llama el generador del proyecto implementado en el paquete de VS cuando un usuario carga un proyecto existente o crea un nuevo proyecto en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El nuevo objeto de proyecto proporciona el IDE con suficiente información para rellenar el Explorador de soluciones. El nuevo objeto de proyecto también proporciona las interfaces necesarias para admitir todas las acciones de interfaz de usuario relevantes iniciadas por el IDE.  
  
 Puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz en una clase en el proyecto. Normalmente, se encuentra en su propio módulo.  
  
 Para obtener un ejemplo de una implementación de la `IVsProjectFactory` de la interfaz, vea PrjFac.cpp que se encuentra en la [básico del proyecto](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) directorio de ejemplo.  
  
 Proyectos compatibles con agregados por un propietario deben conservar una clave de propietario en su archivo de proyecto. Cuando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> método se llama en un proyecto con una clave de propietario, el propio proyecto convierte su clave de propietario a un generador de proyectos, a continuación, llama a GUID el `CreateProject` método en este generador de proyectos para realizar la creación real.  
  
## <a name="creating-an-owned-project"></a>Crear un proyecto de propiedad  
 Un propietario crea un proyecto propio en dos fases:  
  
1.  Mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> método. Esto proporciona el proyecto posee una oportunidad para crear un objeto de proyecto agregado basado en el control de entrada `IUnknown`. El propio proyecto pasa interna `IUnknown` y el objeto agregado hacia el proyecto propietario. Esto proporciona el proyecto posee una oportunidad para almacenar interna `IUnknown`.  
  
2.  Mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> método. El propio proyecto realiza la creación de instancias cuando se llama a este método en lugar de llamar `IVsProjectFactory::CreateProject` como sería el caso de proyectos que no son propiedad. La entrada `VSOWNEDPROJECTOBJECT` enumeración normalmente es el propio proyecto agregado. El proyecto propietario puede usar esta variable para determinar si ya se ha creado su objeto de proyecto (cookie no es igual a NULL) o debe crearse (cookie es igual a NULL).  
  
 Tipos de proyecto se identifican mediante un único GUID, similar al CLSID de un objeto COM cocreatable del proyecto. Normalmente, identificadores de fábrica de un proyecto crear instancias de un único tipo de proyecto, aunque es posible tener un generador de proyectos controlen más de un GUID de tipo de proyecto.  
  
 Tipos de proyecto están asociados con una extensión de nombre de archivo en particular. Cuando un usuario intenta abrir un archivo de proyecto existente o si se intenta crear un nuevo proyecto mediante la clonación de una plantilla, el IDE usa la extensión en el archivo para determinar el GUID del proyecto correspondiente.  
  
 Tan pronto como el IDE determina si debe crear un nuevo proyecto o abrir un proyecto existente de un tipo determinado, el IDE usa la información en el registro del sistema en [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] para saber cuáles VSPackage implementa el generador de proyecto necesarios. El IDE carga este VSPackage. En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método, el VSPackage debe registrar su generador de proyectos con el IDE mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> método.  
  
 El método principal de la `IVsProjectFactory` interfaz es <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> que debe controlar los dos escenarios: abrir un proyecto existente y crear un nuevo proyecto. Mayoría de los proyectos almacena su estado de proyecto en un archivo de proyecto. Normalmente, se crean los nuevos proyectos por realizar una copia del archivo de plantilla que se pasa a la `CreateProject` método y, a continuación, abra la copia. Los proyectos existentes se crea una instancia directamente de abrir el archivo de proyecto pasa a `CreateProject` método. El `CreateProject` método puede mostrar las características de interfaz de usuario adicionales para el usuario según sea necesario.  
  
 Un proyecto puede no usar ningún archivo y, en su lugar, almacenar su estado de proyecto en un mecanismo de almacenamiento que no sea el sistema de archivos, como una base de datos o el servidor Web. En este caso, el parámetro de nombre de archivo pasado a la `CreateProject` método no es realmente una ruta de acceso de sistema de archivos, pero una cadena única, una dirección URL, para identificar los datos del proyecto. No es necesario copiar los archivos de plantilla que se pasan a `CreateProject` para desencadenar la secuencia de construcción adecuadas que se ejecute.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)