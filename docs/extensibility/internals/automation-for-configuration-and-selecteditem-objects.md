---
title: "Automatización para la configuración y objetos SelectedItem | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42a3b8bdd8930c9006ba49fd0f2e2dd2491b38cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para la configuración y objetos SelectedItem
Se pueden automatizar la compilación y procesos del elemento seleccionado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automatización de compilaciones  
 Compilación o la configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).  
  
 Si crea un paquete VSPackage y desea controlar las opciones de configuración, debe usar el modelo de automatización.  
  
## <a name="automation-for-selecteditem"></a>Automatización de SelectedItem  
 No es necesario proporcionar una implementación para el `SelectedItem` porque Visual Studio contiene una implementación estándar de objeto. Sin embargo, puede implementar la `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contiene el `SelectedItem` interfaz y devolver una respuesta a una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método con VSITEMID establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Que contribuyen al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)