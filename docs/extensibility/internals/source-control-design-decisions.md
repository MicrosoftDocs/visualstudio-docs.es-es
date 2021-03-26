---
title: Decisiones de diseño del control de código fuente | Microsoft Docs
description: Obtenga información acerca de varias decisiones de diseño clave que se deben tener en cuenta para los proyectos al implementar el control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82afa3bfee446ab5bd214fd5ac58dbfac9523467
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069327"
---
# <a name="source-control-design-decisions"></a>Decisiones de diseño del control de código fuente
Se deben tener en cuenta las siguientes decisiones de diseño para los proyectos de al implementar el control de código fuente.

## <a name="will-information-be-shared-or-private"></a>¿La información será compartida o privada?
 La decisión de diseño más importante que puede tomar es la información que se puede compartir y lo que es privado. Por ejemplo, la lista de archivos para el proyecto está compartida, pero, en esta lista de archivos, es posible que algunos usuarios deseen tener archivos privados. La configuración del compilador está compartida, pero el proyecto de inicio suele ser privado. La configuración es simplemente compartida, compartida con una invalidación o simplemente privada. Por diseño, los elementos privados, como los archivos de opciones de usuario de la solución (. suo), no se protegen en [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . Asegúrese de almacenar cualquier información privada en archivos privados, como el archivo. suo, o en un archivo privado específico que cree, por ejemplo, un archivo. csproj. User para Visual C# o un archivo. vbproj. User para Visual Basic.

 Esta decisión no es todo-inclusiva y se puede realizar en cada elemento.

## <a name="will-the-project-include-special-files"></a>¿Incluirá el proyecto archivos especiales?
 Otra decisión de diseño importante es si la estructura del proyecto usa archivos especiales. Los archivos especiales son archivos ocultos que subyacen a los archivos que están visibles en Explorador de soluciones y en los cuadros de diálogo proteger y desproteger. Si usa archivos especiales, siga estas instrucciones:

1. No asocie archivos especiales con el nodo raíz del proyecto, es decir, con el propio archivo de proyecto. El archivo de proyecto debe ser un único archivo.

2. Cuando se agregan, quitan o cambian de nombre archivos especiales en un proyecto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> se deben desencadenar los eventos correspondientes con el indicador establecido que indica que los archivos son archivos especiales. El entorno llama a estos eventos en respuesta al proyecto que llama a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos adecuados.

3. Cuando el proyecto o el editor llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> un archivo, los archivos especiales asociados a ese archivo no se desprotegen automáticamente. Pase los archivos especiales en junto con el archivo primario. El entorno detectará la relación entre todos los archivos que se pasan y ocultan correctamente los archivos especiales en la interfaz de usuario de desprotección.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
