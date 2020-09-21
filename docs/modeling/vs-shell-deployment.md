---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809653"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita para interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre el shell aislado de Visual Studio, vea [personalizar el shell aislado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Para establecer un shell de Visual Studio como destino de implementación:

1. En el proyecto **DslPackage** , Abra **source.Extension.TT**.

2. En `<SupportedProducts>` Insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* por el nombre del paquete de Shell aislado.