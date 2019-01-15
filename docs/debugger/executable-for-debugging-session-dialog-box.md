---
title: Archivo ejecutable para el cuadro de diálogo de la sesión de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 681a1b150058c66be42caca7241b9054151098f8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858797"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Archivo ejecutable para sesión de depuración (cuadro de diálogo)
Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable. Visual Studio no puede iniciar un archivo DLL directamente. En su lugar, iniciará el archivo ejecutable especificado. Puede depurar el archivo DLL cuando lo llame el archivo ejecutable.  
  
 **Nombre del archivo ejecutable**  
 Escriba el nombre de ruta de acceso a un archivo ejecutable que llama al archivo DLL que está depurando.  
  
 **Dirección URL del proyecto (solo servidor ATL)**  
 Si está depurando un archivo DLL de un servidor ATL, escriba la dirección URL en la que se puede encontrar el proyecto.  
  
 Una vez escrita, esta configuración se almacena en las Páginas de propiedades del proyecto, por lo que no hace falta volver a escribirla para las siguientes sesiones de depuración. Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores. Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, vea [Depurar archivos DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)