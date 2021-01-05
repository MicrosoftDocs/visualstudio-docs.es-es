---
title: Envío de extensiones de Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo publicar y mantener la extensión del SDK de Visual Studio, incluido el trabajo con archivos. vsix, la publicación, la localización y la actualización.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 812fc4f4e2f8dcf54876e2764f0c091f16348496
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716008"
---
# <a name="shipping-visual-studio-extensions"></a>Suministro de extensiones de Visual Studio
Una vez que haya terminado de desarrollar la extensión, puede instalarla en otras máquinas, compartirla con sus amigos y compañeros o publicarla en el Visual Studio Marketplace. En esta sección se explican todas las cosas que debe hacer para publicar y mantener la extensión: trabajar con archivos. vsix, publicar, localizar y actualizar.

## <a name="working-with-vsix-extensions"></a>Trabajar con extensiones VSIX
 Puede crear una extensión VSIX mediante la creación de un proyecto VSIX en blanco y, a continuación, agregarle distintas plantillas de elementos. Para obtener más información, vea [plantilla de Proyecto VSIX](../extensibility/vsix-project-template.md).

 Puede usar el formato VSIX para empaquetar plantillas de proyecto, plantillas de elementos, VSPackages, componentes de Managed Extensibility Framework (MEF), controles del **cuadro de herramientas** , ensamblados y tipos personalizados (esto incluye páginas de inicio personalizadas para Visual Studio 2017). El formato VSIX usa la implementación basada en archivos. Para obtener más información sobre los paquetes VSIX, vea [anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 El formato VSIX no admite la instalación de fragmentos de código. Tampoco admite otros escenarios, como la escritura en la caché de ensamblados global (GAC) o en el registro del sistema. Si tiene que escribir en la GAC o en el registro de la instalación, debe usar el Windows Installer. Para obtener más información, consulte [preparación de extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publicar la extensión en el Visual Studio Marketplace
 Puede distribuir la extensión a otras personas simplemente enviándoles el archivo. vsix o colocando en un servidor. Pero la mejor manera de obtener el código en manos de muchos usuarios es colocarlo en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Visual Studio Marketplace extensiones están disponibles para los usuarios de Visual Studio a través **de extensiones y actualizaciones**. Para más información, vea [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Para obtener un ejemplo completo que muestra cómo cargar una extensión en el Visual Studio Marketplace, vea [Tutorial: publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 A medida que desarrolla controles, plantillas y herramientas, puede compartirlos con su organización si los publica en una galería privada de la intranet. Para obtener más información, vea [galerías privadas](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localización de la extensión
 Si tiene previsto publicar la extensión en distintas configuraciones regionales, considere la posibilidad de localizarla. Para obtener una explicación de lo que implica, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Actualización y control de versiones de la extensión
 Después de publicar la extensión, habrá una hora en la que necesita actualizarla. Para averiguar cómo actualizar una extensión Publicada en el Visual Studio Marketplace, consulte [Cómo: actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md).

 Puede establecer la extensión para que admita varias versiones de Visual Studio. Para obtener más información, vea [compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica cómo usar la plantilla de Proyecto VSIX para instalar una plantilla de proyecto personalizada.|
|[Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Describe los componentes de un paquete VSIX.|
|[Plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md)|Proporciona instrucciones paso a paso acerca de cómo empaquetar y publicar una extensión.|
|[Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)|Explica cómo proporcionar texto localizado para el proceso de instalación mediante archivos. vsixlangpack de extensión.|
|[Cómo actualizar una extensión](../extensibility/how-to-update-a-visual-studio-extension.md)|Describe cómo actualizar una extensión en el sistema y cómo implementar una actualización en una extensión de Visual Studio existente.|
|[Adición de una dependencia a un paquete VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Describe cómo agregar referencias a los paquetes de implementación de VSIX.|
|[Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica cómo implementar la extensión con Windows Installer.|
|[Firma de paquetes VSIX](../extensibility/signing-vsix-packages.md)|Explica cómo firmar paquetes VSIX.|
|[Galerías privadas](../extensibility/private-galleries.md)|Explica cómo crear galerías privadas para las extensiones.|
|[Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Muestra cómo hacer que la extensión admita varias versiones de Visual Studio.|
|[Búsqueda de Visual Studio](locating-visual-studio.md)|Describe cómo buscar instancias de Visual Studio para la implementación de extensión personalizada.|
