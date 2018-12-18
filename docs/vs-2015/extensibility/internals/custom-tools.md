---
title: Herramientas personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793430"
---
# <a name="custom-tools"></a>Herramientas personalizadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Herramientas personalizadas* le permiten asociar una herramienta con un elemento en un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Determinadas herramientas personalizadas, a veces se denomina *generadores de un solo archivo*, con frecuencia se utilizan para implementar los traductores que generan código de los datos y viceversa. Por ejemplo, creación generadores de un solo archivo [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] código fuera de los archivos .resx y de .settings fuente. El código fuente generado proporciona acceso fuertemente tipado a los datos en los archivos .resx y de .settings. El [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipos de proyectos admiten herramientas personalizadas; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tipos de proyectos no lo hacen. Sus propios tipos de proyecto también pueden admitir herramientas personalizadas.  
  
 Las herramientas personalizadas son componentes registrados que implementan el `IVsSingleFileGenerator` interfaz.  
  
 Herramientas personalizadas están asociadas con un `ProjectItem` objeto de la interfaz y son similares a los diseñadores y editores. Una herramienta personalizada toma el archivo representado por un `ProjectItem` como entrada y escribe un nuevo archivo cuyo nombre de archivo proporciona el `DefaultExtension` método.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)  
 Describe cómo utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz para implementar una herramienta personalizada.  
  
 [Determinar el espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Describe cómo determinar el espacio de nombres correcto según el idioma que se va a usar.  
  
 [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)  
 Proporciona descripciones de todas las entradas del registro para una herramienta personalizada.  
  
 [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica cómo los sistemas de proyecto proporcionan soporte técnico para los diseñadores visuales para acceso genera clases y tipos a través de los archivos ejecutables portables (PE) temporales.  
  
 [Conservación de la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Muestra cómo conservar una propiedad de elemento de proyecto, como el autor de un archivo de código fuente, en el archivo de proyecto.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Proporciona detalles sobre la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, que transforma un archivo de entrada en un único archivo de salida que se compila o se agrega a un proyecto.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica la `ProjectItem` interfaz, que representa un elemento en un proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Proporciona detalles sobre el `DefaultExtension` método, que recupera la extensión de nombre de archivo que se asigna al nombre del archivo de salida.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ampliación de proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.

