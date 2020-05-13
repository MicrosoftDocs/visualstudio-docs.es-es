---
title: Contratos de comandos en ensamblados de interoperabilidad ? Microsoft Docs
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
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709689"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comando en ensamblados de interoperabilidad
El contrato básico para <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> controlar comandos a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> través de la interfaz es que el entorno llama al método para determinar si se admite el comando y, si se admite, para determinar su estado y texto. A continuación, el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> entorno llama al método para ejecutar el comando.

 El <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se controla de forma idéntica para todos los comandos. La comunicación adicional, si es necesario (por ejemplo, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> con listas desplegables), se administra llamando al método con los parámetros adecuados. La interpretación de estos parámetros depende del comando especificado.

 Si el destino del comando devuelve valores en el parámetro de salida, el autor de la llamada siempre es responsable de liberar los recursos que se han asignado. Dado que este parámetro es una variante, la compensación de la variante libera los recursos.

 En los casos en que los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> comandos deben funcionar dentro de una ventana de jerarquía, se debe utilizar la interfaz. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz tiene un contrato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>similar con métodos similares: y .

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementación del comando](../../extensibility/internals/command-implementation.md)
