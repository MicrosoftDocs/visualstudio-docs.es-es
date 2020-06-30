---
title: Ediciones de Visual Studio compatibles con el SDK de visualización y modelado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547659"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Ediciones de Visual Studio compatibles con el &amp; SDK de modelado de visualización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación se muestran las listas de las ediciones de Visual Studio compatibles con [!INCLUDE[dsl](../includes/dsl-md.md)] en los entornos de creación e implementación. Para obtener más información sobre estas ediciones, vea el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Centro para desarrolladores](https://msdn.microsoft.com/vstudio/products/)de Microsoft.

## <a name="authoring-edition"></a>Edición para creación
 Para definir un DSL, debe tener instalados los siguientes componentes:

|Producto|Vínculo de descarga|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|SDK de Visual Studio de visualización y modelado|[Descarga del SDK de modelado](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Ediciones para implementación
 [!INCLUDE[dsl](../includes/dsl-md.md)]admite las siguientes configuraciones para implementar los lenguajes específicos de dominio que se compilan:

- Visual Studio Enterprise

- Visual Studio Professional

- Paquete redistribuible de Visual Studio Shell (modo integrado) paquete redistribuible

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
> Para que un DSL pueda ejecutarse en un producto de Shell, debe establecer el campo **compatible de vs Edition** en el manifiesto de la extensión. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
