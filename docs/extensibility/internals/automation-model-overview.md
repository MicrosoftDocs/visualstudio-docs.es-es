---
title: Información general del modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f13ffca7dc39be65f8a36a9b242bf7f0f82dc4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861962"
---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
El modelo de automatización se compone de un conjunto de objetos en la que puede escribir un complemento de Visual Studio o la extensión. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de los componentes estándar, como el editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización
 El modelo de automatización consta de grupos de objetos que controlan las facetas principales del entorno común relacionados. El diagrama siguiente muestra el amplio conjunto de objetos de Visual Studio que constituyen el modelo de automatización.

 ![Gráfico de objeto de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obtener más información, consulte [ampliar el entorno de Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 El entorno proporciona un modelo para distintas áreas funcionales. Por ejemplo, hay un modelo de código para distintos elementos que puede encontrar en el código. Hay un modelo de documento para diversos elementos de documento. Un área, el área del proyecto, es de especial interés para los proveedores de VSPackage. Probablemente deseará para contribuir en el modelo de automatización de la misma manera que los nuevos tipos de proyecto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuyen al modelo de automatización. Que el proceso se describe en [proporcionar automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lugares donde puede ampliar el modelo de automatización del entorno:

- Proyecto

- Documento

- Código

- Compilar

Para obtener más información sobre la automatización, vea [automatización y extensibilidad de Visual Studio](../extensibility-in-visual-studio.md). En este documento y los documentos se proporcionan vínculos para ayudarle a tomar decisiones con respecto a cómo debe proporcionar automatización para el VSPackage.

## <a name="see-also"></a>Vea también
- [Cómo: Crear un complemento](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)