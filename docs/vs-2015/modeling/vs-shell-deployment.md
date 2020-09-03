---
title: Implementación de VS Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659305"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita para interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre el shell aislado de Visual Studio, vea [personalizar el shell aislado](../extensibility/customizing-the-isolated-shell.md). Puede encontrar más información sobre cómo personalizar el shell aislado en [Personalización del shell aislado](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para establecer un shell de Visual Studio como destino de implementación

1. En el proyecto **DslPackage** , Abra **source.Extension.TT**.

2. En `<SupportedProducts>` Insertar:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Reemplace *MyIsolatedShell* por el nombre del paquete de Shell aislado.
