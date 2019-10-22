---
title: Referencia de API para el SDK de modelado
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3915dc0ee7359c8fb0093f397542afb557d0796a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654330"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referencia de API para modelar el SDK de Visual Studio

El SDK de visualización y modelado de Visual Studio proporciona la plataforma en la que se compilan las herramientas de lenguajes específicos de dominio (DSL).

Esta sección contiene material de referencia para los espacios de nombres que tienen nombres que comienzan por "Microsoft. VisualStudio. Modeling".

|Espacio de nombres|Contenido|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Clases como ModelElement, que es la clase base de todas las clases de dominio que se definen en un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Clases que forman parte de una definición de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|El visor del almacén de modelos y las herramientas de medición de rendimiento.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Clases como ShapeElement, que es la clase base de todas las formas que se definen en un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de gesto y selección.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|La API del diseñador de definiciones de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Clases internas del diseñador de definiciones de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permiten extender el diseñador DSL con comandos, movimientos y validación.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensión para ModelElement que implementan la extensibilidad DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidad|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite hacer que partes de un modelo sean de solo lectura.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|La API de Modelbus, que le ayuda a integrar diferentes modelos.|
|[Microsoft. VisualStudio. Modeling. Integration. Picker](/previous-versions/ee904394(v=vs.140))|El cuadro de diálogo que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|El servicio selector.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Marco de trabajo de adaptadores de Modelbus para Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. Picker](/previous-versions/ee886769(v=vs.140))|El cuadro de diálogo selector que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|La interfaz entre DSL y Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir comandos de menú contextuales (contexto).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite definir restricciones de validación.|

## <a name="see-also"></a>Vea también

- [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)
