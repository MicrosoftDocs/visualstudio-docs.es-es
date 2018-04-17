---
title: Las decisiones de diseño del Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0385d5feb7baf7fe60e253616c8db0f326932e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-design-decisions"></a>Decisiones de diseño del Control de código fuente
Las siguientes decisiones de diseño deberían considerarse para proyectos al implementar el control de código fuente.  
  
## <a name="will-information-be-shared-or-private"></a>¿Será información compartido o privado?  
 La decisión de diseño más importante que puede realizar es qué información se puede compartir y lo que es privado. Por ejemplo, la lista de archivos para el proyecto se comparte, pero dentro de esta lista de archivos, algunos usuarios podrían desear tener archivos privados. Configuración del compilador se comparte, pero el proyecto de inicio es generalmente privado. Configuración es puramente compartidos, compartidos con una invalidación o puramente privada. De forma predeterminada, los elementos privados, como opciones de usuario de solución (.suo) (archivos), no se comprueban en [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. No olvide almacenar cualquier información privada en archivos privados como el archivo .suo, o un archivo privado específico que crea, por ejemplo, un. csproj.user archivo para Visual C# o. vbproj.user archivo en Visual Basic.  
  
 Esta decisión no es exhaustiva y se puede realizar en el elemento por elemento.  
  
## <a name="will-the-project-include-special-files"></a>¿El proyecto incluye archivos especiales?  
 Otra importante decisión de diseño es si la estructura del proyecto utiliza archivos especiales. Archivos especiales están ocultos que subyacen a los archivos que son cuadros de diálogo visible en el Explorador de soluciones y en la protección y desprotección. Si utiliza archivos especiales, siga estas instrucciones:  
  
1.  No asocie archivos especiales con el nodo raíz del proyecto, es decir, con el proyecto de archivo. El archivo de proyecto debe ser un único archivo.  
  
2.  Cuando se agregan, se quitan o se cambió de nombre en un proyecto, la correspondiente archivos especiales <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> eventos deben activarse con el conjunto de marca que indica los archivos son archivos especiales. Estos eventos se denominan por el entorno en respuesta al proyecto de una llamada a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> métodos.  
  
3.  Cuando llama a un proyecto o el editor de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> para un archivo, los archivos especiales asociados a ese archivo no se desprotege automáticamente. Pase los archivos especiales de junto con el archivo principal. El entorno se detecte la relación entre todos los archivos que se pasan y ocultar adecuadamente los archivos especiales de la interfaz de usuario de extracción del repositorio.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)