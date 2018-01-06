---
title: Comando contratos en los ensamblados de interoperabilidad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d32a49d780f6ae7929f1442ee70a8085724ca6e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comando en ensamblados de interoperabilidad
El contrato básico para controlar los comandos a través de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz es que el entorno llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar si se admite el comando y, si procede, para determinar su estado y el texto. A continuación, el entorno llama el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para ejecutar el comando.  
  
 El <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se controla de forma idéntica para todos los comandos. La comunicación posterior, si es necesario (por ejemplo, con listas desplegables), se administra mediante una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método con parámetros adecuados. La interpretación de estos parámetros depende del comando especificado.  
  
 Si el destino del comando devuelve los valores en el parámetro de salida, el autor de la llamada siempre es responsable de liberar los recursos que se habían asignados. Dado que este parámetro es una variante, borrar la variante libera los recursos.  
  
 En casos donde los comandos deben funcionar dentro de una ventana de la jerarquía, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> debe usarse la interfaz. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz tiene un contrato similar con otros métodos similares: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementación](../../extensibility/internals/command-implementation.md)