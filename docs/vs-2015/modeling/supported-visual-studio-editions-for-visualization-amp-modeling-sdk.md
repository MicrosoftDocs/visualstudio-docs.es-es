---
title: Supported Visual Studio Editions for Visualization and Modeling SDK | Microsoft Docs
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
ms.openlocfilehash: b81aaba14acc2c050a770e810c57e99ee43c2ab3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298157"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Supported Visual Studio Editions for Visualization &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The following are lists of the Visual Studio editions that are supported with [!INCLUDE[dsl](../includes/dsl-md.md)] in the authoring and deployment environments. For more information on these editions, see the Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Developer Center](https://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Edición para creación
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

## <a name="deployment-editions"></a>Ediciones para implementación
 [!INCLUDE[dsl](../includes/dsl-md.md)] admite las siguientes configuraciones para implementar los lenguajes específicos del dominio que compile:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrated mode) redistributable package redistributable package

- Paquete redistribuible de Visual Studio Shell (modo aislado) paquete redistribuible

> [!NOTE]
> To make a DSL able to run on a Shell product, you must set the **Supported VS Edition** field in the Extension Manifest. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Vea también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
