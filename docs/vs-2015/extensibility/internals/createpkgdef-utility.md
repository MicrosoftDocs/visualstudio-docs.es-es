---
title: Utilidad CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441488"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toma un archivo .dll para una extensión de Visual Studio como un parámetro y crea un archivo .pkgdef para acompañar el archivo .dll. El archivo .pkgdef contiene toda la información en caso contrario, se escribiría en el registro del sistema cuando se instala la extensión.  
  
> [!NOTE]
> La mayoría de las plantillas de proyecto que se incluyen automáticamente en el SDK de Visual Studio cree los archivos .pkgdef como parte del proceso de compilación. Este documento está destinado a aquellos que quieran crear manualmente paquetes o convertir paquetes existentes para usar la implementación de pkgdef.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumentos  
 /out=`FileName`  
 Obligatorio. Establece el nombre del archivo de salida .pkgdef a`FileName`.  
  
 /codebase  
 Opcional. Registro de las fuerzas con la utilidad de la base de código.  
  
 /Assembly  
 Registro de las fuerzas con la utilidad de ensamblado.  
  
 `AssemblyPath`  
 La ruta de acceso del archivo .dll desde el que desea generar el pkgdef.  
  
## <a name="remarks"></a>Comentarios  
 Implementación de extensión mediante el uso de los archivos .pkgdef reemplaza a los requisitos del registro de versiones anteriores de Visual Studio.  
  
 Los archivos .pkgdef deben instalarse en una de las siguientes ubicaciones: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o %vsinstalldir%\Common7\IDE\Extensions\\. Si la carpeta de instalación es %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, la extensión de Visual Studio reconocerá, pero se deshabilitará de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**. Si la carpeta de instalación es %vsinstalldir%\Common7\IDE\Extensions\\, la extensión está habilitada de forma predeterminada.  
  
> [!NOTE]
> El **extensiones y actualizaciones** herramienta no puede utilizarse para tener acceso a una extensión a menos que se instala como parte de un paquete VSIX.  
  
## <a name="see-also"></a>Vea también  
 [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
