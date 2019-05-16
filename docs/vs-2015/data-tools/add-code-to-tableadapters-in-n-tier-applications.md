---
title: Agregar código a TableAdapters en aplicaciones de n niveles | Documentos de Microsoft
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aa406ab366c9bfb51f506c2dbba0a8408d7ba377
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688554"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Agregar código a TableAdapters en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ampliar la funcionalidad de un `TableAdapter` mediante la creación de un archivo de clase parcial para el `TableAdapter` y agregarle código (en lugar de agregar código a la *DatasetName*. Archivo DataSet.Designer). Las clases parciales permiten código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (tipos)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 El código que define un `TableAdapter` se genera cada vez que se realizan cambios en el `TableAdapter`. Este código también se genera cuando se realizan cambios durante la ejecución de cualquier asistente que modifica la configuración de la `TableAdapter`. Para evitar que el código que se eliminen durante la regeneración de un `TableAdapter`, agregue código al archivo de clase parcial de la `TableAdapter`.  
  
 De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName*. Designer.vb (o *DatasetName*. Designer.cs) que contiene el `TableAdapter` código. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado *DatasetName*. DataSet.Designer.vb (o *DatasetName*. (DataSet.Designer.cs) que contiene el código del conjunto de datos.  
  
> [!NOTE]
> Al separar conjuntos de datos y `TableAdapter`s (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se trasladarán automáticamente. Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
> [!NOTE]
> El Diseñador de DataSet proporciona funcionalidad para generar <xref:System.Data.DataTable.ColumnChanging> y <xref:System.Data.DataTable.RowChanging> controladores de eventos cuando es necesaria la validación. Para obtener más información, consulte [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para agregar código de usuario a un TableAdapter en una aplicación de n niveles  
  
1. Busque el proyecto que contiene el archivo .xsd (el conjunto de datos).  
  
2. Haga doble clic en el **.xsd** archivo para abrir el conjunto de datos.  
  
3. Haga clic en el `TableAdapter` que desea agregar el código a y, a continuación, seleccione**ver código**.  
  
     Una clase parcial se crea y se abre en el Editor de código.  
  
4. Agregue el código dentro de la declaración de clase parcial.  
  
5. El ejemplo siguiente muestra dónde agregar código a la `CustomersTableAdapter` en el `NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)   
 [Agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Información general sobre TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Información general de la actualización jerárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)