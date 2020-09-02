---
title: Extender el cuadro de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: ddf67fba3ae603dbd31d4628c61a6f14cc2441c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686930"
---
# <a name="extending-the-toolbox"></a>Extensión del Cuadro de herramientas
El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Cuadro de herramientas** ofrece una colección de objetos que proporcionan características a los editores y diseñadores a través del mecanismo de arrastrar y colocar del IDE.  
  
 Hay dos formas básicas en que un VSPackage funciona con el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Cuadro de herramientas**:  
  
- Un VSPackage puede agregar nuevos elementos de datos y controles al **Cuadro de herramientas**.  
  
- Un VSPackage puede ser un destino o un consumidor de la característica **Cuadro de herramientas** existente, además de admitir las operaciones de arrastrar y colocar y la configuración del aspecto del **Cuadro de herramientas**.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Crear un control de cuadro de herramientas que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Describe la creación de un control de Cuadro de herramientas mediante la plantilla Windows Forms Toolbox Control.  
  
 [Creación de un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Describe la creación de un control de Cuadro de herramientas mediante la plantilla Control Toolbox de WPF.  
  
 [Managing the Toolbox](../misc/managing-the-toolbox.md)  
 Describe cómo un VSPackage puede administrar el contenido y el aspecto del **Cuadro de herramientas**.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Cómo: Administrar la ventana Cuadro de herramientas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Describe cómo trabajar con el **Cuadro de herramientas** en el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Cómo: Controlar el Cuadro de herramientas](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Describe cómo administrar el **Cuadro de herramientas** mediante el modelo de programación de automatización.  
  
 [Ampliación de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica cómo usar los servicios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear elementos de interfaz de usuario que coincidan con el resto de servicios de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].