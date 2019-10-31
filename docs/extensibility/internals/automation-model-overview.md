---
title: Información general sobre el modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186737"
---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
El modelo de automatización se compone de un conjunto de objetos en el que se puede escribir una extensión o un complemento de Visual Studio. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar las tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de componentes estándar como el editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización
 El modelo de automatización se compone de grupos de objetos relacionados que controlan las principales caras del entorno común. En el diagrama siguiente se muestra el amplio conjunto de objetos de Visual Studio que componen el modelo de automatización.

 ![Gráfico de objetos de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obtener más información, vea [extender el entorno de Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 El entorno proporciona un modelo para las distintas áreas funcionales. Por ejemplo, hay un modelo de código para los distintos elementos que puede encontrar en el código. Hay un modelo de documento para varios elementos de documento. Un área, el área del proyecto, es de especial interés para los proveedores de VSPackage. Probablemente querrá que los nuevos tipos de proyecto contribuyan al modelo de automatización del mismo modo que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuyen al modelo de automatización. Ese proceso se describe en [proporcionar automatización para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lugares en los que puede considerar la posibilidad de extender el modelo de automatización del entorno:

- Proyecto

- Documento

- Código

- Compilar

Para obtener más información sobre automatización, vea [automatización y extensibilidad para Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Este documento y los documentos a los que proporciona vínculos le ayudarán a tomar decisiones sobre cómo debe proporcionar automatización para el VSPackage.

## <a name="see-also"></a>Vea también
- [Cómo: crear un complemento](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)