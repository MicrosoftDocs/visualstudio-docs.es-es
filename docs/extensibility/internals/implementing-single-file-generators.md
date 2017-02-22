---
title: "Implementar generadores de un solo archivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas personalizadas, implementar"
  - "proyectos [Visual Studio SDK], extensibilidad"
  - "proyectos [Visual Studio SDK], administrar herramientas personalizadas"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementar generadores de un solo archivo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una herramienta personalizada \(denominada en ocasiones un generador de un solo archivo \)puede utilizar para extender los sistemas de proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y de[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  una herramienta personalizada es un componente COM que implementa la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  Con esta interfaz, una herramienta personalizada transforma un único archivo de entrada en un archivo de salida única.  El resultado de la transformación puede ser código fuente, o cualquier otra salida que es útil.  Dos ejemplos de archivos herramienta\-generados personalizada de código son código generado en respuesta a cambios en un diseñador visual y archivos generados utilizando el Lenguaje de descripción de servicios web \(WSDL\).  
  
 Cuando una herramienta personalizada se carga, o se guarda el archivo de entrada, el sistema de proyectos el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> , y pasar una referencia a una interfaz de devolución de llamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> , por el que la herramienta puede señalar su progreso al usuario.  
  
 El archivo de salida que la herramienta personalizada genera se agrega al proyecto con una dependencia en el archivo de entrada.  El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación personalizada de la herramienta de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 una herramienta personalizada debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  Opcionalmente, las herramientas personalizadas admiten a la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> que recuperar información de orígenes que no sean del archivo de entrada.  En cualquier caso, para poder utilizar una herramienta personalizada, debe registrarla con el sistema o en el registro local de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Para obtener más información sobre el registro las herramientas personalizadas, vea [Registrar generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md).  
  
## Vea también  
 [Determinación del espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exponer tipos de diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)