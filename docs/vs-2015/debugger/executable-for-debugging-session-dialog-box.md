---
title: Archivo ejecutable para el cuadro de diálogo de la sesión de depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26a7eabe624b75c2b9ded6d14e6bf7c92505ba2d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753620"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Archivo ejecutable para sesión de depuración (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable. Visual Studio no puede iniciar un archivo DLL directamente. En su lugar, iniciará el archivo ejecutable especificado. Puede depurar el archivo DLL cuando lo llame el archivo ejecutable.  
  
 **Nombre del archivo ejecutable**  
 Escriba el nombre de ruta de acceso a un archivo ejecutable que llama al archivo DLL que está depurando.  
  
 **Dirección URL donde puede ser el proyecto de acceso (sólo servidor ATL)**  
 Si está depurando un archivo DLL de un servidor ATL, escriba la dirección URL en la que se puede encontrar el proyecto.  
  
 Una vez escrita, esta configuración se almacena en las Páginas de propiedades del proyecto, por lo que no hace falta volver a escribirla para las siguientes sesiones de depuración. Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores. Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, consulte [depurar archivos DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)



