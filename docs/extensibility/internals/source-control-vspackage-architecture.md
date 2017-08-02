---
title: "Arquitectura de VSPackage del Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquetes de control de código fuente, arquitectura"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Arquitectura de VSPackage del Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un paquete de control de código fuente es un Paquete que usa los servicios que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE proporciona.  En cambio, un paquete de control de código fuente proporciona su funcionalidad como servicio de control de código fuente.  además, un paquete de control de código fuente es una alternativa más versátil que un complemento de control de código fuente para el control de código fuente de integración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 un complemento de control de código fuente que implementa el complemento de control de código fuente API sigue un contrato estricto.  Por ejemplo, un complemento no se puede reemplazar la interfaz de usuario predeterminada de \(UI\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  por otra parte, el complemento de control de código fuente API no permite a un complemento para implementar su propio modelo de control de código fuente.  un paquete de control de código fuente, sin embargo, supera ambas limitaciones.  Un paquete de control de código fuente tiene control total sobre la experiencia de control de código fuente de un usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Además, un paquete de control de código fuente puede utilizar su propio modelo y lógica de control de código fuente, y puede definir todas las interfaces de usuario CONTROL\-relacionadas de origen.  
  
## Empaquetar componentes de control de código fuente  
 Como se muestra en el diagrama de la arquitectura, un componente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] denominado el código auxiliar de control de código fuente es un Paquete que integra un paquete de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 El código auxiliar de control de código fuente controla las tareas siguientes.  
  
-   Proporciona la interfaz de usuario común necesaria para el registro del paquete de control de código fuente.  
  
-   carga un paquete de control de código fuente.  
  
-   Establece un paquete de control de código fuente como activo o inactivo.  
  
 El código auxiliar de control de código fuente busca el servicio activo para el paquete de control de código fuente y enruta todas las llamadas al servicio de entrada del IDE a ese paquete.  
  
 El paquete de adaptador de control de código fuente es un paquete de control de código fuente especial que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona.  Este paquete es el componente central para admitir los complementos de control de código fuente basados en el complemento de control de código fuente API.  Cuando un complemento de control de código fuente es el complemento activo, el código auxiliar de control de código fuente envía sus eventos al paquete de adaptador de control de código fuente.  A su vez, el paquete de adaptador de control de código fuente se comunica con el complemento de control de código fuente utilizando el complemento de control de código fuente API y también proporciona una interfaz de usuario predeterminada que es común para todos los complementos de control de código fuente.  
  
 Cuando un paquete de control de código fuente es el paquete activo, por otra parte, el código auxiliar de control de código fuente se comunica directamente con el paquete mediante interfaces de paquete de control de código fuente de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .  El paquete de control de código fuente es responsable de hospedar su propia interfaz de usuario del control de código fuente.  
  
 ![Gráfico de la arquitectura de control de código fuente](~/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Para un paquete de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no proporciona código de control de código fuente o API para la integración.  Compárelo con el enfoque antes en [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md) donde el complemento de control de código fuente tiene que implementar un conjunto estrictamente de funciones y de devoluciones de llamada.  
  
 Como cualquier VSPackage, un paquete de control de código fuente es un objeto COM que se puede crear con `CoCreateInstance`.  El Paquete se pone a disposición [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Cuando se ha creado una instancia, un VSPackage recibe un puntero de sitio y una interfaz de<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> que proporciona acceso de VSPackage a los servicios y las interfaces disponibles en el IDE.  
  
 La escritura de un paquete de control de código fuente VSPackage\-basado requiere una experiencia más de programación avanzada que escribiendo un complemento API\-basado complemento de control de código fuente.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)