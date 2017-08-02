---
title: "Información general del modelo de automatización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>Información general del modelo de automatización
El modelo de automatización consta de un conjunto de objetos en la que puede escribir un complemento de Visual Studio o la extensión. Un complemento es una aplicación que puede manipular el entorno de Visual Studio y automatizar tareas comunes. Una extensión de Visual Studio puede crear componentes personalizados de Visual Studio o ampliar la funcionalidad de los componentes estándar, como el editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos del modelo de automatización  
 El modelo de automatización consta de grupos de objetos que controlan aspectos principales del entorno común relacionados. El siguiente es un diagrama que muestra el amplio conjunto de objetos que constituyen el modelo de automatización.  
  
 ![Gráfico de objetos de automatización de Visual Studio](~/docs/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automatización de Visual Studio  
  
 Para obtener más información, consulte [ampliar el entorno de Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 El entorno proporciona un modelo para distintas áreas funcionales. Por ejemplo, hay un modelo de código para distintos elementos que puede encontrar en el código. Hay un modelo de documento para distintos elementos de documento. Un área, el área de proyecto, es de particular interés para los proveedores de VSPackage. Probablemente deseará contribuir al modelo de automatización de la misma manera que los nuevos tipos de proyecto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuyen al modelo de automatización. Que el proceso se describe en [proporcionar automatización para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Lugares donde puede ampliar el modelo de automatización del entorno:  
  
-   Proyecto  
  
-   Documento  
  
-   Código  
  
-   Compilar  
  
 Para obtener más información sobre la automatización, consulte [automatización y extensibilidad de Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Este documento y los documentos se proporcionan vínculos para ayudarle a tomar decisiones sobre cómo debería proporcionar automatización para el VSPackage.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un complemento](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
