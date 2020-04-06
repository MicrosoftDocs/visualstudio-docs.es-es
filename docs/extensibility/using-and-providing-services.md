---
title: Uso y prestación de servicios de la aplicación de la aplicación de la información de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698738"
---
# <a name="using-and-providing-services"></a>Uso y prestación de servicios
Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para otro VSPackage para consumir. Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> ofrece el servicio a cualquier VSPackage que cargue. Este servicio <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> proporciona la interfaz, que se puede utilizar para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: Usar el registro](../extensibility/how-to-use-the-activity-log.md)de actividad .

 VSPackages puede ofrecer servicios propios <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> mediante el uso de la interfaz..

 Visual Studio ofrece servicios importantes, como los siguientes:

|Servicio IDE|Descripción|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso a los servicios IDE que se ocupan de la funcionalidad básica, VSPackages y el registro.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona ventanas básicas y funcionalidad relacionada con la interfaz de usuario en el IDE, como la capacidad de crear herramientas y ventanas de documentos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona funcionalidad básica relacionada con la solución, como la capacidad de enumerar proyectos, crear nuevos proyectos y supervisar los cambios de proyecto.|

## <a name="in-this-section"></a>En esta sección
- [Service Essentials](../extensibility/internals/service-essentials.md) Presenta los elementos importantes de un servicio de Visual Studio.

- [Cómo: Obtener un servicio](../extensibility/how-to-get-a-service.md) Describe cómo solicitar (consumir) un servicio.

- [Cómo: Proporcionar un servicio](../extensibility/how-to-provide-a-service.md) Describe cómo proporcionar un servicio.

- [Cómo: Proporcionar un servicio de Visual Studio asincrónico](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Describe cómo proporcionar un servicio asincrónico.

- [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) Discute problemas comunes y les presenta soluciones.

## <a name="related-sections"></a>Secciones relacionadas
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
