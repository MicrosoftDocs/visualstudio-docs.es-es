---
title: Referencia de API para plantillas de texto T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: bef33f10446df92ae8424b23aa17695748222808
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="api-reference-for-t4-text-templates"></a>Referencia de API para plantillas de texto T4

La API de plantillas de texto permite invocar y personalizar la transformación de [plantillas de texto](../modeling/code-generation-and-t4-text-templates.md).

## <a name="namespaces"></a>Espacios de nombres

|Espacio de nombres|Propósito|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.TextTemplating>|Contiene clases para la funcionalidad de transformación de plantillas de texto. El motor de transformación de plantillas de texto está integrado en Visual Studio y transforma archivos de plantilla de texto en archivos de salida de texto generados.|
|<xref:Microsoft.VisualStudio.TextTemplating.Modeling>|Proporciona utilidades de transformación de texto relacionadas con modelos UML y lenguajes específicos del dominio, tales como el acceso a ModelBus de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Proporciona el acceso al servicio de plantillas de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|