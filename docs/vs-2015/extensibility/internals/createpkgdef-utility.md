---
title: Utilidad CreatePkgDef | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 492e34c92019de7f3c0921b853d103252e09b996
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782653"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toma un archivo .dll para una extensión de Visual Studio como un parámetro y crea un archivo .pkgdef para acompañar el archivo .dll. El archivo .pkgdef contiene toda la información en caso contrario, se escribiría en el registro del sistema cuando se instala la extensión.  
  
> [!NOTE]
>  La mayoría de las plantillas de proyecto que se incluyen automáticamente en el SDK de Visual Studio cree los archivos .pkgdef como parte del proceso de compilación. Este documento está destinado a aquellos que quieran crear manualmente paquetes o convertir paquetes existentes para usar la implementación de pkgdef.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumentos  
 / out =`FileName`  
 Requerido. Establece el nombre del archivo de salida .pkgdef a`FileName`.  
  
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
>  El **extensiones y actualizaciones** herramienta no puede utilizarse para tener acceso a una extensión a menos que se instala como parte de un paquete VSIX.  
  
## <a name="see-also"></a>Vea también  
 [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

