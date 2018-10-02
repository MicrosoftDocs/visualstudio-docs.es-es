---
title: Las decisiones de diseño del Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f43c9d2423e0eaafbdcae41169c47d5fcb01912
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566792"
---
# <a name="source-control-design-decisions"></a>Decisiones de diseño del control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [decisiones de diseño del Control de código fuente](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-design-decisions).  
  
Las siguientes decisiones de diseño deben considerarse para los proyectos al implementar el control de código fuente.  
  
## <a name="will-information-be-shared-or-private"></a>¿Será información privada o compartida?  
 La decisión de diseño más importante que puede realizar es qué información se puede compartir y lo que es privada. Por ejemplo, se comparte la lista de archivos para el proyecto, pero dentro de esta lista de archivos, algunos usuarios podrían desear tener archivos privados. Configuración del compilador se comparten, pero el proyecto de inicio es generalmente privado. Configuración es puramente compartidos, compartidos con una invalidación o puramente privada. Por diseño, elementos privados, como las opciones de usuario de la solución (.suo) archivos, no se comprueban en [!INCLUDE[vsvss](../../includes/vsvss-md.md)]. Asegúrese de almacenar información privada en archivos privados como el archivo .suo, o un archivo privado específico, por ejemplo, crea un. csproj.user archivo para Visual C# o. vbproj.user archivo para Visual Basic.  
  
 Esta decisión no es exhaustiva y se puede realizar en una base de los elementos.  
  
## <a name="will-the-project-include-special-files"></a>¿El proyecto incluye archivos especiales?  
 Otra decisión de diseño importante es que si la estructura del proyecto usa archivos especiales. Archivos especiales están ocultos que subyacen a los archivos que son cuadros de diálogo visible en el Explorador de soluciones y en la protección y desprotección. Si usa archivos especiales, siga estas instrucciones:  
  
1.  No asocie archivos especiales con el nodo raíz del proyecto, es decir, con el proyecto propio archivo. El archivo de proyecto debe ser un único archivo.  
  
2.  Cuando se agrega archivos especiales, eliminados o cambiado el nombre de un proyecto, adecuado <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> se deben activar eventos con el conjunto de marca que indica los archivos son archivos especiales. Estos eventos se lo llama el entorno en respuesta al proyecto una llamada a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos.  
  
3.  Cuando llama su editor o proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> para un archivo, los archivos especiales asociados con ese archivo no se desprotege automáticamente. Pase los archivos especiales en junto con el archivo principal. El entorno se detecte la relación entre todos los archivos que se pasan y ocultar adecuadamente los archivos especiales en la interfaz de usuario de desprotección.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)

