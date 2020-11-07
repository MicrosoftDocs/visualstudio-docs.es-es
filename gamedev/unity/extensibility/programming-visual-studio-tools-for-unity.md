---
title: Programación de Visual Studio Tools para Unity | Microsoft Docs
description: Vea ejemplos de programación con la API de Visual Studio Tools para Unity (VSTU). Personalice archivos del proyecto creados mediante VSTU. Comparta la devolución de llamada de registro de Unity con VSTU.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c98a3cdbcece87ad5e8fbe0e91ae76f677494477
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341410"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programa Visual Studio Tools para Unity
En esta sección encontrará ejemplos de uso de la API de Visual Studio Tools para Unity.

## <a name="examples"></a>Ejemplos
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.

### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para obtener más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Ejemplo: generación de archivos de proyecto](./customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para obtener más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Ejemplo: devolución de llamada de registro](./share-the-unity-log-callback-with-vstu.md).
