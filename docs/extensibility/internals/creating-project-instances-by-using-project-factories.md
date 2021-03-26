---
title: Crear instancias de proyecto mediante generadores de proyecto | Microsoft Docs
description: Obtenga información sobre cómo crear instancias de clase de proyecto mediante los generadores de proyectos en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b7c3fbe5b5b7fd59fe0e57376290181f3e9a20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056809"
---
# <a name="create-project-instances-by-using-project-factories"></a>Creación de instancias de proyecto mediante el uso de generadores de proyecto
Los tipos de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usan un *generador de proyectos* para crear instancias de objetos de proyecto. Un generador de proyectos es similar a un generador de clases estándar para objetos COM cocreatbles. Sin embargo, los objetos de proyecto no son cocreatable; solo se pueden crear mediante un generador de proyectos.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE llama al generador de proyectos implementado en el VSPackage cuando un usuario carga un proyecto existente o crea un nuevo proyecto en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . El nuevo objeto Project proporciona al IDE información suficiente para rellenar **Explorador de soluciones**. El nuevo objeto Project también proporciona las interfaces necesarias para admitir todas las acciones de interfaz de usuario pertinentes iniciadas por el IDE.

 Puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaz en una clase del proyecto. Normalmente, reside en su propio módulo.

 Los proyectos que admiten la agregación de un propietario deben conservar una clave propietaria en el archivo del proyecto. Cuando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> se llama al método en un proyecto con una clave propietaria, el proyecto de propiedad convierte su clave propietaria en un GUID del generador del proyecto y, a continuación, llama al `CreateProject` método en este generador de proyectos para realizar la creación real.

## <a name="create-an-owned-project"></a>Crear un proyecto de propiedad
 Un propietario crea un proyecto de propiedad en dos fases:

1. Llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> método. Esto proporciona al proyecto de propiedad una oportunidad para crear un objeto de proyecto agregado basado en el control de entrada `IUnknown` . El proyecto de propiedad pasa el `IUnknown` objeto interno y el agregado de nuevo al proyecto de propietario. Esto proporciona al proyecto de propiedad una oportunidad para almacenar el interior `IUnknown` .

2. Llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> método. El proyecto de propiedad realiza toda la creación de instancias cuando se llama a este método en lugar de llamar a `IVsProjectFactory::CreateProject` , como sería el caso de los proyectos que no son propiedad. La `VSOWNEDPROJECTOBJECT` enumeración de entrada es normalmente el proyecto de propiedad agregado. El proyecto de propiedad puede usar esta variable para determinar si ya se ha creado su objeto de proyecto (la cookie no es igual a NULL) o se debe crear (la cookie es igual a NULL).

   Los tipos de proyecto se identifican mediante un GUID de proyecto único, similar al CLSID de un objeto COM cocreatable. Normalmente, un generador de proyectos controla la creación de instancias de un tipo de proyecto único, aunque es posible tener un controlador de proyecto que trate más de un GUID de tipo de proyecto.

   Los tipos de proyecto están asociados a una extensión de nombre de archivo determinada. Cuando un usuario intenta abrir un archivo de proyecto existente o intenta crear un nuevo proyecto mediante la clonación de una plantilla, el IDE usa la extensión en el archivo para determinar el GUID del proyecto correspondiente.

   En cuanto el IDE determina si debe crear un nuevo proyecto o abrir un proyecto existente de un tipo determinado, el IDE usa la información del registro del sistema en **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** para averiguar qué VSPackage implementa el generador de proyectos necesario. El IDE carga este VSPackage. En el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método, el VSPackage debe registrar su generador de proyectos con el IDE llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> método.

   El método principal de la `IVsProjectFactory` interfaz es <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , que debe administrar dos escenarios: abrir un proyecto existente y crear un nuevo proyecto. La mayoría de los proyectos almacenan el estado del proyecto en un archivo de proyecto. Normalmente, los proyectos nuevos se crean realizando una copia del archivo de plantilla que se pasa al `CreateProject` método y, a continuación, abriendo la copia. Los proyectos existentes se crean mediante la apertura directa del archivo de proyecto que se pasa al `CreateProject` método. El `CreateProject` método puede mostrar características adicionales de la interfaz de usuario para el usuario según sea necesario.

   Un proyecto tampoco puede usar archivos y, en su lugar, almacena su estado del proyecto en un mecanismo de almacenamiento distinto del sistema de archivos, como una base de datos o un servidor Web. En este caso, el parámetro de nombre de archivo pasado al `CreateProject` método no es realmente una ruta de acceso del sistema de archivos, sino una cadena única (una dirección URL) para identificar los datos del proyecto. No es necesario copiar los archivos de plantilla que se pasan a `CreateProject` para desencadenar la secuencia de construcción adecuada que se va a ejecutar.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Lista de comprobación: crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
