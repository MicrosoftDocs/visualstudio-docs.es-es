---
title: Incorporación de un parámetro a una acción rápida de método
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595870"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Incorporación de un parámetro a un método mediante una acción rápida

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** le permite agregar automáticamente un parámetro a un método, en función del uso.

**Cuándo:** necesita agregar un parámetro a un nuevo método y desea declararlo de manera adecuada y automáticamente.

**Por qué:** pudo agregar el parámetro a la declaración del método antes de llamarlo, pero esta característica lo agrega automáticamente según una llamada al método.

## <a name="how-to-use-it"></a>Cómo se usa

1. Agregue un argumento adicional a una llamada al método.

   Un ondulado rojo aparece bajo el nombre del método donde lo llamó.

2. Coloque el puntero sobre el ondulado rojo hasta que aparezca el menú Acciones rápidas. Seleccione la **flecha abajo** en el menú Acciones rápidas y luego seleccione **Agregar parámetro a [método]** .

   ![Incorporación de un parámetro a la acción rápida del método en Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > También puede acceder al menú Acciones rápidas colocando el cursor en la línea de la llamada al método y luego presionando **Ctrl**+ **.** (punto), o bien seleccionando el icono de bombilla en el margen del archivo.

   Visual Studio agrega el nuevo parámetro a la declaración del método.

> [!NOTE]
> Si tiene otras llamadas al método, podrían producir errores después de usar esta acción rápida, dado que no especifican un argumento para el parámetro recién agregado.

## <a name="see-also"></a>Vea también

- [Adición de parámetro a constructor](generate-constructor.md#addparameter)
