---
title: "Envío de extensiones de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf74110cf42daa51521cc7ea706c1b951b23deb8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="shipping-visual-studio-extensions"></a>Extensiones de Visual Studio de envío
Una vez haya terminado de desarrollar la extensión, puede instalar en otros equipos, compartirlo con amigos y compañeros de trabajo o publicarlo en el catálogo de soluciones de Visual Studio. En esta sección se explica todo lo que debe hacer para publicar y mantener la extensión: trabajar con archivos .vsix, publicación, la localización y la actualización.  
  
## <a name="working-with-vsix-extensions"></a>Trabajar con las extensiones VSIX  
 Puede crear un extensiones VSIX creando un proyecto de VSIX en blanco y agregar plantillas de elementos diferentes a ella. Para obtener más información, consulte [plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md).  
  
 Puede usar el formato VSIX para empaquetar plantillas de proyecto, elemento de componentes de plantillas, paquetes VSPackage, Managed Extensibility Framework (MEF), **cuadro de herramientas** controles, ensamblados y tipos personalizados (Esto incluye las páginas de inicio personalizada). El formato VSIX usa una implementación basada en archivos. Para obtener más información acerca de los paquetes VSIX, vea [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 El formato VSIX no admite la instalación de fragmentos de código. No admite ciertas otros escenarios como la escritura en la memoria caché Global de ensamblados (GAC) o en el registro del sistema. Si tiene que escribir en la GAC o el registro en la instalación, debe usar el programa de instalación de Windows. Para obtener más información, consulte [preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión en el catálogo de soluciones de Visual Studio  
 Puede distribuir la extensión a otras personas simplemente por correo el archivo .vsix o poner en un servidor. Pero es la mejor manera de hacer que el código en manos de una gran cantidad de personas lo coloque la [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Extensiones de Visual Studio Marketplace están disponibles para los usuarios de Visual Studio a través de **extensiones y actualizaciones**. Para obtener más información, consulte [buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Para obtener un ejemplo completo que muestra cómo cargar una extensión en Visual Studio Marketplace, vea [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Private Galleries  
 Al desarrollar controles, plantillas y herramientas, puede compartirlos con su organización publicándolas en una galería privada de la intranet. Para obtener más información, consulte [ensamblados privados](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Localizar la extensión  
 Si va a publicar la extensión en distintas configuraciones regionales, considere la posibilidad de localizarlo. Para obtener una explicación de las implicaciones, consulte [adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>La extensión de control de versiones y actualizaciones  
 Después de haber publicado la extensión, llegará un momento en que necesite para actualizarlo y. Para obtener más información sobre cómo actualizar una extensión que se ha publicado en el catálogo de soluciones de Visual Studio, consulte [Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Puede establecer la extensión para admitir varias versiones de Visual Studio. Para obtener más información, consulte [compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica cómo usar la plantilla de proyecto VSIX para instalar una plantilla de proyecto personalizado.|  
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe los componentes de un paquete VSIX.|  
|[Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)|Proporciona instrucciones paso a paso acerca de cómo empaquetar y publicar una extensión.|  
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Explica cómo proporcionar el texto localizado para el proceso de instalación mediante el uso de archivos extension.vsixlangpack.|  
|[Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md)|Describe cómo actualizar una extensión en el sistema y cómo implementar una actualización a una extensión de Visual Studio existente.|  
|[Adición de una dependencia a un paquete VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Describe cómo agregar referencias a los paquetes de implementación de VSIX.|  
|[Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica cómo implementar la extensión con Windows Installer.|  
|[Firma de paquetes VSIX](../extensibility/signing-vsix-packages.md)|Explica cómo firmar paquetes VSIX.|  
|[Galerías privadas](../extensibility/private-galleries.md)|Explica cómo crear galerías privadas para las extensiones.|  
|[Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Muestra cómo hacer que la compatibilidad con extensiones de varias versiones de Visual Studio.|
|[Ubicación de Visual Studio](locating-visual-studio.md)|Describe cómo buscar instancias de Visual Studio para la implementación de extensión personalizada.|
