---
title: "Cómo: guardar datos utilizando una transacción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 23cf5ee9ef7369d8c0f52adde639adad4abe3ae6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Cómo: guardar datos utilizando una transacción
Guardar datos en una transacción mediante el <xref:System.Transactions> espacio de nombres. Use la <xref:System.Transactions.TransactionScope> objeto participe en una transacción que se administra automáticamente.  
  
Los proyectos no se crean con una referencia al ensamblado System.Transactions, por ello, debe agregar manualmente una referencia a proyectos que utilizan transacciones.  
  
La manera más fácil de implementar una transacción consiste en crear una instancia de un <xref:System.Transactions.TransactionScope> objeto en un `using` instrucción. (Para obtener más información, consulte [instrucción Using](/dotnet/visual-basic/language-reference/statements/using-statement), y [instrucción using](/dotnet/csharp/language-reference/keywords/using-statement).) El código que se ejecuta dentro de la `using` instrucción participa en la transacción.  
  
Para confirmar la transacción, llame a la <xref:System.Transactions.TransactionScope.Complete%2A> bloquear el método como el uso de la última instrucción.  
  
Para revertir la transacción, produce una excepción antes de llamar a la <xref:System.Transactions.TransactionScope.Complete%2A> método.  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Para agregar una referencia a la System.Transactions.dll  
  
1.  En el **proyecto** menú, seleccione **Agregar referencia**.  
  
2.  En el **.NET** pestaña (**SQL Server** pestaña para los proyectos de SQL Server), seleccione **System.Transactions**y, a continuación, seleccione **Aceptar**.  
  
     En el proyecto se agrega una referencia a System.Transactions.dll.  
  
## <a name="to-save-data-in-a-transaction"></a>Para guardar los datos en una transacción  
  
-   Agregue código para guardar datos en el uso de la instrucción que contiene la transacción. El código siguiente muestra cómo crear y crear instancias de un <xref:System.Transactions.TransactionScope> objeto en un formulario mediante declaración:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>Vea también
[Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)  
[Tutorial: Guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md)  