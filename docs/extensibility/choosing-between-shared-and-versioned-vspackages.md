---
title: Elección entre VSPackages compartidos y con control de versiones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 705fe42cf158992bb041ac9b75348f7b25945631
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892276"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Elección entre VSPackages compartidos y con control de versiones
Las diferentes versiones de Visual Studio pueden coexistir en el mismo equipo. Los paquetes VSPackage pueden admitir cualquier combinación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versiones.

 Puede permitir que las instalaciones en paralelo de VSPackages a través de cualquiera de las dos estrategias, la estrategia compartida o la estrategia con control de versiones. Ambos dar cabida a la presencia de varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociadas a las versiones de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

 En la estrategia compartida, se registra un VSPackage para su uso en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En la estrategia con control de versiones, se instalan varios archivos DLL de VSPackage, uno para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico.

## <a name="shared-vspackages"></a>VSPackages compartidos
 Uso de un VSPackage compartido es adecuado cuando se usa el mismo paquete de VS en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para implementar un paquete VSPackage compartido, debe realizar los pasos siguientes:

- Hacer que el VSPackage que sean compatibles con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dos maneras de hacerlo así que están disponibles:

  - Limitar el VSPackage para usar solo las características de la versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico.

  - Programar el paquete de VS para adaptarse a la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se está ejecutando. A continuación, si se produce un error en las consultas para los servicios más recientes, el paquete de VS puede ofrecer otros servicios que se admiten en versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Registre el VSPackage adecuadamente. Para obtener más información, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md) y [registro de VSPackage administrado](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Registrar las extensiones de archivo correctamente. Para obtener más información, consulte [registrar las extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Crear un instalador que implementa el VSPackage para las versiones adecuadas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [administración componente](../extensibility/internals/component-management.md).

- Solucionar el problema de conflictos de registro. Para obtener más información, consulte [registro de VSPackage](../extensibility/internals/vspackage-registration.md).

- Que respeten los archivos compartidos y con control de versiones permitir la instalación segura y eliminación de varias versiones de recuento de referencias. Para obtener más información, consulte [administración componente](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VSPackages con control de versiones
 En la estrategia de VSPackage con control de versiones, crea un VSPackage para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que proporciona soporte técnico. Esto es adecuado si tiene previsto aprovechar los servicios proporcionados por las versiones posteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], porque cada VSPackage puede evolucionar sin que afecte a los demás. No obstante, la estrategia de creación de varios archivos binarios, de un único código base o de varias bases de código independiente, con control de versiones puede implicar más el desarrollo inicial de la estrategia compartido. Además, podría requerirse trabajo adicional de la configuración porque debe crear tanto una instalación independiente para cada versión o un programa de instalación único que detecta las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que estén instalados y que admita el VSPackage.

## <a name="binary-compatibility"></a>Compatibilidad binaria
 Por lo general, la compatibilidad binaria habilita a VSPackages de código nativo desarrollados con versiones anteriores de Visual Studio para ejecutar en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones importantes:

- Si el paquete de VS se basa en una versión determinada de common language runtime, a continuación, debe determinar en qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se está ejecutando.

- Un VSPackage podría tener una dependencia en una característica específica de otro VSPackage u otro producto. Por lo tanto, el VSPackage puede ejecutar solo donde se satisfizo la dependencia.

- Un VSPackage podría verse afectado por una revisión de seguridad en un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En esos casos, un VSPackage se desarrolló con una versión anterior de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] podría no ejecutarse en las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] después de que se aplicó la revisión de seguridad. Sin embargo, puede volver a generar el paquete con la versión más reciente y hacer que se ejecute también en versiones anteriores.

  VSPackages administrado debe compilarse con una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que coinciden con la versión de destino [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  Además de planeación para la compatibilidad binaria de los archivos binarios de VSPackage, también debe considerar soluciones y formatos de archivo del proyecto. Si el paquete de VS crea un nuevo tipo de proyecto, debe decidir si se puede ejecutar en una sola versión o en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [actualizar proyectos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Vea también
- [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Administración de componentes](../extensibility/internals/component-management.md)