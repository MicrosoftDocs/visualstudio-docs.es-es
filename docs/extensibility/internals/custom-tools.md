---
title: Herramientas personalizadas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7589c9a2aedf987af79689e8babccb554fbb4ccc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tools"></a>Herramientas personalizadas
*Herramientas personalizadas* le permiten asociar una herramienta con un elemento de un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Determinadas herramientas personalizadas, a veces se denomina *generadores de un solo archivo*, con frecuencia se utilizan para implementar traductores que generan código de datos y viceversa. Por ejemplo, crear generadores de un solo archivo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] código fuera de los archivos .settings y .resx fuente. El código fuente generado proporciona acceso fuertemente tipado a los datos en los archivos .settings y .resx. El [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto admiten herramientas personalizadas; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipos de proyecto no tienen que serlo. Sus propios tipos de proyecto también admiten las herramientas personalizadas.  
  
 Las herramientas personalizadas son componentes registrados que implementan el `IVsSingleFileGenerator` interfaz.  
  
 Herramientas personalizadas están asociadas a un `ProjectItem` objeto de la interfaz y son iguales que los editores y diseñadores. Una herramienta personalizada toma el archivo representado por un `ProjectItem` como entrada y escribe un nuevo archivo cuyo nombre de archivo es proporcionada por el `DefaultExtension` método.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)  
 Describe cómo utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz para implementar una herramienta personalizada.  
  
 [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)  
 Proporciona descripciones de todas las entradas del registro para una herramienta personalizada.  
  
 [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica cómo sistemas del proyecto proporcionan compatibilidad para los diseñadores visuales para acceso genera clases y tipos a través de los archivos ejecutables portables (PE) temporales.  
  
 [Conservación de la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Muestra cómo conservar una propiedad de elemento de proyecto, como el autor de un archivo de origen, en el archivo de proyecto.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Proporciona detalles sobre la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, que transforma un único archivo de entrada en un único archivo de salida que se compila o se agrega a un proyecto.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica la `ProjectItem` interfaz, que representa un elemento en un proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Proporciona detalles sobre la `DefaultExtension` método, que recupera la extensión de nombre de archivo que recibe el nombre de archivo de salida.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ampliación de proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos y soluciones para organizar los archivos de código y archivos de recursos y cómo implementar el control de código fuente.