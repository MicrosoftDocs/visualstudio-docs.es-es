---
title: Estructura VSPackage (VSPackage de control de código fuente) | Microsoft Docs
description: Obtenga información sobre el SDK del paquete de control de código fuente, que proporciona directrices para un VSPackage con un implementador de control de código fuente para integrarlo con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5850dfb2448364124c8f1778eac48ac9c653269
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487964"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de control de código fuente)

El SDK del paquete de control de código fuente proporciona instrucciones para crear un VSPackage que permite a un implementador de control de código fuente integrar su funcionalidad de control de código fuente en el entorno de Visual Studio. Un VSPackage es un componente COM que normalmente se carga a petición por el entorno de desarrollo integrado (IDE) de Visual Studio en función de los servicios anunciados por el paquete en sus entradas del registro. Cada VSPackage debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un VSPackage normalmente consume los servicios que ofrece el IDE de Visual Studio y ofrece algunos servicios propios.

Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado a través del archivo. Vsct. El IDE de Visual Studio muestra los elementos de menú en este estado hasta que se cargue el VSPackage. Posteriormente, se llama a la implementación del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método del VSPackage para habilitar o deshabilitar elementos de menú.

## <a name="source-control-package-characteristics"></a>Características del paquete de control de código fuente

Un VSPackage de control de código fuente se integra profundamente en Visual Studio. La semántica del VSPackage incluye:

- Interfaz que se va a implementar en virtud de ser un VSPackage (la `IVsPackage` interfaz)

- Implementación de comandos de la interfaz de usuario (archivo. Vsct e implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz)

- Registro del VSPackage con Visual Studio.

El VSPackage de control de código fuente debe comunicarse con estas otras entidades de Visual Studio:

- Proyectos

- Editores

- Soluciones

- Windows

- La tabla de documentos en ejecución

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servicios de entorno de Visual Studio que se pueden consumir

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servicio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementadas y llamadas

Un paquete de control de código fuente es un VSPackage y, por tanto, puede interactuar directamente con otros VSPackages que están registrados con Visual Studio. Con el fin de proporcionar toda la funcionalidad de control de código fuente, un VSPackage de control de código fuente puede tratar con las interfaces proporcionadas por los proyectos o el shell.

Cada proyecto de Visual Studio debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> para que se reconozca como un proyecto en el IDE de Visual Studio. Sin embargo, esta interfaz no es lo suficientemente especializada para el control de código fuente. Los proyectos que se espera que estén bajo el control de código fuente implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Esta interfaz la usa el VSPackage de control de código fuente para consultar su contenido en un proyecto y proporcionar glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está bajo control de código fuente).

El VSPackage de control de código fuente implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , que a su vez permite que los proyectos se registren en el control de código fuente y recuperen sus glifos de estado.

Para obtener una lista completa de las interfaces que debe tener en cuenta un VSPackage de control de código fuente, vea [servicios e interfaces relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vea también

- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
