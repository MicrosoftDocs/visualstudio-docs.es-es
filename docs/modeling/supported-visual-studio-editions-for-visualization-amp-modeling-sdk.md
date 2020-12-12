---
title: Ediciones de Visual Studio compatibles con el SDK de visualización y modelado
description: Obtenga información sobre las ediciones de Visual Studio compatibles con las herramientas de DSL en los entornos de creación e implementación.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 714b3d018e2522c9f6acf3b15ffec82a0b5d49ec
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363723"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Ediciones de Visual Studio compatibles con el SDK de visualización y modelado

A continuación se muestran las listas de las ediciones de Visual Studio compatibles con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] en los entornos de creación e implementación. Para obtener más información sobre estas ediciones, vea el [Centro para desarrolladores](https://visualstudio.microsoft.com/)de Microsoft Visual Studio.

## <a name="authoring-edition"></a>Edición para creación

Para definir un DSL, debe tener instalados los siguientes componentes:

|Producto|Vínculo de descarga|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Ediciones para implementación

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] admite las siguientes configuraciones para implementar los lenguajes específicos de dominio que se compilan:

- Visual Studio Enterprise

- Visual Studio Professional

- Paquete redistribuible de Visual Studio Shell (modo integrado) paquete redistribuible

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
> Para que un DSL pueda ejecutarse en un producto de Shell, debe establecer el campo **compatible de vs Edition** en el manifiesto de la extensión. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))