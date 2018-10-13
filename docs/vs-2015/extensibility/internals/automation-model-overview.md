---
title: Información general del modelo de automatización | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c31d3b9f18ede2137b5cffe2dd3600de727b9de1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235695"
---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo de automatización se compone de un conjunto de objetos en la que puede escribir un complemento de Visual Studio o la extensión. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de los componentes estándar, como el editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización  
 El modelo de automatización consta de grupos de objetos que controlan las facetas principales del entorno común relacionados. El siguiente es un diagrama que muestra el amplio conjunto de objetos que componen el modelo de automatización.  
  
 ![Gráfico de objeto de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automatización de Visual Studio  
  
 Para obtener más información, consulte [extender el entorno de Visual Studio](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 El entorno proporciona un modelo para distintas áreas funcionales. Por ejemplo, hay un modelo de código para distintos elementos que puede encontrar en el código. Hay un modelo de documento para diversos elementos de documento. Un área, el área del proyecto, es de especial interés para los proveedores de VSPackage. Probablemente deseará para contribuir en el modelo de automatización de la misma manera que los nuevos tipos de proyecto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuyen al modelo de automatización. Que el proceso se describe en [proporcionar automatización de VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Lugares donde puede ampliar el modelo de automatización del entorno:  
  
-   Proyecto  
  
-   Documento  
  
-   Código  
  
-   Compilar  
  
 Para obtener más información sobre la automatización, vea [automatización y extensibilidad de Visual Studio](http://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). En este documento y los documentos se proporcionan vínculos para ayudarle a tomar decisiones con respecto a cómo debe proporcionar automatización para el VSPackage.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un complemento](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

