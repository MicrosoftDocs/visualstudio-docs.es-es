---
title: "Actualizaci&#243;n de elementos de proyecto | Microsoft Docs"
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
  - "actualizar elementos de proyecto"
  - "proyectos, [SDK de Visual Studio], actualizar elementos"
  - "elementos de proyectos [Visual Studio], actualizar"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Actualizaci&#243;n de elementos de proyecto
Si agrega o administra los elementos dentro de los sistemas de proyectos que no implementa, puede necesitar participar en el proceso de actualización del proyecto.  Crystal Reports es un ejemplo de un elemento que se puede agregar al sistema del proyecto.  
  
 Normalmente, los implementadores de elemento de proyecto desea aprovechar ya totalmente con instancias y proyecto actualizado porque deben conocer cuáles son las referencias de proyecto y cuáles son otras propiedades del proyecto que tomar una decisión de actualización.  
  
### Para obtener la notificación de la actualización de proyectos  
  
1.  Establezca el marcador de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> \(definido en vsshell80.idl\) en la aplicación del elemento de proyecto.  Esto hace que el elemento de proyecto VSPackage a la carga automático cuando el shell de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] determina que un sistema de proyecto está en el proceso de actualización.  
  
2.  Advise la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> mediante el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> .  
  
3.  Se desencadena la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> después de que la aplicación del sistema de proyectos haya completado sus operaciones de actualización y se crea el nuevo proyecto actualizado.  Dependiendo del escenario, la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> se desencadena después de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### Para actualizar los archivos de elementos de proyecto  
  
1.  Debe administrar cuidadosamente el proceso de copia de seguridad de archivo de la aplicación del elemento de proyecto.  Esto solicita en particular en paralelo una copia de seguridad, donde el parámetro de `fUpgradeFlag` del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se establece en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, donde los archivos que se hubieran con copia de seguridad se colocan en los archivos laterales que se designan como “.old”.  Los archivos con copia de seguridad anteriores a la hora del sistema cuando el proyecto se ha actualizado se puede establecer como obsoleto.  Además, puede que se sobrescriban a menos que dé pasos concretos para evitarlo.  
  
2.  Cuando el elemento de proyecto obtiene una notificación de la actualización de proyectos, **Asistente para conversión de Visual Studio** todavía se muestra.  Por consiguiente, debe utilizar los métodos de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para proporcionar mensajes de actualización a la interfaz de usuario del asistente.  
  
## Vea también  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/es-es/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Actualizar proyectos personalizados](../misc/upgrading-custom-projects.md)