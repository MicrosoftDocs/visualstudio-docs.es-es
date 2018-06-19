---
title: Información general sobre soluciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d64175c570c4fbca26bae0aa587b66e04cbee2be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131654"
---
# <a name="solutions-overview"></a>Información general sobre soluciones
Una solución es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. La información de proyecto y de estado relacionada con la solución se almacenan en dos archivos de solución diferente. El archivo de solución (.sln) está basado en texto y se pueden colocar en el control de código fuente y compartirse entre usuarios. El archivo de opción (.suo) de usuario de solución es binario. Como resultado, el archivo .suo no se puede colocar en el control de código fuente y contiene información específica del usuario.  
  
 Puede escribir cualquier VSPackage en cualquier tipo de archivo de solución. Dada la naturaleza de los archivos, hay dos interfaces diferentes implementadas para escribir en ellos. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz escribe información de texto en el archivo .sln y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz escribe secuencias binarias en el archivo .suo.  
  
> [!NOTE]
>  Un proyecto no tiene que escribir explícitamente una entrada para sí mismo en el archivo de solución; el entorno administra el proyecto. Por lo tanto, a menos que desee agregar contenido adicional específicamente para el archivo de solución, no es necesario registrar el VSPackage en este modo.  
  
 Cada VSPackage que admite la persistencia de la solución usa tres interfaces, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz, que es implementada por el entorno y llamado por el VSPackage, y `IVsPersistSolutionProps` y `IVsPersistSolutionOpts`, que son ambos implementados por el VSPackage. El `IVsPersistSolutionOpts` interfaz solo debe implementarse si se escriben por el VSPackage en el archivo .suo información privada.  
  
 Cuando se abre una solución, el siguiente proceso tiene lugar.  
  
1.  El entorno lee la solución.  
  
2.  Si el entorno se encuentra un `CLSID`, carga el VSPackage correspondiente.  
  
3.  Si se carga un paquete VSPackage, el entorno llama `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaz para la interfaz que requiere el VSPackage.  
  
    1.  Cuando se leen desde un archivo .sln, el entorno llama `QueryInterface` para `IVsPersistSolutionProps`.  
  
    2.  Cuando se leen desde un archivo .suo, el entorno llama `QueryInterface` para `IVsPersistSolutionOpts`.  
  
 Información específica sobre el uso de estos archivos puede encontrarse en [solución (. Archivo sln)](../../extensibility/internals/solution-dot-sln-file.md) y [opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Si desea crear una nueva configuración de solución que consta de las configuraciones de dos proyectos y exclusión de un tercio de la compilación, debe utilizar la interfaz de usuario de las páginas de propiedad o la automatización. No se puede cambiar las configuraciones de administrador de compilación de soluciones y sus propiedades directamente, pero puede manipular el Administrador de compilación de soluciones mediante el `SolutionBuild` clase a partir de DTE en el modelo de automatización. Para obtener más información sobre la configuración de soluciones, consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>