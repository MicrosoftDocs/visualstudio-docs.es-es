---
title: Introducción a soluciones
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705297"
---
# <a name="solutions-overview"></a>Introducción a soluciones

Una solución es una agrupación de uno o varios proyectos que trabajan juntos para crear una aplicación. La información de proyecto y estado de la solución se almacena en dos archivos de solución diferentes. El archivo de [solución (.sln)](solution-dot-sln-file.md) está basado en texto y se puede colocar bajo control de código fuente y compartirse entre usuarios. El archivo de opción de [usuario de solución (.suo)](solution-user-options-dot-suo-file.md) es binario. Como resultado, el archivo .suo no se puede colocar bajo control de código fuente y contiene información específica del usuario.

Cualquier VSPackage puede escribir en cualquier tipo de archivo de solución. Debido a la naturaleza de los archivos, hay dos interfaces diferentes implementadas para escribir en ellos. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz escribe información de texto en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> el archivo .sln y la interfaz escribe secuencias binarias en el archivo .suo.

> [!NOTE]
> Un proyecto no tiene que escribir explícitamente una entrada para sí mismo en el archivo de solución; el entorno lo controla para el proyecto. Por lo tanto, a menos que desee agregar contenido adicional específicamente al archivo de solución, no es necesario registrar el VSPackage de esta manera.

Cada VSPackage que admite la persistencia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> de la solución usa tres interfaces, la `IVsPersistSolutionProps` interfaz, que se implementa por el entorno y llama por el VSPackage y `IVsPersistSolutionOpts`, que se implementan por el VSPackage. La `IVsPersistSolutionOpts` interfaz solo debe implementarse si el VSPackage debe escribir información privada en el archivo .suo.

Cuando se abre una solución, se lleva a cabo el siguiente proceso.

1. El entorno lee la solución.

2. Si el entorno `CLSID`encuentra un , carga el VSPackage correspondiente.

3. Si se carga un VSPackage, el entorno llama `QueryInterface` a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaz para la interfaz que requiere el VSPackage.

   - Al leer desde un archivo .sln, el entorno requiere `QueryInterface` `IVsPersistSolutionProps`.

   - Al leer desde un archivo .suo, el entorno requiere `QueryInterface` `IVsPersistSolutionOpts`.

   La información específica relacionada con el uso de estos archivos se puede encontrar en la [solución (. Sln)](../../extensibility/internals/solution-dot-sln-file.md) Opciones de usuario de archivo y [solución (. Suo) Archivo](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Si desea crear una nueva configuración de solución que consta de las configuraciones de dos proyectos y excluir un tercero de la compilación, debe usar la interfaz de usuario de páginas de propiedades o la automatización. No puede cambiar las configuraciones del administrador de compilación de soluciones y sus `SolutionBuild` propiedades directamente, pero puede manipular el administrador de compilación de soluciones mediante la clase de DTE en el modelo de automatización. Para obtener más información acerca de la configuración de soluciones, vea Configuración de la [solución](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
