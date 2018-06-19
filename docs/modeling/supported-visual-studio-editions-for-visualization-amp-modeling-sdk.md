---
title: Admite las ediciones de Visual Studio para visualización &amp; modelado del SDK
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 004a6b75bb66ebf3c1797abac9c1cc6f7faa6eb9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948199"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Admite las ediciones de Visual Studio para visualización &amp; modelado del SDK
Los siguientes son listas de las ediciones de Visual Studio que son compatibles con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] en los entornos de creación y la implementación. Para obtener más información acerca de estas ediciones, vea Microsoft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [Centro para desarrolladores de](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Edición para creación
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Ediciones para implementación
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] admite las siguientes configuraciones para implementar los lenguajes específicos del dominio que compile:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Paquete redistribuible de Visual Studio Shell (modo integrado) paquete redistribuible

-   Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
>  Para realizar un DSL puede ejecutarse en un producto de Shell, debe establecer el **admite la edición de VS** campo en el manifiesto de la extensión. Para obtener más información, consulte [implementar soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
