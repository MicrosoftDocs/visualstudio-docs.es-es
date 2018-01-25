---
title: "Generación de una invalidación: generación de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Generación de una invalidación en Visual Basic
**Qué:** Le permite generar inmediatamente el código para cualquier método que se puede invalidar en una clase base. 

**Cuándo:** Desea reemplazar un método de clase base y generar la firma automáticamente.  

**Por qué:** Podría escribir la firma del método manualmente; sin embargo, esta característica generará la firma automáticamente. 

**Cómo**:

1. Escriba la palabra clave **Invalidaciones**, seguida por un espacio, donde desee insertar una firma de método invalidado y aparecerá una lista desplegable de IntelliSense.

   ![Invalidación de IntelliSense](media/override-intellisense-vb.png)

1. Seleccione el método que le gustaría invalidar en la clase base haciendo clic en él con el mouse o vaya a él con el teclado y presione **ENTRAR**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. La propiedad o el método seleccionado se agregará a la clase como una invalidación, lista para implementarse.

   ![Resultado de la invalidación](media/override-result-vb.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md) 