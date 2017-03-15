---
title: "Exponer tipos de dise&#241;adores visuales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos [Visual Studio SDK] expone a los diseñadores visuales"
  - "diseñadores [Visual Studio SDK], exponer tipos"
  - "herramientas personalizadas, exponer tipos de diseñadores visuales"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Exponer tipos de dise&#241;adores visuales
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe tener acceso a la clase y definiciones de tipos en tiempo de diseño para mostrar un diseñador visual.  Las clases se cargan de un conjunto de ensamblados que contienen la dependencia completa establecida del proyecto actual \(referencias más sus dependencias\).  También puede ser necesario que los diseñadores visuales tengan acceso a las clases y tipos que se definen en los archivos generados por las herramientas personalizadas.  
  
 Los sistemas de proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y de[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proporcionan compatibilidad para tener acceso a las clases y los tipos generados a través de archivos ejecutables portables temporales \(PE temporales\).  Cualquier archivo generado por una herramienta personalizada puede compilar en un ensamblado temporal para poder cargar de esos ensamblados y exponer tipos diseñadores.  La salida de cada herramienta personalizada se compilará en un archivo PE temporal independiente, y el éxito o error de esta compilación temporal sólo depende de si el archivo generado puede compilarse.  Aunque un proyecto no puede compilar en conjunto, PEs temporal individual puede seguir estando disponible diseñadores.  
  
 El sistema de proyectos proporciona compatibilidad completa para realizar cambios en el archivo de salida de una herramienta personalizada, siempre que estos cambios son el resultado de ejecutar la herramienta personalizada.  Cada vez que se ejecuta la herramienta personalizada, se genera un nuevo archivo PE temporal, y las notificaciones adecuadas se envían a los diseñadores.  
  
> [!NOTE]
>  Dado que el archivo ejecutable de compilación del programa temporal en segundo plano, no se notifica ningún error al usuario si se produce un error en la compilación.  
  
 Las herramientas personalizadas que se benefician de compatibilidad temporal PE deben seguir las reglas siguientes:  
  
-   `GeneratesDesignTimeSource` debe establecerse en 1 en el registro.  
  
     Ninguna compilación del archivo ejecutable del programa tiene lugar sin este valor.  
  
-   El código generado debe estar en el mismo idioma que la configuración del proyecto global.  
  
     El archivo PE temporal se compila independientemente de que los informes personalizados de la herramienta como extensión solicitada en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> siempre que `GeneratesDesignTimeSource` se establece en 1 en el registro.  la extensión no necesita ser .vb, .cs, o .jsl; puede ser cualquier extensión.  
  
-   El código generado por la herramienta personalizada debe ser válido, y debe compilar en solitario sólo con el conjunto de referencias presentes en el proyecto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termina de ejecutarse.  
  
     Cuando un archivo PE temporal se compila, el único archivo de código fuente proporcionado al compilador es la herramienta personalizada.  Por consiguiente, una herramienta personalizada que utiliza un archivo PE temporal debe generar archivos de salida que se pueden compilar independientemente de otros archivos del proyecto.  
  
## Vea también  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/es-es/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinación del espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrar generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)