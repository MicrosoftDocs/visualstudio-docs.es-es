---
title: Elegir entre VSPackages compartidos y con control de versiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce7f58d664c6a186146272af16324be2fee90983
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104625"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Elegir entre VSPackages compartidos y con control de versiones
Diferentes versiones de Visual Studio pueden coexistir en el mismo equipo. Paquetes VSPackage puede admitir cualquier combinación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versiones.  
  
 Puede habilitar las instalaciones en paralelo de VSPackages a través de cualquiera de las dos estrategias, la estrategia compartida o la estrategia con control de versiones. Ambos dar cabida a la presencia de varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociados de versiones de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 En la estrategia compartida, un VSPackage está registrado para su uso en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En la estrategia con control de versiones, se instalan varios archivos DLL de VSPackage, uno para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico.  
  
## <a name="shared-vspackages"></a>VSPackages compartidos  
 Uso de un VSPackage compartido es adecuado cuando se usa el mismo paquete de VS en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para implementar un paquete VSPackage compartido, debe seguir los pasos siguientes:  
  
-   Que sea compatible con varias versiones de VS [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dos maneras de hacerlo por lo que están disponibles:  
  
    -   Limitar el VSPackage para usar solo las características de la versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico.  
  
    -   Programar el paquete de VS para adaptarse a la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se está ejecutando. A continuación, si se produce un error en las consultas para los servicios más recientes, el paquete de VS puede ofrecer otros servicios que se admiten en versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registre el VSPackage adecuadamente. Para obtener más información, consulte [VSPackage registro](../extensibility/internals/vspackage-registration.md) y [administra el registro de VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrar las extensiones de archivo correctamente. Para obtener más información, consulte [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Crear un instalador que se puede implementar el paquete de VS para las versiones adecuadas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [componente administración](../extensibility/internals/component-management.md).  
  
-   Solucionar el problema de conflictos de registro. Para obtener más información, consulte [VSPackage registro](../extensibility/internals/vspackage-registration.md).  
  
-   Asegúrese de que los archivos compartidos y con control de versiones respetan recuento de referencias para permitir la instalación de prueba de errores y eliminación de varias versiones. Para obtener más información, consulte [componente administración](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages con control de versiones  
 En la estrategia de VSPackage con control de versiones, crear un VSPackage para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico. Esto resulta adecuado si tiene previsto aprovechar las ventajas de los servicios proporcionados por las versiones posteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], porque cada VSPackage puede evolucionar sin que afecte al resto. No obstante, la estrategia de creación de varios archivos binarios, de una sola base de código o de varias bases de código independiente, con control de versiones puede implicar más desarrollo inicial de la estrategia compartida. Además, el programa de instalación adicionales puede requerirse trabajo porque debe crear o una instalación independiente para cada versión o una única instalación que detecta las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que están instalados y que admita el VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilidad binaria  
 Por lo general, la compatibilidad binaria permite VSPackages de código nativo que se desarrolló con versiones anteriores de Visual Studio para ejecutar en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones principales:  
  
-   Si el paquete de VS se basa en una versión determinada de common language runtime, debe determinar en qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se está ejecutando.  
  
-   Un VSPackage puede tener una dependencia en una característica específica de otro VSPackage u otro producto. Por lo tanto, el VSPackage puede ejecutar solo donde se satisfizo la dependencia.  
  
-   Un VSPackage podría verse afectado por una corrección de seguridad en un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En esos casos, un VSPackage desarrollado con una versión anterior de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] podría no ejecutarse en las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] después de que se aplicó la revisión de seguridad. Sin embargo, puede volver a generar el paquete con la versión más reciente y hacer que se ejecute también en versiones anteriores.  
  
 VSPackages administrado debe compilarse con una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que coincidan con la versión de destino [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Además de planeación para la compatibilidad binaria de los archivos binarios de VSPackage, también debe considerar soluciones y formatos de archivo del proyecto. Si el paquete de VS crea un nuevo tipo de proyecto, debe decidir si se puede ejecutar en una sola versión o en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [actualizar proyectos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Vea también  
 [Instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Administración de componentes](../extensibility/internals/component-management.md)