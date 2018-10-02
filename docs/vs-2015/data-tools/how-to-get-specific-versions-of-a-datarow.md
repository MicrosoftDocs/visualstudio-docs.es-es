---
title: 'Cómo: obtener versiones específicas de un objeto DataRow | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567654"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Cómo: Obtener versiones específicas de una fila de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando los cambios se realizan en las filas de datos, el conjunto de datos retiene tanto la versión original (<xref:System.Data.DataRowVersion>) como las versiones nuevas (<xref:System.Data.DataRowVersion>) de la fila. Por ejemplo, antes de llamar al método `AcceptChanges`, su aplicación puede tener acceso a las distintas versiones de un registro (según se defina en la enumeración <xref:System.Data.DataRowVersion>) y procesar los cambios según corresponda.  
  
> [!NOTE]
>  Las versiones diferentes de una fila sólo existen después de que ésta haya sido revisada y antes de haber llamado al método `AcceptChanges`. Una vez que se ha llamado al método `AcceptChanges`, las versiones actual y original son iguales.  
  
 Si se pasa el valor <xref:System.Data.DataRowVersion> junto con el índice de la columna (o el nombre de la columna como cadena), se devuelve el valor de la versión de fila concreta de esa columna. La columna modificada se identifica durante los eventos <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.ColumnChanged>, por lo que es un buen momento para examinar las versiones de fila que difieran con fines de validación. Sin embargo, si ha suspendido las restricciones temporalmente, esos eventos no se provocarán y deberá identificar mediante programación qué columnas han cambiado. Para ello, recorra en iteración la colección <xref:System.Data.DataTable.Columns%2A> y compare los distintos valores de <xref:System.Data.DataRowVersion>.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Tener acceso a la versión original de un objeto DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Para obtener la versión original de un registro  
  
-   Obtenga acceso al valor de una columna que se pasa en <xref:System.Data.DataRowVersion> de la fila que desea devolver.  
  
     El ejemplo siguiente muestra cómo puede utilizar un valor <xref:System.Data.DataRowVersion> para obtener el valor original de un campo `CompanyName` en un objeto <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Tener acceso a la versión actual de un objeto DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Para obtener la versión actual de un registro  
  
-   Obtenga acceso al valor de una columna y agregue un parámetro al índice donde se indique qué versión de una fila desea que se devuelva.  
  
     El ejemplo siguiente muestra cómo puede utilizar un valor <xref:System.Data.DataRowVersion> para obtener el valor actual de un campo `CompanyName` en un objeto <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Vea también  
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)