---
title: Arquitectura de VSPackage de control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705077"
---
# <a name="source-control-vspackage-architecture"></a>Arquitectura de VSPackage de control de código fuente
Un paquete de control de código fuente es un VSPackage que utiliza los servicios que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona el IDE. A cambio, un paquete de control de código fuente proporciona su funcionalidad como servicio de control de código fuente. Además, un paquete de control de código fuente es una alternativa más versátil que un complemento de control de código fuente para integrar el control de código fuente en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Un complemento de control de código fuente que implementa la API del complemento de control de código fuente se rige por un contrato estricto. Por ejemplo, un complemento no puede reemplazar la interfaz de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario (UI) predeterminada. Además, la API del complemento de control de código fuente no permite que un complemento implemente su propio modelo de control de código fuente. Sin embargo, un paquete de control de código fuente supera estas dos limitaciones. Un paquete de control de código fuente tiene control total sobre la experiencia de control de código fuente de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuario. Además, un paquete de control de código fuente puede utilizar su propio modelo de control de código fuente y lógica, y puede definir todas las interfaces de usuario relacionadas con el control de código fuente.

## <a name="source-control-package-components"></a>Componentes del paquete de control de código fuente
 Como se muestra en el diagrama de arquitectura, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominado código auxiliar de control de código fuente es un VSPackage que integra un paquete de control de código fuente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 El código auxiliar de control de código fuente controla las siguientes tareas.

- Proporciona la interfaz de usuario común necesaria para el registro del paquete de control de código fuente.

- Carga un paquete de control de código fuente.

- Establece un paquete de control de código fuente como activo/inactivo.

  El código auxiliar de control de código fuente busca el servicio activo para el paquete de control de código fuente y enruta todas las llamadas de servicio entrantes desde el IDE a ese paquete.

  El paquete del adaptador de control de código fuente es un paquete de control de código fuente especial que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona. Este paquete es el componente central para admitir complementos de control de código fuente basados en la API del complemento de control de código fuente. Cuando un complemento de control de código fuente es el complemento activo, el código auxiliar de control de código fuente envía sus eventos al paquete del adaptador de control de código fuente. A su vez, el paquete del adaptador de control de código fuente se comunica con el complemento de control de código fuente mediante la API del complemento de control de código fuente y también proporciona una interfaz de usuario predeterminada común para todos los complementos de control de código fuente.

  Por otro lado, cuando un paquete de control de código fuente es el paquete activo, el código auxiliar de control de código fuente se comunica directamente con el paquete mediante las [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de paquete de control de código fuente. El paquete de control de código fuente es responsable de hospedar su propia interfaz de usuario de control de código fuente.

  ![Gráfico de arquitectura de control de código fuente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Para un paquete de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no proporciona código de control de código fuente ni una API para la integración. Compare esto con el enfoque que se describe en [crear un complemento de control de código fuente,](../../extensibility/internals/creating-a-source-control-plug-in.md) donde el complemento de control de código fuente tiene que implementar un conjunto rígido de funciones y devoluciones de llamada.

  Al igual que cualquier VSPackage, un paquete de control de código fuente es un objeto COM que se puede crear mediante `CoCreateInstance` . El VSPackage se pone a disposición del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Cuando se ha creado una instancia, un VSPackage recibe un puntero de sitio y una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz que proporciona acceso a VSPackage a los servicios e interfaces disponibles en el IDE.

  La escritura de un paquete de control de código fuente basado en VSPackage requiere una experiencia de programación más avanzada que escribir un complemento basado en la API del complemento de control de código fuente.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
