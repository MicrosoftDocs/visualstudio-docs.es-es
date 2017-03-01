---
title: Referencia de API para modelar el SDK de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 8
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 88a35ad56924c4e1df22927e64a48c42edb21d4d
ms.lasthandoff: 02/22/2017

---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referencia de API para modelar el SDK de Visual Studio
El SDK de modelado y visualización de Visual Studio proporciona la plataforma en la que se generan las herramientas de lenguajes específicos de dominio (DSL).  
  
 Esta sección contiene material de referencia para los espacios de nombres que tienen nombres que comienzan con "Microsoft.VisualStudio.Modeling".  
  
|Espacio de nombres|Contenido|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Clases como ModelElement, que es la clase base de todas las clases de dominio que se definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Las clases que forman parte de una definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Las herramientas de medición modelo Visor de almacén y el rendimiento.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Clases como ShapeElement, que es la clase base de todas las formas que se definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de selección y movimiento.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|La API del Diseñador de definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Clases internas del Diseñador de definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permiten extender el diseñador DSL con comandos, gestos y validación.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensión para ModelElement que implementan la extensibilidad de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidad|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que los elementos de un modelo de sólo lectura.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|La API de Modelbus, que le ayuda a integrar modelos diferentes.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|El cuadro de diálogo que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|El servicio de selector.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Entorno de adaptador de ModelBus para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|El cuadro de diálogo de selector que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|La interfaz entre lenguajes DSL y [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir los comandos del menú contextual (contexto).|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite definir restricciones de validación.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API para la extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md)   
 [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)

