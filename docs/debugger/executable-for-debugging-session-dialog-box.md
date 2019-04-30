---
title: Archivo ejecutable para el cuadro de diálogo de la sesión de depuración | Documentos de Microsoft
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
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849961"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Archivo ejecutable para sesión de depuración (cuadro de diálogo)

Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable. Visual Studio no puede iniciar directamente un archivo DLL. En su lugar, Visual Studio inicia el ejecutable especificado. Puede depurar la DLL cuando se llama por el archivo ejecutable.

 **Nombre del archivo ejecutable** escriba el nombre de ruta de acceso a un archivo ejecutable que llama a la DLL que se está depurando.

 **Dirección URL donde puede ser el proyecto de acceso (sólo servidor ATL)** si está depurando una DLL de servidor ATL, escriba la dirección URL donde se encuentra el proyecto.

 Una vez escrito, esta configuración se almacena en el proyecto de páginas de propiedades, por lo que no tendrá que escribirlas de nuevo para sesiones de depuración posteriores. Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores. Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, vea [Depurar archivos DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)