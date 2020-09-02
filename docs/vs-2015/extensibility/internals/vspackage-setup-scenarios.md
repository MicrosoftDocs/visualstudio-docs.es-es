---
title: Escenarios de configuración de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696756"
---
# <a name="vspackage-setup-scenarios"></a>Escenarios de instalación de VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es importante diseñar el instalador de VSPackage para que sea más flexible. Por ejemplo, puede que tenga que publicar una revisión de seguridad en el futuro, o bien puede cambiar una estrategia empresarial que requiera compatibilidad exhaustiva con el control de versiones en paralelo.  
  
 En la [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), puede obtener información sobre las ventajas y los problemas de compatibilidad con instalaciones en paralelo de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con instalaciones compartidas o en paralelo del VSPackage. En Resumen, los VSPackages en paralelo proporcionan la máxima flexibilidad para admitir las nuevas características de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Los escenarios descritos en este tema no son las únicas opciones, pero se presentan como prácticas recomendadas.  
  
## <a name="components-privacy-and-sharing"></a>Componentes, privacidad y uso compartido  
  
##### <a name="make-your-components-independent"></a>Haga que sus componentes sean independientes  
 Una vez que se identifica y rellena un componente, se asigna un e `GUID` implementa el componente, no se puede cambiar su composición. Si cambia la composición de un componente, el componente resultante debe ser un componente nuevo con un nuevo `GUID` . Dados estos hechos, la mayor flexibilidad de control de versiones se proporciona al convertir cada componente en una unidad independiente y independiente. Para obtener más información acerca de las reglas que rigen los componentes, consulte [cambiar el código de componente](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) y [Qué sucede si se interrumpen las reglas de componentes](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>No mezclar recursos compartidos y privados en un componente  
 El recuento de referencias se produce en el nivel de componente. Por lo tanto, la combinación de recursos compartidos y privados en un componente hace imposible actualizar los recursos privados, como un archivo ejecutable, sin sobrescribir también los recursos compartidos. En este escenario se crean problemas de compatibilidad con versiones anteriores y se restringe la creación de la funcionalidad en paralelo.  
  
 Por ejemplo, los valores del registro que se usan para registrar el VSPackage con [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] deben mantenerse en un componente independiente de uno usado para registrar el VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Los archivos compartidos o los valores del registro entran aún en otro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Escenario 1: VSPackage compartido  
 En este escenario, se incluye un VSPackage compartido (un único binario que admite varias versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) en un paquete de Windows Installer. El registro con cada versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se controla mediante características seleccionables por el usuario. También significa que, cuando se asigna a características independientes, cada componente se puede seleccionar individualmente para su instalación o desinstalación, lo que permite al usuario controlar la integración del VSPackage en diferentes versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . (Consulte [características de Windows Installer](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obtener más información sobre el uso de características en paquetes de Windows Installer).  
  
 ![Gráfico VS Shared VSPackage](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Instalador de VSPackage compartido  
  
 Como se muestra en la ilustración, los componentes compartidos forman parte de la característica Feat_Common, que siempre está instalada. Al hacer visibles las características Feat_VS2002 y Feat_VS2003, los usuarios pueden elegir en el momento de la instalación en qué versiones desean que se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integre el VSPackage. Los usuarios también pueden usar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso agrega o quita la información de registro del VSPackage de versiones diferentes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Si se establece la columna de presentación de una característica en 0, se oculta. Un valor de columna de nivel bajo, como 1, garantiza que siempre se instalará. Para obtener más información, vea [INSTALLLEVEL Property](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) and [Feature Table](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Escenario 2: actualización compartida de VSPackage  
 En este escenario, se envía una versión actualizada del instalador de VSPackage en el escenario 1. Por motivos de análisis, la actualización agrega compatibilidad para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , pero también podría ser una revisión de seguridad más sencilla o Service Pack de corrección de errores. Las reglas de Windows Installer para instalar componentes más recientes requieren que los componentes sin cambios que ya están en el sistema no se recopien. En este caso, un sistema con la versión 1,0 ya presente sobrescribirá el componente actualizado Comp_MyVSPackage.dll y permitirá a los usuarios elegir agregar el nuevo Feat_VS2005 de características con su componente Comp_VS2005_Reg.  
  
> [!CAUTION]
> Cada vez que un VSPackage se comparte entre varias versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , es fundamental que las versiones posteriores del VSPackage mantengan la compatibilidad con versiones anteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Si no puede mantener la compatibilidad con versiones anteriores, debe usar los VSPackages privados en paralelo. Para obtener más información, vea [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Imagen VS Shared VS Package Update](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Instalador de actualización de VSPackage compartido  
  
 Este escenario presenta un nuevo instalador de VSPackage, que aprovecha la compatibilidad de Windows Installer con las actualizaciones secundarias. Los usuarios simplemente instalan la versión 1,1 y actualizan la versión 1,0. Sin embargo, no es necesario tener la versión 1,0 en el sistema. El mismo instalador instalará la versión 1,1 en un sistema sin la versión 1,0. La ventaja de proporcionar actualizaciones secundarias de esta manera es que no es necesario pasar por el trabajo de desarrollar un instalador de actualización y un instalador completo del producto. Un instalador realiza ambos trabajos. En su lugar, una corrección o Service Pack de seguridad puede aprovechar las revisiones de Windows Installer. Para obtener más información, consulte [revisiones y actualizaciones](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Escenario 3: VSPackage en paralelo  
 Este escenario presenta dos instaladores de VSPackage, uno para cada versión de Visual Studio .NET 2003 y [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Cada instalador instala un VSPackage en paralelo o privado (uno que se crea e instala específicamente para una versión determinada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ). Cada VSPackage está en su propio componente. Por lo tanto, cada una se puede atender individualmente con revisiones o versiones de mantenimiento. Dado que el archivo DLL de VSPackage es ahora específico de la versión, es seguro incluir su información de registro en el mismo componente que el archivo DLL.  
  
 ![VS&#45;del lado&#45;gráfico de vs Package](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Instalador de VSPackage en paralelo  
  
 Cada instalador también incluye código que se comparte entre los dos instaladores. Si el código compartido se instala en una ubicación común, al instalar ambos archivos. msi se instalará el código compartido solo una vez. El segundo instalador solo incrementa un recuento de referencias en el componente. El recuento de referencias garantiza que, si se desinstala uno de los VSPackages, el código compartido permanecerá para el otro VSPackage. Si también se desinstala el segundo VSPackage, se quitará el código compartido.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Escenario 4: actualización de VSPackage en paralelo  
 En este escenario, el VSPackage para [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] sufrió una vulnerabilidad de seguridad y debe emitir una actualización. Como en el escenario 2, puede crear un nuevo archivo. msi que actualice una instalación existente para incluir la corrección de seguridad, así como implementar nuevas instalaciones con la corrección de seguridad ya implementada.  
  
 En este caso, el VSPackage es un VSPackage administrado instalado en la caché de ensamblados global (GAC). Cuando vuelva a generarlo para incluir la corrección de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro del nuevo número de versión de ensamblado sobrescribe la versión anterior, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con lo que se carga el ensamblado fijo.  
  
 ![VS&#45;del lado&#45;gráfico de actualización de VS Package](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalador de la actualización de VSPackage en paralelo  
  
 **Nota:** Para obtener más información sobre la implementación de ensamblados en paralelo, consulte [simplificación de la implementación y solución de DLL Hell con el .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Consulte también  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
