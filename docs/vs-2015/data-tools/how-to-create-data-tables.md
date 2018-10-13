---
title: 'Cómo: crear tablas de datos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8b26bf0cfbd387f33f9f038d5927db795a8f2769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288917"
---
# <a name="how-to-create-data-tables"></a>Cómo: Crear tablas de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los datos se pueden almacenar en memoria en objetos <xref:System.Data.DataTable>. (Los conjuntos de datos están formados por objetos <xref:System.Data.DataTable>.) Normalmente crea nuevas tablas con TableAdapters utilizando el [TableAdapter Configuration Wizard](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) o arrastrando los objetos de base de datos de **Explorador de servidores** hasta la **Diseñador de Dataset** .  
  
 Las tablas de datos se crean como subproducto al crear nuevos TableAdapters en el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) también, pero también se pueden crear por separado. Crear una tabla de datos independiente arrastrando un <xref:System.Data.DataTable> objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.  
  
> [!NOTE]
>  Para crear tablas de datos mediante programación, vea [crear un objeto DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Creación de un DataTable con TableAdapter  
 Las tablas de datos con TableAdapters incluyen métodos que rellenan la tabla con datos y vuelven a escribir los cambios en la base de datos. Crea TableAdapters al ejecutar el **TableAdapter Configuration Wizard** o arrastrando los objetos de base de datos de **Explorador de servidores** hasta la **Diseñador de Dataset**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Para crear una nueva tabla de datos con TableAdapter  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**. Para obtener información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Arrastre un **TableAdapter** desde el **DataSet** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.  
  
     El **TableAdapter Configuration Wizard** se abre.  
  
3.  Complete el asistente. Para obtener más información, consulte [Asistente para configuración de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Para crear una nueva tabla de datos con un TableAdapter desde el Explorador de servidores  
  
1.  Abra el conjunto de datos en el **Diseñador de origen de datos**.  
  
2.  Arrastre un objeto de base de datos (por ejemplo, una tabla) desde **Explorador de servidores** hasta la **Diseñador de Dataset**.  
  
## <a name="creating-a-standalone-datatable"></a>Crear un DataTable independiente  
 Las tablas independientes necesitan tener la lógica `Fill` implementada para poder rellenarse con datos. Para obtener información sobre cómo rellenar tablas de datos independientes, consulte [llenar un DataSet desde un objeto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Para crear una nueva tabla de datos independiente  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**.  
  
2.  Arrastre un <xref:System.Data.DataTable> desde el **DataSet** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.  
  
3.  Agregue columnas para definir su tabla de datos. Para obtener más información, consulte [Cómo: agregar columnas a un objeto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.DataTable>   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Tutorial: Mostrar datos en un formulario de Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)