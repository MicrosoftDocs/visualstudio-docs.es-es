---
title: Agregar comprobaciones de todos los parámetros nulos
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712737"
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
