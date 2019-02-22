---
title: Información general sobre soluciones | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2df03e73d963b7b1b6166b1376d31b517f515dcd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645464"
---
# <a name="solutions-overview"></a>Información general sobre soluciones
Una solución es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. La información de proyecto y el estado correspondiente a la solución se almacenan en dos archivos de solución diferente. El archivo de solución (.sln) está basado en texto y puede ponerse bajo el control de código fuente y comparten los usuarios. El archivo de opción (.suo) de usuario de solución es binario. Como resultado, el archivo .suo no puede colocarse bajo control de código fuente y contiene información específica del usuario.

 Cualquier VSPackage puede escribir en cualquier tipo de archivo de solución. Dada la naturaleza de los archivos, hay dos interfaces diferentes implementadas para escribir en ellos. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz escribe información de texto en el archivo .sln y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz escribe secuencias binarias en el archivo .suo.

> [!NOTE]
>  Un proyecto no tiene que escribir explícitamente una entrada para sí mismo en el archivo de solución el entorno encarga del proyecto. Por lo tanto, a menos que desee agregar contenido adicional específicamente para el archivo de solución, no es necesario registrar el VSPackage en este modo.

 Cada paquete VSPackage que admiten la persistencia de la solución usa tres interfaces, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz, que es implementado por el entorno y lo llama el VSPackage, y `IVsPersistSolutionProps` y `IVsPersistSolutionOpts`, que son ambos implementados por el VSPackage. El `IVsPersistSolutionOpts` interfaz sólo debe implementarse si se se escritos por el VSPackage en el archivo .suo información privada.

 Cuando se abre una solución, el proceso siguiente tiene lugar.

1. El entorno lee la solución.

2. Si el entorno se encuentra un `CLSID`, carga el VSPackage correspondiente.

3. Si se carga un paquete VSPackage, el entorno llama a `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaz para la interfaz que requiere el VSPackage.

   1.  Al leer desde un archivo .sln, el entorno llama a `QueryInterface` para `IVsPersistSolutionProps`.

   2.  Al leer desde un archivo .suo, el entorno llama a `QueryInterface` para `IVsPersistSolutionOpts`.

   Información específica sobre el uso de estos archivos puede encontrarse en [solución (. Los archivos sln)](../../extensibility/internals/solution-dot-sln-file.md) y [opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
>  Si desea crear una nueva configuración de solución que consta de las configuraciones de dos de los proyectos y exclusión de un tercio de la compilación, deberá usar la interfaz de usuario de páginas de propiedad o la automatización. No se puede cambiar las configuraciones de administrador de compilación de soluciones y sus propiedades directamente, pero se puede manipular mediante el Administrador de compilación de soluciones el `SolutionBuild` clase a partir de DTE del modelo de automatización. Para obtener más información sobre la configuración de soluciones, consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>