---
title: Referencia de API para el SDK de modelado
description: Obtenga información sobre cómo Visual Studio SDK de visualización y modelado proporciona la plataforma en la que se han creado las herramientas de lenguajes específicos de dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9603ace5751443c04d0a7503a43e08c044269817
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385466"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referencia de API para modelar el SDK de Visual Studio

El SDK Visual Studio visualización y modelado de aplicaciones proporciona la plataforma en la que se han creado las herramientas de lenguajes específicos de dominio (DSL).

Esta sección contiene material de referencia para los espacios de nombres que tienen nombres que comienzan por "Microsoft.VisualStudio.Modeling".

|Espacio de nombres|Contenido|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Clases como ModelElement, que es la clase base de todas las clases de dominio que se definen en un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Clases que forman parte de una definición de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|El visor de almacén del modelo y las herramientas de medición de rendimiento.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Clases como ShapeElement, que es la clase base de todas las formas que se definen en un DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de gesto y selección.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API del diseñador de definiciones de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Clases internas del diseñador de definiciones de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permiten extender el diseñador DSL con comandos, gestos y validación.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensión para ModelElement que implementan la extensibilidad de DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidad|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite crear partes de un modelo de solo lectura.|
|[Microsoft.VisualStudio.Modeling.Integration](/previous-versions/ee904412(v=vs.140))|La API modelbus, que le ayuda a integrar diferentes modelos.|
|[Microsoft.VisualStudio.Modeling.Integration.Picker](/previous-versions/ee904394(v=vs.140))|Cuadro de diálogo que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|El servicio Selector.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell](/previous-versions/ee869435(v=vs.140))|Marco del adaptador de Modelbus para Visual Studio.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell.Picker](/previous-versions/ee886769(v=vs.140))|Cuadro de diálogo Selector que permite a los usuarios navegar a los modelos y elementos para crear referencias de Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfaz entre los archivos DSL y Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir comandos de menú contextual (acceso directo).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite definir restricciones de validación.|

## <a name="see-also"></a>Vea también

- [Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)
