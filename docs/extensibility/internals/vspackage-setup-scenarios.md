---
title: Escenarios de configuración de VSPackage ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703970"
---
# <a name="vspackage-setup-scenarios"></a>Escenarios de instalación de VSPackage

Es importante diseñar el instalador de VSPackage para la flexibilidad. Por ejemplo, es posible que deba lanzar una revisión de seguridad en el futuro o puede cambiar una estrategia empresarial que requiera una compatibilidad completa con el control de versiones en paralelo.

En [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), puede leer acerca de las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventajas y problemas de admitir instalaciones en paralelo de instalaciones compartidas o en paralelo de su VSPackage. En resumen, en paralelo VSPackages le dan la mayor flexibilidad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]para admitir nuevas características de .

Los escenarios descritos en este tema no son sus únicas opciones, pero se presentan como prácticas recomendadas sugeridas.

## <a name="components-privacy-and-sharing"></a>Componentes, privacidad y uso compartido

### <a name="make-your-components-independent"></a>Haga que sus componentes sean independientes

Una vez que identifique y `GUID`rellene un componente, asigne un archivo y desplegó el componente, no podrá cambiar su composición. Si cambia la composición de un componente, el componente resultante `GUID`debe ser un nuevo componente con un nuevo . Teniendo en cuenta estos hechos, la mayor flexibilidad de control de versiones se ofrece al hacer que cada componente sea independiente y autosuficiente. Para obtener más información acerca de las reglas que rigen los componentes, consulte [Cambiar el código](/windows/desktop/Msi/changing-the-component-code) de componente y qué sucede si las reglas de [componentes están rotas?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>No mezcle recursos compartidos y privados en un componente

El recuento de referencias se produce en el nivel de componente. Por lo tanto, la mezcla de recursos compartidos y privados en un componente hace que sea imposible actualizar recursos privados, como un archivo ejecutable, sin sobrescribir también los recursos compartidos. Este escenario crea problemas de compatibilidad con versiones anteriores y le impide crear capacidaden en paralelo.

Por ejemplo, los valores del Registro [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] que se usan para registrar el VSPackage con el debe mantenerse en un componente independiente de uno utilizado para registrar el VSPackage con Visual Studio. Los archivos compartidos o los valores del Registro van en otro componente.

## <a name="scenario-1-shared-vspackage"></a>Escenario 1: VSPackage compartido

En este escenario, un VSPackage compartido (un único binario que admite varias versiones de Visual Studio se incluye en un paquete de Windows Installer. Registrarse con cada versión de Visual Studio se controla mediante características seleccionables por el usuario. También significa que cuando se asigna a características independientes, cada componente se puede seleccionar individualmente para la instalación [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]o desinstalación, poniendo al usuario en control de la integración del VSPackage en diferentes versiones de . (Consulte [Características de Windows Installer](/windows/desktop/Msi/windows-installer-features) para obtener más información sobre el uso de características en paquetes de Windows Installer.)

![VS Shared VSPackage instalador](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Como se muestra en la ilustración, los componentes compartidos forman parte de la función Feat_Common, que siempre se instala. Al hacer visibles las características de Feat_VS2002 y Feat_VS2003, los usuarios pueden elegir en tiempo de instalación en qué versiones de Visual Studio desean que se integre el VSPackage. Los usuarios también pueden usar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso agrega o quita la información de registro de VSPackage de diferentes versiones de Visual Studio.

> [!NOTE]
> Al establecer la columna Visualización de una entidad en 0, se oculta. Un valor de columna de nivel bajo, como 1, garantiza que siempre se instalará. Para obtener más información, vea [InstallLEVEL Property](/windows/desktop/Msi/installlevel) and [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Escenario 2: Actualización de VSPackage compartida

En este escenario, se incluye una versión actualizada del instalador de VSPackage en el escenario 1. En aras de la discusión, la actualización agrega compatibilidad con Visual Studio, pero también podría ser una revisión de seguridad más sencilla o un Service Pack de corrección de errores. Las reglas de Windows Installer para instalar componentes más recientes requieren que los componentes sin cambios que ya están en el sistema no se vuelvan a copiar. En este caso, un sistema con la versión 1.0 ya presente sobrescribirá el componente actualizado Comp_MyVSPackage.dll y permitirá a los usuarios elegir agregar la nueva característica Feat_VS2005 con su componente Comp_VS2005_Reg.

> [!CAUTION]
> Siempre que un VSPackage se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comparte entre varias versiones de , es esencial que las versiones posteriores de VSPackage mantengan la compatibilidad con versiones anteriores de Visual Studio. Donde no puede mantener la compatibilidad con versiones anteriores, debe usar VSPackages privados en paralelo. Para obtener más información, vea [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalador de actualización de paquetes VS Shared VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Este escenario presenta un nuevo instalador de VSPackage, aprovechando la compatibilidad de Windows Installer para actualizaciones menores. Los usuarios simplemente instalan la versión 1.1 y actualiza la versión 1.0. Sin embargo, no es necesario tener la versión 1.0 en el sistema. El mismo instalador instalará la versión 1.1 en un sistema sin la versión 1.0. La ventaja de proporcionar actualizaciones menores de esta manera es que no es necesario pasar por el trabajo de desarrollo de un instalador de actualización y un instalador de producto completo. Un instalador realiza ambos trabajos. Una corrección de seguridad o Service Pack podrían aprovechar las revisiones de Windows Installer. Para obtener más información, consulte [Parches y actualizaciones](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Escenario 3: VSPackage en paralelo

Este escenario presenta dos instaladores de VSPackage: uno para cada versión de Visual Studio .NET 2003 y Visual Studio. Cada instalador instala un VSPackage en paralelo o privado (uno que se compila e instala específicamente para una versión determinada de Visual Studio). Cada VSPackage está en su propio componente. Por lo tanto, cada uno puede ser reparado individualmente con parches o versiones de mantenimiento. Dado que el archivo DLL de VSPackage ahora es específico de la versión, es seguro incluir su información de registro en el mismo componente que el archivo DLL.

![Vs instalador de paquetes VS en paralelo](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Cada instalador también incluye código que se comparte entre los dos instaladores. Si el código compartido está instalado en una ubicación común, la instalación de ambos archivos .msi instalará el código compartido solo una vez. El segundo instalador solo incrementa un recuento de referencias en el componente. El recuento de referencias garantiza que si se desinstala uno de los VSPackages, el código compartido permanecerá para el otro VSPackage. Si también se desinstala el segundo VSPackage, se quitará el código compartido.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Escenario 4: Actualización de VSPackage en paralelo

En este escenario, el VSPackage para Visual Studio sufrió de una vulnerabilidad de seguridad y debe emitir una actualización. Al igual que en el escenario 2, puede crear un nuevo archivo .msi que actualice una instalación existente para incluir la corrección de seguridad, así como implementar nuevas instalaciones con la corrección de seguridad ya en su lugar.

En este caso, el VSPackage es un VSPackage administrado instalado en la caché global de ensamblados (GAC). Al volver a generarlo para incluir la corrección de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro para el nuevo número de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versión de ensamblado sobrescribe la versión anterior, lo que hace que se cargue el ensamblado fijo.

![Vs instalador de actualización de paquetes VS en paralelo](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Para obtener más información sobre la implementación de ensamblados en paralelo, vea [Simplificar la implementación y resolver DLL Hell con .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Vea también

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
