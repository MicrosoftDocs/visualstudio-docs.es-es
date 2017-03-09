---
title: "C&#243;mo: Obtener un servicio del objeto DTE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servicios, de objeto DTE"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# C&#243;mo: Obtener un servicio del objeto DTE
Un servicio se puede obtener de cualquier programa que tenga acceso al objeto de <xref:EnvDTE.DTEClass> de automatización de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Por ejemplo, puede tener acceso al servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de un asistente a través del objeto DTE.  Puede utilizar este servicio para escribir en el registro de actividad.  Para obtener más información, vea [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
 El objeto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que puede utilizar para consultar un servicio de código administrado mediante <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
### Para obtener un servicio del objeto DTE  
  
1.  El código siguiente crea <xref:Microsoft.VisualStudio.Shell.ServiceProvider> del objeto DTE y llama a <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> con el tipo de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> .  El servicio se convierte a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>, que se utiliza para escribir una entrada en el registro de actividad.  Para obtener más abou de información cómo escribir en el registro de actividad, vea [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## Vea también  
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)