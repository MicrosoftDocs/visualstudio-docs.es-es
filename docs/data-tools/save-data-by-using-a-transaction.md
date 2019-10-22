---
title: Procedimiento para guardar datos mediante una transacción
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641313"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedimiento para guardar datos mediante una transacción

Los datos se guardan en una transacción mediante el espacio de nombres <xref:System.Transactions>. Utilice el objeto <xref:System.Transactions.TransactionScope> para participar en una transacción que se administra automáticamente.

Los proyectos no se crean con una referencia al ensamblado *System. Transactions* , por lo que debe agregar manualmente una referencia a los proyectos que usan transacciones.

La manera más sencilla de implementar una transacción consiste en crear una instancia de un objeto <xref:System.Transactions.TransactionScope> en una instrucción `using`. (Para obtener más información, vea uso de la [instrucción](/dotnet/visual-basic/language-reference/statements/using-statement)y la [instrucción using](/dotnet/csharp/language-reference/keywords/using-statement)). El código que se ejecuta dentro de la instrucción `using` participa en la transacción.

Para confirmar la transacción, llame al método <xref:System.Transactions.TransactionScope.Complete%2A> como la última instrucción del bloque using.

Para revertir la transacción, inicie una excepción antes de llamar al método <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Para agregar una referencia a System. Transactions. dll

1. En el menú **proyecto** , seleccione **Agregar referencia**.

2. En la pestaña **.net** (pestaña**SQL Server** para proyectos de SQL Server), seleccione **System. Transactions**y, después, haga clic en **Aceptar**.

     Se agrega al proyecto una referencia a *System. Transactions. dll* .

## <a name="to-save-data-in-a-transaction"></a>Para guardar datos en una transacción

- Agregue código para guardar los datos en la instrucción using que contiene la transacción. En el código siguiente se muestra cómo crear y crear una instancia de un objeto <xref:System.Transactions.TransactionScope> en una instrucción using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
- [Tutorial: Guardado de datos en una transacción](../data-tools/save-data-in-a-transaction.md)