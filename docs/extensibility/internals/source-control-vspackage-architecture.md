---
title: Arquitectura de VSPackage de Control de código fuente ( Control de código fuente) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705077"
---
# <a name="source-control-vspackage-architecture"></a>Arquitectura de VSPackage de control de código fuente
Un paquete de control de código fuente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es un VSPackage que usa los servicios que proporciona el IDE. A cambio, un paquete de control de código fuente proporciona su funcionalidad como un servicio de control de código fuente. Además, un paquete de control de código fuente es una alternativa más [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]versátil que un complemento de control de código fuente para integrar el control de código fuente en .

 Un complemento de control de código fuente que implementa la API de complemento de Control de código fuente cumple con un contrato estricto. Por ejemplo, un complemento no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede reemplazar la interfaz de usuario (UI) predeterminada. Además, la API de complemento de Control de código fuente no habilita un complemento para implementar su propio modelo de control de código fuente. Sin embargo, un paquete de control de código fuente supera ambas limitaciones. Un paquete de control de código fuente tiene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un control completo sobre la experiencia de control de código fuente de un usuario. Además, un paquete de control de código fuente puede usar su propio modelo de control de código fuente y lógica, y puede definir todas las interfaces de usuario relacionadas con el control de código fuente.

## <a name="source-control-package-components"></a>Componentes del paquete de control de código fuente
 Como se muestra en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el diagrama de arquitectura, un componente denominado el Código auxiliar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de control de código fuente es un VSPackage que integra un paquete de control de código fuente con .

 El Código auxiliar de Control de código fuente controla las siguientes tareas.

- Proporciona la interfaz de usuario común que se requiere para el registro del paquete de control de código fuente.

- Carga un paquete de control de código fuente.

- Establece un paquete de control de código fuente como activo/inactivo.

  El Código Auxiliar de Control de código fuente busca el servicio activo para el paquete de control de código fuente y enruta todas las llamadas de servicio entrantes desde el IDE a ese paquete.

  El paquete de adaptador de control de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fuente es un paquete de control de código fuente especial que proporciona. Este paquete es el componente central para admitir complementos de control de código fuente basados en la API de complemento de Control de código fuente. Cuando un complemento de control de código fuente es el complemento activo, el Código auxiliar de control de código fuente envía sus eventos al paquete de adaptador de Control de código fuente. A su vez, el paquete de adaptador de control de código fuente se comunica con el complemento de control de código fuente mediante el uso de la API de complemento de Control de código fuente y también proporciona una interfaz de usuario predeterminada que es común para todos los complementos de control de código fuente.

  Cuando un paquete de control de código fuente es el paquete activo, por otro lado, el Código auxiliar de control de código fuente se comunica directamente con el paquete mediante el uso de las [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de paquete de control de código fuente. El paquete de control de código fuente es responsable de hospedar su propia interfaz de usuario de control de código fuente.

  ![Gráfico de arquitectura de control de código fuente](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Para un paquete de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] control de código fuente, no proporciona código de control de código fuente ni una API para la integración. Compare esto con el enfoque descrito en Creación de [un complemento](../../extensibility/internals/creating-a-source-control-plug-in.md) de control de código fuente donde el complemento de control de código fuente tiene que implementar un conjunto rígido de funciones y devoluciones de llamada.

  Al igual que cualquier VSPackage, un paquete de control `CoCreateInstance`de código fuente es un objeto COM que se puede crear mediante . El VSPackage se pone [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a disposición del IDE mediante la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>de . Cuando se ha creado una instancia, un VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> recibe un puntero de sitio y una interfaz que proporciona el VSPackage acceso a los servicios e interfaces disponibles en el IDE.

  Escribir un paquete de control de código fuente basado en VSPackage requiere más experiencia en programación avanzada que escribir un complemento basado en API de complemento de Control de código fuente.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
