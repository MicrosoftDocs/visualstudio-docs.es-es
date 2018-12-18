---
title: Los contratos en los ensamblados de interoperabilidad de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ac80125111ebfe3d8a7e5dc89d1f2597f8d3a4
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510860"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comandos en los ensamblados de interoperabilidad
El contrato básico para el control de comandos a través de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz es que el entorno llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar si se admite el comando y, si procede, para determinar su estado y el texto. A continuación, el entorno llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para ejecutar el comando.  
  
 El <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se controla de forma idéntica para todos los comandos. Comunicación posterior, si es necesario (por ejemplo, con las listas desplegables), se administra mediante una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método con parámetros adecuados. La interpretación de estos parámetros depende del comando especificado.  
  
 Si el destino del comando devuelve los valores en el parámetro de salida, el autor de llamada siempre es responsable de liberar todos los recursos que había sido asignados. Dado que este parámetro es una variante, borrar la variante libera los recursos.  
  
 En casos donde los comandos deben funcionar dentro de una ventana de jerarquía, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> se debe usar la interfaz. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz tiene un contrato similar con métodos similares: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementación de comandos](../../extensibility/internals/command-implementation.md)