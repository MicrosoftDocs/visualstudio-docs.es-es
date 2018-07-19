---
title: 'Cómo: guardar datos mediante el uso de una transacción'
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1c5d8d9f961db7c6560f1dd7a73f2ea62a974bac
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174223"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Cómo: guardar datos mediante el uso de una transacción
Guardar datos en una transacción mediante la <xref:System.Transactions> espacio de nombres. Use la <xref:System.Transactions.TransactionScope> objeto participe en una transacción que se administra automáticamente.

Los proyectos no se crean con una referencia a la *System.Transactions* ensamblado, por lo que deberá agregar manualmente una referencia a los proyectos que utilizan transacciones.

La manera más fácil de implementar una transacción es crear una instancia un <xref:System.Transactions.TransactionScope> objeto en un `using` instrucción. (Para obtener más información, consulte [instrucción Using](/dotnet/visual-basic/language-reference/statements/using-statement), y [instrucción Using](/dotnet/csharp/language-reference/keywords/using-statement).) El código que se ejecuta dentro de la `using` instrucción participa en la transacción.

Para confirmar la transacción, llame a la <xref:System.Transactions.TransactionScope.Complete%2A> bloquear el método como el uso de la última instrucción.

Para revertir la transacción, producir una excepción antes de llamar a la <xref:System.Transactions.TransactionScope.Complete%2A> método.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Para agregar una referencia a la System.Transactions.dll.

1.  En el **proyecto** menú, seleccione **Agregar referencia**.

2.  En el **.NET** ficha (**SQL Server** ficha para proyectos de SQL Server), seleccione **System.Transactions**y, a continuación, seleccione **Aceptar**.

     Una referencia a *System.Transactions.dll* se agrega al proyecto.

## <a name="to-save-data-in-a-transaction"></a>Para guardar los datos en una transacción

-   Agregar código para guardar los datos de uso de la instrucción que contiene la transacción. El código siguiente muestra cómo crear y crear una instancia de un <xref:System.Transactions.TransactionScope> objeto en un formulario mediante declaración:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
- [Tutorial: Guardado de datos en una transacción](../data-tools/save-data-in-a-transaction.md)