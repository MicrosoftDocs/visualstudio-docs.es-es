---
title: Incorporación de un parámetro a una acción rápida de método
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7de4c4aec07a3151332c199749bef4409966b3e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929892"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Incorporación de un parámetro a un método mediante una acción rápida

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite agregar automáticamente un parámetro a un método, en función del uso.

**Cuándo:** Necesita agregar un parámetro a un método y quiere declararlo de manera adecuada automáticamente.

**Por qué:** Podría agregar el parámetro a la declaración del método antes de llamarlo, aunque esta característica lo agrega automáticamente en función de una llamada al método.

## <a name="how-to-use-it"></a>Cómo se usa

1. Agregue un argumento adicional a una llamada al método.

   Un "ondulado" rojo aparece bajo el nombre del método donde lo llamó.

2. Coloque el puntero sobre el "ondulado" rojo hasta que aparezca el menú Acciones rápidas. Seleccione la **flecha abajo** en el menú Acciones rápidas y luego seleccione **Agregar parámetro a [método]**.

   ![Incorporación de un parámetro a la acción rápida del método en Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > También puede acceder al menú Acciones rápidas colocando el cursor en la línea de la llamada al método y luego presionando **Ctrl**+**.** O bien, seleccione el icono de bombilla en el margen del archivo.

   Visual Studio agrega el nuevo parámetro a la declaración del método.

> [!NOTE]
> Si tiene otras llamadas al método, podrían producir errores después de usar esta acción rápida, dado que no especifican un argumento para el parámetro recién agregado.

## <a name="see-also"></a>Vea también

- [Adición de parámetro a constructor](generate-constructor.md#addparameter)