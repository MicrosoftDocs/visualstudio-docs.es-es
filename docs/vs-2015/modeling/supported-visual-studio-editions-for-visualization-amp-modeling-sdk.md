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
ms.openlocfilehash: 89d65aab64ba82f152e2fe888ab10b88b73a7c42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672377"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Ediciones de Visual Studio compatibles con el SDK de modelado de &amp; de visualización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación se muestran las listas de las ediciones de Visual Studio compatibles con [!INCLUDE[dsl](../includes/dsl-md.md)] en los entornos de creación e implementación. Para obtener más información sobre estas ediciones, vea el [Centro para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=75628)de Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="authoring-edition"></a>Edición para creación
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

## <a name="deployment-editions"></a>Ediciones para implementación
 [!INCLUDE[dsl](../includes/dsl-md.md)] admite las siguientes configuraciones para implementar los lenguajes específicos del dominio que compile:

- Visual Studio Enterprise

- Visual Studio Professional

- Paquete redistribuible de Visual Studio Shell (modo integrado) Redistributable Package

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
> Para que un DSL pueda ejecutarse en un producto de Shell, debe establecer el campo **compatible de vs Edition** en el manifiesto de la extensión. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
