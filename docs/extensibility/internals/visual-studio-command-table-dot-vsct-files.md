---
title: Tabla de comandos de Visual Studio (. Vsct) Archivos de la casa de la página de música de Vsct (Vs Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704025"
---
# <a name="visual-studio-command-table-vsct-files"></a>Archivos de tabla de comandos de Visual Studio (.Vsct)
Un archivo de configuración de tabla de comandos es un archivo de texto que describe el conjunto de comandos que contiene un VSPackage. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilador de tabla de comandos (VSCT) compila archivos de configuración basados en XML (archivos .vsct) en archivos de salida de tabla de comandos binarios (.cto). Los archivos .cto resultantes son los mismos que los que se crean mediante el compilador de tabla de comandos (CTC) para compilar archivos de configuración .ctc. Sin embargo, los archivos .vsct basados en XML tienen algunas ventajas, como un editor XML e Xml IntelliSense.

 Para obtener más información sobre la sintaxis y la semántica de los archivos .vsct, consulte Diseño de la tabla de [comandos XML (. Vsct) Archivos](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>En esta sección
 [Diseño de archivos de tabla de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Describe cómo diseñar archivos .vsct.

 [Creación de un archivo .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Compara los métodos para crear un archivo .vsct. Describe el proceso para crear manualmente un nuevo archivo .vsct.

## <a name="related-sections"></a>Secciones relacionadas
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Proporciona detalles sobre cada sección del archivo de configuración XML de la tabla de comandos.

 Configuración de la [tabla de comandos (. Ctc) Archivos](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Presenta una visión general del formato de archivo .ctc en desuso.

 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Describe la especificación de formato de tabla de comandos.

 [Recursos de VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Describe cómo usar recursos administrados y no administrados en VSPackages administrados.

 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.
