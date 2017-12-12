---
title: -Clean (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd4b344860190d0dcfc01adf6ccf553d34c5b038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
Limpia todos los archivos intermedios y directorios de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## <a name="arguments"></a>Argumentos  
 `FileName`  
 Obligatorio. Ruta de acceso completa y nombre del archivo de solución o archivo del proyecto.  
  
 /project `ProjName`  
 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto) o la ruta de acceso completa y el nombre del archivo del proyecto.  
  
 /projectconfig `ProjConfigName`  
 Opcional. Nombre de una configuración de compilación de proyecto que se usará para limpiar el `/project` mencionado.  
  
## <a name="remarks"></a>Comentarios  
 Este modificador realiza la misma función que el comando de menú **Limpiar solución** en el entorno de desarrollo integrado (IDE).  
  
 Escriba las cadenas que incluyen espacios entre comillas dobles.  
  
 Se puede mostrar información de resumen de las limpiezas y compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## <a name="example"></a>Ejemplo  
 En el primer ejemplo, se limpia la solución `MySolution`, mediante la configuración predeterminada especificada en el archivo de solución.  
  
 En el segundo ejemplo, se limpia el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Debug` en la configuración de solución `Debug` de `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)