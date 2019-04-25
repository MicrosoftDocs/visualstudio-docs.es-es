---
title: Envío de extensiones de Visual Studio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea2217614ed27a98281cce7a3d34b72f74ae803
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796600"
---
# <a name="shipping-visual-studio-extensions"></a>Suministro de extensiones de Visual Studio
Cuando haya terminado de desarrollar la extensión, puede instalarla en otros equipos, compartirlo con sus amigos y compañeros de trabajo o publicarlo en Visual Studio Marketplace. En esta sección se explican todas las cosas que debe hacer para publicar y mantener su extensión: trabajar con archivos .vsix, publicar, localizar y actualizar.

## <a name="working-with-vsix-extensions"></a>Trabajar con las extensiones VSIX
 Puede crear un extensiones VSIX creando un proyecto de VSIX en blanco y, a continuación, agregar plantillas de elementos diferentes al mismo. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

 Puede usar el formato VSIX para empaquetar las plantillas de proyecto, los componentes de plantillas, paquetes VSPackage, Managed Extensibility Framework (MEF), de elemento **cuadro de herramientas** controles, ensamblados y tipos personalizados (Esto incluye las páginas de inicio personalizada para el objeto Visual Studio de 2017). El formato VSIX usa la implementación basada en archivos. Para obtener más información acerca de los paquetes VSIX, vea [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 El formato VSIX no es compatible con la instalación de fragmentos de código. No admite algunos otros escenarios como la escritura a la caché de ensamblados Global (GAC) o en el registro del sistema. Si tiene que escribir en la GAC o en el registro en la instalación, debe usar al instalador de Windows. Para obtener más información, consulte [preparar las extensiones para Windows Installer implementación](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión de Visual Studio Marketplace
 Puede distribuir la extensión a otras personas simplemente por correo el archivo .vsix o poner en un servidor. Pero es la mejor manera de obtener el código en manos de mucha gente colocarlo en la [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Las extensiones de Visual Studio Marketplace están disponibles para los usuarios de Visual Studio a través de **extensiones y actualizaciones**. Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Para obtener un ejemplo completo que muestra cómo cargar una extensión en Visual Studio Marketplace, consulte [Tutorial: Publicación de una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Desarrollar controles, plantillas y herramientas, puede compartirlos con su organización puedan verlas en una galería privada de la intranet. Para más información, vea [Private Galleries](../extensibility/private-galleries.md) (Galerías privadas).

## <a name="localizing-your-extension"></a>Localización de la extensión
 Si va a liberar su extensión en distintas configuraciones regionales, considere la posibilidad de localizarla. Para obtener una explicación de lo que implica, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>La extensión de control de versiones y actualización
 Después de haber publicado su extensión, llegará un momento en que necesite para actualizarlo. Para averiguar cómo actualizar una extensión que se ha publicado en Visual Studio Marketplace, consulte [Cómo: Actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md).

 Puede establecer la extensión para admitir varias versiones de Visual Studio. Para obtener más información, consulte [que admiten varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica cómo usar la plantilla de proyecto VSIX para instalar una plantilla de proyecto personalizado.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe los componentes de un paquete VSIX.|
|[Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)|Proporciona instrucciones paso a paso sobre cómo empaquetar y publicar una extensión.|
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Explica cómo proporcionar el texto localizado para el proceso de instalación mediante el uso de archivos extension.vsixlangpack.|
|[Cómo: Actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md)|Describe cómo actualizar una extensión en el sistema y cómo implementar una actualización en una extensión de Visual Studio existente.|
|[Cómo: Agregar una dependencia a un paquete VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Describe cómo agregar referencias a paquetes de implementación de VSIX.|
|[Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica cómo implementar la extensión con Windows Installer.|
|[Firma de paquetes VSIX](../extensibility/signing-vsix-packages.md)|Explica cómo firmar paquetes VSIX.|
|[Galerías privadas](../extensibility/private-galleries.md)|Explica cómo crear galerías privadas para las extensiones.|
|[Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Muestra cómo tener soporte técnico de su extensión de varias versiones de Visual Studio.|
|[Localización de Visual Studio](locating-visual-studio.md)|Describe cómo buscar instancias de Visual Studio para la implementación de extensión personalizada.|
