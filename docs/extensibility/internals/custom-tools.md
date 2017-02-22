---
title: "Herramientas personalizadas | Microsoft Docs"
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
  - "VSPackages, herramientas personalizadas"
  - "herramientas [Visual Studio], personalizados"
  - "herramientas personalizadas"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Herramientas personalizadas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*Las herramientas personalizadas* permiten asociar una herramienta con un elemento de un proyecto y ejecutar dicha herramienta cada vez que se guarda el archivo.  Ciertas herramientas personalizadas, denominadas a veces *los generadores de un solo archivo*, se utilizan con frecuencia para implementar los traductores que generan código de datos y viceversa.  Por ejemplo, los generadores de un solo archivo crean [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y el código fuente de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] fuera de los archivos .settings y .resx.  El código fuente generado proporciona acceso fuertemente tipado a los datos en los archivos .settings y .resx.  los tipos de proyecto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y de[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] admiten las herramientas personalizadas; los tipos de proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no.  Poseer tipos de proyecto también puede admitir las herramientas personalizadas.  
  
 Las herramientas personalizadas son componentes registrados que implementan la interfaz de `IVsSingleFileGenerator` .  
  
 Las herramientas personalizadas son asociado con un objeto de interfaz de `ProjectItem` , y son los diseñadores y editores.  Una herramienta personalizada toma el archivo representado por `ProjectItem` como entrada y escriba un nuevo archivo cuyo nombre de archivo es proporcionada por el método de `DefaultExtension` .  
  
## En esta sección  
 [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)  
 describe cómo utilizar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> para implementar una herramienta personalizada.  
  
 [Determinación del espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Describe cómo determinar el espacio de nombres correcto basándose en el lenguaje utilizado.  
  
 [Registrar generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)  
 Proporciona descripciones para todas las entradas de Registro de una herramienta personalizada.  
  
 [Exponer tipos de diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica cómo los sistemas de proyectos proporcionan compatibilidad para los diseñadores visuales a las clases y los tipos generados acceso a través de archivos ejecutables portables \(PE\) temporales.  
  
 [Conservar la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Muestra cómo guardar una propiedad de elemento de proyecto, como el autor de un archivo de código fuente, en el archivo de proyecto.  
  
## Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Proporciona detalles sobre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, que transforma un único archivo de entrada en un archivo de salida única que se puede compilar o agregado a un proyecto.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica la interfaz de `ProjectItem` , que representa un elemento de un proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Proporciona detalles sobre el método de `DefaultExtension` , que recupera la extensión de nombre de archivo que se proporciona el nombre del archivo de salida.  
  
## Secciones relacionadas  
 [Extender proyectos](../../extensibility/extending-projects.md)  
 Describe cómo utilizar los proyectos y las soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de organizar los archivos y los archivos de recursos del código, y cómo implementar el control de código fuente.