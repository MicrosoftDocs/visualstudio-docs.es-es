---
title: Contratos de comandos en ensamblados de interoperabilidad | Microsoft Docs
description: Obtenga información sobre el contrato básico para controlar los comandos a través de la interfaz Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d655bfb3e6f2206156cd3a6d091ea04f18afe91a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304905"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comandos en ensamblados de interoperabilidad
El contrato básico para controlar los comandos a través de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz es que el entorno llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar si se admite el comando y, si se admite, para determinar su estado y el texto. A continuación, el entorno llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para ejecutar el comando.

 El <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se controla de forma idéntica para todos los comandos. La comunicación adicional, si es necesario (por ejemplo, con listas desplegables), se administra llamando al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método con los parámetros adecuados. La interpretación de estos parámetros depende del comando especificado.

 Si el destino del comando devuelve valores en el parámetro de salida, el llamador siempre es responsable de liberar todos los recursos que se hayan asignado. Dado que este parámetro es una variante, el borrado de la variante libera los recursos.

 En los casos en los que los comandos deben funcionar en una ventana de jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> se debe usar la interfaz. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz tiene un contrato similar con métodos similares: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Consulte también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementación de comandos](../../extensibility/internals/command-implementation.md)
