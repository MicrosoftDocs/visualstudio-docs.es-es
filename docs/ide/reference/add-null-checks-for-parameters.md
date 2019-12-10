---
title: Agregar comprobaciones de todos los parámetros nulos
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782346"
---
# <a name="add-null-checks-for-all-parameters"></a>Agregar comprobaciones de todos parámetros nulos 

Esta refactorización se aplica a lo siguiente: 

- C# 

**Qué:** Crea y agrega instrucciones `if` que comprueban la nulidad de todos los parámetros no comprobados que aceptan valores NULL. 

**Cuándo:** Quiere agregar rápidamente comprobaciones de parámetros NULL para todos los parámetros de métodos aplicables.

**Por qué:** La tarea de escribir comprobaciones de valores NULL para muchos parámetros puede tardar mucho y ser repetitiva. El uso de esta refactorización es rápido y permite que el programa sea más sólido.  

## <a name="how-to"></a>Procedimiento 

1. Coloque el cursor en cualquier parámetro dentro del método.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Acciones rápidas y refactorizaciones](media/add-null-checks-for-all-parameters.png)
   
3. Seleccione la opción para **agregar comprobaciones de valores NULL para todos los parámetros**.

   ![Agregar comprobaciones de valores NULL para todos los parámetros](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vea también 

- [Refactorización](../refactoring-in-visual-studio.md)
