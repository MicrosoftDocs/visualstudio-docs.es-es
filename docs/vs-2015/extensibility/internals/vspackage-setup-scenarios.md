---
title: Escenarios de instalación de VSPackage | Microsoft Docs
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
ms.openlocfilehash: c94963b0ebfc6df454870222059a460b2868427d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999306"
---
# <a name="vspackage-setup-scenarios"></a>Escenarios de instalación de VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es importante diseñar al instalador de paquete VSPackage para mayor flexibilidad. Por ejemplo, es posible que deba liberar una revisión de seguridad en el futuro, o podría cambiar una estrategia de negocio que requiere compatibilidad con control de versiones en paralelo exhaustiva.  
  
 En [que admiten varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), puede leer sobre las ventajas y los problemas de compatibilidad con las instalaciones en paralelo de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con compartida o en paralelo de las instalaciones del paquete de VS. En resumen, VSPackages side-by-side ofrecerle la máxima flexibilidad para admitir nuevas características de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Los escenarios descritos en este tema no son las únicas opciones, pero se presentan como sugieren procedimientos recomendados.  
  
## <a name="components-privacy-and-sharing"></a>Componentes, privacidad y uso compartido  
  
##### <a name="make-your-components-independent"></a>Hacer que los componentes independientes  
 Después de identificar y rellenar un componente, asignar un `GUID`e implementar el componente, no se puede cambiar su composición. Si cambia la composición de un componente, el componente resultante debe ser un nuevo componente con un nuevo `GUID`. Dados estos hechos, se permite la máxima flexibilidad de control de versiones mediante la realización de cada unidad de componente independiente, de manera autónoma. Para obtener más información acerca de las reglas que rigen los componentes, consulte [cambiando el código de componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) y [¿qué ocurre si el componente de las reglas se dividen?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>No mezcle los recursos compartidos y privados en un componente  
 Recuento de referencias se produce en el nivel de componente. Por lo tanto, mezclando recursos compartidos y privados en un componente hace imposible actualizar los recursos privados, como un archivo ejecutable, sin sobrescribir también los recursos compartidos. En este escenario crea problemas de compatibilidad con versiones anteriores y le impida crear funcionalidad en paralelo.  
  
 Por ejemplo, los valores del registro se usan para registrar el VSPackage con el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] deben conservarse en un componente independiente de uno se usa para registrar el VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Archivos compartidos o los valores del registro van en otro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Escenario 1: VSPackage compartido  
 En este escenario, un VSPackage compartido (un archivo binario único que admite varias versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) se incluye en un paquete de Windows Installer. Registrar con cada versión de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se controla mediante las características seleccionables por el usuario. También significa que cuando se asigna para separar las características, cada componente se puede seleccionar individualmente para la instalación o desinstalación, colocar el usuario en el control de integrar el VSPackage en diferentes versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Consulte [características de Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obtener más información sobre el uso de características en los paquetes de Windows Installer.)  
  
 ![Gráfico VS Shared VSPackage](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Instalador de VSPackage compartido  
  
 Como se muestra en la ilustración, los componentes compartidos se convierten en parte de la característica Feat_Common, que siempre se instala. Mediante la realización de las características de Feat_VS2002 y Feat_VS2003 visible, los usuarios pueden elegir en tiempo de instalación en las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que desean integrar VSPackage. Los usuarios también pueden usar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso se agrega o quita la información de registro de VSPackage de diferentes versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  Si la columna de presentación de una característica en 0 lo oculta. Un valor de columna de nivel bajo, como 1, garantiza que siempre se instalará. Para obtener más información, consulte [propiedad INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) y [tabla de características](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Escenario 2: Actualizar compartida de VSPackage  
 En este escenario, se incluye una versión actualizada del instalador de VSPackage en el escenario 1. Para ilustrar la explicación, la actualización agrega compatibilidad para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], pero también podría ser un más sencillo security patch o corrección de errores service pack. Las reglas del instalador de Windows para instalar los componentes más recientes requieren que los componentes sin cambios ya está en el sistema no se vuelven a copiar. En este caso, sobrescriba el componente actualizado Comp_MyVSPackage.dll y permitir que los usuarios a optar por agregar la nueva característica Feat_VS2005 a su componente Comp_VS2005_Reg un sistema con la versión 1.0 ya está presente.  
  
> [!CAUTION]
>  Cada vez que un VSPackage se comparte entre varias versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], es esencial que las versiones posteriores del VSPackage mantengan la compatibilidad con versiones anteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Cuando no se puede mantener la compatibilidad con versiones anteriores, debe usar VSPackages side-by-side y privados. Para obtener más información, consulte [que admiten varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![VS Shared VS paquete actualización imagen](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Compartir el instalador de actualización de VSPackage  
  
 Este escenario presenta a un nuevo instalador de VSPackage, que aprovecha la compatibilidad del instalador de Windows para las actualizaciones menores. Los usuarios simplemente instalar la versión 1.1 y actualiza la versión 1.0. Sin embargo, no es necesario tener la versión 1.0 en el sistema. El mismo instalador instalará la versión 1.1 en un sistema sin versión 1.0. La ventaja para proporcionar las actualizaciones menores de esta manera es que no es necesario pasar por el trabajo de desarrollo de un instalador de actualización y un instalador de producto completo. Una instalador realiza dos tareas. Una revisión de seguridad o service pack es posible que en su lugar, aproveche las ventajas de las revisiones de Windows Installer. Para obtener más información, consulte [aplicación de revisiones y actualizaciones](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Escenario 3: Paquete de VS Side-by-Side  
 Este escenario presenta dos instaladores de VSPackage, uno para cada versión de Visual Studio .NET 2003 y [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Cada instalador instala un side-by-side o private, VSPackage (uno que se compila y se instala una versión concreta de específicamente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Cada VSPackage está en su propio componente. Por lo tanto, cada uno de ellos pueden realizarse individualmente con revisiones o mantenimiento de versiones. Dado que la DLL de VSPackage ahora es específica de la versión, es seguro incluir la información de registro en el mismo componente que el archivo DLL.  
  
 ![Lado VS&#45;por&#45;gráfico Side VS Package](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Instalador de paquete de VS Side-by-side  
  
 Cada instalador también incluye código que se comparte entre los dos instaladores. Si el código compartido se instala en una ubicación común, instalar dos archivos .msi se instalará el código compartido una sola vez. El segundo instalador acaba incrementa un recuento de referencias en el componente. El recuento de referencias garantiza que si se desinstala uno de los VSPackages, seguirá siendo el código compartido para el VSPackage del otro. Si el segundo VSPackage se desinstala así, se quitará el código compartido.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Escenario 4: Actualización del paquete de VS Side-by-Side  
 En este escenario, el VSPackage para [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] sufrido una seguridad de una vulnerabilidad y tiene que emitir una actualización. Como se muestra en el escenario 2, puede crear un nuevo archivo .msi que actualiza una instalación existente para incluir la corrección de seguridad, así como implementar las instalaciones nuevas con la corrección de seguridad ya en su lugar.  
  
 En este caso, el VSPackage es un VSPackage administrado instalado en la caché de ensamblados global (GAC). Cuando se recompile para incluir la corrección de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro de nuevo el número de versión de ensamblado sobrescribe la versión anterior, lo que provocará [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para cargar el ensamblado fijo.  
  
 ![Lado VS&#45;por&#45;gráfico Side VS Package Update](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalador de actualización de paquete de VS Side-by-side  
  
 **Tenga en cuenta** para obtener más información sobre la implementación de ensamblados en paralelo, vea [lo que simplifica la implementación y resolver infierno de DLL con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
