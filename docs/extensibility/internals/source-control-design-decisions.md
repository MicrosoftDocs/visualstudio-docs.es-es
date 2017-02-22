---
title: "Decisiones de dise&#241;o del Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], las decisiones de diseño"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Decisiones de dise&#241;o del Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las decisiones de diseño siguientes se deben considerar para proyectos al implementar el control de código fuente.  
  
## ¿La información se compartido o privado?  
 La decisión de diseño más importante que puede tomar es qué es compartible información y qué es privado.  Por ejemplo, la lista de archivos del proyecto se comparte, pero dentro de esta lista de archivos, algunos usuarios deseen tener archivos privados.  Se comparten los valores del compilador, pero el proyecto de inicio suele ser privado.  Los valores o se comparten puramente, compartido con un reemplazo, o puramente privado.  Por diseño, los elementos privados, como archivos de opciones de usuario de la solución \(.suo\), no se comprueban en [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].  Asegúrese de almacenar cualquier archivo privado de información en privado como el archivo .suo, o un archivo privado concreto que crea, por ejemplo, un archivo de .csproj.user para Visual c\# o un archivo .vbproj.user para Visual Basic.  
  
 Esta decisión no es inclusivo y se puede crear individualmente para cada elemento.  
  
## ¿El proyecto incluirá archivos especiales?  
 Otra opción de diseño importante es si la estructura del proyecto utiliza archivos especiales.  Los archivos especiales son archivos ocultos que son la base de los archivos que están visibles en el explorador de soluciones y en los cuadros de diálogo de protección y desprotección.  Si utiliza archivos especiales, siga estas instrucciones:  
  
1.  No asocia los archivos especiales con la raíz del proyecto nodo\-que es, con el propio archivo de proyecto.  el archivo de proyecto debe ser un solo archivo.  
  
2.  Cuando los archivos especiales se agregan, se quitan, o se cambia en un proyecto, los eventos adecuados de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> deben desencadenarse con el marcador establecido que indica que los archivos son archivos especiales.  Estos eventos llama el entorno en respuesta al proyecto que llama a los métodos adecuados de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3.  Cuando el proyecto o el editor llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> para un archivo, archivos especiales asociado a ese archivo no se desprotegen automáticamente.  Pase los archivos especiales de junto con el archivo principal.  El entorno detectará la relación entre todos los archivos que se pasen y ocultar correctamente los archivos especiales en la interfaz de usuario de desprotección.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Compatibilidad con Control de código fuente](../../extensibility/internals/supporting-source-control.md)