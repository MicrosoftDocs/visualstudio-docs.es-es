---
title: Anatomía de un paquete VSIX ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740091"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomía de un paquete VSIX
Un paquete VSIX es un archivo *.vsix* que contiene una o varias extensiones de Visual Studio, junto con los metadatos que Visual Studio usa para clasificar e instalar las extensiones. Esos metadatos se encuentran en el manifiesto VSIX y en el archivo *[Content_Types].xml.* Un paquete VSIX también puede contener uno o varios archivos *Extension.vsixlangpack* para proporcionar texto de instalación localizado y puede contener paquetes VSIX adicionales para instalar dependencias.

 El formato de paquete VSIX sigue el estándar Open Packaging Conventions (OPC). El paquete contiene archivos binarios y archivos auxiliares, junto con un archivo *[Content_Types].xml* y un archivo de manifiesto *.vsix.* Un paquete VSIX puede contener la salida de varios proyectos, o incluso varios paquetes que tienen sus propios manifiestos.

> [!NOTE]
> Los nombres de los archivos incluidos en los paquetes VSIX no deben incluir espacios ni caracteres reservados en identificadores uniformes de recursos (URI), tal como se define en [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>El manifiesto VSIX
 El manifiesto VSIX contiene información sobre la extensión que se va a instalar y sigue el esquema VSX. Para obtener más información, vea Referencia 1.0 del esquema de [extensión VSIX.](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) Para obtener un manifiesto VSIX de ejemplo, vea [Elemento PackageManifest (elemento raíz, esquema VSX).](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187)

 El manifiesto VSIX `extension.vsixmanifest` debe tener nombre cuando se incluye en un archivo .vsix*.

## <a name="the-content"></a>El contenido
 Un paquete VSIX puede contener plantillas, elementos de cuadro de herramientas, VSPackages o cualquier otro tipo de extensión compatible con Visual Studio.

## <a name="language-packs"></a>Paquetes de idioma
 Un paquete VSIX puede contener una o más archivos *Extension.vsixlangpack* para proporcionar texto localizado durante la instalación. Para obtener más información, consulte Localización de [paquetes VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dependencias y referencias
 Un paquete VSIX puede contener otros paquetes VSIX como referencias. Cada uno de estos otros paquetes debe incluir su propio manifiesto VSIX.

 Si un usuario intenta instalar una extensión que tiene dependencias, el instalador comprueba que los ensamblados necesarios están instalados en el sistema de usuario. Si no se encuentran los ensamblados necesarios, **Extensiones y actualizaciones** muestra una lista de los ensamblados que faltan.

 Si el manifiesto de extensión incluye uno o varios elementos [Reference,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **Extensiones y actualizaciones** compara el manifiesto de cada referencia con las extensiones instaladas en el sistema e instala la extensión a la que se hace referencia si aún no está instalada. Si se instala una versión anterior de una extensión a la que se hace referencia, la versión más reciente la reemplaza.

 Si un proyecto de una solución de varios proyectos incluye una referencia a otro proyecto de la misma solución, el paquete VSIX incluye las dependencias de ese proyecto. Puede invalidar este comportamiento haciendo clic en la referencia del proyecto interno y, a `BuiltProjectOutputGroup`continuación, en la ventana **Propiedades,** estableciendo la propiedad Grupos de salida incluidos en **VSIX en** .

 Para incluir archivos DLL satélite de ensamblados a `SatelliteDllsProjectOutputGroup` los que se hace referencia en el paquete VSIX, agregue a la propiedad Grupos de **salida incluidos en VSIX.**

## <a name="installation-location"></a>Ubicación de la instalación
 Durante la instalación, **Extensiones y actualizaciones** busca el contenido del paquete VSIX en una carpeta en *%LocalAppData%-Microsoft-VisualStudio-14.0-Extensions*.

 De forma predeterminada, la instalación solo se aplica al usuario actual, porque *%LocalAppData%* es un directorio específico del usuario. Sin embargo, si establece el elemento `True` [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) del manifiesto en , la extensión se instalará en <em>.. \\ </em>VisualStudioInstallationFolder<em>.Common7,IDE,Extensions</em> y estará disponible para todos los usuarios del equipo.

## <a name="content_typesxml"></a>[Content_Types].xml
 El archivo *[Content_Types].xml* identifica los tipos de archivo en el archivo *.vsix* expandido. Visual Studio usa este archivo durante la instalación del paquete, pero no instala el archivo en sí. Para obtener más información acerca de este archivo, vea [La estructura del archivo [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 El estándar Open Packaging Conventions (OPC) requiere un archivo *[Content_Types].xml.* Para obtener más información acerca de OPC, consulte [OPC: Un nuevo estándar para empaquetar](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) los datos en el sitio Web de MSDN.
