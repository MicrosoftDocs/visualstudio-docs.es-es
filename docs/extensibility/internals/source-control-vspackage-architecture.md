---
title: Arquitectura de VSPackage de Control de origen | Documentos de Microsoft
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
ms.openlocfilehash: e8a6b4c1e36f092bce89c57a2ead07a9e1a96a0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884139"
---
# <a name="source-control-vspackage-architecture"></a>Arquitectura de VSPackage de control de código fuente
Un paquete de control de código fuente es un paquete VSPackage que usa los servicios que la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE proporciona. En cambio, un paquete de control de código fuente proporciona su funcionalidad como un servicio de control de código fuente. Además, un paquete de control de código fuente es una alternativa más versátil que el complemento para la integración de control de código fuente en un control de código fuente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un complemento que implementa la API de complemento de Control de código fuente de control de código fuente se rige por un contrato estricta. Por ejemplo, un complemento no puede reemplazar el valor predeterminado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario (UI). Además, la API de complemento de Control de código fuente no se permite un complemento implementar su propio modelo de control de código fuente. Sin embargo, un paquete de control de código fuente, permite superar ambas limitaciones. Un paquete de control de código fuente tiene control completo sobre la experiencia de control de código fuente de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario. Además, un paquete de control de código fuente puede usar su propio modelo de control de código fuente y la lógica y pueden definir todas las interfaces de usuario relacionados con el control de código fuente.  
  
## <a name="source-control-package-components"></a>Componentes del paquete de Control de código fuente  
 Como se muestra en el diagrama de arquitectura, una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominado el código auxiliar de Control de código fuente es un paquete VSPackage que se integra un paquete de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Código auxiliar de Control de código fuente controla las tareas siguientes.  
  
- Proporciona la interfaz de usuario comunes que se requiere para el registro del paquete de control de código fuente.  
  
- Carga un paquete de control de código fuente.  
  
- Un paquete de control de código fuente se establece como activo o inactivo.  
  
  Código auxiliar de Control de origen busca el servicio activo para el paquete de control de código fuente y enruta todas las llamadas de servicio desde el IDE para que el paquete.  
  
  El paquete de adaptador de Control de código fuente es un control especial de origen del paquete que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona. Este paquete es el componente central para la compatibilidad con complementos código fuente control en función de la API de complemento de Control de código fuente. Cuando un complemento de control de origen es el complemento activa, el código auxiliar de Control de origen envía sus eventos para el paquete de adaptador de Control de código fuente. A su vez, el paquete de adaptador de Control de código fuente se comunica con el complemento de control de código fuente mediante la API de complemento de Control de código fuente y también proporciona una interfaz de usuario que es común para todos los complementos código fuente control predeterminada.  
  
  Cuando un paquete de control de código fuente es el paquete activo, por otro lado, el código auxiliar de Control de origen se comunica directamente con el paquete mediante el uso de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de paquete de Control de código fuente. El paquete de control de código fuente es responsable de alojar su propio control de código fuente de la interfaz de usuario.  
  
  ![Gráfico de arquitectura del Control de código fuente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  Para un paquete de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no proporciona código de control de código fuente o una API para la integración. Compare esto con el enfoque descrito en [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md) donde tiene el complemento de control de código fuente implementar un conjunto de funciones y las devoluciones de llamada rígido.  
  
  Al igual que cualquier VSPackage, un paquete de control de código fuente es un objeto COM que se puede crear mediante el uso de `CoCreateInstance`. El VSPackage pone a disposición el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Cuando se ha creado una instancia, un VSPackage recibe un puntero de sitio y un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz que proporciona acceso a los servicios disponibles y las interfaces en el IDE de VSPackage.  
  
  Escribir un paquete de control de código fuente basado en un VSPackage requiere experiencia de programación más avanzado que escribir una basada en API de complemento de Control de origen de complemento.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)