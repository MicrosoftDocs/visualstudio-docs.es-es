---
title: Referencia de API para modelar el SDK de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65f8fffbe86bfb80916aa62d3f148795a3c279d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573722"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referencia de API para modelar el SDK de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [referencia de API de SDK de modelado para Visual Studio](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-modeling-sdk-for-visual-studio).  
  
El SDK de modelado y visualización de Visual Studio proporciona la plataforma en la que se generan los lenguajes específicos de dominio (DSL) y las herramientas UML.  
  
> [!NOTE]
>  Para obtener información acerca de la API de modelado UML, vea [referencia de API de extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Para obtener información acerca de la transformación de texto, consulte [personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md).  
  
 Esta sección contiene material de referencia para espacios de nombres que tienen nombres que comienzan con "Microsoft.VisualStudio.Modeling".  
  
|Espacio de nombres|Contenido|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Clases como ModelElement, que es la clase base de todas las clases de dominio que se definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Las clases que forman parte de una definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Las herramientas de medición modelo Visor Store y el rendimiento.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Clases como ShapeElement, que es la clase base de todas las formas que se definen en un DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de gesto y selección.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|La API del Diseñador de definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Clases internas del Diseñador de definición de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permiten ampliar el Diseñador de DSL con gestos, los comandos y la validación.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensión para ModelElement que implementan la extensibilidad de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidad|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Le permite hacer que partes de un modelo de solo lectura.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|La API de Modelbus, que le ayuda a integrar modelos diferentes.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|El cuadro de diálogo que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|El servicio de selector.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Entorno de adaptador de ModelBus para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|El cuadro de diálogo de selector que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|La interfaz entre lenguajes DSL y [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Le permite definir comandos del menú contextual (contexto).|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Le permite definir restricciones de validación.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API de extensibilidad del modelado UML](../modeling/api-reference-for-uml-modeling-extensibility.md)   
 [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)



