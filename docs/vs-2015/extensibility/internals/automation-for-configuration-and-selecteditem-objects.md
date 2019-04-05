---
title: Automatización de la configuración y objetos SelectedItem | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996167"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para configuración y objetos SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Se pueden automatizar la compilación y los procesos del elemento seleccionado en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="automation-for-builds"></a>Automatización de compilaciones  
 Compilación o la configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).  
  
 Si crea un VSPackage y desea controlar las opciones de configuración, debe usar el modelo de automatización.  
  
## <a name="automation-for-selecteditem"></a>Automatización de SelectedItem  
 No es necesario proporcionar una implementación para el `SelectedItem` porque Visual Studio contiene una implementación estándar de objeto. Sin embargo, puede implementar la `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contiene el `SelectedItem` interfaz y devolver una respuesta a una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método con VSITEMID establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribución al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
