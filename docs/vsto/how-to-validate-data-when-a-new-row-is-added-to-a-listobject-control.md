---
title: Validar datos cuando se agrega una nueva fila al control ListObject
description: Obtenga información sobre cómo puede Visual Studio para validar los datos cuando se agrega una nueva fila a un control ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825724"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Cómo: Validar datos cuando se agrega una nueva fila a un control ListObject
  Los usuarios pueden agregar filas nuevas a un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazado a datos. Puede validar los datos del usuario antes de confirmar los cambios al origen de datos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Validación de datos
 Cada vez que se agrega una fila a un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a datos, se produce el evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Puede controlar este evento para realizar la validación de datos. Por ejemplo, si la aplicación requiere que solo se puedan agregar al origen de datos empleados de entre 18 y 65 años, compruebe que la edad especificada se encuentra dentro de ese intervalo antes de agregar la fila.

> [!NOTE]
> Debe comprobar siempre las entradas de los usuarios en el servidor, además del cliente. Para obtener más información, vea [Proteger aplicaciones cliente.](/dotnet/framework/data/adonet/secure-client-applications)

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Para validar datos cuando se agrega una fila nueva a un control ListObject enlazado a datos

1. Cree variables para el identificador y <xref:System.Data.DataTable> en el nivel de clase.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Cree un nuevo y agregue columnas y datos de ejemplo en el controlador de eventos de la clase (en un proyecto de nivel de documento) o de la clase (en un proyecto de <xref:System.Data.DataTable> `Startup` complemento de `Sheet1` `ThisAddIn` VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Agregue código al controlador de eventos `list1_BeforeAddDataBoundRow` para comprobar si la edad escrita está dentro del intervalo aceptable.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo de código supone que dispone de un <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Control ListObject](../vsto/listobject-control.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Asignación de columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)
