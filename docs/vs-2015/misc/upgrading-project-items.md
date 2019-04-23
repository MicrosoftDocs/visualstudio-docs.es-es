---
title: Actualizar elementos de proyecto | Documentos de Microsoft
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
ms.openlocfilehash: c07f8f62fb7ae84b5f3ee6140cccecf744c759e5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083925"
---
# <a name="upgrading-project-items"></a>Actualización de elementos de proyecto
Si agrega o administrar los elementos incluidos en los sistemas de proyectos que no implementa, deberá participar en el proceso de actualización del proyecto. Crystal Reports es un ejemplo de un elemento que se puede agregar al sistema del proyecto.  
  
 Normalmente, los implementadores de elemento de proyecto desean aprovechar un proyecto totalmente ya creado o actualizado porque necesitan saber qué proyecto son referencias y qué otras propiedades del proyecto existen tomar una decisión de actualización.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obtener la notificación de actualización de proyecto  
  
1. Establecer el <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> marca (definido en vsshell80.idl del explorador) en la implementación del elemento de proyecto. Esto hace que el elemento de proyecto VSPackage automáticamente cargarse cuando el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell determina que es un sistema de proyectos en el proceso de actualización.  
  
2. Notificar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa después de la implementación de sistema de proyecto haya completado sus operaciones de actualización y se crea el nuevo proyecto actualizado. Según el escenario, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa tras la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.  
  
### <a name="to-upgrade-the-project-item-files"></a>Para actualizar los archivos de elementos de proyecto  
  
1. Debe administrar con cuidado el proceso de copia de seguridad de archivos en la implementación del elemento de proyecto. Esto se aplica en especial para una copia de seguridad en paralelo, donde el `fUpgradeFlag` parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, donde se colocan los archivos que habían sido una copia de seguridad a lo largo de los archivos del que se designan como ".old". Los archivos de copiados de seguridad anteriores a la hora del sistema cuando se actualiza el proyecto pueden designarse como obsoletos. Además, pueden sobrescribir a menos que realice los pasos específicos para evitar esto.  
  
2. En el momento en el elemento de proyecto recibe una notificación de la actualización del proyecto, el **Asistente para conversión de Visual Studio** se sigue mostrando. Por lo tanto, debe usar los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaz para proporcionar los mensajes de actualización a la interfaz de usuario del asistente.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para conversión de Visual Studio](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Actualizar proyectos personalizados](../misc/upgrading-custom-projects.md)