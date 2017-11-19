---
title: Utilidad CreatePkgDef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32e9c8ffa2a9ca2bba889436f37cc4f5c3d188bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="createpkgdef-utility"></a>Utilidad de CreatePkgDef
Toma un archivo .dll para una extensión de Visual Studio como un parámetro y crea un archivo .pkgdef para acompañar la DLL. El archivo .pkgdef contiene toda la información que en caso contrario, se escribirán en el registro del sistema cuando se instala la extensión.  
  
> [!NOTE]
>  La mayoría de las plantillas de proyecto que se incluyen automáticamente en el SDK de Visual Studio cree archivos .pkgdef como parte del proceso de compilación. Este documento está destinado a las personas que deseen crear paquetes de forma manual o convertir los paquetes existentes para usar .pkgdef implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumentos  
 / out =`FileName`  
 Obligatorio. Establece el nombre del archivo de salida .pkgdef a`FileName`.  
  
 /codebase  
 Opcional. Registro de las fuerzas con la utilidad de código base.  
  
 /Assembly  
 Registro de las fuerzas con la utilidad de ensamblado.  
  
 `AssemblyPath`  
 La ruta de acceso del archivo .dll desde el que desea generar el .pkgdef.  
  
## <a name="remarks"></a>Comentarios  
 Implementación de extensión mediante archivos .pkgdef reemplaza a los requisitos del registro de versiones anteriores de Visual Studio.  
  
 Los archivos .pkgdef deben instalarse en una de las siguientes ubicaciones: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o %vsinstalldir%\Common7\IDE\Extensions\\. Si la carpeta de instalación es %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, la extensión se reconocerán por Visual Studio, pero se deshabilitará de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**. Si la carpeta de instalación es %vsinstalldir%\Common7\IDE\Extensions\\, la extensión está habilitada de forma predeterminada.  
  
> [!NOTE]
>  El **extensiones y actualizaciones** herramienta no se puede usar para tener acceso a una extensión a menos que se instala como parte de un paquete VSIX.  
  
## <a name="see-also"></a>Vea también  
 [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)