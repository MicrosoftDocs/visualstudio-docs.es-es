---
title: "Env&#237;o de extensiones de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Implementación de VSIX"
  - "implementación de VSIX"
  - "archivos DLL satélite, en paquetes VSIX"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Env&#237;o de extensiones de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una vez haya terminado de desarrollar su extensión, puede instalar en otros equipos, compartir con sus amigos y compañeros de trabajo o publicar en la Galería de Visual Studio. En esta sección se explica todo lo que necesita hacer para publicar y mantener su extensión: trabajar con archivos .vsix, publicación, localizar y actualizar.  
  
## Trabajar con las extensiones VSIX  
 Puede crear extensiones de VSIX creando un proyecto VSIX en blanco y, a continuación, agregar plantillas de elementos diferentes al mismo. Para obtener más información, consulta [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
 Puede usar el formato VSIX para empaquetar plantillas de proyecto, elementos componentes de plantillas, VSPackages, Managed Extensibility Framework \(MEF\), **herramientas** controles, ensamblados y tipos personalizados \(Esto incluye las páginas principales personalizadas\). El formato VSIX usa basado en el archivo de implementación. Para obtener más información acerca de los paquetes VSIX, consulte [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 El formato VSIX no admite la instalación de fragmentos de código. No admite ciertas otros escenarios como la escritura en la caché Global de ensamblados \(GAC\) o en el registro del sistema. Si necesita escribir en la GAC o el registro de la instalación, debe utilizar al instalador de Windows. Para obtener más información, consulta [Preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## Publicar la extensión en la Galería de Visual Studio  
 Puede distribuir la extensión a otras personas simplemente por correo el archivo .vsix o poner en un servidor. Pero es la mejor manera de hacer que el código en manos de mucha gente lo coloque la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Extensiones de la Galería de Visual Studio están disponibles para usuarios de Visual Studio mediante **extensiones y actualizaciones**. Para obtener más información, consulta [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Para obtener un ejemplo completo que muestra cómo cargar una extensión en la Galería de Visual Studio, consulte [Tutorial: Publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Galerías privadas  
 Al desarrollar controles, plantillas y herramientas, se puede compartir con su organización publicándolos en una galería de la intranet privada. Para obtener más información, consulta [Galerías privadas](../extensibility/private-galleries.md).  
  
## Localización de la extensión  
 Si va a liberar su extensión en distintas configuraciones regionales, considere la posibilidad de localizarlo. Para obtener una explicación de lo que implica, consulte [Adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## La extensión de control de versiones y actualizaciones  
 Después de haber publicado su extensión, llegará un momento en que necesite actualizarla. Para obtener información sobre cómo actualizar una extensión que se ha publicado en la Galería de Visual Studio, consulte [Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Puede establecer la extensión para admitir varias versiones de Visual Studio. Para obtener más información, consulta [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica cómo utilizar la plantilla de proyecto VSIX para instalar una plantilla de proyecto personalizadas.|  
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe los componentes de un paquete VSIX.|  
|[Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md)|Proporciona instrucciones paso a paso acerca de cómo empaquetar y publicar una extensión.|  
|[Adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Explica cómo proporcionar el texto localizado para el proceso de instalación mediante archivos extension.vsixlangpack.|  
|[Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md)|Describe cómo actualizar una extensión en el sistema y cómo implementar una actualización en una extensión existente de Visual Studio.|  
|[Cómo: agregar una dependencia a un paquete VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Describe cómo agregar referencias a los paquetes de implementación de VSIX.|  
|[Preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica cómo implementar la extensión con Windows Installer.|  
|[Firma de paquetes VSIX](../extensibility/signing-vsix-packages.md)|Explica cómo firmar los paquetes VSIX.|  
|[Galerías privadas](../extensibility/private-galleries.md)|Explica cómo crear galerías privadas para las extensiones.|  
|[Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Muestra cómo admitir la extensión de varias versiones de Visual Studio.|