---
title: "Escenarios de instalaci&#243;n de VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, consideraciones de implementación"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Escenarios de instalaci&#243;n de VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es importante diseñar al instalador de VSPackage flexibilidad. Por ejemplo, debe liberar una revisión de seguridad en el futuro, o podría cambiar una estrategia de negocio que requiere compatibilidad con control de versiones en paralelo exhaustiva.  
  
 En [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), encontrará información acerca de las ventajas y los problemas de compatibilidad con las instalaciones en paralelo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con las instalaciones compartidas o side\-by\-side de su paquete VSPackage. En resumen, side\-by\-side VSPackages ofrecerle la máxima flexibilidad para admitir nuevas características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Los escenarios descritos en este tema no son las únicas opciones, pero que se presentan como recomendaciones sugeridas.  
  
## Componentes, privacidad y uso compartido  
  
##### Hacer que los componentes independientes  
 Después de identificar y llenar un componente, asignar un `GUID`, e implementar el componente, no puede cambiar su composición. Si cambia la composición de un componente, el componente resultante debe ser un nuevo componente con un nuevo `GUID`. Dados estos hechos, la máxima flexibilidad de control de versiones es proporcionada por realizar cada unidad independiente, independiente de componente. Para obtener más información acerca de las reglas que rigen los componentes, consulte [cambiar el código de componente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) y [¿Qué sucede si el componente reglas están divididos?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### No mezcle los recursos compartidos y privados en un componente  
 Recuento de referencias se produce en el nivel de componente. Por lo tanto, recursos compartidos y privados en un componente de mezcla hace imposible actualizar recursos privados, como un archivo ejecutable, sin sobrescribir también recursos compartidos. Este escenario crea problemas de compatibilidad con versiones anteriores e impide la creación de capacidad side\-by\-side.  
  
 Por ejemplo, usan los valores del registro para registrar el VSPackage con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] debe mantenerse en un componente independiente de usado para registrar el VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Archivos compartidos o valores de registro van en otro componente.  
  
## Escenario 1: Compartir VSPackage  
 En este escenario, un VSPackage compartido \(binario único que admite varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) se incluye en un paquete de Windows Installer. Registrar con cada versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se controla mediante las características seleccionables por el usuario. También significa que cuando se asigna para separar las características, cada componente se puede seleccionar individualmente para la instalación o desinstalación, colocar el usuario en el control de integrar VSPackage en diferentes versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. \(Consulte [características de Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) para obtener más información sobre el uso de características de paquetes de Windows Installer.\)  
  
 ![Gráfico VS Shared VSPackage](~/docs/extensibility/internals/media/vs_sharedpackage.gif "VS\_SharedPackage")  
Instalador de VSPackage compartido  
  
 Como se muestra en la ilustración, los componentes compartidos se convierten en parte de la característica Feat\_Common, que siempre está instalada. Hacer visible las características Feat\_VS2002 y Feat\_VS2003, los usuarios pueden elegir durante la instalación en las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que desean integrar VSPackage. Los usuarios también pueden utilizar el modo de mantenimiento de Windows Installer para agregar o quitar características, que en este caso se agrega o quita la información de registro de VSPackage de diferentes versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Establecer la columna de visualización de una característica en 0, oculta. Un valor de columna de nivel bajo, como 1, garantiza que siempre se va a instalar. Para obtener más información, consulte [propiedad INSTALLLEVEL](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) y [tabla de características](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## Escenario 2: Actualización de VSPackage compartido  
 En este escenario, se incluye una versión actualizada del instalador en el escenario 1 VSPackage. Para ilustrar la explicación, la actualización agrega compatibilidad para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], pero también podría ser un más sencillo security patch o corrección de errores service pack. Las reglas de Windows Installer para instalar los componentes más recientes requieren que los componentes sin modificar ya en el sistema no se vuelven a copiar. En este caso, sobrescriba el componente actualizado Comp\_MyVSPackage.dll y permiten a los usuarios elegir agregar la nueva característica Feat\_VS2005 con su componente Comp\_VS2005\_Reg un sistema con la versión 1.0 ya está presente.  
  
> [!CAUTION]
>  Cada vez que un paquete VSPackage se comparte entre varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], es esencial que las versiones posteriores de VSPackage mantengan la compatibilidad con versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cuando no se puede mantener la compatibilidad con versiones anteriores, debe utilizar VSPackages side\-by\-side y privada. Para obtener más información, consulta [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Imagen VS Shared VS Package Update](~/docs/extensibility/internals/media/vs_sharedpackageupdate.gif "VS\_SharedPackageUpdate")  
Compartir el instalador de actualización de VSPackage  
  
 Este escenario presenta a un nuevo instalador de VSPackage, aprovechando de soporte técnico de Windows Installer para actualizaciones menores. Los usuarios simplemente instalen la versión 1.1 y actualiza la versión 1.0. Sin embargo, no es necesario tener la versión 1.0 en el sistema. El mismo programa de instalación instalará la versión 1.1 en un sistema sin versión 1.0. La ventaja de proporcionar actualizaciones menores de esta manera es que no es necesario completar el trabajo de desarrollo de un instalador de actualización y un producto completo. Un instalador realiza dos tareas. Una revisión de seguridad o un service pack es posible que en su lugar, aprovechar las revisiones de Windows Installer. Para obtener más información, consulte [aplicación de revisiones y actualizaciones](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## Escenario 3: Side\-by\-Side VSPackage  
 Este escenario presenta dos instaladores de VSPackage, uno para cada versión de Visual Studio .NET 2003 y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada instalador instala un side\-by\-side o privado, VSPackage \(uno específicamente creado e instalado en una versión determinada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\). Cada paquete VSPackage que se encuentra en su propio componente. Por consiguiente, cada uno puede servicio individualmente con revisiones o mantenimiento libera. Dado que la DLL de VSPackage ahora es específica de la versión, es seguro incluir su información de registro en el mismo componente como el archivo DLL.  
  
 ![Gráfico VS Side&#45;by&#45;Side VS Package](~/docs/extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
Instalador de VSPackage Side\-by\-side  
  
 Cada instalador también incluye código que se comparte entre los dos instaladores. Si está instalado el código compartido en una ubicación común, instalar ambos archivos .msi se instalará el código compartido sólo una vez. El segundo instalador acaba incrementa un recuento de referencias en el componente. El recuento de referencias garantiza que si uno de los VSPackages se desinstala, el código compartido permanecerá para otro VSPackage. Si el segundo VSPackage se desinstala también se quitará el código compartido.  
  
## Escenario 4: Side\-by\-Side VSPackage actualización  
 En este escenario, el VSPackage para [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] sufrido de seguridad y vulnerabilidad necesita una actualización. Como en el escenario 2, puede crear un nuevo archivo .msi que se actualiza una instalación existente para incluir la revisión de seguridad, así como implementar nuevas instalaciones con la revisión de seguridad ya en su lugar.  
  
 En este caso, el VSPackage es un VSPackage administrado instalado en la caché de ensamblados global \(GAC\). Cuando se regenera, que incluye la revisión de seguridad, debe cambiar la parte del número de revisión del número de versión del ensamblado. La información de registro para el nuevo número de versión de ensamblado sobrescribe la versión anterior, causando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar el ensamblado fijo.  
  
 ![Gráfico VS Side&#45;by&#45;Side VS Package Update](~/docs/extensibility/internals/media/vs_sbys_packageupdate.gif "VS\_SbyS\_PackageUpdate")  
Instalador de actualización de VSPackage Side\-by\-side  
  
 **Nota** para obtener más información sobre la implementación de ensamblados en paralelo, vea [simplifica la implementación y resolver infierno de DLL con .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## Vea también  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)