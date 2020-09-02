---
title: Contratos de comandos en ensamblados de interoperabilidad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195127"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comandos en los ensamblados de interoperabilidad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El contrato básico para controlar los comandos a través de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz es que el entorno llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar si se admite el comando y, si se admite, para determinar su estado y el texto. A continuación, el entorno llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para ejecutar el comando.  
  
 El <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se controla de forma idéntica para todos los comandos. La comunicación adicional, si es necesario (por ejemplo, con listas desplegables), se administra llamando al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método con los parámetros adecuados. La interpretación de estos parámetros depende del comando especificado.  
  
 Si el destino del comando devuelve valores en el parámetro de salida, el llamador siempre es responsable de liberar todos los recursos que se hayan asignado. Dado que este parámetro es una variante, el borrado de la variante libera los recursos.  
  
 En los casos en los que los comandos deben funcionar en una ventana de jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> se debe usar la interfaz. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz tiene un contrato similar con métodos similares: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
## <a name="see-also"></a>Consulte también  
 [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementación](../../extensibility/internals/command-implementation.md)
