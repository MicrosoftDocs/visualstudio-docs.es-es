---
title: Estructura de VSPackage (VSPackage de Control de código fuente) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d36e31db9c47325e62fe759cd5030c5f24fb73be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057628"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de control de código fuente)

El SDK de paquete de Control de código fuente proporciona directrices para crear un VSPackage que permiten un implementador de control de origen para integrar su propia funcionalidad de control de código fuente con el entorno de Visual Studio. Un VSPackage es un componente COM que normalmente se carga a petición mediante el entorno de desarrollo integrado de Visual Studio (IDE) en función de los servicios que se anuncian el paquete en sus entradas del registro. Cada VSPackage debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Normalmente, un VSPackage consume servicios ofrecidos por el IDE de Visual Studio y ofrece algunos servicios propios.

Un VSPackage declara sus elementos de menú y establece el estado de un elemento de forma predeterminada mediante el archivo .vsct. El IDE de Visual Studio muestra los elementos de menú en este estado hasta que se carga el VSPackage. Posteriormente, la implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se llama para habilitar o deshabilitar elementos de menú.

## <a name="source-control-package-characteristics"></a>Características del paquete de Control de código fuente

Un VSPackage de control de código fuente está muy integrado en Visual Studio. La semántica de VSPackage incluye:

-   Interfaz que se implementa en virtud de ser un paquete VSPackage (el `IVsPackage` interfaz)

-   Implementación de comandos de la interfaz de usuario (archivo .vsct y la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz)

-   Registro del VSPackage con Visual Studio.

El control de código fuente VSPackage debe comunicarse con estas otras entidades de Visual Studio:

-   Proyectos

-   Editores

-   Soluciones

-   Windows

-   La tabla de documentos en ejecución

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servicios del entorno de Visual Studio que pueden consumir

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servicio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementado y llamado

Un paquete de control de código fuente es un paquete VSPackage y, por lo tanto puede interactuar directamente con otros VSPackages que están registrados con Visual Studio. Con el fin de proporcionar la gran variedad de funcionalidad de control de código fuente, un control de código fuente VSPackage puede tratar con interfaces proporcionadas por el shell o proyectos.

Todos los proyectos de Visual Studio deben implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> sea reconocida como un proyecto en el IDE de Visual Studio. Sin embargo, no está especializada en esta interfaz suficiente para el control de código fuente. Proyectos que se esperan que esté en el origen de control de implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Esta interfaz se usa por el VSPackage de control de código fuente para consultar un proyecto para su contenido y proporcionarla glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está por debajo control de código fuente).

El control de código fuente VSPackage implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, que a su vez permite a los proyectos se registran para el control de código fuente y recuperar los glifos de estado.

Para obtener una lista completa de interfaces que debe tener en cuenta un VSPackage de control de código fuente, consulte [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vea también

- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)