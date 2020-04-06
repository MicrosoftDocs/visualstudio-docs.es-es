---
title: Decisiones de diseño de control de código fuente ( Source Control Design Decisions) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705253"
---
# <a name="source-control-design-decisions"></a>Decisiones de diseño del control de código fuente
Las siguientes decisiones de diseño deben tenerse en cuenta para los proyectos al implementar el control de código fuente.

## <a name="will-information-be-shared-or-private"></a>¿La información será compartida o privada?
 La decisión de diseño más importante que puede tomar es qué información se puede retar y qué es privada. Por ejemplo, la lista de archivos para el proyecto se comparte, pero dentro de esta lista de archivos, es posible que algunos usuarios deseen tener archivos privados. La configuración del compilador se comparte, pero el proyecto de inicio es generalmente privado. La configuración es puramente compartida, compartida con una invalidación o puramente privada. Por diseño, los elementos privados, como los archivos de [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]opciones de usuario de solución (.suo), no se protegen en . Asegúrese de almacenar cualquier información privada en archivos privados, como el archivo .suo, o un archivo privado específico que cree, por ejemplo, un archivo .csproj.user para Visual C. o un archivo .vbproj.user para Visual Basic.

 Esta decisión no es todo incluido y se puede tomar artículo por artículo.

## <a name="will-the-project-include-special-files"></a>¿El proyecto incluirá archivos especiales?
 Otra decisión de diseño importante es si la estructura del proyecto utiliza archivos especiales. Los archivos especiales son archivos ocultos que subyacen a los archivos visibles en el Explorador de soluciones y en los cuadros de diálogo de protección y desprotección. Si utiliza archivos especiales, siga estas pautas:

1. No asocie archivos especiales con el nodo raíz del proyecto, es decir, con el propio archivo de proyecto. El archivo de proyecto debe ser un único archivo.

2. Cuando se agregan, quitan o se cambia el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> nombre de archivos especiales en un proyecto, los eventos adecuados deben desencadenarse con el conjunto de indicadores que indica que los archivos son archivos especiales. El entorno llama a estos eventos en respuesta <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> al proyecto que llama a los métodos adecuados.

3. Cuando el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> o el editor llama a un archivo, los archivos especiales asociados a ese archivo no se desprotegen automáticamente. Pase los archivos especiales junto con el archivo principal. El entorno detectará la relación entre todos los archivos que se pasan y ocultará adecuadamente los archivos especiales en la interfaz de usuario de desprotección.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
