---
title: Estructura de VSPackage (VSPackage de control de código fuente) | Microsoft Docs
description: Obtenga información sobre el SDK del paquete de control de código fuente, que proporciona instrucciones para que un VSPackage con un implementador de control de código fuente se integre con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898827"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de control de código fuente)

El SDK del paquete de control de código fuente proporciona instrucciones para crear un VSPackage que permite a un implementador de control de código fuente integrar su funcionalidad de control de código fuente con el Visual Studio código fuente. Un VSPackage es un componente COM que normalmente el entorno de desarrollo integrado (IDE) de Visual Studio carga a petición en función de los servicios anunciados por el paquete en sus entradas del Registro. Cada VSPackage debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Normalmente, un VSPackage consume los servicios ofrecidos por Visual Studio IDE y ofrece algunos servicios propios.

Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado a través del archivo .vsct. El IDE Visual Studio muestra los elementos de menú en este estado hasta que se carga el VSPackage. Posteriormente, se llama a la implementación del vsPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para habilitar o deshabilitar elementos de menú.

## <a name="source-control-package-characteristics"></a>Características del paquete de control de código fuente

Un VSPackage de control de código fuente está profundamente integrado en Visual Studio. La semántica de VSPackage incluye:

- Interfaz que se va a implementar en virtud de ser un VSPackage (la `IVsPackage` interfaz )

- Implementación del comando de interfaz de usuario (archivo .vsct e implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz)

- Registro del VSPackage con Visual Studio.

El VSPackage del control de código fuente debe comunicarse con estas otras Visual Studio entidades:

- Proyectos

- Editores

- Soluciones

- Windows

- Tabla de documentos en ejecución

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio servicios de entorno que se pueden consumir

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servicio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementadas y llamadas

Un paquete de control de código fuente es un VSPackage y, por tanto, puede interactuar directamente con otros VSPackages registrados con Visual Studio. Para proporcionar toda la gama de funcionalidades de control de código fuente, un VSPackage de control de código fuente puede tratar con interfaces proporcionadas por proyectos o el shell.

Todos los proyectos Visual Studio implementar para que se reconozcan como un proyecto dentro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> IDE Visual Studio proyecto. Sin embargo, esta interfaz no está lo suficientemente especializada para el control de código fuente. Los proyectos que se espera que estén bajo control de código fuente implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . El VSPackage del control de código fuente usa esta interfaz para consultar su contenido en un proyecto y para proporcionar glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está bajo control de código fuente).

El control de código fuente VSPackage implementa , que a su vez permite que los proyectos se registren para el control de código fuente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> y recuperen sus glifos de estado.

Para obtener una lista completa de las interfaces que debe tener en cuenta un VSPackage de control de código fuente, vea [Servicios e interfaces relacionados.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>Consulta también

- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
