---
title: Programación de Visual Studio Tools para Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0811445e2dcf985aef7b6449ff3fb86c5ac9a1c8
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027385"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programa Visual Studio Tools para Unity
En esta sección encontrará ejemplos de uso de Visual Studio Tools para la API de Unity.

## <a name="examples"></a>Ejemplos
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para obtener más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Ejemplo: generación de archivos de proyecto](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para obtener más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Ejemplo: devolución de llamada de registro](../cross-platform/share-the-unity-log-callback-with-vstu.md).
