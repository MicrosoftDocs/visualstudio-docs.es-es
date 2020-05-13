---
title: Descripción general del modelo de automatización (Automation Model Overview) Microsoft Docs
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
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710008"
---
# <a name="automation-model-overview"></a>Visión general del modelo de automatización
El modelo de automatización consta de un conjunto de objetos en el que puede escribir un complemento o extensión de Visual Studio. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de componentes estándar, como el editor de texto.

## <a name="objects-in-the-automation-model"></a>Objetos en el modelo de automatización
 El modelo de automatización consta de grupos relacionados de objetos que controlan las principales facetas del entorno común. En el diagrama siguiente se muestra el amplio conjunto de objetos de Visual Studio que componen el modelo de automatización.

 ![Gráfico de objetos de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Para obtener más información, vea [Extender el entorno](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)de Visual Studio .

 El entorno proporciona un modelo para diferentes áreas funcionales. Por ejemplo, hay un modelo de código para varios elementos que puede encontrar en el código. Hay un modelo de documento para varios elementos de documento. Un área, el área de proyecto, es de particular interés para los proveedores de VSPackage. Es probable que desee que los nuevos tipos de proyecto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuyan al modelo de automatización de la misma manera que el modelo de automatización y contribuye a ellos. Ese proceso se describe en [Proporcionar automatización para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Lugares donde puede considerar la ampliación del modelo de automatización del entorno:

- proyecto

- Documento

- Código

- Compilar

Para obtener más información sobre la automatización, vea [Automatización y extensibilidad para Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Este documento y los documentos a los que proporciona vínculos, le ayudan a tomar decisiones con respecto a cómo debe proporcionar automatización para el VSPackage.

## <a name="see-also"></a>Vea también
- [Cómo: Crear un complemento](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
