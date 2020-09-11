---
title: Tabla de comandos de Visual Studio (. Archivos de Vsct) | Microsoft Docs
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
ms.openlocfilehash: 24ebac7aee2294d2ad8cee06cd88102bb8d3fd78
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012352"
---
# <a name="visual-studio-command-table-vsct-files"></a>Archivos de tabla de comandos de Visual Studio (.Vsct)
Un archivo de configuración de tabla de comandos es un archivo de texto que describe el conjunto de comandos que contiene un VSPackage. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilador de la tabla de comandos (VSCT) compila archivos de configuración basados en XML (archivos. VSCT) en archivos de salida de tabla de comandos binarios (. CTO). Los archivos. CTO resultantes son los mismos que los creados mediante el compilador de la tabla de comandos (CTC) para compilar los archivos de configuración. CTC. Sin embargo, los archivos. Vsct basados en XML tienen algunas ventajas, como un editor XML y XML IntelliSense.

 Para obtener más información sobre la sintaxis y la semántica de los archivos. Vsct, vea [diseñar una tabla de comandos XML (. Archivos de Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>En esta sección
 [Diseño de archivos de tabla de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Describe cómo diseñar archivos. Vsct.

 [Creación de un archivo .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Compara los métodos para crear un archivo. Vsct. Describe el proceso para crear manualmente un nuevo archivo. Vsct.

## <a name="related-sections"></a>Secciones relacionadas
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Proporciona detalles sobre cada sección del archivo de configuración XML de la tabla de comandos.

 [Configuración de la tabla de comandos (. CTC)](/previous-versions/bb165153(v=vs.100)) presenta información general sobre el formato de archivo. CTC en desuso.

 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Describe la especificación de formato de tabla de comandos.

 [Recursos de VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Describe cómo usar recursos administrados y no administrados en VSPackages administrados.

 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.