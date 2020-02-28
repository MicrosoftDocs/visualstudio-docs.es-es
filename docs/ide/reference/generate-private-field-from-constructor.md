---
title: Generar campo privado desde constructor
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529417"
---
# <a name="generate-private-field-from-constructor"></a>Generar campo privado desde constructor

Esta refactorización se aplica a lo siguiente: 

- C# 

**Qué:** genere un campo privado a partir de un constructor. 

**Cuándo:** quiere agregar rápidamente un campo privado a partir de un constructor.

**Por qué:** la escritura de campos privados puede llevar mucho tiempo y ser repetitiva. El uso de esta refactorización es rápido y permite que el programa sea más sólido.

## <a name="how-to"></a>Procedimiento 

1. Coloque el cursor en el nombre de parámetro dentro del constructor.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   
3. Seleccione la opción **Crear e inicializar campo**.

   ![Generar campo privado desde constructor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vea también 

- [Refactorización](../refactoring-in-visual-studio.md)
