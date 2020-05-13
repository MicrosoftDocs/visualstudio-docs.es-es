---
title: Elegir entre VSPackages compartidos y versionados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739878"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Elija entre VSPackages compartidos y versionados
Diferentes versiones de Visual Studio pueden coexistir en el mismo equipo. VSPackages puede admitir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cualquier combinación de versiones.

 Puede habilitar las instalaciones en paralelo de VSPackages a través de cualquiera de las dos estrategias, la estrategia compartida o la estrategia versionada. Ambos admiten la presencia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de varias versiones y versiones asociadas de .NET Framework.

 En la estrategia compartida, un VSPackage se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]registra para su uso en varias versiones de . En la estrategia versionada, se instalan varios archivos DLL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de VSPackage, uno para cada versión que admite.

## <a name="shared-vspackages"></a>VSPackages compartidos
 El uso de un VSPackage compartido es adecuado cuando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]se usa el mismo VSPackage en varias versiones de . Para implementar un VSPackage compartido, debe seguir los pasos siguientes:

- Haga que el VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sea compatible con varias versiones de . Hay dos formas de hacerlo disponibles:

  - Limite el VSPackage a usar solo las [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] características de la versión más antigua de la que admite.

  - Programe el VSPackage para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adaptarlo a la versión en la que se está ejecutando. A continuación, si se produce un error en las consultas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]servicios más recientes, el VSPackage puede ofrecer otros servicios que se admiten en versiones anteriores de .

- Registre el VSPackage correctamente. Para obtener más información, vea Registro de [VSPackage](../extensibility/internals/vspackage-registration.md) y [Registro de VSPackage administrado](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Registre las extensiones de archivo correctamente. Para obtener más información, consulte Registro de extensiones de nombre de [archivo para implementaciones en paralelo.](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)

- Cree un instalador que implemente el VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]para las versiones adecuadas de . Para obtener más información, vea [Instalar VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y Administración de [componentes](../extensibility/internals/component-management.md).

- Abordar el problema de las colisiones de registro. Para obtener más información, vea Registro de [VSPackage](../extensibility/internals/vspackage-registration.md).

- Asegúrese de que los archivos compartidos y versionados respeten el recuento de referencias para permitir la instalación y eliminación seguras de varias versiones. Para obtener más información, consulte [Gestión de componentes](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VSPackages versionados
 En la estrategia de VSPackage versionada, se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea un VSPackage para cada versión que admite. Esto es adecuado cuando se espera aprovechar los servicios [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]proporcionados por versiones posteriores de , porque cada VSPackage puede evolucionar sin afectar a los demás. Sin embargo, la estrategia versionada de crear varios binarios, ya sea desde una única base de código o desde varias bases de código independientes, podría implicar más desarrollo inicial que la estrategia compartida. Además, es posible que sea necesario realizar un trabajo de instalación adicional porque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe crear una instalación independiente para cada versión o una única configuración que detecte las versiones de las que están instaladas y que admite el VSPackage.

## <a name="binary-compatibility"></a>Compatibilidad binaria
 Por lo general, la compatibilidad binaria permite que los VSPackages de código nativo desarrollados con versiones anteriores de Visual Studio se ejecuten en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones importantes:

- Si el VSPackage se basa en una versión determinada de Common [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Language Runtime, debe determinar en qué versión se está ejecutando.

- Un VSPackage puede tener una dependencia en una característica específica de otro VSPackage u otro producto. Por lo tanto, el VSPackage solo puede ejecutarse donde se satisface la dependencia.

- Un VSPackage podría verse afectado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] una corrección de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]seguridad en un Service Pack o una versión posterior de . En esos casos, un VSPackage desarrollado con [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] una versión [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anterior de la podría no ejecutarse en versiones de después de aplicar la corrección de seguridad. Sin embargo, puede volver a generar el paquete con la versión posterior y hacer que también se ejecute en versiones anteriores.

  VSPackages administrados deben compilarse [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] una versión [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]y que coincidan con la versión de destino de .

  Además de planear la compatibilidad binaria para los archivos binarios de VSPackage, también debe tener en cuenta los formatos de archivo de solución y proyecto. Si el VSPackage crea un nuevo tipo de proyecto, debe decidir si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]se puede ejecutar en una sola versión o en varias versiones de . Para obtener más información, consulte [Actualización de proyectos personalizados.](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)

## <a name="see-also"></a>Vea también
- [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gestión de componentes](../extensibility/internals/component-management.md)
