---
title: Información general sobre el modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa06b58ccd8d4cba8e16b17bc725798ae02d7e8f
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414443"
---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
El modelo de automatización se compone de un conjunto de objetos en el que se puede escribir una extensión o un complemento de Visual Studio. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar las tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de componentes estándar como el editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización
 El modelo de automatización se compone de grupos de objetos relacionados que controlan las principales caras del entorno común. En el diagrama siguiente se muestra el amplio conjunto de objetos de Visual Studio que componen el modelo de automatización.

 ![Gráfico de objetos de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obtener más información, vea [extender el entorno de Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 El entorno proporciona un modelo para las distintas áreas funcionales. Por ejemplo, hay un modelo de código para los distintos elementos que puede encontrar en el código. Hay un modelo de documento para varios elementos de documento. Un área, el área del proyecto, es de especial interés para los proveedores de VSPackage. Probablemente querrá que los nuevos tipos de proyecto contribuyan al modelo de automatización de la misma manera que [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuyen al modelo de automatización. Ese proceso se describe en [proporcionar automatización para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lugares en los que puede considerar la posibilidad de extender el modelo de automatización del entorno:

- Project

- Documento

- Código

- Build

Para obtener más información sobre automatización, vea [automatización y extensibilidad para Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Este documento y los documentos a los que proporciona vínculos le ayudarán a tomar decisiones sobre cómo debe proporcionar automatización para el VSPackage.

## <a name="see-also"></a>Consulte también
- [Cómo: crear un complemento](/previous-versions/80493a3w(v=vs.140))