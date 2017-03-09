---
title: "C&#243;mo: Guardar datos utilizando una transacci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar"
  - "guardar datos, mediante transacciones"
  - "System.Transactions (espacio de nombres)"
  - "transacciones, guardar datos"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Guardar datos utilizando una transacci&#243;n
Los datos de una transacción se guardan con el espacio de nombres <xref:System.Transactions>.  Utilice el objeto <xref:System.Transactions.TransactionScope> para participar en una transacción que se administra automáticamente.  
  
 Los proyectos no se crean con una referencia al ensamblado System.Transactions, por lo que necesita agregar manualmente una referencia a proyectos que utilizan transacciones.  
  
> [!NOTE]
>  El espacio de nombres <xref:System.Transactions> se admite en Windows 2000 y posterior.  
  
 La manera más fácil de implementar una transacción es crear instancias de un objeto <xref:System.Transactions.TransactionScope> en una instrucción `using`.  Para obtener más información, vea [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement) y [using \(Instrucción\)](/dotnet/csharp/language-reference/keywords/using-statement). El código ejecutado dentro de la instrucción `using` participará en la transacción.  
  
 Para confirmar la transacción, llame al método <xref:System.Transactions.TransactionScope.Complete%2A> como la última instrucción en el bloque Using.  
  
 Para revertir la transacción, inicie una excepción antes de llamar al método <xref:System.Transactions.TransactionScope.Complete%2A>.  
  
 Para obtener más información, vea [Tutorial: Guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md).  
  
### Para agregar una referencia a la dll System.Transactions  
  
1.  En el menú **Proyecto**, elija **Agregar referencia**.  
  
2.  Seleccione **System.Transactions** en la ficha **.NET** \(ficha **SQL Server** para los proyectos SQL Server\) y haga clic en **Aceptar**.  
  
     En el proyecto se agrega una referencia a System.Transactions.dll.  
  
### Para guardar datos en una transacción  
  
-   Agregue código para guardar datos dentro de la instrucción Using que contiene la transacción.  El código siguiente muestra cómo crear y crear instancias de un objeto <xref:System.Transactions.TransactionScope> en una instrucción Using:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## Vea también  
 [Tutorial: Guardar datos en una transacción](../data-tools/save-data-in-a-transaction.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)