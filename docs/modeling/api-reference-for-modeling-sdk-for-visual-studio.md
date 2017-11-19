---
title: Referencia de API de modelado del SDK para Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: "8"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1acbeb95ed7fa59fd64feefe050debc0ce9b6461
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referencia de API para modelar el SDK de Visual Studio
El SDK de modelado y visualización de Visual Studio proporciona la plataforma en la que se generan las herramientas de lenguajes específicos de dominio (DSL).  
  
 Esta sección contiene material de referencia para los espacios de nombres que tienen nombres que comienzan por "Microsoft.VisualStudio.Modeling".  
  
|Espacio de nombres|Contenido|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Clases, como ModelElement, que es la clase base de todas las clases de dominio que definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Clases que forman parte de una definición DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Las herramientas de medición modelo Visor de almacén y el rendimiento.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Clases, como ShapeElement, que es la clase base de todas las formas en que definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de movimiento y la selección.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|La API del Diseñador de definición DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Clases internas del Diseñador de definición DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permiten ampliar el diseñador DSL con comandos, gestos y validación.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensión para ModelElement que implementan DSL extensibilidad.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidad|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Le permite hacer que partes de un modelo de solo lectura.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|La API de Modelbus, que le ayuda a integrar diferentes modelos.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|El cuadro de diálogo que permite a los usuarios navegar a modelos y elementos que se va a crear Modelbus referencias.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|El servicio de selector.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Marco de trabajo ModelBus para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|El cuadro de diálogo de selector que permite a los usuarios navegar a modelos y elementos que se va a crear Modelbus referencias.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|La interfaz entre DSL y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Le permite definir los comandos de menú contextual.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Le permite definir restricciones de validación.|  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)
