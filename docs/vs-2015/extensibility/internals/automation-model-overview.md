---
title: Información general sobre el modelo de automatización | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699508"
---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo de automatización se compone de un conjunto de objetos en el que se puede escribir una extensión o un complemento de Visual Studio. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar las tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o agregar a la funcionalidad de componentes estándar como el editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización  
 El modelo de automatización se compone de grupos de objetos relacionados que controlan las principales caras del entorno común. El siguiente es un diagrama que muestra el amplio conjunto de objetos que componen el modelo de automatización.  
  
 ![Modelo de objetos de automatización de Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automatización de Visual Studio  
  
 Para obtener más información, vea [extender el entorno de Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 El entorno proporciona un modelo para las distintas áreas funcionales. Por ejemplo, hay un modelo de código para los distintos elementos que puede encontrar en el código. Hay un modelo de documento para varios elementos de documento. Un área, el área del proyecto, es de especial interés para los proveedores de VSPackage. Probablemente querrá que los nuevos tipos de proyecto contribuyan al modelo de automatización de la misma manera que [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuyen al modelo de automatización. Este proceso se describe en [proporcionar automatización para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Lugares en los que puede considerar la posibilidad de extender el modelo de automatización del entorno:  
  
- Proyecto  
  
- Documento  
  
- Código  
  
- Compilar  
  
  Para obtener más información sobre automatización, vea [automatización y extensibilidad para Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Este documento y los documentos a los que proporciona vínculos le ayudarán a tomar decisiones sobre cómo debe proporcionar automatización para el VSPackage.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: Crear un complemento](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
