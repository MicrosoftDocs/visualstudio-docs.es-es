---
title: Ejecutable para la sesión de depuración (cuadro de diálogo) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14d4ac95aae860e0750af66aec6adb2969434f11
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211046"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Archivo ejecutable para sesión de depuración (cuadro de diálogo)

Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable. Visual Studio no puede iniciar un archivo DLL directamente. En su lugar, Visual Studio inicia el archivo ejecutable especificado. Puede depurar el archivo DLL cuando el archivo ejecutable lo llama.

 **Nombre del archivo ejecutable** Escriba el nombre de la ruta de acceso a un archivo ejecutable que llama al archivo DLL que está depurando.

 **Dirección URL a la que se puede tener acceso al proyecto (solo en el servidor ATL)** Si va a depurar un archivo DLL de servidor ATL, escriba la dirección URL donde se encuentra el proyecto.

 Una vez escritas, esta configuración se almacena en las páginas de propiedades del proyecto, por lo que no tendrá que volver a escribirlas en las sesiones de depuración posteriores. Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores. Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, vea [Depurar archivos DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)