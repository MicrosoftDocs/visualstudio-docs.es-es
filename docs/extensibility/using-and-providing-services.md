---
title: Usar y proporcionar servicios | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698738"
---
# <a name="using-and-providing-services"></a>Uso y prestación de servicios
Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para que lo consuma otro VSPackage. Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servicio a cualquier VSPackage que se cargue. Este servicio proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que se puede utilizar para escribir en el registro de actividad. Para obtener más información, vea [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).

 Los VSPackages pueden ofrecer servicios propios mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz.

 Visual Studio ofrece servicios importantes, como los siguientes:

|Servicio IDE|Descripción|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso a los servicios IDE que se ocupan de la funcionalidad básica, los VSPackages y el registro.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funciones básicas de ventana y de interfaz de usuario en el IDE, como la capacidad de crear herramientas y ventanas de documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona una funcionalidad básica relacionada con la solución, como la posibilidad de enumerar proyectos, crear nuevos proyectos y supervisar cambios en el proyecto.|

## <a name="in-this-section"></a>En esta sección
- [Aspectos básicos del servicio](../extensibility/internals/service-essentials.md) Presenta los elementos importantes de un servicio de Visual Studio.

- [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md) Describe cómo solicitar (consumir) un servicio.

- [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md) Describe cómo proporcionar un servicio.

- [Cómo: proporcionar un servicio de Visual Studio asincrónico](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Describe cómo proporcionar un servicio asincrónico.

- [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) Aborda los problemas comunes y presenta soluciones a ellos.

## <a name="related-sections"></a>Secciones relacionadas
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
