---
title: Implementación de VS Shell
description: Obtenga información sobre cómo un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita para interactuar con el DSL y cómo debe aparecer esa solución.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361266"
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