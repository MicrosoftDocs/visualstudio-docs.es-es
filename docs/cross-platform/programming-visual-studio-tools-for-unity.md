---
title: Programación de Visual Studio Tools para Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 48a557addca76c4be56b19890e9abdf8c9eca38d
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252445"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programa Visual Studio Tools para Unity
En esta sección encontrará ejemplos de uso de Visual Studio Tools para la API de Unity.

## <a name="examples"></a>Ejemplos
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para obtener más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Personalizar archivos de proyecto creados por VSTU](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Compartir la devolución de llamada de registro de Unity con VSTU](../cross-platform/share-the-unity-log-callback-with-vstu.md).
