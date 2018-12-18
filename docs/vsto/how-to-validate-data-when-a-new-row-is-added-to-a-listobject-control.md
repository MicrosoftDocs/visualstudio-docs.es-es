---
title: 'Cómo: validar datos cuando se agrega una nueva fila a un control ListObject'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268365"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Cómo: validar datos cuando se agrega una nueva fila a un control ListObject
  Los usuarios pueden agregar filas nuevas a un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazado a datos. Puede validar los datos del usuario antes de confirmar los cambios al origen de datos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Validación de datos  
 Cada vez que se agrega una fila a un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a datos, se produce el evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Puede controlar este evento para realizar la validación de datos. Por ejemplo, si la aplicación requiere que solo los empleados las edades comprendidas entre 18 y 65 pueden agregarse al origen de datos, compruebe que la edad escrita está dentro de ese intervalo antes de agrega la fila.  
  
> [!NOTE]  
>  Debe comprobar siempre las entradas de los usuarios en el servidor, además del cliente. Para obtener más información, consulte [proteger las aplicaciones cliente](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Para validar datos cuando se agrega una fila nueva a un control ListObject enlazado a datos  
  
1.  Cree variables para el identificador y <xref:System.Data.DataTable> en el nivel de clase.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Crear un nuevo <xref:System.Data.DataTable> y agregue columnas de ejemplo y datos en el `Startup` controlador de eventos de la `Sheet1` clase (en un proyecto de nivel de documento) o `ThisAddIn` clase (en un proyecto de complemento de VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Agregue código al controlador de eventos `list1_BeforeAddDataBoundRow` para comprobar si la edad escrita está dentro del intervalo aceptable.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Este ejemplo de código supone que dispone de un <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.  
  
## <a name="see-also"></a>Vea también  
 [Ampliar documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject (control)](../vsto/listobject-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: las columnas de mapa ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  