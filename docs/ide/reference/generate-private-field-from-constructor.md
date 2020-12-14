---
title: Generación de un campo y propiedad privados a partir de un constructor
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar un campo privado o una propiedad a partir de un constructor.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617466"
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
