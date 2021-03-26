---
title: Anatomía de un paquete VSIX | Microsoft Docs
description: Obtenga información sobre el contenido de un paquete VSIX en Visual Studio, un archivo que contiene una o varias extensiones de Visual Studio y un archivo de manifiesto de metadatos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b3775509e330ad55a2531a9e42a7cca93c50a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097505"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomía de un paquete VSIX
Un paquete VSIX es un archivo *. vsix* que contiene una o varias extensiones de Visual Studio, junto con los metadatos que Visual Studio usa para clasificar e instalar las extensiones. Esos metadatos se incluyen en el manifiesto de VSIX y en el archivo *[Content_Types]. XML* . Un paquete VSIX también puede contener uno o más archivos *Extension. vsixlangpack* para proporcionar el texto de instalación localizado y puede contener paquetes VSIX adicionales para instalar las dependencias.

 El formato de paquete VSIX sigue el estándar de convenciones de empaquetado abierto (OPC). El paquete contiene archivos binarios y archivos auxiliares, junto con un archivo *[Content_Types]. XML* y un archivo de manifiesto *. vsix* . Un paquete VSIX puede contener la salida de varios proyectos, o incluso varios paquetes que tienen sus propios manifiestos.

> [!NOTE]
> Los nombres de los archivos incluidos en los paquetes VSIX no deben incluir espacios ni caracteres que estén reservados en los identificadores uniformes de recursos (URI), tal como se define en [ \[ RFC2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>El manifiesto de VSIX
 El manifiesto de VSIX contiene información sobre la extensión que se va a instalar y sigue el esquema VSX. Para obtener más información, vea [Referencia del esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110)). Para obtener un ejemplo de manifiesto VSIX, vea [elemento PackageManifest (elemento root, esquema VSX)](/previous-versions/dd393754(v=vs.110)).

 El manifiesto de VSIX se debe denominar `extension.vsixmanifest` cuando se incluye en un archivo ^. vsix *.

## <a name="the-content"></a>El contenido
 Un paquete VSIX puede contener plantillas, elementos del cuadro de herramientas, VSPackages o cualquier otro tipo de extensión compatible con Visual Studio.

## <a name="language-packs"></a>Paquetes de idioma
 Un paquete VSIX puede contener uno o más archivos *Extension. vsixlangpack* para proporcionar texto localizado durante la instalación. Para obtener más información, consulte [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dependencias y referencias
 Un paquete VSIX puede contener otros paquetes VSIX como referencias. Cada uno de estos otros paquetes debe incluir su propio manifiesto de VSIX.

 Si un usuario intenta instalar una extensión que tiene dependencias, el instalador comprueba que los ensamblados necesarios están instalados en el sistema del usuario. Si no se encuentran los ensamblados necesarios, **extensions and updates** muestra una lista de los ensamblados que faltan.

 Si el manifiesto de la extensión incluye uno o más elementos de [referencia](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) , las **extensiones y actualizaciones** comparan el manifiesto de cada referencia con las extensiones que están instaladas en el sistema e instala la extensión a la que se hace referencia si aún no está instalada. Si se instala una versión anterior de una extensión a la que se hace referencia, la versión más reciente la reemplaza.

 Si un proyecto de una solución de varios proyectos incluye una referencia a otro proyecto en la misma solución, el paquete VSIX incluye las dependencias de ese proyecto. Puede invalidar este comportamiento seleccionando la referencia del proyecto interno y, a continuación, en la ventana **propiedades** , estableciendo los **grupos de salida incluidos en** la propiedad VSIX en `BuiltProjectOutputGroup` .

 Para incluir los archivos dll satélite de los ensamblados a los que se hace referencia en el paquete VSIX, agregue `SatelliteDllsProjectOutputGroup` a los **grupos de salida incluidos en** la propiedad VSIX.

## <a name="installation-location"></a>Ubicación de la instalación
 Durante la instalación, **extensions and updates** busca el contenido del paquete VSIX en una carpeta en *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 De forma predeterminada, la instalación solo se aplica al usuario actual, ya que *% LocalAppData%* es un directorio específico del usuario. Sin embargo, si establece el elemento [AllUsers](/previous-versions/ee191547(v=vs.110)) del manifiesto en `True` , la extensión se instalará en <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> y estará disponible para todos los usuarios del equipo.

## <a name="content_typesxml"></a>[Content_Types]. XML
 El archivo *[Content_Types]. XML* identifica los tipos de archivo en el archivo *. vsix* expandido. Visual Studio usa este archivo durante la instalación del paquete, pero no instala el propio archivo. Para obtener más información acerca de este archivo, consulte [la estructura del archivo [Content_types]. XML](the-structure-of-the-content-types-dot-xml-file.md).

 El estándar de convenciones de empaquetado abierto (OPC) requiere un archivo *[Content_Types]. XML* . Para obtener más información acerca de OPC, consulte [OPC: un nuevo estándar para empaquetar los datos](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) en el sitio web de MSDN.