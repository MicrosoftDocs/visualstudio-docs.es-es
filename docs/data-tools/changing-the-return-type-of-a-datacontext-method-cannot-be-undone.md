---
title: El cambio del tipo devuelto de un método DataContext no se puede deshacer
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: abec4dd6d5cded79e1f25a6dbb5ec2e55c2d444f
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282760"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>El cambio del tipo devuelto de un método DataContext no se puede deshacer

El cambio del tipo devuelto de un método DataContext no se puede deshacer. Para volver al tipo generado automáticamente, debe arrastrar el elemento de **Explorador de servidores** o **Database Explorer** en el Object Relational Designer nuevo. ¿Está seguro de que desea cambiar el tipo devuelto?

El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y haga clic en el **Return Type** propiedad en el **propiedades** ventana.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Para cambiar el tipo de valor devuelto de un método de DataContext

- Haga clic en **Sí**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Para salir del cuadro de mensaje sin modificar el tipo de valor devuelto

- Haga clic en **No**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Para revertir al tipo de valor devuelto original después de cambiar el tipo de valor devuelto

1. Seleccione el <xref:System.Data.Linq.DataContext> método en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y elimínelo.

2. Busque el elemento en **Server Explorer/Database Explorer** y arrástrelo hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto predeterminado original.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)