---
title: /Upgrade (devenv.exe) | Microsoft Docs
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
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79a00da92ac2da6eb37fa1eef90fa112598d23f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264967"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Actualiza el archivo de solución y todos sus archivos de proyecto, o el archivo de proyecto especificado, a los formatos actuales de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para estos archivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argumentos  
 `SolutionFile`  
 Necesario si va a actualizar una solución completa y sus proyectos. Ruta de acceso y nombre de un archivo de solución. Se puede escribir solo el nombre del archivo de solución o una ruta de acceso completa y el nombre del archivo de solución. Si la carpeta o el archivo especificados no existen todavía, se crean.  
  
 `ProjectFile`  
 Necesario si va a actualizar un único proyecto. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Se puede escribir solo el nombre del archivo de proyecto o una ruta de acceso completa y el nombre del archivo de proyecto. Si la carpeta o el archivo especificados no existen todavía, se crean.  
  
## <a name="remarks"></a>Comentarios  
 Se crean automáticamente copias de seguridad y se copian en un directorio denominado Backup que se crea en el directorio actual.  
  
 Se deben desproteger las soluciones o los proyectos bajo el control de código fuente antes de poderse actualizar.  
  
 Al utilizar el modificador `/upgrade` no se inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Los resultados de la actualización se pueden ver en el informe de actualización para el lenguaje de desarrollo de la solución o el proyecto. No se devuelve ninguna información de error o de uso. Para obtener más información sobre cómo actualizar proyectos en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consulte [Cómo: solucionar problemas de incorrecta Visual Studio actualizaciones de proyecto](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se actualiza un archivo de solución denominado "MyProject.sln" en la carpeta predeterminada para las soluciones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)



