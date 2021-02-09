---
title: Escenarios de configuración de VSPackage | Microsoft Docs
description: Obtenga información sobre las prácticas recomendadas para admitir instalaciones en paralelo de Visual Studio con instalaciones compartidas o en paralelo del VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81e298229bb12d906a3061e0b547553518cce204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900000"
---
# <a name="vspackage-setup-scenarios"></a>Escenarios de instalación de VSPackage

Es importante diseñar el instalador de VSPackage para que sea más flexible. Por ejemplo, puede que tenga que publicar una revisión de seguridad en el futuro, o bien puede cambiar una estrategia empresarial que requiera compatibilidad exhaustiva con el control de versiones en paralelo.

En la [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), puede obtener información sobre las ventajas y los problemas de compatibilidad con instalaciones en paralelo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con instalaciones compartidas o en paralelo del VSPackage. En Resumen, los VSPackages en paralelo proporcionan la máxima flexibilidad para admitir las nuevas características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Los escenarios descritos en este tema no son las únicas opciones, pero se presentan como prácticas recomendadas.

## <a name="components-privacy-and-sharing"></a>Componentes, privacidad y uso compartido

### <a name="make-your-components-independent"></a>Haga que sus componentes sean independientes

Una vez que se identifica y rellena un componente, se asigna un e `GUID` implementa el componente, no se puede cambiar su composición. Si cambia la composición de un componente, el componente resultante debe ser un componente nuevo con un nuevo `GUID` . Dados estos hechos, la mayor flexibilidad de control de versiones se proporciona al convertir cada componente en una unidad independiente y independiente. Para obtener más información acerca de las reglas que rigen los componentes, consulte [cambiar el código de componente](/windows/desktop/Msi/changing-the-component-code) y [Qué sucede si se interrumpen las reglas de componentes](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>No mezclar recursos compartidos y privados en un componente

El recuento de referencias se produce en el nivel de componente. Por lo tanto, la combinación de recursos compartidos y privados en un componente hace imposible actualizar los recursos privados, como un archivo ejecutable, sin sobrescribir también los recursos compartidos. En este escenario se crean problemas de compatibilidad con versiones anteriores y se restringe la creación de la funcionalidad en paralelo.

Por ejemplo, los valores del registro que se usan para registrar el VSPackage con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] deben mantenerse en un componente independiente de uno usado para registrar el VSPackage con Visual Studio. Los archivos compartidos o los valores del registro entran aún en otro componente.

## <a name="scenario-1-shared-vspackage"></a>Escenario 1: VSPackage compartido

En este escenario, se incluye un VSPackage compartido (un solo binario que admite varias versiones de Visual Studio en un paquete de Windows Installer. El registro con cada versión de Visual Studio se controla mediante características seleccionables por el usuario. También significa que, cuando se asigna a características independientes, cada componente se puede seleccionar individualmente para su instalación o desinstalación, lo que permite al usuario controlar la integración del VSPackage en diferentes versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . (Consulte [características de Windows Installer](/windows/desktop/Msi/windows-installer-features) para obtener más información sobre el uso de características en paquetes de Windows Installer).

![Instalador del VSPackage compartido VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Como se muestra en la ilustración, los componentes compartidos forman parte de la característica Feat_Common, que siempre está instalada. Al hacer visibles las características Feat_VS2002 y Feat_VS2003, los usuarios pueden elegir en el momento de la instalación en qué versiones de Visual Studio desean que se integre el VSPackage. Los usuarios también pueden usar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso agrega o quita la información de registro de VSPackage de distintas versiones de Visual Studio.

> [!NOTE]
> Si se establece la columna de presentación de una característica en 0, se oculta. Un valor de columna de nivel bajo, como 1, garantiza que siempre se instalará. Para obtener más información, vea [INSTALLLEVEL Property](/windows/desktop/Msi/installlevel) and [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Escenario 2: actualización compartida de VSPackage

En este escenario, se envía una versión actualizada del instalador de VSPackage en el escenario 1. Por motivos de debate, la actualización agrega compatibilidad con Visual Studio, pero también podría ser una revisión de seguridad más sencilla o Service Pack de corrección de errores. Las reglas de Windows Installer para instalar componentes más recientes requieren que los componentes sin cambios que ya están en el sistema no se recopien. En este caso, un sistema con la versión 1,0 ya presente sobrescribirá el componente actualizado Comp_MyVSPackage.dll y permitirá a los usuarios elegir agregar el nuevo Feat_VS2005 de características con su componente Comp_VS2005_Reg.

> [!CAUTION]
> Cada vez que un VSPackage se comparte entre varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , es fundamental que las versiones posteriores del VSPackage mantengan la compatibilidad con versiones anteriores de Visual Studio. Si no puede mantener la compatibilidad con versiones anteriores, debe usar los VSPackages privados en paralelo. Para obtener más información, vea [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalador de actualización VS compartido VS Package](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Este escenario presenta un nuevo instalador de VSPackage, que aprovecha la compatibilidad de Windows Installer con las actualizaciones secundarias. Los usuarios simplemente instalan la versión 1,1 y actualizan la versión 1,0. Sin embargo, no es necesario tener la versión 1,0 en el sistema. El mismo instalador instalará la versión 1,1 en un sistema sin la versión 1,0. La ventaja de proporcionar actualizaciones secundarias de esta manera es que no es necesario pasar por el trabajo de desarrollar un instalador de actualización y un instalador completo del producto. Un instalador realiza ambos trabajos. En su lugar, una corrección o Service Pack de seguridad puede aprovechar las revisiones de Windows Installer. Para obtener más información, consulte [revisiones y actualizaciones](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Escenario 3: VSPackage en paralelo

Este escenario presenta dos instaladores de VSPackage, uno para cada versión de Visual Studio .NET 2003 y Visual Studio. Cada instalador instala un VSPackage en paralelo o privado (uno que se crea e instala específicamente para una versión determinada de Visual Studio). Cada VSPackage está en su propio componente. Por lo tanto, cada una se puede atender individualmente con revisiones o versiones de mantenimiento. Dado que el archivo DLL de VSPackage es ahora específico de la versión, es seguro incluir su información de registro en el mismo componente que el archivo DLL.

![Instalador de vs paquete VS en paralelo](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Cada instalador también incluye código que se comparte entre los dos instaladores. Si el código compartido se instala en una ubicación común, al instalar ambos archivos. msi se instalará el código compartido solo una vez. El segundo instalador solo incrementa un recuento de referencias en el componente. El recuento de referencias garantiza que, si se desinstala uno de los VSPackages, el código compartido permanecerá para el otro VSPackage. Si también se desinstala el segundo VSPackage, se quitará el código compartido.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Escenario 4: actualización de VSPackage en paralelo

En este escenario, el VSPackage para Visual Studio sufrió una vulnerabilidad de seguridad y debe emitir una actualización. Como en el escenario 2, puede crear un nuevo archivo. msi que actualice una instalación existente para incluir la corrección de seguridad, así como implementar nuevas instalaciones con la corrección de seguridad ya implementada.

En este caso, el VSPackage es un VSPackage administrado instalado en la caché de ensamblados global (GAC). Cuando vuelva a generarlo para incluir la corrección de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro del nuevo número de versión de ensamblado sobrescribe la versión anterior, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con lo que se carga el ensamblado fijo.

![Instalador de la actualización en paralelo de VS Package](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Para obtener más información sobre la implementación de ensamblados en paralelo, consulte [simplificación de la implementación y solución de DLL Hell con el .NET Framework](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Vea también

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)