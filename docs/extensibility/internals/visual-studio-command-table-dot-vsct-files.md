---
title: "Tabla de comandos de Visual Studio (. Archivos de Vsct) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivos VSCT, información general"
  - "Comando tabla Configuración los archivos Visual Studio (VSCT), información general"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Tabla de comandos de Visual Studio (. Archivos de Vsct)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un archivo de configuración de la tabla de comandos es un archivo de texto que describe el conjunto de comandos que contiene un paquete VSPackage. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando compilador tabla \(VSCT\) compila los archivos de configuración basado en XML \(archivos .vsct\) en archivos de salida \(.cto\) de tabla de comando binary. Los archivos resultantes .cto son los mismos que los que se crean mediante el compilador de tabla \(CTC\) del comando para compilar los archivos de configuración .ctc. Sin embargo, los archivos .vsct basado en XML tiene algunas ventajas, como un editor XML y XML IntelliSense.  
  
 Para obtener más información acerca de la sintaxis y semántica de los archivos .vsct, vea [Diseñar la tabla de comandos XML \(. Archivos de Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## En esta sección  
 [Diseñar la tabla de comandos XML \(. Archivos de Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Describe cómo diseñar los archivos .vsct.  
  
 [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compara los métodos para crear un archivo de vsct. Describe el proceso para crear manualmente un nuevo archivo de vsct.  
  
## Secciones relacionadas  
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Proporciona detalles sobre cada sección del archivo de configuración XML de tabla de comandos.  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/es-es/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Ofrece información general sobre el formato de archivo .ctc en desuso.  
  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Describe la especificación de formato de la tabla de comandos.  
  
 [Recursos de VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Describe cómo utilizar los recursos administrados y de VSPackages administrado.  
  
 [Barras de herramientas, menús y comandos](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluye menús, barras de herramientas y cuadros combinados de comando.