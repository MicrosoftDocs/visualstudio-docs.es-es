---
title: Elegir entre VSPackages compartidos y con control de versiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821976"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Elección entre VSPackages compartidos y con versiones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las distintas versiones de Visual Studio pueden coexistir en el mismo equipo. Los VSPackages pueden admitir cualquier combinación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versiones.  
  
 Puede habilitar instalaciones en paralelo de VSPackages a través de una de estas dos estrategias: la estrategia compartida o la estrategia con versión. Ambos admiten la presencia de varias versiones de y de las [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versiones asociadas de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 En la estrategia compartida, un VSPackage se registra para su uso en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . En la estrategia con versión, se instalan varios archivos dll de VSPackage, uno para cada versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que admita.  
  
## <a name="shared-vspackages"></a>VSPackages compartidos  
 El uso de un VSPackage compartido es adecuado cuando se usa el mismo VSPackage en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para implementar un VSPackage compartido, debe seguir estos pasos:  
  
- Haga que el VSPackage sea compatible con varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Están disponibles dos maneras de hacerlo:  
  
  - Limite el VSPackage al uso de las características de la versión más antigua de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que admita.  

  - Programe el VSPackage para adaptarse a la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en la que se ejecuta. A continuación, si se produce un error en las consultas de los servicios más recientes, el VSPackage puede ofrecer otros servicios que se admiten en versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Registre el VSPackage adecuadamente. Para obtener más información, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md) y registro de [VSPackage administrado](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registrar las extensiones de archivo de forma adecuada. Para obtener más información, consulte [registro de extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Cree un instalador que implemente el VSPackage para las versiones adecuadas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obtener más información, vea [instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [Administración de componentes](../extensibility/internals/component-management.md).  
  
- Solucione el problema de las colisiones de registro. Para obtener más información, consulte el [registro de VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Asegúrese de que los archivos compartidos y con versiones respetan el recuento de referencias para permitir la instalación y eliminación seguras de varias versiones. Para obtener más información, vea [Administración de componentes](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages con versión  
 En la estrategia con control de versiones, cree un VSPackage para cada versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que admita. Hacerlo es adecuado cuando se espera aprovechar los servicios proporcionados por versiones posteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ya que cada VSPackage puede evolucionar sin afectar a los demás. No obstante, la estrategia con versión de la creación de varios archivos binarios, ya sea desde una sola base de código o desde varias bases de código independientes, puede implicar un mayor desarrollo inicial que la estrategia compartida. Además, puede que sea necesario realizar trabajo de instalación adicional porque debe crear una instalación independiente para cada versión o una configuración única que detecte las versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que están instaladas y que admite el VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilidad binaria  
 Por lo general, la compatibilidad binaria permite que los VSPackages de código nativo desarrollados con versiones anteriores de Visual Studio se ejecuten en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones importantes:  
  
- Si el VSPackage se basa en una versión determinada del Common Language Runtime, debe determinar en qué versión de se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] está ejecutando.  
  
- Un VSPackage puede tener una dependencia en una característica específica de otro VSPackage u otro producto. Por consiguiente, el VSPackage solo puede ejecutarse cuando se cumple la dependencia.  
  
- Un VSPackage puede verse afectado por una corrección de seguridad en un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Service Pack o una versión posterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . En estos casos, es posible que un VSPackage desarrollado con una versión anterior de [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] no se ejecute en versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de aplicar la corrección de seguridad. Sin embargo, puede volver a generar el paquete con la versión más reciente y hacer que también se ejecute en versiones anteriores.  
  
  Los VSPackages administrados deben compilarse con una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] que coincidan con la versión de destino de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Además de planear la compatibilidad binaria con los archivos binarios de VSPackage, también debe tener en cuenta los formatos de archivo de proyecto y de solución. Si el VSPackage crea un nuevo tipo de proyecto, debe decidir si puede ejecutarse en una sola versión o en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obtener más información, vea [actualizar proyectos personalizados](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Consulte también  
 [Instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Administración de componentes](../extensibility/internals/component-management.md)
