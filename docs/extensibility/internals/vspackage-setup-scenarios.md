---
title: "Escenarios de instalación de VSPackage | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2128d4c2659d7e6e389384c4bf7e133a4fb32e47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-setup-scenarios"></a>Escenarios de instalación de VSPackage
Es importante para el instalador de VSPackage la flexibilidad de diseño. Por ejemplo, es posible que deba liberar una revisión de seguridad en el futuro, o podría cambiar una estrategia de negocio que requiere la compatibilidad con versiones de side-by-side exhaustiva.  
  
 En [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), puede leer sobre las ventajas y los problemas de compatibilidad con las instalaciones en paralelo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con las instalaciones compartidas o side-by-side del paquete de VS. En resumen, VSPackages side-by-side ofrecen la máxima flexibilidad para admitir nuevas características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Los escenarios descritos en este tema no son las únicas opciones, pero que se presentan como sugieren procedimientos recomendados.  
  
## <a name="components-privacy-and-sharing"></a>Componentes, la privacidad y el uso compartido  
  
##### <a name="make-your-components-independent"></a>Hacer que sus componentes independientes  
 Una vez que se identifican y rellena un componente, asignar un `GUID`e implementar el componente, no se puede cambiar su composición. Si cambia la composición de un componente, el componente resultante debe ser un nuevo componente con un nuevo `GUID`. Dados estos hechos, se ofrece la máxima flexibilidad de control de versiones mediante la realización de cada unidad independiente, independiente de componente. Para obtener más información acerca de las reglas que rigen los componentes, consulte [cambiar el código de componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) y [¿qué ocurre si el componente de las reglas se dividen?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>No mezcle los recursos compartidos y privados en un componente  
 Recuento de referencias se produce en el nivel de componente. Por lo tanto, la combinación de recursos compartidos y privados de un componente sería imposible actualizar recursos privados, como un archivo ejecutable, sin sobrescribir también los recursos compartidos. En este escenario crea problemas de compatibilidad con versiones anteriores y restringe la creación de capacidad en paralelo.  
  
 Por ejemplo, los valores del registro se usan para registrar el paquete de VS con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] debe mantenerse en un componente independiente de se utilizó para registrar el paquete de VS con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Archivos compartidos o valores del registro, vaya en otro componente.  
  
## <a name="scenario-1-shared-vspackage"></a>Escenario 1: Compartido VSPackage  
 En este escenario, un VSPackage compartido (un archivo binario único que admite varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) se incluye en un paquete de Windows Installer. Registrar con cada versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se controla mediante características seleccionables por el usuario. También significa que cuando se asigna a distintos características, cada componente puede seleccionar individualmente para la instalación o desinstalación, contar con el usuario de control de integrar el VSPackage en diferentes versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Consulte [las características de Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obtener más información sobre el uso de características en paquetes de Windows Installer.)  
  
 ![Gráfico VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")  
Instalador de VSPackage compartido  
  
 Como se muestra en la ilustración, los componentes compartidos se convierten en parte de la característica Feat_Common, que siempre se instala. Mediante la realización de las características de Feat_VS2002 y Feat_VS2003 visible, los usuarios pueden elegir en tiempo de instalación en las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desean VSPackage para integrar. Los usuarios también pueden utilizar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso se agrega o quita la información de registro de VSPackage de distintas versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Si establece la columna de presentación de una característica en 0, oculta. Un valor de columna de nivel bajo, por ejemplo, 1, garantiza que siempre se va a instalar. Para obtener más información, consulte [propiedad INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) y [tabla de características](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Escenario 2: Actualizar de VSPackage compartida  
 En este escenario, se incluye una versión actualizada del instalador de VSPackage en el escenario 1. En aras de la discusión, la actualización agrega compatibilidad para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], pero también podría ser un más sencillo seguridad revisión o corrección de errores service pack. Las reglas del instalador de Windows para instalar los componentes más recientes requieren que los componentes sin modificar ya en el sistema no se vuelven a copiar. En este caso, un sistema con la versión 1.0 ya está presente se sobrescriba el Comp_MyVSPackage.dll del componente actualizado y permiten a los usuarios optar por agregar la nueva característica Feat_VS2005 con su componente Comp_VS2005_Reg.  
  
> [!CAUTION]
>  Cada vez que un paquete VSPackage se comparte entre varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], es fundamental que las versiones posteriores de VSPackage mantengan la compatibilidad con versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cuando no se puede mantener la compatibilidad con versiones anteriores, debe usar VSPackages side-by-side, privadas. Para obtener más información, consulte [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![VS Shared VS paquete actualización imagen](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Comparten el instalador de la actualización de VSPackage  
  
 Este escenario presenta a un nuevo instalador de VSPackage, al aprovechar la posibilidad de soporte técnico de Windows Installer para actualizaciones menores. Los usuarios simplemente instalen la versión 1.1 y actualiza la versión 1.0. Sin embargo, no es necesario tener la versión 1.0 en el sistema. El mismo programa de instalación instalará la versión 1.1 en un sistema sin versión 1.0. La ventaja para proporcionar actualizaciones secundarias de esta manera es que no es necesario pasar por el trabajo de desarrollo de un instalador de actualización y un producto completo. Un instalador realiza dos tareas. Una revisión de seguridad o service pack es posible que en su lugar, aprovechar las ventajas de las revisiones de Windows Installer. Para obtener más información, consulte [aplicación de revisiones y actualizaciones](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Escenario 3: Side-by-Side VSPackage  
 Este escenario presenta dos instaladores de VSPackage: uno para cada versión de Visual Studio .NET 2003 y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada instalador instala un side-by-side o private, VSPackage (uno que específicamente se compila y se instala una versión concreta de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]). Cada VSPackage está en su propio componente. Por lo tanto, cada uno de ellos puede atenderán individualmente con revisiones o mantenimiento libera. Dado que la DLL de VSPackage ahora es específico de la versión, es seguro incluir la información de registro en el mismo componente como el archivo DLL.  
  
 ![Lado de VS &#45; por &#45; Gráfico de VS Package lado](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")  
Instalador de paquete de VS Side-by-side  
  
 Cada instalador también incluye código que se comparte entre los dos instaladores. Si el código compartido se instala en una ubicación común, instalar dos archivos .msi se instalará el código compartido una sola vez. El instalador de segundo se limita a incrementar un recuento de referencias en el componente. El recuento de referencias garantiza que si uno de los VSPackages se desinstala, el código compartido permanecerá para otro VSPackage. Si el segundo VSPackage se desinstala así, se quitará el código compartido.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Escenario 4: Actualización de paquete de VS Side-by-Side  
 En este escenario, el paquete de VS para [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] han presentado un incremento de la seguridad de una vulnerabilidad y se necesita emitir el método update. Como en el escenario 2, puede crear un nuevo archivo .msi que se actualiza una instalación existente para incluir la revisión de seguridad, así como para implementar las instalaciones nuevas con la revisión de seguridad ya en su lugar.  
  
 En este caso, el VSPackage es un VSPackage administrado instalado en la caché de ensamblados global (GAC). Cuando se regenera, que incluyen la revisión de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro para el nuevo número de versión de ensamblado sobrescribe la versión anterior, provocando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar el ensamblado fijo.  
  
 ![Lado de VS &#45; por &#45; Gráfico de VS Package Update lado](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")  
Instalador de actualizaciones de paquete de VS Side-by-side  
  
 **Tenga en cuenta** para obtener más información acerca de la implementación de ensamblados en paralelo, vea [simplificar la implementación y resolver el caos de DLL con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Instalador de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)