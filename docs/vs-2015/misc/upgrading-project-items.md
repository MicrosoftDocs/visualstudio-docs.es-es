---
title: Actualizar elementos de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698684"
---
# <a name="upgrading-project-items"></a>Actualización de elementos de proyecto
Si agrega o administra elementos dentro de los sistemas de proyecto que no implementa, es posible que deba participar en el proceso de actualización del proyecto. Crystal Reports es un ejemplo de un elemento que se puede Agregar al sistema del proyecto.  
  
 Normalmente, los implementadores de elementos de proyecto quieren aprovechar un proyecto actualizado y con una instancia completa, ya que necesitan saber cuáles son las referencias del proyecto y qué otras propiedades del proyecto hay para tomar una decisión de actualización.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obtener la notificación de actualización del proyecto  
  
1. Establezca la <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> marca (definida en vsshell80. idl) en la implementación del elemento de proyecto. Esto hace que el VSPackage del elemento de proyecto se cargue automáticamente cuando el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell determina que un sistema de proyectos está en proceso de actualización.  
  
2. Aconseje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> a la interfaz a través del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa después de que la implementación del sistema del proyecto haya completado sus operaciones de actualización y se haya creado el nuevo proyecto actualizado. Dependiendo del escenario, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa después de los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> métodos, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> .  
  
### <a name="to-upgrade-the-project-item-files"></a>Para actualizar los archivos de elemento de proyecto  
  
1. Debe administrar cuidadosamente el proceso de copia de seguridad de archivos en la implementación del elemento de proyecto. Esto se aplica en concreto para una copia de seguridad en paralelo, donde el `fUpgradeFlag` parámetro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método se establece en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , donde los archivos de los que se ha realizado una copia de seguridad se colocan en los archivos de lado que se designan como ". old". Los archivos de los que se ha realizado una copia de seguridad anteriores a la hora del sistema cuando se actualizó el proyecto se pueden designar como obsoletos. Además, es posible que se sobrescriban a menos que realice pasos específicos para evitarlo.  
  
2. En el momento en que el elemento de proyecto recibe una notificación de la actualización del proyecto, se sigue mostrando el **Asistente para conversión de Visual Studio** . Por lo tanto, debe utilizar los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaz para proporcionar mensajes de actualización a la interfaz de usuario del asistente.  
  
## <a name="see-also"></a>Consulte también  
 [Asistente para conversión de Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Actualizar proyectos personalizados](../misc/upgrading-custom-projects.md)