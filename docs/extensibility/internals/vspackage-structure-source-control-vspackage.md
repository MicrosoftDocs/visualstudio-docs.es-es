---
title: Estructura de VSPackage (Control de código fuente VSPackage) Microsoft Docs
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
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703805"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de control de código fuente)

El SDK de paquete de Control de código fuente proporciona instrucciones para crear un VSPackage que permiten a un implementador de control de código fuente integrar su funcionalidad de control de código fuente con el entorno de Visual Studio. Un VSPackage es un componente COM que normalmente se carga a petición por el entorno de desarrollo integrado (IDE) de Visual Studio en función de los servicios que anuncia el paquete en sus entradas del Registro. Cada VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>debe implementar . Un VSPackage normalmente consume servicios ofrecidos por el IDE de Visual Studio y ofrece algunos servicios propios.

Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado a través del archivo .vsct. El IDE de Visual Studio muestra los elementos de menú en este estado hasta que se carga el VSPackage. Posteriormente, se llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> implementación del método de VSPackage para habilitar o deshabilitar los elementos de menú.

## <a name="source-control-package-characteristics"></a>Características del paquete de control de código fuente

Un control de código fuente VSPackage está profundamente integrado en Visual Studio. La semántica de VSPackage incluye:

- Interfaz que se implementará en virtud `IVsPackage` de ser un VSPackage (la interfaz)

- Implementación del comando UI (archivo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .vsct e implementación de la interfaz)

- Registro del VSPackage con Visual Studio.

El control de código fuente VSPackage debe comunicarse con estas otras entidades de Visual Studio:

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

Un paquete de control de código fuente es un VSPackage y, por lo tanto, puede interactuar directamente con otros VSPackages que están registrados con Visual Studio. Con el fin de proporcionar la amplitud completa de la funcionalidad de control de código fuente, un control de código fuente VSPackage puede tratar con las interfaces proporcionadas por los proyectos o el shell.

Cada proyecto de Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Studio debe implementarse para que se reconozca como un proyecto dentro del IDE de Visual Studio. Sin embargo, esta interfaz no está lo suficientemente especializada para el control de código fuente. Los proyectos que se espera <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>que estén bajo control de código fuente implementan . Esta interfaz se utiliza el control de código fuente VSPackage para consultar un proyecto para su contenido y para proporcionar glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación de disco de un proyecto que está bajo control de código fuente).

El control de código <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>fuente que implementa VSPackage , que a su vez permite que los proyectos se registren para el control de código fuente y recuperar sus glifos de estado.

Para obtener una lista completa de interfaces que un control de código fuente VSPackage debe tener en cuenta, vea [Servicios e interfaces relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vea también

- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
