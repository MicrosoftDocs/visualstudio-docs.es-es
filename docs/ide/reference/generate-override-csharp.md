---
title: "Generación de una invalidación - generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-c"></a>Generación de una invalidación en C# #

**Qué:** Le permite generar inmediatamente el código para cualquier método que se puede invalidar en una clase base.

**Cuándo:** Desea reemplazar un método de clase base y generar la firma automáticamente.

**Por qué:** Podría escribir la firma del método manualmente; sin embargo, esta característica generará la firma automáticamente.

**Cómo**:

1. Escriba la palabra clave **invalidación**, seguida por un espacio, donde desee insertar una firma de método invalidado y aparecerá una lista desplegable de IntelliSense.

   ![Invalidación de IntelliSense](media/override-intellisense-cs.png)

1. Seleccione el método que le gustaría invalidar en la clase base haciendo clic en él con el mouse o vaya a él con el teclado y presione **ENTRAR**.

   >[!TIP]
   >* Use el icono Propiedad ![Icono de propiedad](media/override-property-cs.png) para mostrar u ocultar las propiedades en la lista.
   >* Use el icono Método ![Icono de método](media/override-method-cs.png) para mostrar u ocultar los métodos en la lista.

1. La propiedad o el método seleccionado se agregará a la clase como una invalidación, lista para implementarse.

   ![Resultado de la invalidación](media/override-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)
