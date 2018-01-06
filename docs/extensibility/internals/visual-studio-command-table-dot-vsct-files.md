---
title: Tabla de comandos de Visual Studio (. Archivos Vsct) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabla de comandos de Visual Studio (. Archivos Vsct)
Un archivo de configuración de la tabla de comandos es un archivo de texto que describe el conjunto de comandos que contiene un paquete VSPackage. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando compilador de tabla (VSCT) compila los archivos de configuración basado en XML (archivos .vsct) en archivos de salida (.cto) de tabla de comando binary. Los archivos .cto resultantes son los mismos que los que se crean mediante el compilador de tabla (CTC) del comando para compilar archivos de configuración de .ctc. Sin embargo, los archivos de vsct basado en XML tiene algunas ventajas, como un editor XML y XML IntelliSense.  
  
 Para obtener más información sobre la sintaxis y semántica de los archivos de vsct, consulte [diseñar la tabla de comandos de XML (. Archivos Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>En esta sección  
 [Diseño de archivos de tabla de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Describe cómo diseñar los archivos de vsct.  
  
 [Creación de un archivo .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compara los métodos para crear un archivo .vsct. Describe el proceso para crear manualmente un nuevo archivo de vsct.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Proporciona detalles sobre cada sección del archivo de configuración de comando tabla XML.  
  
 [Configuración de la tabla de comandos (. Archivos de CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Presenta información general sobre el formato de archivo .ctc en desuso.  
  
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Describe la especificación de formato de tabla de comandos.  
  
 [Recursos de VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Describe cómo utilizar los recursos no administrados y no administrados en VSPackages administrado.  
  
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.