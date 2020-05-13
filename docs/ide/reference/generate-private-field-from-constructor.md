---
title: Generar campo privado desde constructor
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094022"
---
# <a name="generate-private-field-from-constructor"></a>Generar campo privado desde constructor

Esta refactorización se aplica a lo siguiente: 

- C# 

- Visual Basic

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
