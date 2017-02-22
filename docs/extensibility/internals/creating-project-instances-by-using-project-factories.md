---
title: "Creaci&#243;n de instancias de proyecto mediante generadores de proyecto | Microsoft Docs"
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
  - "generadores de proyecto"
  - "proyectos de generadores de proyecto [Visual Studio SDK],"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de instancias de proyecto mediante generadores de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los tipos de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizan *un generador de proyecto* para crear instancias de objetos del proyecto.  Un generador de proyecto es similar a un generador estándar de la clase para los objetos COM cocreatable.  Sin embargo, los objetos del proyecto no son cocreatable: sólo pueden crearse mediante un generador del proyecto.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE llama al generador de proyectos implementada en el Paquete cuando un usuario carga un proyecto existente o cree un nuevo proyecto en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  El nuevo objeto de proyecto proporciona el IDE con suficiente información para rellenar el explorador de soluciones.  El nuevo objeto de proyecto también proporciona interfaces necesarias para admitir todas las acciones importantes de la interfaz de usuario iniciados por el IDE.  
  
 Puede implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> en una clase del proyecto.  Normalmente, reside en su propio módulo.  
  
 Para obtener un ejemplo de una implementación de la interfaz de `IVsProjectFactory` , vea PrjFac.cpp incluido en el directorio del ejemplo de [Basic Project](http://msdn.microsoft.com/es-es/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) .  
  
 Proyectos que permiten agregar por un propietario deben conservar una clave propietario en el archivo de proyecto.  Cuando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> se llama un proyecto con una clave de propietario, el proyecto propiedad convierte su clave de propietario a un generador el GUID del proyecto después llama al método de `CreateProject` en esta generador de proyectos para realizar la creación real.  
  
## crear un proyecto de Owned  
 Un propietario crea un proyecto que pertenece en dos fases:  
  
1.  Llamando el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>.  Esto proporciona a proyecto que pertenece una oportunidad de crear un objeto agregado de proyecto basado en la entrada que controla `IUnknown`.  El proyecto propiedad devuelve `IUnknown` interno y el objeto agregado al proyecto propietario.  Esto proporciona a proyecto que pertenece una oportunidad de almacenar `IUnknown`interno.  
  
2.  Llamando el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>.  El proyecto propiedad hace toda su instancia cuando se llama a este método en lugar de llamar a `IVsProjectFactory::CreateProject` como es el caso para los proyectos que no se poseen.  La enumeración de `VSOWNEDPROJECTOBJECT` de entrada es normalmente el proyecto propiedad agregado.  El proyecto propiedad puede utilizar esta variable para determinar si el objeto del proyecto se ha creado \(la cookie no es NULL\) o debe crear \(la cookie es NULL\).  
  
 Un proyecto único GUID identifican los tipos de proyecto, similar al CLSID de un objeto COM cocreatable.  Normalmente, un generador de proyecto controla crear instancias de un único tipo de proyecto, aunque es posible tener un identificador de generador de proyecto más de un tipo de proyecto GUID.  
  
 Los tipos de proyecto están asociados con una extensión de nombre de archivo determinada.  Cuando un usuario intenta abrir un archivo de proyecto existente o que intenta crear un nuevo proyecto clonando una plantilla, el IDE utiliza la extensión del archivo para determinar el proyecto correspondiente GUID.  
  
 En cuanto el IDE determina si debe crear un nuevo proyecto o abrir un proyecto existente de un tipo determinado, el IDE utiliza la información del sistema bajo \[HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0\\Projects\] to find which VSPackage implementa el generador necesaria del proyecto.  El IDE cargar este paquete VSPackage.  En el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , el Paquete debe registrar el generador del proyecto con el IDE llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> .  
  
 El método primario de la interfaz de `IVsProjectFactory` es el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> que deben administrar dos escenarios: abrir un proyecto existente y crear un nuevo proyecto.  La mayoría de los proyectos almacenan su estado en un archivo de proyecto.  Normalmente, los nuevos proyectos se crean creando una copia del archivo de plantilla pasada al método de `CreateProject` y después abriendo la copia.  Los proyectos existentes se crean instancias directamente abriendo el archivo de proyecto pasada al método de `CreateProject` .  El método de `CreateProject` puede mostrar características adicionales de la interfaz de usuario según sea necesario.  
  
 Un proyecto no puede utilizar ningún archivo y, en su lugar, almacena su estado en un mecanismo de almacenamiento distinta del sistema de archivos, como una base de datos o un servidor web.  En este caso, el parámetro de nombre de archivo pasado al método de `CreateProject` no es realmente una ruta de acceso del sistema de archivos pero una cadena\-uno única Dirección URL\-a identifica los datos del proyecto.  No es necesario copiar los archivos de plantilla que se pasan a `CreateProject` para desencadenar la secuencia adecuada de la construcción que se ejecutará.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)