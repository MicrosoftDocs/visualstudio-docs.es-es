---
title: Ampliar el cuadro de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: douge
ms.openlocfilehash: 674b9d1dcebc7ec4a9019c652f0909904fe952c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568063"
---
# <a name="extending-the-toolbox"></a>Extensión del Cuadro de herramientas
El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **cuadro de herramientas** proporciona una colección de objetos que proporcionan funcionalidad a los editores y diseñadores a través del mecanismo de arrastrar y colocar del IDE.  
  
 Hay dos formas básicas en que un VSPackage funciona con el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **cuadro de herramientas**:  
  
-   Un VSPackage puede agregar nuevos elementos de datos y controles al **Cuadro de herramientas**.  
  
-   Un VSPackage puede ser un destino o un consumidor de la característica **Cuadro de herramientas** existente, además de admitir las operaciones de arrastrar y colocar y la configuración del aspecto del **Cuadro de herramientas**.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear un control de cuadro de herramientas que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Describe la creación de un control de Cuadro de herramientas mediante la plantilla Windows Forms Toolbox Control.  
  
 [Creación de un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Describe la creación de un control de Cuadro de herramientas mediante la plantilla Control Toolbox de WPF.  
  
 [Administración del cuadro de herramientas](../misc/managing-the-toolbox.md)  
 Describe cómo un VSPackage puede administrar el contenido y el aspecto del **Cuadro de herramientas**.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Cómo: Administrar la ventana Cuadro de herramientas](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Describe cómo trabajar con el **cuadro de herramientas** en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE).  
  
 [Cómo: controlar el cuadro de herramientas](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Describe cómo administrar el **Cuadro de herramientas** mediante el modelo de programación de automatización.  
  
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] servicios para crear elementos de interfaz de usuario que coinciden con el resto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].