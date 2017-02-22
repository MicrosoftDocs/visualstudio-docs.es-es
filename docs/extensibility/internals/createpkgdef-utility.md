---
title: "Utilidad de CreatePkgDef | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definición de paquete"
  - "crear pkgdef"
  - "pkgdef"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilidad de CreatePkgDef
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Toma un archivo .dll de una extensión de Visual Studio como un parámetro y crea un archivo .pkgdef para acompañar la DLL. El archivo .pkgdef contiene toda la información que de lo contrario, se escribirán en el registro del sistema cuando se instala la extensión.  
  
> [!NOTE]
>  La mayoría de las plantillas de proyecto que se incluyen automáticamente en el SDK de Visual Studio cree archivos .pkgdef como parte del proceso de compilación. Este documento está destinado a aquellos que deseen crear paquetes de forma manual o convertir paquetes existentes para utilizar la implementación pkgdef.  
  
## Sintaxis  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## Argumentos  
 \/ out \=`FileName`  
 Obligatorio. Establece el nombre del archivo de salida .pkgdef a```FileName`.  
  
 \/codebase  
 Opcional. Registro de fuerzas con la utilidad de código base.  
  
 \/Assembly  
 Registro de fuerzas con la utilidad de ensamblado.  
  
 `AssemblyPath`  
 La ruta de acceso del archivo .dll desde el que desea generar el pkgdef.  
  
## Comentarios  
 Implementación de extensión mediante archivos .pkgdef reemplaza a los requisitos del registro de versiones anteriores de Visual Studio.  
  
 Los archivos .pkgdef deben instalarse en una de las siguientes ubicaciones: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ o % vsinstalldir%\\Common7\\IDE\\Extensions\\. Si la carpeta de instalación es %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\, la extensión de Visual Studio reconoce pero se deshabilitará de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**. Si la carpeta de instalación es % vsinstalldir%\\Common7\\IDE\\Extensions\\, la extensión está habilitada de forma predeterminada.  
  
> [!NOTE]
>  El **extensiones y actualizaciones** no se puede utilizar para tener acceso a una extensión a menos que se instala como parte de un paquete VSIX.  
  
## Vea también  
 [Utilidad de CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)