---
title: Admite las ediciones de Visual Studio de visualización y modelado de SDK
titleSuffix: ''
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
ms.openlocfilehash: 65014d8c697adbf5fb8e13d28708090360bb9c17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049961"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Versiones de Visual Studio compatibles con el SDK de modelado y virtualización

Los siguientes son las listas de las ediciones de Visual Studio que son compatibles con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] en los entornos de creación e implementación. Para obtener más información acerca de estas ediciones, vea Microsoft Visual Studio [Centro para desarrolladores de](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Edición para creación

Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|Programa para la mejora|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
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
> Para hacer que un DSL pueda ejecutarse en un producto Shell, debe establecer el **admite VS Edition** campo en el manifiesto de la extensión. Para obtener más información, consulte [implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)