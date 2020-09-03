---
title: Guardar datos mediante una transacción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652831"
---
# <a name="save-data-by-using-a-transaction"></a>Guardar datos mediante una transacción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los datos se guardan en una transacción mediante el <xref:System.Transactions> espacio de nombres. Utilice el <xref:System.Transactions.TransactionScope> objeto para participar en una transacción que se administra automáticamente.

 Los proyectos no se crean con una referencia al ensamblado System. Transactions, por lo que debe agregar manualmente una referencia a los proyectos que usan transacciones.

> [!NOTE]
> El <xref:System.Transactions> espacio de nombres se admite en Windows 2000 o posterior.

 La forma más fácil de implementar una transacción es crear una instancia <xref:System.Transactions.TransactionScope> de un objeto en una `using` instrucción. (Para obtener más información, vea uso de la [instrucción](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)y la [instrucción using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3)). El código que se ejecuta dentro de la `using` instrucción participa en la transacción.

 Para confirmar la transacción, llame al <xref:System.Transactions.TransactionScope.Complete%2A> método como la última instrucción del bloque using.

 Para revertir la transacción, inicie una excepción antes de llamar al <xref:System.Transactions.TransactionScope.Complete%2A> método.

 Para obtener más información, vea [guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Para agregar una referencia a la dll de System. Transactions

1. En el menú **Proyecto**, seleccione **Agregar referencia**.

2. En la pestaña **.net** (pestaña**SQL Server** para proyectos de SQL Server), seleccione **System. Transactions**y, después, haga clic en **Aceptar**.

     Se agrega al proyecto una referencia a System.Transactions.dll.

### <a name="to-save-data-in-a-transaction"></a>Para guardar datos en una transacción

- Agregue código para guardar los datos en la instrucción using que contiene la transacción. En el código siguiente se muestra cómo crear y crear instancias <xref:System.Transactions.TransactionScope> de un objeto en una instrucción using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Consulte también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
