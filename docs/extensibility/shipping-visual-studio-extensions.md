---
title: Envío de extensiones de Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700117"
---
# <a name="shipping-visual-studio-extensions"></a>Suministro de extensiones de Visual Studio
Una vez que haya terminado de desarrollar la extensión, puede instalarla en otros equipos, compartirla con sus amigos y compañeros de trabajo o publicarla en Visual Studio Marketplace. En esta sección te explicamos todas las cosas que necesitas hacer para publicar y mantener tu extensión: trabajar con archivos .vsix, publicar, localizar y actualizar.

## <a name="working-with-vsix-extensions"></a>Trabajar con extensiones VSIX
 Puede crear una extensión VSIX creando un proyecto VSIX en blanco y, a continuación, agregándole diferentes plantillas de elementos. Para obtener más información, consulte [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

 Puede usar el formato VSIX para empaquetar plantillas de proyecto, plantillas de elementos, VSPackages, componentes de Managed Extensibility Framework (MEF), controles de **Toolbox,** ensamblados y tipos personalizados (esto incluye páginas de inicio personalizadas para Visual Studio 2017). El formato VSIX utiliza la implementación basada en archivos. Para obtener más información acerca de los paquetes VSIX, consulte [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 El formato VSIX no admite la instalación de fragmentos de código. Tampoco admite otros escenarios, como escribir en la caché global de ensamblados (GAC) o en el registro del sistema. Si necesita escribir en la GAC o en el registro de la instalación, debe usar Windows Installer. Para obtener más información, consulte [Preparación de extensiones para](../extensibility/preparing-extensions-for-windows-installer-deployment.md)la implementación de Windows Installer .

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publicación de la extensión en Visual Studio Marketplace
 Puede distribuir su extensión a otras personas simplemente enviándoles por correo el archivo .vsix o poniéndolo en un servidor. Pero la mejor manera de poner el código en manos de mucha gente es ponerlo en [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Las extensiones de Visual Studio Marketplace están disponibles para los usuarios de Visual Studio a través de **Extensiones y actualizaciones.** Para obtener más información, vea [Buscar y usar extensiones](../ide/finding-and-using-visual-studio-extensions.md)de Visual Studio .

 Para obtener un ejemplo completo que muestra cómo cargar una extensión en Visual Studio Marketplace, vea [Tutorial: publicación](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)de una extensión de Visual Studio .

## <a name="private-galleries"></a>Private Galleries
 A medida que desarrolla controles, plantillas y herramientas, puede compartirlas con su organización publicándolos en una galería privada en la intranet. Para obtener más información, consulte [Galerías privadas](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localizar la extensión
 Si está planeando liberar la extensión en diferentes configuraciones regionales, debe considerar la posibilidad de localizarla. Para obtener una explicación de lo que implica, vea [Localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Actualización y control de versiones de la extensión
 Después de publicar la extensión, llegará un momento en el que necesite actualizarla. Para averiguar cómo actualizar una extensión que se ha publicado en Visual Studio Marketplace, vea [Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md).

 Puede establecer la extensión para admitir varias versiones de Visual Studio. Para obtener más información, vea [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica cómo usar la plantilla de proyecto VSIX para instalar una plantilla de proyecto personalizada.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe los componentes de un paquete VSIX.|
|[Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)|Proporciona instrucciones paso a paso sobre cómo empaquetar y publicar una extensión.|
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Explica cómo proporcionar texto localizado para el proceso de instalación mediante archivos extension.vsixlangpack.|
|[Cómo actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md)|Describe cómo actualizar una extensión en el sistema y cómo implementar una actualización en una extensión de Visual Studio existente.|
|[Adición de una dependencia a un paquete VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Describe cómo agregar referencias a paquetes de implementación VSIX.|
|[Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica cómo implementar la extensión con Windows Installer.|
|[Firma de paquetes VSIX](../extensibility/signing-vsix-packages.md)|Explica cómo firmar paquetes VSIX.|
|[Galerías privadas](../extensibility/private-galleries.md)|Explica cómo crear galerías privadas para extensiones.|
|[Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Muestra cómo hacer que la extensión admita varias versiones de Visual Studio.|
|[Búsqueda de Visual Studio](locating-visual-studio.md)|Describe cómo buscar instancias de Visual Studio para la implementación de extensiones personalizadas.|
