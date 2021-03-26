---
title: Introducción a soluciones
description: Obtenga información sobre los aspectos internos de una solución, para los desarrolladores de extensiones que deseen trabajar con soluciones en extensiones de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 914f1744accc10eb55cfb0b321a04560c27bca05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069379"
---
# <a name="solutions-overview"></a>Introducción a soluciones

Una solución es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. El proyecto y la información de estado relativa a la solución se almacenan en dos archivos de solución diferentes. El [archivo de solución (. sln)](solution-dot-sln-file.md) está basado en texto y puede colocarse bajo control de código fuente y compartirse entre usuarios. El archivo de la opción de usuario de la [solución (. suo)](solution-user-options-dot-suo-file.md) es binario. Como resultado, no se puede colocar el archivo. suo bajo control de código fuente y contiene información específica del usuario.

Cualquier VSPackage puede escribir en cualquier tipo de archivo de solución. Debido a la naturaleza de los archivos, hay dos interfaces diferentes implementadas para escribir en ellas. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz escribe información de texto en el archivo. sln y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz escribe secuencias binarias en el archivo. suo.

> [!NOTE]
> Un proyecto no tiene que escribir explícitamente una entrada en el archivo de solución; el entorno se encarga del proyecto. Por lo tanto, a menos que desee agregar contenido adicional específicamente al archivo de solución, no es necesario registrar el VSPackage de esta manera.

Cada VSPackage que admite la persistencia de la solución usa tres interfaces, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz, que implementa el entorno y a las que llama el VSPackage, y `IVsPersistSolutionProps` y `IVsPersistSolutionOpts` , que ambos implementa el VSPackage. La `IVsPersistSolutionOpts` interfaz solo debe implementarse si el VSPackage va a escribir información privada en el archivo. suo.

Cuando se abre una solución, se produce el siguiente proceso.

1. El entorno lee la solución.

2. Si el entorno encuentra un `CLSID` , carga el VSPackage correspondiente.

3. Si se carga un VSPackage, el entorno llama `QueryInterface` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> la interfaz para la interfaz que requiere el VSPackage.

   - Al leer desde un archivo. sln, el entorno llama a `QueryInterface` para `IVsPersistSolutionProps` .

   - Al leer desde un archivo. suo, el entorno de llama a `QueryInterface` para `IVsPersistSolutionOpts` .

   Puede encontrar información específica relacionada con el uso de estos archivos en la [solución (. Sln)](../../extensibility/internals/solution-dot-sln-file.md) opciones de usuario de archivos y [soluciones (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Si desea crear una nueva configuración de soluciones formada por dos configuraciones de proyectos y excluida una tercera de la compilación, debe usar la interfaz de usuario de las páginas de propiedades o la automatización. No puede cambiar las configuraciones del administrador de compilación de soluciones y sus propiedades directamente, pero puede manipular el administrador de compilación de soluciones mediante la `SolutionBuild` clase de dte en el modelo de automatización. Para obtener más información sobre la configuración de soluciones, vea [configuración de soluciones](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Consulte también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
