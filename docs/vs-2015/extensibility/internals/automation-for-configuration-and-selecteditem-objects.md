---
title: Automatización para objetos Configuration y SelectedItem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157262"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para configuración y objetos SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede automatizar los procesos de compilación y elementos seleccionados en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automatización para compilaciones  
 La compilación o configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).  
  
 Si crea un VSPackage y desea controlar las opciones de configuración, debe utilizar el modelo de automatización.  
  
## <a name="automation-for-selecteditem"></a>Automatización para SelectedItem  
 No es necesario proporcionar una implementación para el `SelectedItem` objeto porque Visual Studio contiene una implementación estándar. Sin embargo, puede implementar el `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contenga la `SelectedItem` interfaz y devolver una respuesta a una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método con VSITEMID establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuir al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
