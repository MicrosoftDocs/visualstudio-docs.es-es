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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441243"
---
# <a name="upgrading-projects"></a>Actualización de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los cambios en el modelo de proyecto desde una versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] al siguiente puede requerir que los proyectos y soluciones se puede actualizar para que pueda ejecutar en la versión más reciente. El [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] proporciona interfaces que pueden usarse para implementar la compatibilidad con la actualización en sus propios proyectos.  
  
## <a name="upgrade-strategies"></a>Estrategias de actualización  
 Para admitir una actualización, la implementación de sistema de proyecto debe definir e implementar una estrategia de actualización. Para determinar la estrategia, puede elegir admitir la copia de seguridad paralelo (SxS), copia de seguridad o ambos.  
  
- Copia de seguridad de SxS significa que un proyecto de sólo copia los archivos que se deben actualizar en su lugar, agrega un sufijo de nombre de archivo adecuado, por ejemplo, ".old".  
  
- Copia de seguridad significa que un proyecto copia todos los elementos de proyecto en una ubicación de copia de seguridad proporcionada por el usuario. A continuación, se actualizan los archivos correspondientes en la ubicación del proyecto original.  
  
## <a name="how-upgrade-works"></a>Cómo funcionan las actualizaciones  
 Cuando una solución creada en una versión anterior de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se abre en una versión más reciente, las comprobaciones IDE que la solución de archivo para determinar si debe actualizarse. Si la actualización es necesaria, el **Asistente para actualización** se inicia automáticamente para guiar al usuario a través del proceso de actualización.  
  
 Cuando una solución necesita actualizarse, consulta cada generador de proyectos para su estrategia de actualización. La estrategia determina si el generador de proyectos admite la copia de seguridad de copia o SxS. La información se envía a la **Asistente para actualización**, que recopila la información necesaria para la copia de seguridad y presenta las opciones aplicables al usuario.  
  
### <a name="multi-project-solutions"></a>Soluciones de varios proyectos  
 Si una solución contiene varios proyectos y las estrategias de actualización son diferentes, como cuando un proyecto de C++ que solo es compatible con copia de seguridad de SxS y un proyecto Web que solo admiten la copia de seguridad, los generadores de proyecto deben negociar la estrategia de actualización.  
  
 Cada generador de proyectos para consultas de la solución <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. A continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver si es necesario actualizar archivos del proyecto global y para determinar las estrategias de actualización compatibles. El **Asistente para actualización** , a continuación, se invoca.  
  
 Después de que el usuario completa el asistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se llama en cada generador de proyectos para realizar la actualización real. Para facilitar la copia de seguridad, proporcionan métodos IVsProjectUpgradeViaFactory el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servicio para registrar los detalles del proceso de actualización. Este servicio no se puede almacenar en caché.  
  
 Después de actualizar todos los archivos pertinentes de globales, puede elegir cada generador de proyectos crear instancias de un proyecto. La implementación del proyecto debe admitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , a continuación, se llama el método para actualizar todos los elementos de proyecto correspondiente.  
  
> [!NOTE]
> El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método no proporciona el servicio SVsUpgradeLogger. Este servicio se puede obtener mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Procedimientos recomendados  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servicio para comprobar si puede editar un archivo antes de editarlo y guardarlo antes de guardarlo. Esto le ayudará a la copia de seguridad y actualización implementaciones controlan los archivos de proyecto bajo control de código fuente, los archivos con permisos insuficientes y así sucesivamente.  
  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas las fases de copia de seguridad de servicio y actualizar para proporcionar información sobre el éxito o error del proceso de actualización.  
  
 Para obtener más información acerca de la copia de seguridad y actualización de proyectos, vea los comentarios de IVsProjectUpgrade en vsshell2.idl.  
  
## <a name="see-also"></a>Vea también  
 [Proyectos](../../extensibility/internals/projects.md)   
 [Actualizar proyectos personalizados](../../misc/upgrading-custom-projects.md)   
 [Actualizar elementos de proyecto](../../misc/upgrading-project-items.md)
