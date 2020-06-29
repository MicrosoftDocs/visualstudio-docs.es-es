---
title: Generación de un campo y propiedad privados a partir de un constructor
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283728"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generación de un campo y propiedad privados a partir de un constructor

Esta refactorización se aplica a lo siguiente: 

- C# 

**Qué:** genere un campo o propiedad privados a partir de un constructor. 

**Cuándo:** desea agregar e inicializar rápidamente un campo o propiedad privados a partir de un constructor.

**Por qué:** la escritura de campos o propiedades privados puede llevar mucho tiempo y ser repetitiva. El uso de esta refactorización es rápido y permite que el programa sea más sólido.

## <a name="how-to"></a>Procedimiento 

1. Coloque el cursor en el nombre de parámetro dentro del constructor.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   
3. A continuación, seleccione una de las siguientes opciones:

- **Crear e inicializar campo** o **Crear e inicializar propiedad**.

   ![Generar campo privado desde constructor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vea también 

- [Refactorización](../refactoring-in-visual-studio.md)
