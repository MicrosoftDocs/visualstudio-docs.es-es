---
title: Admite las ediciones de Visual Studio de visualización y modelado SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aa8ec46036bbb9a133f2036f1c54cad87d064618
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105492"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Admite las ediciones de Visual Studio para la visualización &amp; SDK de modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los siguientes son las listas de las ediciones de Visual Studio que son compatibles con [!INCLUDE[dsl](../includes/dsl-md.md)] en los entornos de creación e implementación. Para obtener más información acerca de estas ediciones, vea Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Centro para desarrolladores de](http://go.microsoft.com/fwlink/?LinkId=75628).

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

- Paquete redistribuible de Visual Studio Shell (modo integrado) paquete redistribuible

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
>  Para hacer que un DSL pueda ejecutarse en un producto Shell, debe establecer el **admite VS Edition** campo en el manifiesto de la extensión. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también
 [Glosario de las Herramientas del lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
