---
title: La propiedad participa en la Asociación
description: No se puede eliminar la propiedad porque participa en la asociación. Ver información acerca de este mensaje Object Relational Designer (Object Relational Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 99115a3c04aec71e7d000dfa4e707eacb0e28cf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866403"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>No se puede eliminar la propiedad &lt;nombre de propiedad&gt; porque participa en la asociación &lt;nombre de asociación&gt;

La propiedad seleccionada está establecida como **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.

Establezca la **propiedad de asociación** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Seleccione la línea de asociación en el Object Relational **Designer** que conecta las clases de datos indicadas en el mensaje de error.

2. Haga doble clic en la línea para abrir el cuadro de diálogo **Editor de asociaciones**.

3. Quite la propiedad de **Propiedades de la asociación**.

4. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)