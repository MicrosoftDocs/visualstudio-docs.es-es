---
title: Arquitectura de VSPackage del Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a423b270eb8a26e9573f957da48915db37bf6851
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-vspackage-architecture"></a>Arquitectura de VSPackage del Control de código fuente
Un paquete de control de código fuente es un VSPackage que usa los servicios que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE proporciona. En cambio, un paquete de control de código fuente proporciona su funcionalidad como un servicio de control de código fuente. Además, un paquete de control de código fuente es una alternativa más versátil que un complemento para integrar el control de código fuente en control de código fuente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un complemento que implementa la API de complemento de Control de origen de control de código fuente se rige por un contrato estricto. Por ejemplo, un complemento no puede reemplazar el valor predeterminado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario (UI). Además, la API de complementos de Control de código fuente no habilitar un complemento implementar su propio modelo de control de código fuente. Sin embargo, un paquete de control de código fuente, supera ambas de estas limitaciones. Un paquete de control de código fuente tiene un control completo sobre la experiencia de control de código fuente de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario. Además, un paquete de control de código fuente puede utilizar su propio modelo de control de origen y la lógica, y puede definir todas las interfaces de usuario relacionada con el control de código fuente.  
  
## <a name="source-control-package-components"></a>Componentes del paquete de Control de código fuente  
 Como se muestra en el diagrama de arquitectura, una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominado el código auxiliar de Control de código fuente es un VSPackage que integra un paquete de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Código auxiliar de Control de código fuente controla las siguientes tareas.  
  
-   Proporciona la interfaz de usuario comunes que es necesario para registrar paquetes de control de código fuente.  
  
-   Carga un paquete de control de código fuente.  
  
-   Un paquete de control de código fuente se establece como activo o inactivo.  
  
 Código auxiliar de Control de origen busca el servicio activo para el paquete de control de código fuente y los enruta todas las llamadas de servicio desde el IDE para que el paquete.  
  
 El paquete de adaptador de Control de origen es un control especial de origen del paquete que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona. Este paquete es el componente central para admitir origen control complementos en función de la API de complementos de Control de código fuente. Cuando un complemento de control de origen es el complemento activo, el código auxiliar de Control de origen envía sus eventos para el paquete de adaptador de Control de origen. A su vez, el paquete de adaptador de Control de origen se comunica con el complemento de control de código fuente mediante la API de complemento de Control de origen y también proporciona una interfaz de usuario que es común para todos los complementos código fuente control predeterminada.  
  
 Cuando un paquete de control de código fuente es el activo, por otro lado, el código auxiliar de Control de origen se comunica directamente con el paquete mediante el uso de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de paquete de Control de código fuente. El paquete de control de código fuente es responsable de hospedaje de su propia interfaz de usuario de control de código fuente.  
  
 ![Gráfico de arquitectura de Control de código fuente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Para un paquete de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no proporciona código de control de código fuente o una API para la integración. Compare esto con el enfoque descrito en [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md) donde tiene el complemento de control de código fuente implementar un conjunto rígido de las funciones y las devoluciones de llamada.  
  
 Al igual que cualquier VSPackage, un paquete de control de código fuente es un objeto COM que se pueden crear mediante el uso de `CoCreateInstance`. El VSPackage pone a disposición la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Cuando se ha creado una instancia, un VSPackage recibe un puntero de sitio y un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz que proporciona acceso a los servicios disponibles y interfaces en el IDE de VSPackage.  
  
 Escribir un paquete de control de código fuente en función de VSPackage requiere experiencia de programación más avanzado de escribir basado en la API de complementos de Control de origen de complemento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)