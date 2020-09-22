---
title: Actualizar proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842467"
---
# <a name="upgrading-projects"></a>Actualización de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los cambios en el modelo de proyecto de una versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a la siguiente pueden requerir que se actualicen los proyectos y las soluciones para que puedan ejecutarse en la versión más reciente. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Proporciona interfaces que se pueden utilizar para implementar la compatibilidad de actualización en sus propios proyectos.  
  
## <a name="upgrade-strategies"></a>Estrategias de actualización  
 Para admitir una actualización, la implementación del sistema del proyecto debe definir e implementar una estrategia de actualización. A la hora de determinar la estrategia, puede elegir admitir copias de seguridad en paralelo (SxS), copia de seguridad de copia o ambas.  
  
- La copia de seguridad SxS significa que un proyecto copia solo los archivos que necesitan actualizarse, agregando un sufijo de nombre de archivo adecuado, por ejemplo, ". old".  
  
- Copiar copia de seguridad significa que un proyecto copia todos los elementos de proyecto en una ubicación de copia de seguridad proporcionada por el usuario. A continuación, se actualizan los archivos relevantes en la ubicación del proyecto original.  
  
## <a name="how-upgrade-works"></a>Cómo funciona la actualización  
 Cuando una solución creada en una versión anterior de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se abre en una versión más reciente, el IDE comprueba el archivo de solución para determinar si es necesario actualizarlo. Si es necesaria la actualización, el **Asistente para actualización** se inicia automáticamente para guiar al usuario a través del proceso de actualización.  
  
 Cuando una solución necesita actualizar, consulta cada generador de proyectos para obtener su estrategia de actualización. La estrategia determina si el generador de proyectos admite copias de seguridad de copia o de copia de seguridad SxS. La información se envía al **Asistente para actualización**, que recopila la información necesaria para la copia de seguridad y presenta las opciones aplicables al usuario.  
  
### <a name="multi-project-solutions"></a>Soluciones de varios proyectos  
 Si una solución contiene varios proyectos y las estrategias de actualización difieren, por ejemplo, cuando un proyecto de C++ que solo admite la copia de seguridad de SxS y un proyecto web que solo admite copia de seguridad, los generadores del proyecto deben negociar la estrategia de actualización.  
  
 La solución consulta cada generador de proyectos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . A continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> a para ver si es necesario actualizar los archivos de proyecto globales y determinar las estrategias de actualización admitidas. A continuación, se invoca el **Asistente para actualización** .  
  
 Una vez que el usuario completa el asistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se llama a en cada generador de proyectos para realizar la actualización real. Para facilitar la copia de seguridad, los métodos IVsProjectUpgradeViaFactory proporcionan el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servicio para registrar los detalles del proceso de actualización. Este servicio no se puede almacenar en caché.  
  
 Después de actualizar todos los archivos globales relevantes, cada generador de proyectos puede elegir crear una instancia de un proyecto. La implementación del proyecto debe admitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>A continuación, se llama al método para actualizar todos los elementos de proyecto pertinentes.  
  
> [!NOTE]
> El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método no proporciona el servicio SVsUpgradeLogger. Este servicio se puede obtener llamando a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Prácticas recomendadas  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servicio para comprobar si puede editar un archivo antes de editarlo y guardarlo antes de guardarlo. Esto ayudará a que las implementaciones de copia de seguridad y actualización controlen los archivos de proyecto bajo control de código fuente, archivos con permisos insuficientes, etc.  
  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servicio durante todas las fases de copia de seguridad y actualización para proporcionar información sobre el éxito o error del proceso de actualización.  
  
 Para obtener más información sobre la copia de seguridad y la actualización de proyectos, vea los comentarios de IVsProjectUpgrade en vsshell2. idl.  
  
## <a name="see-also"></a>Consulte también  
 [Proyecto](../../extensibility/internals/projects.md)   
 [Actualizar proyectos personalizados](../../misc/upgrading-custom-projects.md)   
 [Actualización de elementos de proyecto](../../misc/upgrading-project-items.md)
