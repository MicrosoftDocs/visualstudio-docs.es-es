---
title: "Automatizaci&#243;n para la configuraci&#243;n y objetos SelectedItem | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automatización [Visual Studio SDK] objeto SelectedItem"
  - "compilaciones de automatización [Visual Studio SDK]"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Automatizaci&#243;n para la configuraci&#243;n y objetos SelectedItem
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede automatizar la generación y procesos seleccionada del elemento en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Automatización de las compilaciones  
 Compilación o configuración tiene un modelo de automatización se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>.  Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).  
  
 Si crea un VSPackage y desea controlar los valores de configuración, debe utilizar el modelo de automatización.  
  
## automatización para SelectedItem  
 No tiene que proporcionar una implementación del objeto de `SelectedItem` porque Visual Studio contiene una implementación estándar.  Sin embargo, puede implementar el objeto de `SelectedItem` si prefiere.  Debe implementar un objeto que contiene la interfaz de `SelectedItem` y devuelve una respuesta a una llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> con VSITEMID establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Que contribuyen al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)