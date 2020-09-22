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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842411"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toma un archivo. dll para una extensión de Visual Studio como parámetro y crea un archivo. pkgdef para acompañar a. dll. El archivo. pkgdef contiene toda la información que, de lo contrario, se escribiría en el registro del sistema cuando se instala la extensión.  
  
> [!NOTE]
> La mayoría de las plantillas de proyecto que se incluyen en el SDK de Visual Studio crean automáticamente archivos. pkgdef como parte del proceso de compilación. Este documento está destinado a aquellos que desean crear paquetes manualmente, o convertir paquetes existentes para usar la implementación de. pkgdef.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumentos  
 /out =`FileName`  
 Obligatorio. Establece el nombre del archivo de salida. pkgdef en `FileName` .  
  
 /codebase  
 Opcional. Fuerza el registro con la utilidad codebase.  
  
 /Assembly  
 Fuerza el registro con la utilidad de ensamblado.  
  
 `AssemblyPath`  
 La ruta de acceso del archivo. dll desde el que desea generar el archivo. pkgdef.  
  
## <a name="remarks"></a>Notas  
 La implementación de extensiones mediante archivos. pkgdef reemplaza los requisitos del registro de versiones anteriores de Visual Studio.  
  
 Los archivos. pkgdef deben instalarse en una de las siguientes ubicaciones:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o%vsinstalldir%\Common7\IDE\Extensions \\ . Si la carpeta de instalación es%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , Visual Studio reconocerá la extensión, pero se deshabilitará de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**. Si la carpeta de instalación es%vsinstalldir%\Common7\IDE\Extensions \\ , la extensión está habilitada de forma predeterminada.  
  
> [!NOTE]
> No se puede usar la herramienta **extensiones y actualizaciones** para tener acceso a una extensión a menos que se instale como parte de un paquete VSIX.  
  
## <a name="see-also"></a>Consulte también  
 [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
