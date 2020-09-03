---
title: Herramientas personalizadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196916"
---
# <a name="custom-tools"></a>Herramientas personalizadas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Las herramientas personalizadas* permiten asociar una herramienta a un elemento de un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Ciertas herramientas personalizadas, que a veces se denominan *generadores de un solo archivo*, se usan con frecuencia para implementar traductores que generan código a partir de datos y viceversa. Por ejemplo, los generadores de un solo archivo crean [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] código fuente de los archivos. Settings y. resx. El código fuente generado proporciona acceso fuertemente tipado a los datos de los archivos. Settings y. resx. Los [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipos de proyecto y admiten herramientas personalizadas; los [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tipos de proyecto no. Sus propios tipos de proyecto también pueden admitir herramientas personalizadas.  
  
 Las herramientas personalizadas son componentes registrados que implementan la `IVsSingleFileGenerator` interfaz.  
  
 Las herramientas personalizadas están asociadas a un `ProjectItem` objeto de interfaz y son similares a los diseñadores y editores. Una herramienta personalizada toma el archivo representado por `ProjectItem` como entrada y escribe un archivo nuevo cuyo nombre de archivo lo proporciona el `DefaultExtension` método.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)  
 Describe cómo utilizar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz para implementar una herramienta personalizada.  
  
 [Determinar el espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Describe cómo determinar el espacio de nombres correcto en función del lenguaje utilizado.  
  
 [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)  
 Proporciona descripciones de todas las entradas del registro de una herramienta personalizada.  
  
 [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explica cómo los sistemas de proyecto proporcionan compatibilidad para que los diseñadores visuales tengan acceso a clases y tipos generados a través de archivos ejecutables portables (PE).  
  
 [Conservación de la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Muestra cómo conservar una propiedad de elemento de proyecto, como el autor de un archivo de código fuente, en el archivo de proyecto.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Proporciona detalles sobre el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , que transforma un único archivo de entrada en un único archivo de salida que se puede compilar o agregar a un proyecto de.  
  
 <xref:EnvDTE.ProjectItem>  
 Explica la `ProjectItem` interfaz, que representa un elemento de un proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Proporciona detalles sobre el `DefaultExtension` método, que recupera la extensión de nombre de archivo que se proporciona al nombre del archivo de salida.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ampliación de proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
