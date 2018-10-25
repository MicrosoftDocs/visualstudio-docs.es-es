---
title: Elección entre VSPackages compartidos y con control de versiones | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75bc095ba4e9fc12033787b64dd516459e574b26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859941"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Elección entre VSPackages compartidos y con versiones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las diferentes versiones de Visual Studio pueden coexistir en el mismo equipo. Los paquetes VSPackage pueden admitir cualquier combinación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versiones.  
  
 Puede permitir que las instalaciones en paralelo de VSPackages a través de cualquiera de las dos estrategias, la estrategia compartida o la estrategia con control de versiones. Ambos dar cabida a la presencia de varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y asociadas a las versiones de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 En la estrategia compartida, se registra un VSPackage para su uso en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En la estrategia con control de versiones, se instalan varios archivos DLL de VSPackage, uno para cada versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que proporciona soporte técnico.  
  
## <a name="shared-vspackages"></a>VSPackages compartidos  
 Uso de un VSPackage compartido es adecuado cuando se usa el mismo paquete de VS en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para implementar un paquete VSPackage compartido, debe realizar los pasos siguientes:  
  
-   Hacer que el VSPackage que sean compatibles con varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dos maneras de hacerlo así que están disponibles:  
  
    -   Limitar el VSPackage para usar solo las características de la versión anterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que proporciona soporte técnico.  
  
    -   Programar el paquete de VS para adaptarse a la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en que se está ejecutando. A continuación, si se produce un error en las consultas para los servicios más recientes, el paquete de VS puede ofrecer otros servicios que se admiten en versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Registre el VSPackage adecuadamente. Para obtener más información, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md) y [administra el registro de VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrar las extensiones de archivo correctamente. Para obtener más información, consulte [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Crear un instalador que implementa el VSPackage para las versiones adecuadas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, consulte [Installing VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [componente administración](../extensibility/internals/component-management.md).  
  
-   Solucionar el problema de conflictos de registro. Para obtener más información, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Que respeten los archivos compartidos y con control de versiones permitir la instalación segura y eliminación de varias versiones de recuento de referencias. Para obtener más información, consulte [componente administración](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages con control de versiones  
 En la estrategia de VSPackage con control de versiones, crea un VSPackage para cada versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que proporciona soporte técnico. Esto es adecuado si tiene previsto aprovechar los servicios proporcionados por las versiones posteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], porque cada VSPackage puede evolucionar sin que afecte a los demás. No obstante, la estrategia de creación de varios archivos binarios, de un único código base o de varias bases de código independiente, con control de versiones puede implicar más el desarrollo inicial de la estrategia compartido. Además, podría requerirse trabajo adicional de la configuración porque debe crear tanto una instalación independiente para cada versión o un programa de instalación único que detecta las versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que estén instalados y que admita el VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilidad binaria  
 Por lo general, la compatibilidad binaria habilita a VSPackages de código nativo desarrollados con versiones anteriores de Visual Studio para ejecutar en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones importantes:  
  
- Si el paquete de VS se basa en una versión determinada de common language runtime, a continuación, debe determinar en qué versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se está ejecutando.  
  
- Un VSPackage podría tener una dependencia en una característica específica de otro VSPackage u otro producto. Por lo tanto, el VSPackage puede ejecutar solo donde se satisfizo la dependencia.  
  
- Un VSPackage podría verse afectado por una revisión de seguridad en un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] service pack o una versión posterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En esos casos, un VSPackage se desarrolló con una versión anterior de la [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] podría no ejecutarse en las versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de que se aplicó la revisión de seguridad. Sin embargo, puede volver a generar el paquete con la versión más reciente y hacer que se ejecute también en versiones anteriores.  
  
  VSPackages administrado debe compilarse con una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] que coinciden con la versión de destino [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Además de planeación para la compatibilidad binaria de los archivos binarios de VSPackage, también debe considerar soluciones y formatos de archivo del proyecto. Si el paquete de VS crea un nuevo tipo de proyecto, debe decidir si se puede ejecutar en una sola versión o en varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, consulte [actualizar proyectos personalizados](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Vea también  
 [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Administración de componentes](../extensibility/internals/component-management.md)

