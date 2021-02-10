---
title: Archivo ejecutable para sesión de depuración (Cuadro de diálogo) | Microsoft Docs
description: Para depurar un archivo DLL, debe especificar un archivo ejecutable que llame al archivo DLL. Obtenga información sobre el cuadro de diálogo que aparece cuando no se especifica ningún archivo ejecutable.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870836"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Archivo ejecutable para sesión de depuración (cuadro de diálogo)

Este cuadro de diálogo aparece si se intenta depurar un archivo DLL para el que no se ha especificado ningún archivo ejecutable. Visual Studio no puede iniciar un archivo DLL directamente, sino que inicia el archivo ejecutable especificado. Puede depurar el archivo DLL cuando lo llame el archivo ejecutable.

 **Nombre del archivo ejecutable** Escriba el nombre de la ruta de acceso a un archivo ejecutable que llama al archivo DLL que se está depurando.

 **Dirección URL del proyecto (sólo servidor ATL)** Si está depurando un archivo DLL de un servidor ATL, escriba la dirección URL en la que se puede encontrar el proyecto.

 Una vez escrito, este valor se almacena en las Páginas de propiedades del proyecto, por lo que no hace falta volver a escribirlo para las siguientes sesiones de depuración. Si necesita cambiar la configuración, puede abrir las Páginas de propiedades y cambiar los valores. Para obtener más información sobre cómo especificar un archivo ejecutable para la sesión de depuración, vea [Depuración de archivos DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)