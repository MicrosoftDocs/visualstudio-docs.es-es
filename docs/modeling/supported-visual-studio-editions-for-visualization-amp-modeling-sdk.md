---
title: Admite las ediciones de Visual Studio de visualización y modelado de SDK
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
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591910"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Ediciones de Visual Studio compatibles con el SDK de visualización y modelado

Los siguientes son las listas de las ediciones de Visual Studio que son compatibles con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] en los entornos de creación e implementación. Para obtener más información acerca de estas ediciones, vea Microsoft Visual Studio [Centro para desarrolladores de](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Edición para creación

Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|Programa para la mejora|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|SDK de visualización y modelado de Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Ediciones para implementación

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] admite las siguientes configuraciones para implementar los lenguajes específicos del dominio que compile:

- Visual Studio Enterprise

- Visual Studio Professional

- Paquete redistribuible de Visual Studio Shell (modo integrado) paquete redistribuible

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
> Para hacer que un DSL pueda ejecutarse en un producto Shell, debe establecer el **admite VS Edition** campo en el manifiesto de la extensión. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
