---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cbf9608bc4f476599676b27f12bc125fd170fc71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211008"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Especifica un archivo que se va a almacenar y muestra los errores al ejecutar, compilar, recompilar o implementar una solución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argumentos  
 `FileName`  
 Requerido. Ruta de acceso y nombre del archivo que va a recibir los errores al compilar un ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica un nombre de archivo que no existe, se crea automáticamente el archivo. Si el archivo ya existe, los resultados se anexan al contenido existente del archivo.  
  
 Los errores de compilación de la línea de comandos se muestran en la ventana **Comando** y la vista Generador de soluciones de la ventana **Salida**. Esta opción es útil si está ejecutando generaciones desatendidas y necesita ver los resultados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se ejecuta `MySolution` y se escriben los errores en el archivo `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)



