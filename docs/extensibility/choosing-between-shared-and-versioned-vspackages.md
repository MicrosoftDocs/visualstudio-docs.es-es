---
title: "Elegir entre VSPackages compartido y su versi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SxS"
  - "instalación en paralelo"
  - "instalación [Visual Studio SDK], en paralelo"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Elegir entre VSPackages compartido y su versi&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diferentes versiones de Visual Studio pueden coexistir en el mismo equipo. VSPackages puede admitir cualquier combinación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versiones.  
  
 Puede habilitar las instalaciones en paralelo de VSPackages mediante cualquiera de las dos estrategias, la estrategia compartida o la estrategia de versiones. Ambos dar cabida a la presencia de varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociadas a las versiones de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 En la estrategia compartida, un VSPackage está registrado para su uso en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En la estrategia de versiones, se instalan varios archivos DLL de VSPackage, uno para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se admiten.  
  
## VSPackages compartido  
 Utilizando un VSPackage compartido es adecuado cuando se utiliza el mismo VSPackage en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para implementar un paquete VSPackage compartido, debe seguir los pasos siguientes:  
  
-   Hacer el VSPackage sean compatibles con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dos maneras de hacerlo así que están disponibles:  
  
    -   Limitar el VSPackage a usar sólo las características de la versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se admiten.  
  
    -   Programar el VSPackage para adaptarse a la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se ejecute. A continuación, si se produce un error en las consultas de servicios más recientes, el VSPackage puede ofrecer otros servicios que se admiten en versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrar el VSPackage adecuadamente. Para obtener más información, vea [Registro de VSPackage](../extensibility/internals/vspackage-registration.md) y [Managed VSPackage Registration](http://msdn.microsoft.com/es-es/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrar extensiones de archivo correctamente. Para obtener más información, consulta [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Crear un instalador que implementa el VSPackage para las versiones adecuadas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, vea [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) y [Administración de componentes](../extensibility/internals/component-management.md).  
  
-   Solucionar el problema de conflictos de registro. Para obtener más información, consulta [Registro de VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Asegúrese de que archivos compartidos y con versiones respetarán el recuento de referencias para permitir la seguridad de instalación y eliminación de varias versiones. Para obtener más información, consulta [Administración de componentes](../extensibility/internals/component-management.md).  
  
## VSPackages con versiones  
 En la estrategia de VSPackage con versiones, crear un VSPackage para cada versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se admiten. Esto resulta adecuado si tiene previsto aprovechar los servicios proporcionados por las versiones posteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], porque cada VSPackage puede evolucionar sin que afecte al resto. No obstante, la estrategia de versiones de la creación de varios archivos binarios, de una sola base de código o de varias bases de código independiente, puede implicar más el desarrollo inicial de la estrategia compartido. Además, el programa de instalación adicionales puede requerirse trabajo porque debe crear en una configuración independiente para cada versión o un programa de instalación único que detecta las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que están instalados y que admite el VSPackage.  
  
## Compatibilidad binaria  
 Por lo general, la compatibilidad binaria permite VSPackages código nativo desarrolladas con las versiones anteriores de Visual Studio para ejecutar en versiones posteriores de Visual Studio. Sin embargo, hay tres excepciones importantes:  
  
-   Si el VSPackage depende de una versión determinada de common language runtime, debe determinar en qué versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se está ejecutando.  
  
-   Un VSPackage podría tener una dependencia en una característica específica de VSPackage otro u otro producto. Por consiguiente, el VSPackage puede ejecutar sólo cuando se cumple la dependencia.  
  
-   Un VSPackage podría verse afectado por una revisión de seguridad en un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versión posterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En esos casos, un VSPackage se desarrolló con una versión anterior de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] podría no ejecutarse en las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] después de aplica la revisión de seguridad. Sin embargo, puede volver a generar el paquete con la versión más reciente y que también se ejecutan en versiones anteriores.  
  
 VSPackages administrado debe compilarse con una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que coincidan con la versión de destino de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Además de planeación para la compatibilidad binaria de los archivos binarios de VSPackage, también debe considerar la solución y formatos de archivo de proyecto. Si su VSPackage crea un nuevo tipo de proyecto, debe decidir si se puede ejecutar en una sola versión o en varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulta [Actualizar proyectos personalizados](../misc/upgrading-custom-projects.md).  
  
## Vea también  
 [Instalación de VSPackages con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Administración de componentes](../extensibility/internals/component-management.md)